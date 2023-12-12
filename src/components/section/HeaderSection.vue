<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>AniMovie</h1>
                <nav>
                    <ul>
                        <li><a href="#">DISNEY Movie</a></li>
                        <li><a href="#">PIXAR Movie</a></li>
                        <li><a href="#">MARVEL Movie</a></li>
                    </ul>
                </nav>
            </div>
            <div class="header__intro"
                style="backgroundImage:url(https://image.tmdb.org/t/p/w500/kjQBrc00fB2RjHZB3PGR4w9ibpz.jpg)">
                <div class="container">
                    <div class="left">
                        <img src="https://image.tmdb.org/t/p/w500/4Y1WNkd88JXmGfhtWR7dmDAo1T2.jpg" alt="dd">
                    </div>
                    <div class="right">
                        <h2>Elemental</h2>
                        <p class="desc">In a city where fire, water, land, and air residents live together, a fiery young
                            woman and a go-with-flow guy are about to discover something elemental: How much they actually
                            have in common.</p>
                        <p class="date">RELEASE: June, 16, 2023</p>
                        <p class="average">RATE: 7/10</p>
                        <div class="credits">
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/qoOp8XvZ4v7B0C9ZmtoRCl9CDSO.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/mLKvNuCJSgyK0WdLd4ogO81sOO1.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/lm2FKwj2zO8ZsqMNFHm4KMtlNlM.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/cDcB8mKP1GiIeoM3Qe7GIucs0iv.jpg" alt="">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w500/w2t30L5Cmr34myAaUobLoSgsLfS.jpg" alt="">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        justify-content: space-between;
        align-items: center;

        h1 {
            font-size: 23px;
            font-weight: 800;
            color: #fff;
            background-color: #2D2F3B;
            margin: 20px;
            border-radius: 20px;
            display: inline-block;
            padding: 10px;
        }

        nav {
            ul {
                display: flex;

                li {
                    margin: 1rem;
                    padding: 0.8rem;
                    border-radius: 10px;
                    color: #fff;
                    font-weight: 800;
                    font-size: 15px;

                    &:hover {
                        background-color: #3e4151;
                    }
                }
            }
        }

    }


}

.header__intro {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;
    background-color: #fff;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #ffffff00;
        backdrop-filter: blur(40px);
        z-index: 1;
    }

    .container {
        display: flex;
        justify-content: space-between;
        position: relative;
        z-index: 10;


        .left {
            width: 350px;
        }

        .right {
            width: calc(100% - 400px);
            color: #fff;

            h2 {
                font-size: 30px;
                margin-bottom: 10px;
            }

            .desc {
                margin-bottom: 10px;

            }
        }
    }
}

.credits {
    display: flex;
    padding-top: 6.5rem;
}

.credits img {
    padding-left: 0.5rem;

}
</style>