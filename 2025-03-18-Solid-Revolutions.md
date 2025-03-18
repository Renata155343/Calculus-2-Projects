# Solids of Revolution
I chose the function $$Arccos(x)$$ with a domain from -1 to 1. I then rotated my graph around the x-axis to create a solid of revolution.  
**Here is my code for the function:**
```mathematica
(*Define the function,range,and number of disks*)f[x_] := ArcCos[x];
a = -1;
b = 1;
n = 20; (*Increase n for a finer approximation*)

(*Generate the disks*)
disks = Table[
      With[{x = a + (i - 0.5)*((b - a)/n), 
          r = f[a + (i - 0.5)*((b - a)/n)]}, {Cylinder[{{x, 0, 
                0}, {x + (b - a)/n, 0, 0}}, r]}], {i, 1, n}];

(*Combine the disks into one graphics object*)
solid = Graphics3D[Flatten@disks, Axes -> True, Boxed -> True];
```

**Here is the digital mathematical modeling of my function with 20 sub-intervals:**  

<img width="260" alt="image" src="https://github.com/user-attachments/assets/5151aec4-04c4-42c3-80f7-2589281e80bb" />


I then modeled my function to create the exact revolution.  
**Here is my code:**
```mathematica
T = RevolutionPlot3D[ArcCos[t], {t, -1, 1}, 
   RevolutionAxis -> {1, 0, 0}];
   ```

**Here is the model of that exact rotation:**  

<img width="251" alt="image" src="https://github.com/user-attachments/assets/5ac8dfe1-354f-4c11-ba33-f5e1ac348814" />
