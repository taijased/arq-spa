<template>
    <div class="error" @click="$router.push('/')">
        <div class="error-title">404</div>
        <div class="error-subtitle">Страница не найдена</div>
        <div class="btn-error">Вернуться на главную</div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="less" scoped>
@import url('../styles/variables.less');
@import url('../styles/font.less');

.error {
    width: 400px;
    height: 400px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, 25%);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .error-title {
        color: @purple;
        font-family: TT Norms Bold;
        line-height: normal;
        font-size: 200px;
    }
    .error-subtitle {
        font-family: TT Norms Medium;
        line-height: normal;
        font-size: 26px;
        color: #000;
    }
    .btn-error {
        font-family: TT Norms Regular;
        background: @purple;
        border-radius: 40px;
        padding: 10px 20px;
        color: white;
        margin-top: 30px;
        transition: background @time-description ease-in;
        &:hover {
            cursor: pointer;
            background: rgba(61, 69, 238, 0.7);
            transition: background @time-description ease-in;
        }
    }
}
</style>
