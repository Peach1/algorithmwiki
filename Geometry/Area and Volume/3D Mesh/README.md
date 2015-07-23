Volume of 3D Triangle Mesh
===============

This algorithm can be used on any 3D mesh that is composed of triangles.
A mesh that uses n-gons or quads would have to be converted to a triangle mesh before this algorithm can be used on it.
The mesh topology should be water tight(no holes) for the most accurate result

```typescript
function SignedVolumeOfTriangle(vec3 p1, vec3 p2, vec3 p3) returns float
{
    float v321 = p3.x*p2.y*p1.z;
    float v231 = p2.x*p3.y*p1.z;
    float v312 = p3.x*p1.y*p2.z;
    float v132 = p1.x*p3.y*p2.z;
    float v213 = p2.x*p1.y*p3.z;
    float v123 = p1.x*p2.y*p3.z;
    return (1.0f/6.0f)*(-v321 + v231 + v312 - v132 - v213 + v123);
}

function VolumeOfMesh(Mesh mesh) returns float
 {
    float volumesum = 0;
    for(int i = 0; i < mesh.Triangles.length(); i++)
    {
        volumesum += SignedVolumeOfTriangle(t.a, t.b, t.c);
    }
    return fabs(volumesum); // floating point absolute value
}
```
