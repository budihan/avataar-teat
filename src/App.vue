<template>
    <div id="app">
        <div class="main">
            <div class="head" id="head">
                <avataaars
                    :isCircle="istrue"
                    :circleColor="circleColor"
                    :clotheType="clotheType"
                    :accessoriesType="accessoriesType"
                    :clotheColor="clotheColor"
                    :eyebrowType="'Angry'"
                    :eyeType="'Cry'"
                    :mouthType="'Eating'"
                    :facialHairColor="'Blonde'"
                    :graphicType="'Cumbia'"
                >
                </avataaars>
            </div>
            <div class="radio">
                <el-radio v-model="istrue" :label="true">Circle</el-radio>
                <el-radio v-model="istrue" :label="false"
                    >Transparent
                </el-radio>
            </div>
            <div class="colorChoose">
                <el-color-picker v-model="circleColor"></el-color-picker>
            </div>
            <div class="select">
                <el-select
                    v-model="accessoriesType"
                    @change="handleChange"
                    placeholder="please select"
                >
                    <el-option
                        v-for="item in options1"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value"
                    >
                    </el-option>
                </el-select>
            </div>
            <div class="select">
                <el-select v-model="clotheType" placeholder="please select">
                    <el-option
                        v-for="item in options2"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value"
                    >
                    </el-option>
                </el-select>
            </div>
            <div class="select">
                <el-select v-model="clotheColor" placeholder="please select">
                    <el-option
                        v-for="item in options3"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value"
                    >
                    </el-option>
                </el-select>
            </div>
            <el-button type="primary" @click="exportPic('head')"
                >下载图片</el-button
            >
        </div>
    </div>
</template>

<script>
import Avataaars from "vuejs-avataaars";
import html2Canvas from "html2canvas";
export default {
    name: "App",
    components: {
        Avataaars,
    },
    data() {
        return {
            istrue: true,
            circleColor: "#6fb8e0",
            accessoriesType: "Kurt",
            clotheType: "BlazerShirt",
            clotheColor: "Blue02",
            options1: [
                { labal: "Blank", value: "Blank" },
                { labal: "Kurt", value: "Kurt" },
                { labal: "Prescription01", value: "Prescription01" },
                { labal: "Prescription02", value: "Prescription02" },
                { labal: "Round", value: "Round" },
                { labal: "Sunglasses", value: "Sunglasses" },
                { labal: "Wayfarers", value: "Wayfarers" },
            ],
            options2: [
                { labal: "BlazerShirt", value: "BlazerShirt" },
                { labal: "BlazerSweater", value: "BlazerSweater" },
                { labal: "CollarSweater", value: "CollarSweater" },
                { labal: "GraphicShirt", value: "GraphicShirt" },
                { labal: "Hoodie", value: "Hoodie" },
                { labal: "Overall", value: "Overall" },
                { labal: "ShirtCrewNeck", value: "ShirtCrewNeck" },
                { labal: "ShirtScoopNeck", value: "ShirtScoopNeck" },
                { labal: "ShirtVNeck", value: "ShirtVNeck" },
            ],
            options3: [
                { labal: "Black", value: "Black" },
                { labal: "Blue01", value: "Blue01" },
                { labal: "Blue02", value: "Blue02" },
                { labal: "Blue03", value: "Blue03" },
                { labal: "Gray01", value: "Gray01" },
                { labal: "Gray02", value: "Gray02" },
                { labal: "Heather", value: "Heather" },
                { labal: "PastelBlue", value: "PastelBlue" },
                { labal: "PastelGreen", value: "PastelGreen" },
                { labal: "PastelOrange", value: "PastelOrange" },
                { labal: "PastelRed", value: "PastelRed" },
                { labal: "PastelYellow", value: "PastelYellow" },
                { labal: "Pink", value: "Pink" },
                { labal: "Red", value: "Red" },
                { labal: "White", value: "White" },
            ],
        };
    },
    methods: {
        handleChange(value) {
            console.log(value);
        },
        exportPic(DivID) {
            html2Canvas(document.querySelector("#" + DivID)).then((canvas) => {
                let dataURL = canvas.toDataURL("image/png");
                console.log(dataURL);
                if (dataURL !== "") {
                    var a = document.createElement("a");
                    a.download = "头像";
                    a.href = dataURL;
                    a.click();
                }
            });
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.main {
    width: 600px;
    margin: 60px auto;
    text-align: center;
}
.head {
    width: 300px;
    margin: 0px auto;
}
</style>
