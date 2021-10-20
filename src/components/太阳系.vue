<template>
  <!-- <div class="css-demo" data-title="太阳系图"> -->
  <div class="solar-syst">
    <div class="planet sun"></div>
    <div class="planet mercury"></div>
    <div class="planet venus"></div>
    <div class="planet earth"></div>
    <div class="planet mars"></div>
    <div class="planet jupiter"></div>
    <div class="planet saturn"></div>
    <div class="planet uranus"></div>
    <div class="planet neptune"></div>
    <div class="planet pluto"></div>
    <div class="planet asteroids-belt"></div>
    <!-- </div> -->
  </div>
</template>
<style lang="scss" scoped>
$sun: 40px; // 太阳大小
$mercury-orbital: 70px;
$mercury-planet: 4px; //水星轨道和星球半径
$venus-orbital: 100px;
$venus-planet: 8px; //金星轨道和星球半径
$earth-orbital: 145px;
$earth-planet: 6px; //地球轨道和星球半径
$mars-orbital: 190px;
$mars-planet: 6px; //火星轨道和星球半径
$jupiter-orbital: 340px;
$jupiter-planet: 18px; //木星轨道和星球半径
$saturn-orbital: 440px;
$saturn-planet: 12px; //土星轨道和星球半径
$uranus-orbital: 520px;
$uranus-planet: 10px; //天王星轨道和星球半径
$neptune-orbital: 630px;
$neptune-planet: 10px; //水星轨道和星球半径
$pluto-orbital: 780px;
$pluto-planet: 3px; //水星轨道和星球半径

$asteroids-belt-orbital: 300px;
$asteroids-belt-planet: 210px; // 小行星带

$year-in-second: 30; // 30s = 地球一年

@function revolution($pl-year-in-days) {
  @return $pl-year-in-days * $year-in-second / 365 + s;
}

@function alphaRandom() {
  @return random(1000) * 0.001;
}

// 随机生成num个星星
@function stars($num, $max-area, $min-area: 0, $star-size: 0) {
  $stars: #{$min-area + random($max-area)}px #{$min-area + random($max-area)}px
    0 #{$star-size}px rgba(255, 255, 255, alphaRandom());
  @for $i from 1 to $num {
    $stars: "#{$stars}, #{$min-area + random($max-area)}px #{$min-area + random($max-area)}px 0 #{$star-size}px rgba(255,255,255, #{alphaRandom()})";
  }
  @return unquote($stars);
}
@keyframes rolate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(-360deg);
  }
}
html,
body {
  width: 100%;
  height: 100%;
}

.solar-syst {
  position: relative;
  height: 100vh;
  background: radial-gradient(ellipse at bottom, #1c2837 0%, #050608 100%);
  overflow: hidden;
  &:after {
    content: "";
    position: absolute;
    top: -2px;
    width: 2px;
    height: 2px;
    border-radius: 100px;
    background: #fff;
    box-shadow: stars(500, 1800);
  }
  .planet {
    position: absolute;
    top: 50%;
    left: 50%;
    border-radius: 1000px;
    z-index: 999;
    &:not(.sun) {
      border: 1px solid rgba(102, 166, 229, 0.12);
      &::before {
        content: "";
        position: absolute;
        border-radius: 100px;
        left: 50%;
      }
    }
  }
}

// 太阳
.sun {
  background: linear-gradient(
    #ffd000 1%,
    #e06317 40%,
    #f9b700 70%,
    #f9b700 100%
  );
  width: $sun;
  height: $sun;
  margin-top: -$sun / 2;
  margin-left: -$sun / 2;
  box-shadow: 0 0 10px 2px rgba(255, 107, 0, 0.4),
    0 0 22px 11px rgba(255, 203, 0, 0.13);
}

// 水星
.mercury {
  width: $mercury-orbital;
  height: $mercury-orbital;
  margin-top: -$mercury-orbital / 2;
  margin-left: -$mercury-orbital / 2;
  animation: rolate revolution(87.5) linear infinite;
  &::before {
    width: $mercury-planet;
    height: $mercury-planet;
    margin-top: -$mercury-planet / 2;
    margin-left: -$mercury-planet / 2;
    background: #9f5e26;
  }
}

// 金星
.venus {
  width: $venus-orbital;
  height: $venus-orbital;
  margin-top: -$venus-orbital / 2;
  margin-left: -$venus-orbital / 2;
  animation: rolate revolution(224.7) linear infinite;
  &::before {
    width: $venus-planet;
    height: $venus-planet;
    margin-top: -$venus-planet / 2;
    margin-left: -$venus-planet / 2;
    background: #beb768;
  }
}

// 地球
.earth {
  width: $earth-orbital;
  height: $earth-orbital;
  margin-top: -$earth-orbital / 2;
  margin-left: -$earth-orbital / 2;
  animation: rolate revolution(365) linear infinite;
  &::before {
    height: $earth-planet;
    width: $earth-planet;
    background: #11abe9;
    margin-top: -$earth-planet / 2;
    margin-left: -$earth-planet / 2;
  }
  //月亮
  &::after {
    content: "";
    position: absolute;
    top: 0px;
    left: 50%;
    width: 18px;
    height: 18px;
    margin-left: -9px;
    margin-top: -9px;
    border-radius: 100px;
    box-shadow: 0 -10px 0 -8px grey;
    animation: rolate revolution(27) linear infinite;
  }
}

// 火星
.mars {
  width: $mars-orbital;
  height: $mars-orbital;
  margin-top: -$mars-orbital / 2;
  margin-left: -$mars-orbital / 2;
  animation: rolate revolution(687) linear infinite;
  &::before {
    width: $mars-planet;
    height: $mars-planet;
    margin-top: -$mars-planet / 2;
    margin-left: -$mars-planet / 2;
    background: #cf3921;
  }
}

// 木星
.jupiter {
  width: $jupiter-orbital;
  height: $jupiter-orbital;
  margin-top: -$jupiter-orbital / 2;
  margin-left: -$jupiter-orbital / 2;
  animation: rolate revolution(4331) linear infinite;
  &::before {
    width: $jupiter-planet;
    height: $jupiter-planet;
    margin-top: -$jupiter-planet / 2;
    margin-left: -$jupiter-planet / 2;
    background: #c76e2a;
  }
}

// 土星
.saturn {
  width: $saturn-orbital;
  height: $saturn-orbital;
  margin-top: -$saturn-orbital / 2;
  margin-left: -$saturn-orbital / 2;
  animation: rolate revolution(10747) linear infinite;
  &::before {
    width: $saturn-planet;
    height: $saturn-planet;
    margin-top: -$saturn-planet / 2;
    margin-left: -$saturn-planet / 2;
    background: #e7c194;
  }
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    width: 4.676%;
    height: 2.34%;
    margin-top: -1.2%;
    margin-left: -2.3%;
    border-radius: 50%;
    box-shadow: 0 1px 0 1px #987641, 3px 1px 0 #987641, -3px 1px 0 #987641;
  }
}

// 天王星
.uranus {
  width: $uranus-orbital;
  height: $uranus-orbital;
  margin-top: -$uranus-orbital / 2;
  margin-left: -$uranus-orbital / 2;
  animation: rolate revolution(30589) linear infinite;
  &::before {
    width: $uranus-planet;
    height: $uranus-planet;
    margin-top: -$uranus-planet / 2;
    margin-left: -$uranus-planet / 2;
    background: #b5e3e3;
  }
}

// 海王星
.neptune {
  width: $neptune-orbital;
  height: $neptune-orbital;
  margin-top: -$neptune-orbital / 2;
  margin-left: -$neptune-orbital / 2;
  animation: rolate revolution(59802) linear infinite;
  &::before {
    width: $neptune-planet;
    height: $neptune-planet;
    margin-top: -$neptune-planet / 2;
    margin-left: -$neptune-planet / 2;
    background: #175e9e;
  }
}

// 冥王星
.pluto {
  width: $pluto-orbital;
  height: $pluto-orbital;
  margin-top: -$pluto-orbital / 2 - 60;
  margin-left: -$pluto-orbital / 2 + 70;
  animation: rolate revolution(90580) linear infinite;
  &::before {
    width: $pluto-planet;
    height: $pluto-planet;
    margin-top: -$pluto-planet / 2;
    margin-left: -$pluto-planet / 2;
    background: #fff;
  }
}

// 小行星带
.asteroids-belt {
  height: $asteroids-belt-orbital;
  width: $asteroids-belt-orbital;
  border: 0 !important;
  margin-top: -$asteroids-belt-orbital / 2;
  margin-left: -$asteroids-belt-orbital / 2;
  opacity: 0.7;
  overflow: hidden;
  animation: rolate revolution(2191) linear infinite;
  &::before {
    top: 50%;
    height: $asteroids-belt-planet;
    width: $asteroids-belt-planet;
    margin-left: -$asteroids-belt-planet / 2;
    margin-top: -$asteroids-belt-planet / 2;
    box-shadow: stars(390, 290, -130, -104);
  }
}
</style>