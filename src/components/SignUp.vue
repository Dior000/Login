<template>
    <div class="submitErr" v-if="submitError">{{ submitError }}</div>
   <form @submit.prevent="subMit">
    <label>Email:</label>
    <input type="email" placeholder="Enter your email" v-model="email">
    <label>Password:</label>
    <div class="passwordField">
        <input type="password" placeholder="Enter your password" v-model="password" ref="passWord">
        <button class="visibility" @click="showOrNot">Show/Hide</button>
    </div>
    
    <label for="">Your position:</label>
    <select v-model="position">
        <option value="Frontend developer">Frontend developer</option>
        <option value="Backend developer">Backend developer</option>
        <option value="Android developer">Android developer</option>
    </select>
    <label for="">Languages:</label>
     <div class="checkBox">
        <input type="checkbox" value="english" v-model="languages"><span>English</span>
     </div>
     <div class="checkBox">
        <input type="checkbox" value="russian" v-model="languages"><span>Russian</span>
     </div>
    <div class="checkBox">
        <input type="checkbox" value="uzbek" v-model="languages"><span>Uzbek</span>
    </div>
    <label for="">Skills:</label>
    <input type="text" @keyup="handleSkill" v-model="skill">
    <button>Submit</button>
    
   </form>
    
   
</template>
<script>
export default {
     data(){
        return{
       email:'',
       password:'',
       position:'Frontend developer',
       checked:false,
       languages:[],
       skill:'',
       skills:[],
       submitError:''
       
        }
       
     },
     methods:{
        handleSkill(event){
          if(event.key==',' && this.skill.length>1){
            if(!this.skills.includes(this.skill.substring(0, this.skill.length-1))){
                this.skills.push(this.skill.substring(0, this.skill.length-1))
                this.skill=''
            }else{
                this.skill=''
            }
            

          }
        },
        subMit(){
            if(this.email==''){
                this.submitError='Please, enter your email'
            }
            else if(this.password.length < 5){
                this.submitError='Password must be at least 5 characters'
            }
            else if(this.languages.length < 1){
                this.submitError='You must choose at least 1 language'
            }
            else if(this.skills.length < 3){
                this.submitError='You must enter at least 3 technologies'
            }
            else{
                this.submitError=''
                let user = {
                email:this.email,
                password:this.password,
                position:this.position,
                languages:this.languages,
                skills:this.skills
            }
            console.log(user)
            }
            
        },
        showOrNot(){
            if(this.$refs.passWord.getAttribute("type") === "password")
                this.$refs.passWord.setAttribute("type", "text");
            else
                this.$refs.passWordd.setAttribute("type", "text");
            
        }
     }
}
</script>
<style scoped>
*{
    box-sizing: border-box;
}

.submitErr{
    text-align: center;
    align-items: center;
    border: 2px solid #f80606;
    color: #f12d2d;
    width: 500px;
    height: 40px;
    margin-left: 450px;
    margin-top: 40px;
    border-radius: 10px;
    font-size: 25px;
    backdrop-filter: blur(10px);
}
 form{
    display: flex;
    flex-direction: column;
     
    width: 500px;
    height: 600px;
    margin-left: 450px;
    margin-top: 10px;
    background-color: #aaa;
    border-radius: 10px;
    padding: 8px;

 }
 label{
    font-size: 30px;
    font-family: Rubik Iso;
    font-weight: 600;
    margin-left: 5px;
    margin-top: 10px;
 }
 input{
    width: 100%;
    height: 30px;
    border-radius: 5px;
    padding: 5px;
    font-family: Georgia, 'Times New Roman', Times, serif;
 }
 .passwordField{
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
    
 }
 .visibility{
    width: 25%;
    margin-left: 3px;
    margin-top: -4px;
    height: 32px;
 }
 select{
    margin-top: 7px;
    padding: 2px 5px;
    width: 100%;
    height: 30px;
    font-family: Georgia, 'Times New Roman', Times, serif;
    border-radius: 5px;
 }
 input[type=checkbox]{
    width: 20px;
    height: 20px;
    margin-top: 10px;
    display: inline-block;
    
 }
 .checkBox{
    display: inline-block;
    margin-left: 15px;
 }
 span{
    position: relative;
    bottom: 5px;
    font-size: 15px;
    margin-left: 5px;
    }
button{
    width: 400px;
    height: 35px;
    margin-left: 45px;
    margin-top: 10px;
    border-radius: 8px;
    cursor: pointer;
    font: 1em Georgia, 'Times New Roman', Times, serif;
    background: #ccc;

}

</style>
