<template>



    <!-- error -->
    <div v-if="err" class="backdrop">
        <div class="card">
            <h1 style="color:red;">Error !!</h1>
            <p>Pleas Change Players Name</p>
            <button @click="replayClick_err()">Replay</button>
        </div>
    </div>
    <!-- win card -->
    <div v-if="result_card" class="backdrop">
        <div class="card">
            <h1>Congratulations {{win_player}}</h1>
            <p>You Win 😊😊</p>
            <button @click="replayClick_win()">Replay</button>
        </div>
    </div>
    <!-- Draw card -->
    <div v-if="draw_statu" class="backdrop">
        <div class="card">
            <h1>Draw !!</h1>
            <p>Good Game 😊😊</p>
            <button @click="replayClick_draw()">Replay</button>
        </div>
    </div>
   <div class="title">
       <h1>
            <div class="first_p">TIC</div>
            TAC 
            <div class="first_p">TOE</div>
       </h1>
   </div>
  
  
  <div v-if="turn" class="turn_card">
          <div class="title">
              <h2>It's {{player_2_name}} Turn</h2>
          </div>
          <div class="symb">
              <h2>O</h2>
          </div>
   </div>
   <div v-else class="turn_card">
          <div class="title">
              <h2>It's {{player_1_name}} Turn</h2>
          </div>
          <div class="symb">
              <h2>X</h2>
          </div>
   </div>
  <!-- <h2 v-if="turn">Player 2 Turn : O</h2> -->
  <!-- <h2 v-else>Player 1 Turn : X</h2> -->
  <div class="content">
      <div class="platyer_card">
          <div class="title">
              <input type="text" onclick="this.select()" v-model="player_1_name" >
              <!-- <h1>Player 1</h1> -->
          </div>
          <div class="score">
              <h2>{{player_1_score}}</h2>
          </div>
      </div>
      
    <div class="board">
      <div class="row">
        <hr class="l_1_v_s" id="l_1_v">
        <hr class="l_1_h_s" id="l_1_h">
        <div @click="boxClick('r_1_1')" id="r11" class="box"><span>{{r_1_1}}</span></div>
        <div @click="boxClick('r_1_2')" id="r12" class="box"><span>{{r_1_2}}</span></div>
        <div @click="boxClick('r_1_3')" id="r13" class="box"><span>{{r_1_3}}</span></div>
      </div>
      <div class="row">
        <hr class="l_2_v_s" id="l_2_v">
        <hr class="l_2_h_s" id="l_2_h">
        <hr class="l_1_x_s" id="l_1_x">
        <hr class="l_2_x_s" id="l_2_x">
        <div @click="boxClick('r_2_1')" id="r21" class="box"><span>{{r_2_1}}</span></div>
        <div @click="boxClick('r_2_2')" id="r22" class="box"><span>{{r_2_2}}</span></div>
        <div @click="boxClick('r_2_3')" id="r23" class="box"><span>{{r_2_3}}</span></div>
      </div>
      <div class="row">
        <hr class="l_3_v_s" id="l_3_v">
        <hr class="l_3_h_s" id="l_3_h">
        <div @click="boxClick('r_3_1')" id="r31" class="box"><span>{{r_3_1}}</span></div>
        <div @click="boxClick('r_3_2')" id="r32" class="box"><span>{{r_3_2}}</span></div>
        <div @click="boxClick('r_3_3')" id="r33" class="box"><span>{{r_3_3}}</span></div>
      </div>
    </div>
     <div class="platyer_card">
          <div class="title">
              <input type="text" onclick="this.select()" v-model="player_2_name" >
              <!-- <h1>Player 2</h1> -->
          </div>
          <div class="score">
              <h2>{{player_2_score}}</h2>
          </div>
      </div>
  </div>
  

  
</template>

<script>
export default {
data(){
    return{
        turn:false,
        symb:"",
        r_1_1:null,
        r_1_2:'',
        r_1_3:'',
        r_2_1:'',
        r_2_2:'',
        r_2_3:'',
        r_3_1:'',
        r_3_2:'',
        r_3_3:'',
        nbr_turn:0,
        player_1_score:0,
        player_2_score:0,
        win_player:'',
        result_card:false,
        draw_statu:false,
        player_1_name:'Player 1',
        player_2_name:'Player 2',
        err:false,
      
        
    }
},
methods:{
    
    boxClick(x){
        if (this.player_1_name===this.player_2_name) {
            this.err=!this.err;
        }
        
        this.nbr_turn++;
       if (!this.turn) {           
            //X
            this.ture="x";
            if (x==='r_1_1') {
                this.r_1_1='X'
                this.turn=!this.turn;
                document.getElementById('r11').classList.add('block');
            }
            if (x==='r_1_2') {
                this.r_1_2='X'
                this.turn=!this.turn;
                document.getElementById('r12').classList.add('block');
            }
            if (x==='r_1_3') {
                this.r_1_3='X'
                this.turn=!this.turn;
                document.getElementById('r13').classList.add('block');
            }
            if (x==='r_2_1') {
                this.r_2_1='X'
                this.turn=!this.turn;
                document.getElementById('r21').classList.add('block');
            }
            if (x==='r_2_2') {
                this.r_2_2='X'
                this.turn=!this.turn;
                document.getElementById('r22').classList.add('block');
            }
            if (x==='r_2_3') {
                this.r_2_3='X'
                this.turn=!this.turn;
                document.getElementById('r23').classList.add('block');
            }
            if (x==='r_3_1') {
                this.r_3_1='X'
                this.turn=!this.turn;
                document.getElementById('r31').classList.add('block');
            }
            if (x==='r_3_2') {
                this.r_3_2='X'
                this.turn=!this.turn;
                document.getElementById('r32').classList.add('block');
            }
            if (x==='r_3_3') {
                this.r_3_3='X'
                this.turn=!this.turn;
                document.getElementById('r33').classList.add('block');
            }
       }
       else{
           //O
           this.ture="o";
           if (x==='r_1_1') {
                this.r_1_1='O'
                this.turn=!this.turn;
                document.getElementById('r11').classList.add('block');
            }
            if (x==='r_1_2') {
                this.r_1_2='O'
                this.turn=!this.turn;
                document.getElementById('r12').classList.add('block');
            }
            if (x==='r_1_3') {
                this.r_1_3='O'
                this.turn=!this.turn;
                document.getElementById('r13').classList.add('block');
            }
            if (x==='r_2_1') {
                this.r_2_1='O'
                this.turn=!this.turn;
                document.getElementById('r21').classList.add('block');
            }
            if (x==='r_2_2') {
                this.r_2_2='O'
                this.turn=!this.turn;
                document.getElementById('r22').classList.add('block');
            }
            if (x==='r_2_3') {
                this.r_2_3='O'
                this.turn=!this.turn;
                document.getElementById('r23').classList.add('block');
            }
            if (x==='r_3_1') {
                this.r_3_1='O'
                this.turn=!this.turn;
                document.getElementById('r31').classList.add('block');
            }
            if (x==='r_3_2') {
                this.r_3_2='O'
                this.turn=!this.turn;
                document.getElementById('r32').classList.add('block');
            }
            if (x==='r_3_3') {
                this.r_3_3='O'
                this.turn=!this.turn;
                document.getElementById('r33').classList.add('block');
            }
       }
       this.result();
      
    },
    win_info(pl_name,lign,turn){
            this.win_player=pl_name;
            this.result_card=!this.result_card;
            if(turn==="x")
            {
                this.player_1_score++;
            }else{
                this.player_2_score++;
            }
            
            document.getElementById(lign).style.visibility="visible";
           
            this.nbr_turn=0;
            return;
    }
    ,
    result(){
        //Player X
         //Row
        if (this.r_1_1 === 'X' && this.r_1_2 === 'X' && this.r_1_3 === 'X') {
           this.win_info(this.player_1_name,'l_1_v',"x");
        }
        if (this.r_2_1 === 'X' && this.r_2_2 === 'X' && this.r_2_3 === 'X') {
           this.win_info(this.player_1_name,'l_2_v',"x");
        }
        if (this.r_3_1 === 'X' && this.r_3_2 === 'X' && this.r_3_3 === 'X') {
            this.win_info(this.player_1_name,'l_3_v',"x");
        }
         //Colum
        if (this.r_1_1 === 'X' && this.r_2_1 === 'X' && this.r_3_1 === 'X') {
           this.win_info(this.player_1_name,'l_1_h',"x");
        }
        if (this.r_1_2 === 'X' && this.r_2_2 === 'X' && this.r_3_2 === 'X') {
           this.win_info(this.player_1_name,'l_2_h',"x");
        }
        if (this.r_1_3 === 'X' && this.r_2_3 === 'X' && this.r_3_3 === 'X') {
           this.win_info(this.player_1_name,'l_3_h',"x");
        }
         //Cros
        if (this.r_1_1 === 'X' && this.r_2_2 === 'X' && this.r_3_3 === 'X') {
           this.win_info(this.player_1_name,'l_1_x',"x");
        }
        if (this.r_1_3 === 'X' && this.r_2_2 === 'X' && this.r_3_1 === 'X') {
           this.win_info(this.player_1_name,'l_2_x',"x");
        }
        //Player O
        if (this.r_1_1 === 'O' && this.r_1_2 === 'O' && this.r_1_3 === 'O') {
            this.win_info(this.player_2_name,'l_1_v',"o");
        }
        if (this.r_2_1 === 'O' && this.r_2_2 === 'O' && this.r_2_3 === 'O') {
            this.win_info(this.player_2_name,'l_2_v',"o");
        }
        if (this.r_3_1 === 'O' && this.r_3_2 === 'O' && this.r_3_3 === 'O') {
            this.win_info(this.player_2_name,'l_3_v',"o");
        }
         //Colum
        if (this.r_1_1 === 'O' && this.r_2_1 === 'O' && this.r_3_1 === 'O') {
           this.win_info(this.player_2_name,'l_1_h',"o");
        }
        if (this.r_1_2 === 'O' && this.r_2_2 === 'O' && this.r_3_2 === 'O') {
           this.win_info(this.player_2_name,'l_2_h',"o");
        }
        if (this.r_1_3 === 'O' && this.r_2_3 === 'O' && this.r_3_3 === 'O') {
           this.win_info(this.player_2_name,'l_3_h',"o");
        }
         //Cros
        if (this.r_1_1 === 'O' && this.r_2_2 === 'O' && this.r_3_3 === 'O') {
           this.win_info(this.player_2_name,'l_1_x',"o");
        }
        if (this.r_1_3 === 'O' && this.r_2_2 === 'O' && this.r_3_1 === 'O') {
           this.win_info(this.player_2_name,'l_2_x',"o");
        }
        
        //Draw
        if (this.nbr_turn===9) {
            this.draw_statu=!this.draw_statu;
            
            return;
        }
        
    },
    clearBoard(){
        document.getElementById('r11').classList.remove('block');
        document.getElementById('r12').classList.remove('block');
        document.getElementById('r13').classList.remove('block');
        document.getElementById('r21').classList.remove('block');
        document.getElementById('r22').classList.remove('block');
        document.getElementById('r23').classList.remove('block');
        document.getElementById('r31').classList.remove('block');
        document.getElementById('r32').classList.remove('block');
        document.getElementById('r33').classList.remove('block');
        document.getElementById('l_1_v').style.visibility="hidden";
        document.getElementById('l_2_v').style.visibility="hidden";
        document.getElementById('l_3_v').style.visibility="hidden";
        document.getElementById('l_1_h').style.visibility="hidden";
        document.getElementById('l_2_h').style.visibility="hidden";
        document.getElementById('l_3_h').style.visibility="hidden";
        document.getElementById('l_1_x').style.visibility="hidden";
        document.getElementById('l_2_x').style.visibility="hidden";
        this.r_1_1='';
        this.r_1_2='';
        this.r_1_3='';
        this.r_2_1='';
        this.r_2_2='';
        this.r_2_3='';
        this.r_3_1='';
        this.r_3_2='';
        this.r_3_3='';
        this.nbr_turn=0;
        this.turn=false;
        this.player_1_name='Player 1';
        this.player_2_name='Player 2';
        
        
    },
    replayClick_win(){
        this.result_card=!this.result_card;
        this.clearBoard();
    },
    replayClick_draw(){
        this.draw_statu=!this.draw_statu;
        this.clearBoard();
    }
    ,
    replayClick_err(){
        this.err=!this.err;
        this.clearBoard();
    }
}
}
</script>

<style>
.board{
    min-height: 500px;
    width: 500px;
    background: rgb(15, 110, 110);
    border-radius: 15px;
    border: 5px rgb(15, 110, 110) solid;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    margin: 30px;
}
    
.row{
    display: flex;
    flex-direction: row;
    position: relative;
}
.box{
    height: 162px;
    width: 162px;
    background: paleturquoise;
    margin: 8px;
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    position: relative;
}
.box:hover{
    opacity: 0.8;
}

.box span{
    width: 150px;
    height: 150px;
    color: black;
    font-size: 130px;
}


.block{
    pointer-events: none;
    opacity: 0.4;
    
}
.content{
    display: flex;
    align-items: center;
}
.l_1_v_s{
    z-index: 1000;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    transform: rotateZ(90deg);
    border: none;
    border-radius:50px ;
    right: 47%;
    pointer-events: none;
    top: -84%;
    visibility: hidden;
}
.l_2_v_s{
    z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    transform: rotateZ(90deg);
    border: none;
    border-radius:50px ;
    right: 47%;
    pointer-events: none;
    top: -84%;
    visibility: hidden;
}
.l_3_v_s{
    z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    transform: rotateZ(90deg);
    border: none;
    border-radius:50px ;
    right: 47%;
    pointer-events: none;
    top: -84%;
    visibility: hidden;
}

.l_1_h_s{
    z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    border: none;
    border-radius:50px ;
    right: 47%;
    pointer-events: none;
    top: 14%;
    right: 80%;
    visibility: hidden;
}
.l_2_h_s{
    z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    border: none;
    border-radius:50px ;
    pointer-events: none;
    top: -84%;
    right: 232px;
    visibility: hidden;
}
.l_3_h_s{
    z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    border: none;
    border-radius:50px ;
    pointer-events: none;
    top: -330px;
    right: 67px;
    visibility: hidden;
}
.l_1_x_s{
     z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    border: none;
    border-radius:50px ;
    pointer-events: none;
    transform: rotateZ(-45deg);
    top: -150px;
    right: 235px;
    visibility: hidden;
}
.l_2_x_s{
     z-index: 5;
    position: absolute;
    width: 30px;
    height: 470px;
    background: teal;
    box-shadow: paleturquoise 1px -1px 20px 7px;
    border: none;
    border-radius:50px ;
    pointer-events: none;
    transform: rotateZ(45deg);
    top: -150px;
    right: 235px;
    visibility: hidden;
}
.platyer_card{
    background: turquoise;
   border-radius: 15px;
    display: flex;
    flex-direction: column;
    border: 5px white solid;
}
.platyer_card .title{
    background: teal;
    padding: 0 20px;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    border-bottom: 5px white solid;
}
.platyer_card input{
    background: teal;
    color: white;
    border: none;
    font-size: 2rem;
    font-weight: 700;
    text-align: center;
    width: 162px;
    height: 80px;
}


.platyer_card .score{
    color: black;
    font-size: 1.2rem;
}

.turn_card{
    background: turquoise;
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    width: 280px;
    margin: 0 auto;
    border: 5px white solid;
}
.turn_card .title{
    background: teal;
    padding: 0 20px;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    border-bottom: 5px white solid;
}

.turn_card .symb{
    color: black;
    font-size: 1.5rem;
    height: 100px;
}

.backdrop{
    top:0;
    left: 0;
    position: fixed;
    background: rgba(0, 0, 0,0.5);
    width: 100%;
    height: 100%;
    z-index: 1000;  
}
.card{
    width: 400px;
    padding: 30px;
    margin: 80px auto;
    background: turquoise;
    border-radius: 10px;
    border: 5px white solid;
    box-shadow: paleturquoise 1px -1px 20px 7px;
     z-index: 1000; 
}

.card h1{
    color: #000000;
    border: none;
    padding:0;
}
.card p{
    font-style: normal;
    color: #000000;
    font-size: 1.5rem;
}
.card button{
    border: 2px white solid;
    padding: 15px 40px;
    border-radius: 10px;
    color: white;
    background: teal;
    font-size: 1.5rem;
    cursor: pointer;
}
.card button:hover{
 opacity: 0.7;
}

@media screen and (max-width: 450px) {
    .content{
        flex-direction: column;
        padding: 20px auto;
         transform: scale(0.8);
    }
    .card{
        transform: scale(0.8);
    }
}


.title h1{
    font-size: 5rem;
}
.title h1 .first_p{
    color: turquoise;
    display: contents;
}
</style>
