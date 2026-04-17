<template>
    <!--  -->
    <div class="house" v-if="info.houseInfos.length > 0">
        <div class="flex h-full flex-col md:flex-row items-center justify-between">
            
            <div class="flex-1 items-center justify-center py-10 font-['Noto_Sans_TC']">
                <div class="h-full info-box mx-auto flex flex-col items-center justify-center">
                    <div class="title">建案資訊</div>
                    <div class="info-items mt-4 w-full grid grid-cols-1 md:grid-cols-2 ">
                        <div class="item font-bold flex items-center w-full whitespace-nowrap"
                            v-for="item in info.houseInfos">
                            <p class="sub mr-5 pl-2 text-[#fff]" v-html="item[0]"></p>
                            <p class="whitespace-pre-line leading-normal text-left font-normal"
                                v-html="item[1]">
                            </p>
                        </div>
                        <div class="item font-bold flex items-center w-full whitespace-nowrap">
                            <p class=" pl-2 whitespace-pre-line leading-normal text-left font-normal">民間新建建築類(H-2住宅)
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- -->
    <div class="footer flex items-center justify-center w-full h-[40px] bg-[#302626]">
        <a href="https://www.lixin.com.tw/" target="_blank"><img class="hover:opacity-50"
                src="//h35.banner.tw/img//footerLogo.gif" alt="立炘數位" srcset=""></a>
        <a href="https://www.h65.tw/admin/test/login" target="_blank" class="text-white text-xs">網頁製作</a>
    </div>
</template>

<style lang="scss">
@import "@/assets/style/function.scss";

$house-c1:#32B8C3;
$house-c2:#000;
.displaynone{display: none;}
.house {
   // height: auto;
    color: $house-c2;
    font-size: size(22);
    // height:4em;
    img{height: 1.3em;vertical-align: middle;}
}
.info-box {
    width: size(800);

    .title {
        font-size: size(40);
        font-weight: 700;
        color: $house-c1;
        margin: 0 auto 1em auto;
    }

    .info-items {
        row-gap: size(20);
        column-gap: size(20);

        .item {
            line-height: size(17);
            font-size: size(16);
            align-items: flex-start;
            line-height: 1.5;
            text-align: left;
            border-left: 2px solid $house-c1;

             .sub{
              color: $house-c1;
                // min-width: 4.5em;
            }
        }
    }
}

@media screen and (max-width:768px) {
.house {
    // background:#fff;
  //  height: sizem(400);
    font-size: sizem(13);
}
    .footer {
        margin-bottom: sizem(0);
        //margin-bottom: sizem(63);
    }

    .info-box {
        width: sizem(313);
        padding: 0;

        .title {
            font-size: sizem(29);
            width: auto;
        }

        .info-items {
            row-gap: sizem(20);

            .item {
                font-size: sizem(13);
            }
        }
    }

}
</style>

<script setup>
import info from "@/info"


</script>