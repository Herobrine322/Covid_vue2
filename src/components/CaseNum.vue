<template>
   <div class="case-num">
      <div class="container">
          <div class="title">
              <span>截至{{formatData(modifyTime)}}全国数据统计</span>
          </div>
      </div>
            <div class="num">
          <ul class="count">
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>       
                              较昨日
                              <em style="color:rgb(247,76,49)">{{ dataIncrDecr(caseNumData.currentConfirmedIncr) }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(247,76,49)">{{ caseNumData.currentConfirmedCount }}</strong>
                      <span>现存确诊</span>
                  </div>
              </li>
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>
                              较昨日
                              <em style="color:rgb(247,130,7)">{{ dataIncrDecr(caseNumData.suspectedIncr) }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(247,130,7)">{{ caseNumData.suspectedCount }}</strong>
                      <span>现存疑似</span>
                  </div>
              </li>
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>
                              较昨日
                              <em style="color:rgb(162,90,78)">{{ dataIncrDecr(caseNumData.seriousIncr) }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(162,90,78)">{{ caseNumData.seriousCount }}</strong>
                      <span>现存重症</span>
                  </div>
              </li>
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>
                              较昨日
                              <em style="color:rgb(174, 33, 44)">+{{ caseNumData.confirmedIncr }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(174, 33, 44)">{{ caseNumData.confirmedCount }}</strong>
                      <span>累计确诊</span>
                  </div>
              </li>
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>
                              较昨日
                              <em style="color:rgb(93, 112, 146)">+{{ caseNumData.deadIncr }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(93, 112, 146)">{{ caseNumData.deadCount }}</strong>
                      <span>累计死亡</span>
                  </div>
              </li>
              <li>
                  <div class="create-item">
                      <div class="create-count">
                          <b>
                              较昨日
                              <em style="color:rgb(40, 183, 163)">+{{ caseNumData.curedIncr }}</em>
                          </b>
                      </div>
                      <strong style="color:rgb(40, 183, 163)">{{ caseNumData.curedCount }}</strong>
                      <span>累计治愈</span>
                  </div>
              </li>
          </ul>
      </div>
   </div>
</template>

<script>
export default {
    props:{
        modifyTime:{
            type: Number,
            default:function(){
                return{}
            }
        },
        caseNumData:{
            type: Object,
            default:function(){
                return{}
            }
        }
    },
     methods:{
        formatData(date){
            var date = new Date(date);
            var YY = date.getFullYear()+"-";
            var MM = ((date.getMonth()) + 1 < 10 ? "0"+ ((date.getMonth()) + 1) : (date.getMonth()) + 1) + "-" ;
            var DD = (date.getDate() < 10 ? "0"+ date.getDate() : date.getDate()) + "   "
            var hh = (date.getHours() < 10 ? "0" + date.getHours() : date.getHours()) + ":"
            var mm = date.getMinutes() < 10 ? "0" + date.getMinutes() : date.getMinutes()
            return YY + MM + DD + hh + mm;
        },
                dataIncrDecr(data){
            if(data >0 && data != 0){
                return "+"+data
            }else if(data <0 && data!=0){
                return "-"+data
            }else{
                return data;
            }
        }
     },

}
</script>

<style scoped>

.case-num {
    padding: 0.16rem;
    background: #fff;
}
.container {
    margin: -0.16rem 0 0;
    font-size: 0.12rem;
}
.title {
    display: flex;
    align-items: center;
    /* justify-content: space-between; */
    padding: 0.08rem 0 0.07rem;
    line-height: 0.24rem;
}
.title span {
    color: #666;
}
.title em {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 0.24rem;
    margin-right: -0.16rem;
    padding: 0 0.08rem;
    color: #666;
    font-style: normal;
    background-color: #f7f7f7;
    border-radius: 0.12rem 0 0 0.12rem;
}
.title em img {
    width: 0.123rem;
    height: 0.123rem;
    margin-right: 0.037rem;
}
.num {
    position: relative;
    text-align: center;
    background: #fff;
}
.num::after {
    position: absolute;
    top: -0.01rem;
    left: -0.01rem;
    display: block;
    width: 200%;
    height: 200%;
    border: 0.01rem solid #ebebeb;
    border-radius: 0.08rem;
    box-shadow: 0 0.04rem 0.12rem 0 rgba(0, 0, 0, 0.05);
    transform: scale(0.5);
    transform-origin: 0 0;
    content: "";
}
.num ul {
    flex-flow: wrap;
    position: relative;
    display: flex;
    margin: 0;
    padding: 0.08rem 0 0.12rem;
}
.num ul li {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    width: 33.3333333%;
    margin: 10px 0;
}
.num ul li .create-item {
    position: relative;
    text-align: center;
}
.num ul li .create-item .create-count {
    display: flex;
    align-items: center;
    height: 0.12rem;
    margin-bottom: 0.02rem;
    color: #666;
    font-weight: 400;
    font-size: 0.09rem;
}
.num ul li .create-item .create-count em {
    font-weight: 400;
    font-style: normal;
}
.num ul li strong {
    margin-bottom: 0.01rem;
    font-weight: 700;
    font-size: 0.2rem;
    line-height: 0.25rem;
}
.num ul li span {
    display: block;
    color: #333;
    font-weight: 700;
    font-size: 0.11rem;
    line-height: 0.15rem;
}

</style>