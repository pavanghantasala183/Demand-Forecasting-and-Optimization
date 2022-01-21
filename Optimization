proc optmodel;

var w11 >= 25000;
var w12 >= 25000;
var w13 >= 25000;
var w14 >= 25000;

var w21 >= 0;
var w22 >= 0;
var w23 >= 0;
var w24 >= 0;

/*Environmental Body Constraints*/
con w21 >= 0.25*(w11+w21);
con w22 >= 0.25*(w12+w22);
con w23 >= 0.25*(w13+w23);
con w24 >= 0.25*(w14+w24);

/*Forecast Constraints*/
con w11+w21 >= 54172.24337;
con w12+w22 >= 54223.41891;
con w13+w23 >= 53514.75712;
con w14+w24 >= 53675.53614;

/*Storage Tank Constraints*/
con 62500 + 12000 - w21 >= 30000;
con 62500 + 12000 - w21 + 18000 - w22 >= 30000;
con 62500 + 12000 - w21 + 18000 - w22 + 20000 - w23 >= 30000;
con 62500 +12000 - w21 + 18000 - w22 + 20000 - w23 + 22000 - w24 >= 30000;

/*Objective Function*/
min cost = ((w11+w12+w13+w14)*0.15 + (w21+w22)*0.18 + (w23+w24)*0.10);

solve;

/*print the optimal parameters*/
print cost;

print w11; 
print w12; 
print w13; 
print w14;

print w21;
print w22;
print w23;
print w24;

quit;
/*******************************************************************************************/

proc optmodel;

var w11 >= 30000;
var w12 >= 30000;
var w13 >= 30000;
var w14 >= 30000;

var w21 >= 0;
var w22 >= 0;
var w23 >= 0;
var w24 >= 0;


/*Environmental Body Constraints*/
con w21 >= 0.25*(w11+w21);
con w22 >= 0.25*(w12+w22);
con w23 >= 0.25*(w13+w23);
con w24 >= 0.25*(w14+w24);

/*Forecast Constraints*/
con w11+w21 >= 54172.24337;
con w12+w22 >= 54223.41891;
con w13+w23 >= 53514.75712;
con w14+w24 >= 53675.53614;

/*Storage Tank Constraints*/
con 62500 + 12000 - w21 >= 30000;
con 62500 + 12000 - w21 + 18000 - w22 >= 30000;
con 62500 + 12000 - w21 + 18000 - w22 + 20000 - w23 >= 30000;
con 62500 +12000 - w21 + 18000 - w22 + 20000 - w23 + 22000 - w24 >= 30000;

/*Objective Function*/
min cost = ((w11+w12+w13+w14)*0.12 + (w21+w22)*0.18 + (w23+w24)*0.10);

solve;

/*print the optimal parameters*/
print cost;

print w11; 
print w12; 
print w13; 
print w14;

print w21;
print w22;
print w23;
print w24;

quit;
