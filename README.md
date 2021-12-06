p := 3;
m := 8;
F<w> := GF(p^m);
i:=0;
C :=[];
weight := function(a)
    e:= 0;
    for i in a do
        if i ne 0 then
          e := e + 1;
        end if;  
    end for;
    return e;
end function;
D :=[];
v := 0;
dist := [];
for i in F do
    x := i;
    if x ne 0 and Trace(w*x^4+w^816*x^2) eq 0 then
        v := v + 1;
        D[v] := x;
    end if;
end for;
n := v;
D;
z := 0;
for i in F do
    x := i;
    for j in [1..n] do
        C[j] := Trace(D[j] * x ,GF(p));
    end for;
    if weight(C) notin dist then 
        z := z + 1;
        dist[z] := weight(C);
    end if;
end for;
dist;
