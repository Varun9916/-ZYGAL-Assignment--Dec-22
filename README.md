# -ZYGAL-Assignment--Dec-22

final color COLOR1 = color(255, 200, 0);
final color COLOR2 = color(0, 200, 200);

final float BUTTON_SIZE = 50;

float buttonX, buttonY;
color buttonColor = COLOR1;
boolean wasPressed = false;
int counter = 5;

boolean gameOver = false;

void setup() {
    size(400, 400);
    relocateButton();
}

void draw() {
    background(0);
    
    fill(buttonColor);
    square(buttonX, buttonY, BUTTON_SIZE);
    printCounter();
}

void mousePressed() {
    clickedOnButton();
}

void mouseReleased() {
    clickedOffButton();
}

void clickedOnButton() {
    if (mouseX > 0 && mouseX < buttonX + BUTTON_SIZE && 
        mouseY > 0 && mouseY < buttonY + BUTTON_SIZE) {
        buttonColor = COLOR2;
        wasPressed = true;
    }
}

void clickedOffButton() {
    if (wasPressed) {
        wasPressed = false;
        buttonColor = COLOR1;
        relocateButton();
        --counter;
        if (counter == 0) {
            gameOver = true;       
        }
    }
}

void printCounter() {
    fill(0);
    
    if (gameOver) {
        text("STOP", buttonX + BUTTON_SIZE / 2 - textWidth("STOP") / 2, buttonY + BUTTON_SIZE / 2 + textWidth('1') / 2);
        noLoop();
    }
    else {
        text(counter, buttonX + BUTTON_SIZE / 2 - textWidth('1') / 2, buttonY + BUTTON_SIZE / 2 + textWidth('1') / 2);
    }
}

void relocateButton() {
    buttonX = random(width - BUTTON_SIZE);
    buttonY = random(height - BUTTON_SIZE);
}
