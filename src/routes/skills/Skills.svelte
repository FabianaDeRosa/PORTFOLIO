<script>
    import P5 from 'p5-svelte';
  
    const sketch = (p) => {
      let tools = [];
      let numTools = 19;
      let imgs = [];
      let imgUrls = [
        './assets/tools_logos/ableton.png',
        './assets/tools_logos/after-effect.png',
        './assets/tools_logos/arduino.png',
        './assets/tools_logos/canva.png',
        './assets/tools_logos/figma.png',
        './assets/tools_logos/illustrator.png',
        './assets/tools_logos/indesign.png',
        './assets/tools_logos/lightroom.png',
        './assets/tools_logos/maya.png',
        './assets/tools_logos/p5.png',
        './assets/tools_logos/photoshop.png',
        './assets/tools_logos/processing.png',
        './assets/tools_logos/spline.png',
        './assets/tools_logos/svelte.svg.png',
        './assets/tools_logos/touchdesigner.png',
        './assets/tools_logos/unreal.png',
        './assets/tools_logos/visual-studio.png',
        './assets/tools_logos/wwise.png',
        './assets/tools_logos/xd.png',
      ];
  
      p.preload = () => {
        for (let i = 0; i < imgUrls.length; i++) {
          imgs[i] = p.loadImage(imgUrls[i]);
        }
      };
  
      p.setup = () => {
        p.createCanvas(1000, 1000);
        for (let i = 0; i < numTools; i++) {
          let x = p.random(p.width);
          let y = p.random(p.height);
          let img = imgs[i % imgs.length];
          tools[i] = new Tool(x, y, img, 50);
        }
      };
  
      p.draw = () => {
        p.background(255);
        for (let i = 0; i < tools.length; i++) {
          tools[i].show();
          tools[i].move();
          tools[i].collision(tools, i);
        }
      };
  
      class Tool {
        constructor(x, y, img, w) {
          this.x = x;
          this.y = y;
          this.w = w;
          this.img = img;
          this.velX = p.random(1, 2);
          this.velY = p.random(1, 2);
        }
  
        show() {
          p.image(this.img, this.x, this.y, this.w, this.w);
        }
  
        move() {
          this.x += this.velX;
          this.y += this.velY;
  
          if (this.x - this.w / 2 < 0 || this.x + this.w / 2 > p.width) {
            this.velX *= -1;
          }
  
          if (this.y - this.w / 2 < 0 || this.y + this.w / 2 > p.height) {
            this.velY *= -1;
          }
        }
  
        collision(other, index) {
          for (let i = 0; i < other.length; i++) {
            if (i !== index) {
              let d = p.dist(this.x, this.y, other[i].x, other[i].y);
              let sum = this.w / 2 + other[i].w / 2;
              if (d < sum) {
                this.velX *= -1;
                this.velY *= -1;
              }
            }
          }
        }
      }
    };
  </script>
  
  <P5 {sketch} />
  