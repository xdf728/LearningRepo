## Digital Image Homework 2

[toc]

> 10185101210 陈俊潼

原矩阵为：

     1     2     7     9     4     3
     0     1     6     8     3     2
     7     6    15    18     9     8
     1     2     7     9     4     3
     1     2     7     9     4     3
### Sobel 算子

Gx 运算结果：

     1     8    21    25    16     7
    16    22    29    31    24    15
     3     4     4     4     4     3
     -16   -22   -29   -31   -24   -15
     -4   -12   -25   -29   -20   -10
Gy 运算结果：

     5    18    21    -9   -18   -11
    10    26    33   -15   -28   -19
    15    28    38   -18   -32   -25
    12    26    33   -15   -28   -21
     6    18    21    -9   -18   -12
二者累计，运算$\sqrt{Gx^2 + Gy^2}$ 得：

    5.0990   19.6977   29.6985   26.5707   24.0832   13.0384
    18.8680   34.0588   43.9318   34.4384   36.8782   24.2074
    15.2971   28.2843   38.2099   18.4391   32.2490   25.1794
    20.0000   34.0588   43.9318   34.4384   36.8782   25.8070
    7.2111   21.6333   32.6497   30.3645   26.9072   15.6205
### Prewitt 算子

Gx 运算结果：

    1	7	15	17	13	5
    10	18	21	22	19	10
    2	3	3	3	3	2
    -10	-18	-21	-22	-19	-10
    -3	-10	-18	-20	-16	-7

Gy 运算结果：

    3	12	14	-6	-12	-7
    9	20	26	-12	-22	-16
    9	20	26	-12	-22	-16
    10	20	26	-12	-22	-17
    4	12	14	-6	-12	-8

二者累计，运算$\sqrt{Gx^2 + Gy^2}$ 得：

```
3.1623   13.8924   20.5183   18.0278   17.6918    8.6023
13.4536   26.9072   33.4215   25.0599   29.0689   18.8680
9.2195   20.2237   26.1725   12.3693   22.2036   16.1245
14.1421   26.9072   33.4215   25.0599   29.0689   19.7231
5.0000   15.6205   22.8035   20.8806   20.0000   10.6301
```

### Sobel 算子

Gx 运算结果：

    0	-4	-1	6	2	3
    -6	-14	-12	-1	-5	2
    5	-1	6	14	6	8
    -1	-5	-2	5	1	3
    1	2	7	9	4	3

Gy 运算结果：

    2	6	3	-4	0	-2
    -6	0	-7	-15	-7	-8
    5	13	11	0	4	-3
    1	5	2	-5	-1	-3
    2	7	9	4	3	0

二者累计，运算$\sqrt{Gx^2 + Gy^2}$ 得：

```
2.0000    7.2111    3.1623    7.2111    2.0000    3.6056
8.4853   14.0000   13.8924   15.0333    8.6023    8.2462
7.0711   13.0384   12.5300   14.0000    7.2111    8.5440
1.4142    7.0711    2.8284    7.0711    1.4142    4.2426
2.2361    7.2801   11.4018    9.8489    5.0000    3.0000
```

### 附录：

Matlab 代码如下：

```matlab
t  = [1   2    7   9   4    3
0   1    6   8   3   2
7   6   15  18   9   8
1   2    7   9   4   3
1   2    7   9   4   3]

%% Sobel
sx = [-1,0,1;-2,0,2;-1,0,1];
sy = sx'
Sx = filter2(sx, t); 
Sy = filter2(sy, t);
S = sqrt(Sx.^2 + Sy.^2)

%% Prewitt
px = [-1,0,1;-1,0,1;-1,0,1];
py = sx'
Px = filter2(px, t); 
Py = filter2(py, t);
P = sqrt(Px.^2 + Py.^2)

%% Roberts
rx = [1,0;0,-1];
ry = [0,1;-1,0];
Rx = filter2(rx, t); 
Ry = filter2(ry, t);
R = sqrt(Rx.^2 + Ry.^2)
```

$$

$$

- a
- b
- c
- d