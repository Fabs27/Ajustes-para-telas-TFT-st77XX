# Ajustes-para-telas-TFT-st77XX
Vim aqui pra tentar ajudar aqueles q estao com problemas com as telas txt  st77XX seja o problema com as corres ou ate msm a resoluçao falhada

https://github.com/Fabs27/ColorCorrection_St77xx.git

 Esta é minha biblioteca q corrige automatico os problemas das cores invertidas e a falha no preenchimento da tela, segue o codigo :

#include <Arduino.h>
#include <Adafruit_GFX.h>
#include <Adafruit_ST7789.h>
#include "ColorCorrection_St77xx.h" // Inclua a biblioteca ColorCorrection_St77xx

#define TFT_CS    5
#define TFT_RST   4
#define TFT_DC    2

Adafruit_ST7789 tft = Adafruit_ST7789(TFT_CS, TFT_DC, TFT_RST);

ColorCorrection colors[] = {
    {ST77XX_BLACK, "0x0000", "Black"},
    {ST77XX_BLUE, "0x001F", "Blue"},
    {ST77XX_RED, "0xF800", "Red"},
    {ST77XX_GREEN, "0x07E0", "Green"},
    {ST77XX_CYAN, "0x07FF", "Cyan"},
    {ST77XX_MAGENTA, "0xF81F", "Magenta"},
    {ST77XX_YELLOW, "0xFFE0", "Yellow"},
    {ST77XX_WHITE, "0xFFFF", "White"}
};

// Instancia o conversor e corrige as cores automaticamente ao incluir a biblioteca
ColorCorrection_St77xx converter(colors, sizeof(colors) / sizeof(colors[0]));

void setup() {
    tft.init(240, 320); // Inicializa o display com a resolução 240x320 (mude pra esoluçao da sua tela)
    tft.setRotation(0); // Define a orientação do display sendo 0 vertical, 1 horizontal e etc...
    tft.fillScreen(ST77XX_BLACK); //Preenche o fundo td de preto ou da cor desejada
}

void loop() {
    // Deixe o loop vazio
}

nele vc define a resoluçao da sua tela e ja seta no codigo td no meu caso foi a tela tft st7789  2.4 cujo resoluçao é 240 por 320 como no codigo acima ..
