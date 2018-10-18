#自定义富途的指标

##肯特纳通道(KC)
- [Keltner Channel](http://stockcharts.com/school/doku.php?id=chart_school:technical_indicators:keltner_channels)

      TR1:MAX(MAX((HIGH-LOW),ABS(REF(CLOSE,1)-HIGH)),ABS(REF(CLOSE,1)-LOW)),COLORFF8D1E;
      ATR1:MA(TR1,SD),COLOR0CAEE6;
      
      
      MID:MA(CLOSE,SD),COLORFFAEC9;
      UPPER1:MID+(2*WIDTH*ATR1),COLORFFC90E;
      UPPER2:MID+(WIDTH*ATR1),COLORFFC90E;
      LOWER2:MID-(WIDTH*ATR1),COLOR0CAEE6;
      LOWER1:MID-(2*WIDTH*ATR1),COLOR0CAEE6;

##狄马克指标(TD)
- [Tom DeMark](https://forextraininggroup.com/introduction-tom-demark-indicators-studies/)

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
