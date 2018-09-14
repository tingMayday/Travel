<template>
    <div class="adverts">
        <ul class="adverts_list">
            <li class="item left">
                <a href="">
                    <img src="@/assets/images/ad1.png" alt="">
                </a>
            </li>
            <li class="item">
                <a href="">
                    <img src="@/assets/images/ad2.png" alt="">
                </a>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'HomeAdvert',
    data(){
        return{
        }
    }
}
</script>

<style lang="scss" scped>
    .adverts{
        padding: .2rem 0;
        background: #eee;
        .adverts_list{
            display: flex;
            background: #fff;
            .item{
                width: 50%;
                &.left{
                    border-right: .01rem solid #eee;
                }
                img{
                    width: 100%;
                    padding: .2rem;
                    box-sizing: border-box;
                }
            }
        }
    }
</style>
