# Riemann Sums
The unique function I chose for this project was $$e^x$$. I modeled it in Mathematica by editing the template function for a left Riemann sum to include my function and then plotted it with various n values to show how the accuracy increased as more rectangles were created.  
Here is a sample of my code for 3 subintervals (n=3):  
```
LeftRiemannSum3DPositive[f_, {a_?NumericQ, b_?NumericQ}, n_Integer?Positive, thickness_?Positive, plotFunction_ : True] := 
  Module[{dx, cuboids, funcPlot, combinedPlot},
   If[b <= a, Return[$Failed, Module]];
   dx = (b - a)/n;
   cuboids = 
    Table[{Opacity[0.5], Blue, 
      Cuboid[{a + i*dx, 0, 0}, {a + (i + 1)*dx, thickness, 
        f[a + i*dx]}]}, {i, 0, n - 1}];
   funcPlot = 
    Plot3D[f[x], {x, a, b}, {y, 0, thickness}, 
     PlotStyle -> Opacity[0.3], Mesh -> None, 
     AxesLabel -> {"x", "y (thickness)", "z (f(x))"}];
   combinedPlot = 
    If[TrueQ[plotFunction], 
     Show[funcPlot, Graphics3D[cuboids], PlotRange -> All, 
      BoxRatios -> {1, 0.1, 1}], 
     Show[Graphics3D[cuboids], PlotRange -> All, 
      BoxRatios -> {1, 0.1, 1}]];
   combinedPlot];
   
myPlot = LeftRiemannSum3DPositive[Exp, {0, 2}, 3, 0.1, False];
Show[myPlot]
(* If you installed Mathematcia on your computer *)
Export["sinPlot1.stl", myPlot];
(* If you use mathematica online *)
CloudExport[myPlot, "STL", CloudObject["ExpPlot1.stl"]]
```
After creating my graph, I uploaded it to BambuStudio and increased its size to reasonable proportions.  
Then, after downloading Fusion 360, I designed the base with slits to hold my function inserts. I also embedded the name of my function onto the base for increased identification and clarity.  

Here is my function modeled with left Riemann sums in Bambu:  
<img width="519" alt="Screenshot 2025-02-24 at 1 11 15 PM" src="https://github.com/user-attachments/assets/82c277b6-12fd-44ae-98f7-10bfd3a43c9b" />

And here is my base modeled in Fusion:
<img width="950" alt="Screenshot 2025-02-24 at 1 13 16 PM" src="https://github.com/user-attachments/assets/e4a4f7cb-1abf-4268-b45a-41271d77ccb0" />
