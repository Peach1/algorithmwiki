The Area of a Triangle (2D/3D)
======

// Formula to find the area of any 2D or 3D triangle
function TriangleArea(vec3 v1, vec3 v2, vec3 v3) returns double
{
  double a = v1.dist(v2);
  double b = v2.dist(v3);
  double c = v3.dist(v1);
  
  double p = (a+b+c)/2.0; // yes divide by 2
  
  double areasquared = p*(p-a)*(p-b)*(p-c);
  
  if (areasquared < 0)
    return 0;
  
  return sqrt(areasquared);
}