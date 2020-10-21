# Making-a-game-

    return i;
};

var tw=512, th=tw/2, s=tw*0.705, a=Math.PI/4;
var asin=acos=Math.sin(a);
var floorMap=[
    "000000000000000000000000000000000000000000000000".split(""),
    "011110000000000000000000000000000000000000000000".split(""),
    "000210000000000000000000000000000000000000000000".split(""),
    "000111111111111111110000000000000000000000000000".split(""),
    "000000001000000001000000000000000000000000000000".split(""),
    "000000001000000001111111100000000000000000000000".split(""),
    "000000001000000000000000011111100000000000000000".split(""),
    "000000001000000000000000000000000000000000000000".split(""),
    "000000001100000000000000000000000000000000000000".split(""),
    "000000001111111000000000000000000000000000000000".split(""),
    "000000000100011000000000000000000000000000000000".split(""),
    "000000000100001000000000000000000000000000000000".split(""),
    "000000000100002000000000000000000000000000000000".split(""),
    "000000000100000000000000000000000000000000000000".split(""),
    "000000000110000000000000000000000000000000000000".split(""),
    "000002111111112000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
    "000000000000000000000000000000000000000000000000".split(""),
];

var floor=document.getElementById("floor").getContext("2d");
floor.w=floor.canvas.width;
floor.h=floor.canvas.height;

var barrelSprite=loadImage("sprite/barrel64.png");
var coinSprite=loadImage("sprite/coins10.png");
var potionSprite=loadImage("sprite/potions.png");
var houseSprite=loadImage("sprite/house.png");
var tileMap={
    "0000": loadImage("dirt/dirt0000.png"),
    "0001": loadImage("dirt/dirt0001.png"),
    "0010": loadImage("dirt/dirt0010.png"),
    "0011": loadImage("dirt/dirt0011.png"),
    "0100": loadImage("dirt/dirt0100.png"),
    "0101": loadImage("dirt/dirt0101.png"),
    "0110": loadImage("dirt/dirt0110.png"),
    "0111": loadImage("dirt/dirt0111.png"),
    "1000": loadImage("dirt/dirt1000.png"),
    "1001": loadImage("dirt/dirt1001.png"),
    "1010": loadImage("dirt/dirt1010.png"),
    "1011": loadImage("dirt/dirt1011.png"),
    "1100": loadImage("dirt/dirt1100.png"),
    "1101": loadImage("dirt/dirt1101.png"),
    "1110": loadImage("dirt/dirt1110.png"),
    "1111": loadImage("dirt/dirt1111.png"),
    "0":    loadImage("dirt/gray.png"),
};

var tileMap={};
var 
ti=0; for(var tj=0;tj<=54;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=1; for(var tj=0;tj<=24;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=2; for(var tj=0;tj<=24;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=3; for(var tj=0;tj<=15;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=4; for(var tj=0;tj<=1 ;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=5; for(var tj=0;tj<=28;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=6; for(var tj=0;tj<=11;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=7; for(var tj=0;tj<=11;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=8; for(var tj=0;tj<=5 ;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=9; for(var tj=0;tj<=4 ;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");
ti=10;for(var tj=0;tj<=5 ;tj++) tileMap[ti+"-"+tj]=loadImage("dirt/"+ti+"-"+tj+".png");


var tw=160, th=tw/2, s=tw*0.705, a=Math.PI/4, visible=7;
var asin=acos=Math.sin(a);

var floorMap=[
    "0-0, 5-0 ,5-14,5-17,5-18,5-21,5-22,5-23,5-24,5-25,5-26,5-27,5-28,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-0 ,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-0 ,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-14,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-17,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-18,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-21,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-22,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),

    "5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,5-23,10-5,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-50,0-51,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/),
    "5-0 ,0-52,0-53,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,5-0 ,".split(/\s*,\s*/), 
];
function isWayFloor(x,y) {
    return floorMap[y] ? floorMap[y][x] !== " " : false;
}
function isStep(x,y){
    return isWayFloor(Math.floor(x/s), Math.floor(y/s));
}
function getFloorTile(x, y) {
    var f = floorMap[y][x];
    return tileMap[f];
}

var monsterMap={
    SK: {
        A1: loadImage("monsters/SK/A1/map.png",8,16,true),
@@ -107,14 +130,16 @@ setInterval(function(){
},2000);

// aggresive mobs
var monsters=[];
var deathmobs=[];
for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'SK'));
monsters.push(new AgressiveMob(100,100,'SI'));
for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'FS'));
for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'SI'));
var monsters=[],deathmobs=[],barrels=[],coins=[],potions=[];
//for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'SK'));
//for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'FS'));
//for(var i=0;i<10;i++) monsters.push(new AgressiveMob(randomx(),randomy(), 'SI'));
//for(var i=0;i<33;i++) barrels.push(new Barrel(randomx(),randomy()));
//for(var i=0;i<33;i++) potions.push(new PotionHealth(randomx(), randomy()));


setInterval(function() { // random step for mobs, attack hero
    if(monsters.length==0)return;
    var m=monsters[Math.ceil(Math.random()*(monsters.length-1))];
    if(typeof m.attacked != "object"){
        m.to_x=m.x+(Math.random()*s-s/2);
@@ -136,17 +161,6 @@ setInterval(function() { // random step for mobs, attack hero
    }
}, 200);

var barrels=[];
for(var i=0;i<33;i++) barrels.push(new Barrel(randomx(),randomy()));
var coins=[];
var potions=[];
for(var i=0;i<33;i++) potions.push(new PotionHealth(randomx(), randomy()));
var houses=[];
for(var y in floorMap) // pre fetch house;
    for(var x in floorMap[y])
        if(floorMap[y][x]=="2")
            houses.push(new House((parseInt(x)+0.5)*s,(parseInt(y)+0.5)*s));

floor.canvas.onclick=function(e) { 
    var mx=e.offsetX - floor.w/2;
    var my=e.offsetY - floor.h/2;
@@ -224,7 +238,7 @@ function renderHeroBelt(){

function loadZb(order,click){
    var tmp_zb=[], zb=[];
    var all=[click?[]:houses,monsters,potions,barrels,click?[]:[hero]];
    var all=[monsters,potions,barrels,click?[]:[hero]];
    for(var t in all) 
        for(var m in all[t]) 
            if(all[t][m].isAboveHero()) 
@@ -265,7 +279,6 @@ function renderObjects(){
            sy=(m.x + m.y)/2*asin+m.offset_y;
        var tile=m.sprite;
        // render sprite
        if(m.isOverHero && m.isOverHero()) floor.globalAlpha=0.5;
        var tw = tile.width;
        var th = tile.height
        if(tile.steps && tile.angles){
@@ -299,10 +312,10 @@ function renderFloor() {
    floor.translate(floor.w/2-th, floor.h/2);// translate to center
    var fdx=Math.floor(hero.x/s), // hero tile
        fdy=Math.floor(hero.y/s),
        miny=Math.max(0, fdy-3), // calculate camera visible tiles
        maxy=Math.min(floorMap.length-1,fdy+3),
        minx=Math.max(0, fdx-3),
        maxx=Math.min(floorMap[0].length-1,fdx+3);
        miny=Math.max(0, fdy-visible), // calculate camera visible tiles
        maxy=Math.min(floorMap.length-1,fdy+visible),
        minx=Math.max(0, fdx-visible),
        maxx=Math.min(floorMap[0].length-1,fdx+visible);
    // translate to hero
    var mrx=hero.x * acos - hero.y * asin,
        mry=hero.x * asin + hero.y * acos;
@@ -324,47 +337,18 @@ function renderFloor() {
    floor.restore();
}

function getFloorTile(x, y) {
    var f = floorMap[y][x];
    switch(f){
        case "2":
        case "0":
            return tileMap["0"];
        case "1":
            var tileCode="";
            tileCode+=(isWayFloor(x, y+1)?"1":"0");
            tileCode+=(isWayFloor(x+1, y)?"1":"0");
            tileCode+=(isWayFloor(x, y-1)?"1":"0");
            tileCode+=(isWayFloor(x-1, y)?"1":"0");
            return tileMap[tileCode];
        default:
            return null;
    }
}

function isWayFloor(x, y) {
    return floorMap[y] ? floorMap[y][x] == "1" : false;
}

function remove(ar,v){var i=ar.indexOf(v);if(i>=0)ar.splice(i,1);}
function randomx(){return Math.floor(Math.random()*(floorMap[0].length)*s);}
function randomy(){return Math.floor(Math.random()*(floorMap.length)*s);}

function isStep(x,y){
    var dx=Math.floor(x/s), 
        dy=Math.floor(y/s);
    var t = floorMap[dy] ? floorMap[dy][dx] : floorMap[dy];
    return t=="0"||t=="1";
}

function Shape(sprite,x,y){
    this.x=x;
    this.y=y;
    this.offset_x=0;
    this.offset_y=0;
    this.sprite=sprite;
    this.isAboveHero=function(){
        var maxlen=tw*1.5;
        var maxlen=tw*visible/2;
        return (Math.abs(this.x-hero.x)<=maxlen) && (Math.abs(this.y-hero.y)<=maxlen);
    };
}
@@ -381,21 +365,6 @@ function DeathMob(mob){
    }
}

function House(x,y){
    Shape.call(this,houseSprite,x,y);
    this.offset_y=th/2;
    this.isOverHero=function(){
        var hx=(hero.x - hero.y) * acos,
            hy=(hero.x + hero.y)/2 * asin;
        var sx=(this.x - this.y) * acos,
            sy=(this.x + this.y)/2 * asin;
        return (hx >= sx-houseSprite.width/2)
            && (hx <= sx+houseSprite.width/2)
            && (hy >= sy+this.offset_y-houseSprite.height)
            && (hy <= sy)
    }
}

function Barrel(x, y){
    Shape.call(this,barrelSprite,x,y);
    this.use=function(mob){
