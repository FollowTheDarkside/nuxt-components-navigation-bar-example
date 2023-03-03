<template>
<header class="header" id="head_wrap">
    <div class="inner">
        <div id="mobile-head">
            <h1 class="logo">
                HOGE
            </h1>
            <div id="nav-toggle"> 
                <div>
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </div>
        </div>
        <nav id="global-nav">
            <ul>
                <li class=""><NuxtLink to="/">TOP</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink to="/about">ABOUT</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink to="/info">INFO</NuxtLink></li>
                <li class="navbar-menu hover:text-gray-400 duration-150"><NuxtLink to="/contact">CONTACT</NuxtLink></li>
            </ul>
        </nav>
    </div> 
</header>
</template>

<style lang="scss" scoped>
$mobileSize: 768px; // tailwind's md size
$baseBackgroundColor: rgba(250,250,250,0.5);
$baseTextColor: rgba(25,25,25,1.0);

#head_wrap {
    top: -100px;
    position: relative;
    width: 100%;
    margin: 100px auto 0;
    line-height: 1;
    z-index: 999;
    height: 0px;
    text-decoration: none;
    a {
        text-decoration: none;
    }
    .inner {
        width: 100%;
        margin: 0 auto;
        &:after {
            content: "";
            clear: both;
            display: block;
        }
        position: relative;
    }
    .logo {
        float: left;
        font-size: 36px;
    }
}
#global-nav {
    position: absolute;
    right: 0;
    top: 0;
    ul {
        list-style: none;
        font-size: 14px;
        margin-right: 10px;
        display: inline-flex;
        @media (max-width: ($mobileSize)) {
            display: block;
            margin-right: 0px;
        }
        li{
            padding: 20px 10px;
            &:last-child{
                border-right: none;
            }
            @media (max-width: ($mobileSize)) {
                border-right: none;
            }
            a {
                padding: 0 5px;
                padding: 2px;
                transition : all .6s ease 0s;
                box-sizing: border-box;
                font-weight: bold;
                // &:hover {
                // }
            }
        }
    }
} 
/* Fixed */
#head_wrap.fixed {
    // background-color: $baseBackgroundColor;
    margin-top: 0;
    top: 0;
    position: fixed;
    height: 100px;
    transition: top 0.65s ease-in;
    -webkit-transition: top 0.65s ease-in;
    -moz-transition: top 0.65s ease-in;
    z-index: 9999;
    .logo {
        font-size: 36px;
        color: ($baseTextColor);
    }
    #global-nav ul li a {
        color: ($baseTextColor);
        padding: 0 20px;
    }
}
/* Toggle Button */
#nav-toggle {
    display: none;
    position: absolute;
    right: 12px;
    top: 14px;
    width: 34px;
    height: 36px;
    cursor: pointer;
    z-index: 101;
    div {
        position: relative;
    }
}
@media (max-width: ($mobileSize)) {
    #head_wrap {
        top: 0;
        position: fixed;
        margin-top: 0;
        width: 100%;
        padding: 0;
        .inner {
            width: 100%;
            padding: 0;
        }
        /* Fixed reset */
        .fixed {
            padding-top: 0;
            background: transparent;
        }
    }
    #mobile-head {
        background: ($baseBackgroundColor);
        box-shadow: 0px 2px 2px 1px rgba(0, 0, 0, 0.2);
        width: 100%;
        height: 56px;
        z-index: 999;
        position: relative;
    }
    #head_wrap.fixed .logo,
    #head_wrap .logo {
        position: absolute;
        left: 13px;
        top: 13px;
        color: ($baseTextColor);
        font-size: 26px;
    }
    #global-nav {
        position: absolute;
        /* 開いてないときは画面外に配置 */
        top: -500px;
        background: ($baseBackgroundColor);
        width: 100%;
        text-align: center;
        -webkit-transition: .5s ease-in-out;
        -moz-transition: .5s ease-in-out;
        transition: .5s ease-in-out;
        ul {
            list-style: none;
            position: static;
            right: 0;
            bottom: 0;
            font-size: 14px;
            margin-top: 20px;
            li {
                float: none;
                position: static;
            }
        }
    }
    #head_wrap #global-nav ul li a,
    #head_wrap.fixed #global-nav ul li a {
        width: 100%;
        display: block;
        padding: 5px 0;
    }
    #nav-toggle {
        display: block;
    }
    /* #nav-toggle 切り替えアニメーション */
    #nav-toggle {
        span {
        display: block;
        position: absolute;
        height: 4px;
        width: 100%;
        background: ($baseTextColor);
        left: 0;
        -webkit-transition: .35s ease-in-out;
        -moz-transition: .35s ease-in-out;
        transition: .35s ease-in-out;
            &:nth-child(1) {
            top: 0;
            }
            &:nth-child(2) {
            top: 11px;
            }
            &:nth-child(3) {
            top: 22px;
            }
        }
    }
    .open {
        #nav-toggle {
            span {
                &:nth-child(1) {
                    top: 11px;
                    -webkit-transform: rotate(315deg);
                    -moz-transform: rotate(315deg);
                    transform: rotate(315deg);
                }
                &:nth-child(2) {
                    width: 0;
                    left: 50%;
                }
                &:nth-child(3) {
                    top: 11px;
                    -webkit-transform: rotate(-315deg);
                    -moz-transform: rotate(-315deg);
                    transform: rotate(-315deg);
                }
            }
        }
    } 

    /* #global-nav スライドアニメーション */
    .open #global-nav {
        /* #global-nav top + #mobile-head height */
        -moz-transform: translateY(556px);
        -webkit-transform: translateY(556px);
        transform: translateY(556px);
    }
}
</style>

<script>
// import { ref } from 'vue';
export default {
//   setup() {
//     let showMenu = ref(false);
//     const toggleNav = () => (showMenu.value = !showMenu.value);
//     const closeNav = () => (showMenu.value = false);
//     return { showMenu, toggleNav, closeNav};
//   },
  mounted(){
    console.log("Mounted...");

    // Fix nav when scrolling specified width
    window.addEventListener("scroll",function () {
        let scrollPos = document.documentElement.scrollTop || document.body.scrollTop;
        var h = document.getElementById("head_wrap");
        if(scrollPos > 350){
            h.classList.add("fixed");
        }else{
            h.classList.remove("fixed");
        }
    },
        { passive: true } // for smooth scrolling
    );

    // Nav Toggle Button
    document.getElementById("nav-toggle").addEventListener("click",function () {
        document.getElementById("head_wrap").classList.toggle("open");
    }, { passive: true });
    document.getElementById("global-nav").addEventListener("click",function () {
        document.getElementById("head_wrap").classList.toggle("open");
    }, { passive: true });
  },
};
</script>