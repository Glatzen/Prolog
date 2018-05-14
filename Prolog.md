% Autor:
% Datum: 14.05.2018

varcons(X,s(o)):- const(X).
varcons(X,s(o)):- vari(X).
varcons(g(Xb),N):- varcons(Xb,N).
varcons(f(X1b, X2b),N):- varcons(X1b,N1),varcons(X2b,N2),add(N1,N2,N).
varcons(h(X1b, X2b, X3b),N):- varcons(X1b,N1),varcons(X2b,N2), varcons(X3b,N3),add(N1,N2,H), add(H,N3,N).

functs(X,o):- const(X).
functs(X,o):- vari(X).
functs(g(Xb),s(N)):- functs(Xb,N).
functs(f(X1b, X2b),s(N)):- functs(X1b,N1), functs(X2b,N2),add(N1,N2,N).
functs(h(X1b, X2b, X3b),s(N)):- functs(X1b,N1), functs(X2b,N2), functs(X3b,N3),add(N1,N2,H), add(H,N3,N).


height(X,o):- const(X).
height(X,o):- vari(X).
height(g(Xb),s(N)):- height(Xb,N).
height(f(X1b, X2b),s(N)):- height(X1b,N1), height(X2b,N2),add(N1,N2,N).
height(h(X1b, X2b, X3b),s(N)):- height(X1b,N1), height(X2b,N2), height(X3b,N3),max(N1,N2,H), max(H,N3,N).

invList([]).
invList([0]).
invList([X|[Y|Rs]]):- invList([Y|RS]), X is Y + 1.
