
##均线
- [EMA_MA]()

###参数



###代码

      //@version=4
      study(title="Moving Average", shorttitle="EMA_MA", overlay=true)
      len3 = input(3, minval=1, title="Length")
      len5 = input(5, minval=1, title="Length")
      len8 = input(8, minval=1, title="Length")
      len13 = input(13, minval=1, title="Length")
      len20 = input(20, minval=1, title="Length")
      len21 = input(21, minval=1, title="Length")
      len34 = input(34, minval=1, title="Length")
      len36 = input(36, minval=1, title="Length")
      len50 = input(50, minval=1, title="Length")
      len55 = input(55, minval=1, title="Length")
      len90 = input(90, minval=1, title="Length")
      len200 = input(200, minval=1, title="Length")
      src = input(close, title="Source")
      plot(ema(src, len3), title="EMA3", color=#008792)
      plot(sma(src, len5), title="SMA5", color=#f36c21)
      plot(ema(src, len8), title="EMA8", color=color.yellow)
      plot(ema(src, len13), title="EMA13", color=#87481f)
      plot(ema(src, len20), title="SMA20", color=#375830)
      plot(ema(src, len21), title="EMA21", color=color.green)
      plot(ema(src, len34), title="EMA34", color=#78a355)
      plot(ema(src, len36), title="SMA36", color=#d1c7b7)
      plot(sma(src, len50), title="SMA50", color=#a1a3a6)
      plot(ema(src, len55), title="EMA55", color=color.blue)
      plot(sma(src, len90), title="SMA90", color=#f2eada,linewidth=3)
      plot(sma(src, len200), title="SMA200", color=color.red,linewidth=3)



##RSI5
- [RSI5]()

###参数



###代码

      //@version=4
      study(title="Relative Strength Index", shorttitle="RSI5", format=format.price, precision=2)
      rsisrc = close, rsilen = input(5, minval=1, title="Length")
      up = rma(max(change(rsisrc), 0), rsilen)
      down = rma(-min(change(rsisrc), 0), rsilen)
      rsi = down == 0 ? 100 : up == 0 ? 0 : 100 - (100 / (1 + up / down))
      prsi=plot(rsi, color=color.purple)
      band5 = hline(80,title="80",color=#d71345)
      band4 = hline(70,title="70",color=#f05b72)
      band3 = hline(50,title="50")
      band2 = hline(30,title="30",color=#45b97c)
      band1 = hline(20,title="20",color=#1d953f)
      
      
      fill(band4,band2, color=color.purple, transp=90)
      
      
      //oversold = rsi < 30
      //overbought = rsi > 70
      //barcolor(oversold? #7fff00 : overbought? color.red : na )
      
      level_70 = 70
      level_70rsi = rsi > level_70 ? rsi : level_70
      level_30 = 30
      level_30rsi = rsi < 30 ? rsi : level_30
      
      
      
      p1 = plot(series=level_70, color=color.red, linewidth=1, transp=100)
      p2 = plot(series=level_70rsi, color=color.red, linewidth=1, transp=100)
      p3 = plot(series=level_30, color=color.green, linewidth=1, transp=100)
      p4 = plot(series=level_30rsi, color=color.green, linewidth=1, transp=100)
      fill(p1, p2, color=color.red, transp=50)
      fill(p3, p4, color=#7fff00, transp=50)

##Boll
- [Boll]()

###参数



###代码

      //@version=4
      study(shorttitle="BB_EMA", title="Bollinger Bands", overlay=true)
      length56 = input(56, minval=1)
      bbsrc = input(close, title="Source")
      mult = input(2.0, minval=0.001, maxval=50)
      basis56 = sma(bbsrc, length56)
      dev56 = mult * stdev(bbsrc, length56)
      upper56 = basis56 + dev56
      lower56 = basis56 - dev56
      plot(basis56, color=color.blue)
      p156 = plot(upper56, color=color.blue)
      p256 = plot(lower56, color=color.blue)
      fill(p156, p256 ,color=color.blue, transp=90)
      
      length14 = input(14, minval=1)
      basis14 = sma(bbsrc, length14)
      dev14 = mult * stdev(bbsrc, length14)
      upper14 = basis14 + dev14
      lower14 = basis14 - dev14
      plot(basis14, color=color.green)
      p114 = plot(upper14, color=color.green)
      p214 = plot(lower14, color=color.green)
      fill(p114, p214, color=color.green, transp=90)
      
      
      
      
      
      emalen5 = input(5, minval=1, title="Length")
      emalen13 = input(13, minval=1, title="Length")
      emasrc = input(close, title="Source")
      plot(ema(emasrc, emalen5), title="EMA", color=color.yellow)
      plot(ema(emasrc, emalen13), title="EMA", color=color.red)













