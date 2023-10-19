<template>
    <h1>Photo editor</h1>
    <div class="container editor">
        <div class="row text-light">
            <!-- 
                  <div class="col-lg-6 col-md-6 d-col-block">
                <form class="w-100 text-end" @change="editImg">
                <div class="form-control bg-dark my-2 c">
                    <label class="form-label d-inline-block fs-4" for="saturate">saturate :</label> <span>{{ saturate }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="saturate" id="saturate"  v-model="saturate">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Contrast">Contrast :</label> <span>{{ contrast }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Contrast" id="Contrast"  v-model="contrast">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Brightness">Brightness :</label> <span>{{ brightness }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Brightness" id="Brightness" v-model="brightness">
                </div>
            </form>
            </div>
             -->
            <div class="col-lg-6 col-md-6 ">
                <div class="img">
                <img class="w-100 py-3 mt-3 d-none" src=""  id="Img">
                <canvas id="canvas" class="w-100 py-3 mt-3 "></canvas>
                </div>
                <input type="file" id="file" class="btn mx-5 text-light d-none" style="border: white 2px dashed;" @change="uploadImg">
                <label class="btn mt-2 upload text-light" for="file" style="border: white 2px dashed;">Upload</label>
            </div>
            <div class="col-lg-6 col-md-6 pb-3">
                <form class="w-100 text-end" @change="editImg">
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label d-inline-block fs-4" for="saturate">saturate :</label> <span>{{ saturate }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="saturate" id="saturate"  v-model="saturate">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Contrast">Contrast :</label> <span>{{ contrast }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Contrast" id="Contrast"  v-model="contrast">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Brightness">Brightness :</label> <span>{{ brightness }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Brightness" id="Brightness" v-model="brightness">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Sepia">Sepia :</label> <span>{{ sepia }}%</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Sepia" id="Sepia" v-model="sepia">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Grayscale">Grayscale :</label> <span>{{ grayscale }}</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Grayscale" id="Grayscale" v-model="grayscale">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="Blur">Blur :</label> <span>{{ blur }}</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="Blur" id="Blur" v-model="blur">
                    </div>
                    <div class="form-control bg-dark my-2 c">
                    <label class="form-label  d-inline-block fs-4" for="HueRotate">Hue Rotate</label> <span>{{ hueRotate }}</span>
                    <input class="w-100 pointer" type="range" dir="rtl" name="HueRotate" id="HueRotate" v-model="hueRotate">
                    </div>
                </form>
                <div class="form-control bg-dark my-2 c BG" id="BG"> <!--  BG is btn group    -->
                <a id="dawnlode" class="btn btn-success mx-5 mt-2 Dawnlode" download="true" @click=" Download">Download</a>
                <button class="btn btn-success mx-5 mt-2" @click="Reset">Reset</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "PhotoEditor",
    data: () => {
        return{
        saturate: "100",
        contrast: "100",
        brightness: "100",
        sepia: "0",
        grayscale: "0",
        blur: "0",
        hueRotate: "0",
        }
    },
    methods: {
        uploadImg(){
            // this.ImgSrc = file;
            let btns = document.getElementById("BG")
            let File = document.getElementById("file");
            let img = document.getElementById("Img");
            let canvas =  document.getElementById("canvas");
            const ctx = canvas.getContext("2d");
            File = File.files[0];
            let fileReader = new FileReader();
            fileReader.readAsDataURL(File); 
            fileReader.onload = function() {
            //  alert(fileReader.result);
            // this.ImgSrc = fileReader.result;
            img.src = fileReader.result;
            img.alt  = "Photo";
            img.onload = () => {
            canvas.width = img.width;
            canvas.height = img.height;
            let Width = img.width;
            let height = img.height;
            ctx.drawImage(img, 0, 0,Width ,height);
            };
            }; 
            fileReader.onerror = function() {
             alert(fileReader.error);
            }; 
            btns.style.display = "block"
            img.style.filter = `
            blur(0px)
            saturate(100%)
            hue-rotate(0deg)
            contrast(100%)
            brightness(100%)
            sepia(0%)
            grayscale(0)
            `;
            this.saturate = "100"
            this.contrast = "100"
            this.brightness = "100"
            this.sepia = "0"
            this.grayscale = "0"
            this.blur = "0"
            this.hueRotate = "0"
        },
        Reset() {
            let img = document.getElementById("Img");
            let canvas =  document.getElementById("canvas");
            const ctx = canvas.getContext("2d");
            canvas.width = img.width;
            canvas.height = img.height;
            let Width = img.width;
            let height = img.height;
            console.log(Width, height);
            ctx.drawImage(img, 0, 0,Width ,height);
            ctx.filter = `
            blur(0px)
            saturate(100%)
            hue-rotate(0deg)
            contrast(100%)
            brightness(100%)
            sepia(0%)
            grayscale(0)
            `;
            ctx.drawImage(img, 0, 0,Width ,height);
            this.saturate = "100"
            this.contrast = "100"
            this.brightness = "100"
            this.sepia = "0"
            this.grayscale = "0"
            this.blur = "0"
            this.hueRotate = "0"
        },

        editImg(){
            let canvas =  document.getElementById("canvas");
            const ctx = canvas.getContext("2d");
            let img = document.getElementById("Img");
            canvas.width = img.width;
            canvas.height = img.height;
            let Width = img.width;
            let height = img.height;
            console.log(Width, height);
            ctx.drawImage(img, 0, 0,Width ,height);
            
            ctx.filter = `
            blur(${this.blur}px)
            saturate(${this.saturate}%)
            hue-rotate(${this.hueRotate}deg)
            contrast(${this.contrast}%)
            brightness(${this.brightness}%)
            sepia(${this.sepia}%)
            grayscale(${this.grayscale})
            `;
            ctx.drawImage(img, 0, 0,Width ,height);
        },
        Download(){
            let download = document.getElementById("dawnlode");
            let canvas =  document.getElementById("canvas");
            download.href = canvas.toDataURL()
        },
    },
}
</script>
<style scoped>
.editor {
    background: rgba(33, 34, 41, 0.788);
    box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.322);
    border-radius: 10px;
}
.c {
    color: white;
    border: none;
}
.pointer{
    cursor: pointer;
}
.c:hover {
    box-shadow: 10px 8px 20px rgba(0, 0, 0, 0.151);
}
.BG {
    display: none;
}
/* message styles */
/* .message {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    z-index: 50;
    background: rgb(33, 37, 41);
} */
</style>