---
layout: post
title: "Fox Ears Water Shader"
modified:
categories: 
excerpt: "How our water shader works for Fox Ears in Unity."
tags: [ggj15, fox, ears, terrain, low poly, shaders]
image:
  feature: foxears/water-shader/banner.png
date: 2015-02-17T21:26:15-05:00
---

One of the parts of Fox Ears I personally was really happy with after the jam was the water. It definitely needed to be cleaned up, but we had a solid base in place to work with. In this post I outline how the shader that drives our water works.

### Overview

<figure>
	<a href="../images/foxears/water-shader/flat-water.png"><img src="../images/foxears/water-shader/flat-water.png"></a>
</figure>

The image above shows our water as it looks in editor. For the most part, it's a simple plane (as outlined in <a href="../terrain-generation-in-fox-ears/">this post</a>). All of the magic happens in its shader. Before we get into the shader code, however, we need to generate some additional information for the shader and store it in our water mesh. Let's take a look at the **LowPolyWater** class, which extends **LowPolyTerrain**:

{% highlight c# %}
using UnityEngine;
using System.Collections;

[System.Serializable]
public class LowPolyWater : LowPolyTerrain {

	public override void GenerateMesh() {
		GenerateUniqueID();
		mesh = new Mesh();
		mesh.name = "Low Poly Water Plane";
		GetComponent<MeshFilter>().mesh = mesh;

		mesh.vertices = GenerateVertices();
		mesh.uv = GenerateUVs();
		GenerateUVOffsets();
		mesh.triangles = GenerateTriangles();
		mesh.normals = GenerateNormals();
	}

	void GenerateUVOffsets() {
		Vector3[] faceInfo = new Vector3[mesh.vertices.Length];
		int index = 0;
		for (int i = 0; i < (widthInVerts-1)*(lengthInVerts-1); i++) {
			faceInfo[index++] = new Vector3(0, 0, 0);
			faceInfo[index++] = new Vector3(0, 1, 0);
			faceInfo[index++] = new Vector3(0, 3, 0);

			faceInfo[index++] = new Vector3(1, 3, 0);
			faceInfo[index++] = new Vector3(1, 1, 0);
			faceInfo[index++] = new Vector3(1, 2, 0);
		}

		Vector2[] v1s = new Vector2[mesh.vertices.Length];
		Vector4[] v2s = new Vector4[mesh.vertices.Length];
		for (int i = 0; i < v1s.Length; i++) {
			if (faceInfo[i].x == 0) {
				if (faceInfo[i].y == 0) {
					v1s[i] = mesh.uv[i + 2];
					v2s[i] = mesh.uv[i + 1];
				} else if (faceInfo[i].y == 1) {
					v1s[i] = mesh.uv[i - 1];
					v2s[i] = mesh.uv[i + 1];
				} else if (faceInfo[i].y == 3) {
					v1s[i] = mesh.uv[i - 1];
					v2s[i] = mesh.uv[i - 2];
				}
			} else {
				if (faceInfo[i].y == 3) {
					v1s[i] = mesh.uv[i + 2];
					v2s[i] = mesh.uv[i + 1];
				} else if (faceInfo[i].y == 1) {
					v1s[i] = mesh.uv[i - 1];
					v2s[i] = mesh.uv[i + 1];
				} else if (faceInfo[i].y == 2) {
					v1s[i] = mesh.uv[i - 1];
					v2s[i] = mesh.uv[i - 2];
				}
			}
		}

		mesh.uv2 = v1s;
		mesh.tangents = v2s;

	}
}

{% endhighlight %}