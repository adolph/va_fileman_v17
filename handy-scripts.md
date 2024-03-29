# Handy Scripts

[Language Guide at SourceForge](https://mumps.sourceforge.net/docs.html)

Iterate over global subscripts with values:

```
>s max=10,rf=$na(^DIE)                                                                     

>f  {s rf=$q(@rf) q:(rf="")!($i(ctr)>max)  w ctr,$c(9),$q(@rf),"=""",@$q(@rf),"""",!} k ctr
1	^DIE(0,0)="S1 ENTRY^2880607^F^102012^^F"
2	^DIE(0,"DR",1,2012)=".01;1;168;210;223;277;221;224;18;15;37;38;39;16;17;19;20;21;22;23;24;25;45;26;27;28;29;30;31;32;33;34;35;36;590;401;265;266;267;268;269;270;271;355;118;119;120;78;173;272;251;252;253;254;255;256;257;258;259;260;261;262;553;611;612;"
3	^DIE(0,"DR",1,2012,1)="301;222;83;304;306;308;82;84;79;80;81;122;316;318;320;322;324;326;328;85;86;87;88;89;90;91;92;554;338;406;341;343;345;347;349;351;353;358;174;362;364;366;368;370;372;374;376;378;380;382;384;386;555;617;618;170;169;516;172;166;124;"
4	^DIE(0,"DR",1,2012,2)="171;396;407;"
5	^DIE(0,"DR",2,2012.02)=".01:2;"
6	^DIE(0,"DR",2,2012.04)=".01:2;"
7	^DIE(6,0)="OFFSTUDY^2930329^CcpEe^60060^^CcpEe"
8	^DIE(6,"DR",1,60060)=".01;1;1.5;14;16;7;8;19;20;20.5;23;5;23.2;36;"
9	^DIE(6,"DR",2,60060.016)="1;"
10	^DIE(17,0)="BACKGROUND BACKUP^2980327^Z^2001^^@"
```

Count subscripts for a global:

```
>s rf=$na(^DIE),ctr=0

>f  {s i=$o(@rf@(i)) q:i=""  s %=$i(ctr)} zw ctr
ctr=7746
```

How many subscripts for ^DIE(0)? Output them:
```
>s rf=$na(^DIE(0)),ctr=0                                     

>f  {s i=$o(@rf@(i)) q:i=""  s %=$i(ctr)} zw ctr s ctr=0     
ctr=2

>f  {s i=$o(@rf@(i)) q:i=""  s %=$i(ctr) zw i} zw ctr s ctr=0
i=0
i="DR"
ctr=2
```

Dictionary names:
```
>s rf=$na(^DIC),ctr=0

>f  {s i=$o(@rf@(i)) q:(i="")!($i(ctr)>max)  w i,$c(9),@rf@(i,0),!} k ctr
0	PROTOCOL
.2	DESTINATION^.21^79^40
.21	TEST^.21^2^2
.4	PRINT TEMPLATE
.401	SORT TEMPLATE
.402	INPUT TEMPLATE
.5	FUNCTION^.5I
.7	MUMPS OPERATING SYSTEM
1	FILE
1.1	AUDIT
```

Global Names:
```
>s rf="",ctr=0,max=10

>f  {s rf=$o(^$GLOBAL(rf)) q:(rf="")!($i(ctr)>max)  i (rf'["%q")&(rf'["CacheTemp")&(rf'["ISC.")  { w rf,$c(9),$d(@rf),$c(9),"""",$s($d(@rf)#2=1:@rf,1:""),"""",!}} k ctr
^%ET	11	""
^%ZIS	11	"0"
^%ZMED	11	""
^%ZOSF	11	""
^%ZRTL	10	""
^%ZSIGN	10	""
^%ZTMS	11	""
^%ZTSCH	11	""
^%ZTSK	11	""
^%ZUA	11	""
```