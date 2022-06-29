//variáveis da bolinha
let xBolinha = 300;
let yBolinha = 200;
let diametro = 13;
let raio = diametro /2;
let velocidadeXBolinha = 6;
let velocidadeYBolinha = 6;

//variáveis das raquetes
let comprimentoRaquete = 10;
let alturaRaquete = 90;
let xRaquete = 5;
let yRaquete = 150;
let xRaqueteOponente = 585;
let yRaqueteOponente = 150;
let velocidadeYOponente;
let chanceDeErrar = 0;

//variável para verificação de colisão das raquetes
let colidiu = false;

//placar do jogo
let meusPontos = 0;
let pontosDoOponente = 0;

//sons do jogo
let somRaquetada;
let somPonto;
let somTrilha;

function preload(){
  somTrilha = loadSound("trilha.mp3");
  somPonto = loadSound("ponto.mp3");
  somRaquetada = loadSound("raquetada.mp3");
}

function setup() {
  createCanvas(600, 400);
  somTrilha.loop();
}

function draw() {
  background(0); 
  mostraBolinha();
  movimentoBolinha();
  verificaColisaoBorda();
  mostraRaquete(xRaquete, yRaquete);
  mostraRaquete(xRaqueteOponente,yRaqueteOponente);e
  movimentaRaquete();
  movimentaRaqueteOponente();
  verificaColisaoRaquete(xRaquete, yRaquete);
  verificaColisaoRaquete(xRaqueteOponente,yRaqueteOponente);
  incluiPlacar();
  marcaPonto();
  bugBolinhaPresa();
}


function mostraBolinha(){
  circle(xBolinha, yBolinha, diametro);
}


function movimentoBolinha(){
  xBolinha += velocidadeXBolinha;
  yBolinha += velocidadeYBolinha;
}


function verificaColisaoBorda(){
  if (xBolinha + raio > width ||
      xBolinha - raio < 0) {
        velocidadeXBolinha *= -1;
  } 
  if (yBolinha + raio > height ||
      yBolinha - raio <0){
        velocidadeYBolinha *= -1;
  }
}
  

function mostraRaquete(x,y){
  rect(x,y,comprimentoRaquete,alturaRaquete);
}


function movimentaRaquete(){
  if (keyIsDown(UP_ARROW)){
      yRaquete -= 10;  
  }
  if (keyIsDown(DOWN_ARROW)){
      yRaquete += 10;  
  }
}


function movimentaRaqueteOponente(){
  velocidadeYOponente = yBolinha - yRaqueteOponente - comprimentoRaquete / 2 -30;
  yRaqueteOponente += velocidadeYOponente + chanceDeErrar
  calculaChanceDeErrar()
}


function calculaChanceDeErrar() {
  if (pontosDoOponente >= meusPontos) {
    chanceDeErrar += 1
    if (chanceDeErrar >= 39){
    chanceDeErrar = 40
    }
  } else {
    chanceDeErrar -= 1
    if (chanceDeErrar <= 35){
    chanceDeErrar = 35
    }
  }
}


//função "collideRectCircle" importada da biblioteca 
function verificaColisaoRaquete(x, y){
  colidiu = collideRectCircle(x, y, 
  comprimentoRaquete, alturaRaquete, xBolinha, yBolinha, raio);
  
  if(colidiu){
    velocidadeXBolinha *= -1;
    somRaquetada.play();
  }
}


function incluiPlacar(){
  stroke(255);
  textSize(16);
  textAlign(CENTER);
  fill(225,140,0);
  rect(150,10,40,20);
  fill(225);
  text(meusPontos, 170,26)
  fill(225,140,0);
  rect(450,10,40,20);
  fill(225);
  text(pontosDoOponente,470,26)
}


function marcaPonto(){
  if (xBolinha > 590){
    meusPontos +=1;
    somPonto.play();
  }
  if (xBolinha <10){
    pontosDoOponente += 1;
    somPonto.play();
  }
}

// funçao pra evitar que a bolinha fique presa atrás da raquete
function bugBolinhaPresa(){
    if (XBolinha - raio < 0){
    XBolinha = 23
    }
}
