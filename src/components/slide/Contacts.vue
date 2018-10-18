<template>
  <div class="container">
    <div class="left-bar fade-in-left">
      <div v-show="!send_success" >
        <h4 v-show="!send_error">{{$t("contacts.title")}}</h4>
        <h4 v-show="send_error">{{$t("contacts.error_title")}}</h4>
        <h6 v-show="!send_error">{{$t("contacts.description")}}</h6>
        <div class="buttons">
          <input
            v-model="email"
            type="text" 
            :placeholder="$t('contacts.email')" 
            class="buttons-input"
            :class="{'buttons-input-error': send_error}"
          >
          <div class="btn-main" @click="sendMail()">
            <div class="btn-title" >{{$t("contacts.subscribe")}}</div>
          </div>
        </div>
      </div>
      <div class="success-bar" v-show="send_success">
        <h4>{{$t("contacts.success_title")}}</h4>
        <div class="btn-main" @click="sendMail()">
          <div class="btn-title">{{$t("contacts.goback")}}</div>
        </div>
      </div>
    </div>
    <div class="right-bar">
    </div>
    <div class="email fade-in-fwd"><a href="mailto:hello@arq.su">hello@arq.su</a></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: null,
      send_success: false,
      send_error: false
    };
  },
  methods: {
    sendMail () {
      this.send_success = this.validEmail();
      this.send_error = !this.validEmail();
    },
    validEmail () {
      var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(this.email);
    }
  }
};
</script>

<style lang="less" scoped>
@import url("../../styles/variables.less");

.container {
  display: flex;
  flex-direction: row;
  .left-bar {
    width: @lb;
    display: flex;
    flex-direction: column;
    justify-content: center;
    @media @xs {
      width: 100%;
    }
    h4,
    h6 {
      margin-bottom: 20px;
      @media @xs {
        width: 80%;
      }
    }
    .buttons {
      display: flex;
      flex-direction: row;
      align-items: center;
      font-family: TT Norms Regular;
      font-size: 16px;
      @media @xs {
        font-size: 12px;
        width: 80%;
      }
      .buttons-input {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        border-radius: 50px;
        outline: none;
        border: none;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
        transition: box-shadow @time-description ease-in;
        margin-right: 15px;
        height: 37px;
        padding-left: 15px;
        width: 500px;
        @media @xs {
          height: 26px;
          font-size: 12px;
        }
      }
      .buttons-input:hover {
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
        transition: box-shadow @time-description ease-in;
        // color: rgba(0,0,0,1);
        // transition: color 0.5s ease-in;
      }
      .buttons-input-error {
        box-shadow: 0 2px 10px rgba(255, 0, 0, 0.5);
        transition: box-shadow @time-description ease-in;
      }
      .btn-main {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        background: rgba(61, 69, 238, 1);
        transition: background @time-description ease-in;
        border-radius: 50px;
        padding: 10px 20px;
        .btn-title {
          color: white;
          margin-left: 5px;
        }
        @media @xs {
          margin: 0;
          padding: 5px 10px;
          font-size: 12px;
        }
      }
      .btn-main:hover {
        cursor: pointer;
        background: rgba(61, 69, 238, 0.7);
        transition: background @time-description ease-in;
      }
      input {
        font-size: 16px;
        font-family: TT Norms Regular;
      }
    }
  }
  .right-bar {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: @rb;
    @media @xs {
      display: none;
    }
  }
  .email {
    position: absolute;
    font-family: TT Norms Medium;
    top: 90%;
    right: 10%;
    color: rgba(0, 0, 0, 0.3);
    -webkit-transition: color @time-description ease-in;
    transition: color @time-description ease-in;
    font-size: 16px;
    cursor: pointer;
    margin-right: 4.5%;
    margin-bottom: 5.5%;
    @media @xs {
      margin-right: 0;
      right: 14%;
      top: 90%;
      font-size: 16px;
    }
    a {
      color: inherit;
      text-decoration: inherit;
    }
  }
  .email:hover {
    color: rgba(0, 0, 0, 1);
    transition: color @time-description ease-in;
  }
  .success-bar {
    .btn-main {
      font-family: TT Norms Regular;
      background: @purple;
      border-radius: 40px;
      padding: 10px 20px;
      color: white;
      transition: background @time-description ease-in;
      display: inline-block;
      &:hover {
        cursor: pointer;
        background: rgba(61, 69, 238, 0.7);
        transition: background @time-description ease-in;
      }
    }
  }
}
.fade-in-left {
  -webkit-animation: fade-in-left @time cubic-bezier(0.39, 0.575, 0.565, 1) both;
  animation: fade-in-left @time cubic-bezier(0.39, 0.575, 0.565, 1) both;
}

@-webkit-keyframes fade-in-left {
  0% {
    -webkit-transform: translateX(-50px);
    transform: translateX(-50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0);
    transform: translateX(0);
    opacity: 1;
  }
}
@keyframes fade-in-left {
  0% {
    -webkit-transform: translateX(-50px);
    transform: translateX(-50px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0);
    transform: translateX(0);
    opacity: 1;
  }
}
.fade-in-fwd {
  -webkit-animation: fade-in-fwd 1s cubic-bezier(0.39, 0.575, 0.565, 1) both;
  animation: fade-in-fwd 1s cubic-bezier(0.39, 0.575, 0.565, 1) both;
}
@-webkit-keyframes fade-in-fwd {
  0% {
    -webkit-transform: translateZ(-80px);
    transform: translateZ(-80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
    transform: translateZ(0);
    opacity: 1;
  }
}
@keyframes fade-in-fwd {
  0% {
    -webkit-transform: translateZ(-80px);
    transform: translateZ(-80px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateZ(0);
    transform: translateZ(0);
    opacity: 1;
  }
}
</style>
