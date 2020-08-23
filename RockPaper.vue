<template>
    <div>
        <div id="computer" :style="computedStyleObject"></div>
        <div>
            <button @oclick="onClickButton('바위')">바위</button>
            <button @oclick="onClickButton('가위')">가위</button>
            <button @oclick="onClickButton('보')">보</button>
        </div>
        <div>{{result}}</div>
        <div>현재 {{score}}점</div>
    </div>
</template>

<script>

const rspCoords = {
    바위: '0',
    가위: '-142px',
    보: '-274px',
}

let interval = null;
export default {
    data() {
        return {
            imgCoord: rspCoords.바위,
            result: '',
            score: 0,
        }
    },
    computed :{
        computedStyleObject(){
            return {
                background: `url(https://en.pimg.jp/023/182/267/1/23182267.jpg) ${this.imgCoord} 0`,
                width: '125px',
                height: '200px'
            }
        }
    },
    methods: {
        onClickButton(choice) {


        }
    },
    mounted() {
        console.log('mounted');
        interval = setInterval(()=> {
            if(this.imgCoord === rspCoords.바위){
                this.imgCoord = rspCoords.가위;
            }else if(this.imgCoord === rspCoords.가위){
                this.imgCoord = rspCoords.보;
            }else if(this.imgCoord === rspCoords.보){
                this.imgCoord = rspCoords.바위;
            }
        }, 100);
    },
    beforeDestroy() {
        clearInterval(interval);
    }
};
</script>

<style>


</style>