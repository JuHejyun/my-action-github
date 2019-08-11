#自定义富途的指标

##肯特纳通道(KC)
- [Keltner Channel](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:keltner_channels)

###参数

      0<SD<120 def=20
      2<WIDTH<20 def=2

###代码

      TR1:MAX(MAX((HIGH-LOW),ABS(REF(CLOSE,1)-HIGH)),ABS(REF(CLOSE,1)-LOW));
      ATR1:MA(TR1,SD);
      
      
      MID:MA(CLOSE,SD),COLORFFAEC9;
      UPPER1:MID+(2*WIDTH*ATR1),COLORFFC90E;
      UPPER2:MID+(WIDTH*ATR1),COLORFFC90E;
      LOWER2:MID-(WIDTH*ATR1),COLOR0CAEE6;
      LOWER1:MID-(2*WIDTH*ATR1),COLOR0CAEE6;


##成交量加权平均价(VWAP)
- [VWAP](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:vwap_intraday)

###参数

      0<D<20 def=20
      2<WIDTH<20 def=2

###代码

      VM:=VOL*((HIGH+LOW+CLOSE)/3);
      VWSUM:=SUM(VM,D);
      VOLSUM:=SUM(VOL,D);
      VWAP:VWSUM/VOLSUM,COLORLIGREEN;
      STV:=STD(VWAP,D);
      
      
      UPPER: VWAP + STV*WIDTH,COLORFFC90E;
      LOWER: VWAP-STV*WIDTH,COLOR0CAEE6;





##狄马克指标(TD)
- [Tom DeMark](https://forextraininggroup.com/introduction-tom-demark-indicators-studies/)

###参数

      0<P1<1000 def=5
      0<P2<1000 def=10
      0<P3<1000 def=20
      0<P4<1000 def=50

###代码

      MA1:MA(CLOSE,P1),COLORFF8D1E;
      MA2:MA(CLOSE,P2),COLOR0CAEE6;
      MA3:MA(CLOSE,P3),COLORE970DC;
      MA4:MA(CLOSE,P4),COLOR0080FF;
      A1:=C>REF(C,4);
      NT:=BARSLASTCOUNT(A1);
      TJ11:=NT=9;
      TJ13:=ISLASTBAR AND BETWEEN(NT,1,8);
      AY:=(BACKSET(TJ11>0,9) OR BACKSET(TJ13>0,NT))*NT;
      DRAWNUMBER(AY>0,H+(H-L)*0.2,AY),COLORFF00FF;
      DRAWTEXT(NT=9,H+(H-L)*0.2,'9'),COLORGREEN;
      B1:=C<REF(C,4);
      NT0:=BARSLASTCOUNT(B1);
      TJ21:=NT0=9 ;
      TJ23:=ISLASTBAR AND BETWEEN(NT0,1,8);
      AY1:=(BACKSET(TJ21>0,9)  OR  BACKSET(TJ23>0,NT0))*NT0;
      DRAWNUMBER(AY1>0,L-(H-L)*0.2,AY1),COLORFF00FF;
      DRAWTEXT(NT0=9,L-(H-L)*0.2,'9'),COLORGREEN;




##相对强弱指标(RSI5)
- [Relative Strength Index (RSI)](https://school.stockcharts.com/doku.php?id=technical_indicators:relative_strength_index_rsi)

###参数

      2<P1<120 def=5

###代码

      LC:=REF(CLOSE,1);
      TEMP1:=MAX(CLOSE-LC,0);
      TEMP2:=ABS(CLOSE-LC);
      RSI5:SMA(TEMP1,P1,1)/SMA(TEMP2,P1,1)*100,COLORFF8D1E;
      FILLRGN(RSI5,30,RSI5<=30),COLORGREEN;
      FILLRGN(70,RSI5,RSI5>=70),COLORRED;
      
      LINE1:70,COLORLIRED,DOTLINE;
      LINE2:80,COLORRED,DOTLINE;
      LINE3:30,COLORLIGREEN,DOTLINE;
      LINE4:20,COLORGREEN,DOTLINE;
      LINE5:50,COLORWHITE,DOTLINE;




##指数平滑移动平均线(MACD)
- [MACD (Moving Average Convergence/Divergence Oscillator)](https://school.stockcharts.com/doku.php?id=technical_indicators:moving_average_convergence_divergence_macd)

###参数

      2<SHORT<200 def=12
      2<LONG<200 def=26
      2<M<200 def=9

###代码

      DIF:EMA(CLOSE,SHORT)-EMA(CLOSE,LONG),COLORFF8D1E;
      DEA:EMA(DIF,M),COLOR0CAEE6;
      MACD:=(DIF-DEA)*2;
      STICKLINE(MACD>0 AND MACD>=REF(MACD,1),0,MACD,0.2,0),COLOR45B97C;
      STICKLINE(MACD>0 AND MACD<REF(MACD,1),0,MACD,0.2,0),COLOR005831;
      STICKLINE(MACD<0 AND MACD>=REF(MACD,1),0,MACD,0.2,0),COLOR54211D;
      STICKLINE(MACD<0 AND MACD<REF(MACD,1),0,MACD,0.2,0),COLORF15B6C;



##BCH
- []()

###参数

      0<P1<1000 def=13
      0<P2<1000 def=26
      0<P3<1000 def=55
      0<P4<1000 def=110
      0<SD<120 def=56
      0<WIDTH<100 def=2

###代码

      EMA13:EMA(CLOSE,P1),COLORFF8D1E;
      EMA26:EMA(CLOSE,P2),COLOR0CAEE6;
      MA50:MA(CLOSE,P3),COLOR954FFF;
      MA200:MA(CLOSE,P4),LINETHICK3,COLOR808080;
      
      
      DIS:=STDP(CLOSE,SD);
      MID:=MA(CLOSE,SD);
      UPPER:MID+WIDTH*DIS,DOTLINE,COLORFFC90E;
      LOWER:MID-WIDTH*DIS,DOTLINE, COLORFFC90E;





