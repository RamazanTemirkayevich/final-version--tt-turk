<template>
    <header class="header">
        <div class="container header-container">
            <div class="header-nav">
                <div class="header-nav__logo">
                    <img src="@/assets/TTlogo.svg" alt="">
                </div>
                <div class="header-nav__btns">
                    <div class="btns-settings">
                        <a href="#">
                            <img src="@/assets/icons/settings.svg" alt="">
                        </a>
                    </div>
                    <div class="btns-admin">
                        <a href="#">
                            <img src="@/assets/icons/admin.svg" alt="">
                            Log in
                        </a>
                    </div>
                </div>
            </div>
            <div class="header-nav--desk">
                <ul class="header-nav--desk__list">
                    <li class="header-nav--desk__list-link">
                        <a class="dropdown-01 link-dropdown" href="#">
                            <select class="select-wrapper" id="">
                                <option value="">Sell at Turk</option>
                                <option value="">Sell at Turk</option>
                                <option value="">Sell at Turk</option>
                            </select>    
                        </a>
                    </li>
                    <div>
                        <p>I</p>
                    </div>
                    <li class="header-nav--desk__list-link">
                        <a class="dropdown-02 link-dropdown" href="#">
                            <select class="select-wrapper" id="">
                                <option value="">Help</option>
                                <option value="">Help</option>
                                <option value="">Help</option>
                            </select>
                        </a>
                    </li>
                    <li class="header-nav--desk__list-link">
                        <a class="dropdown-03" href="#">Mobile app
                            <div>
                                <p>I</p>
                            </div>
                        </a>
                    </li>
                    <li class="header-nav--desk__list-link">
                        <a class="dropdown-04 link-dropdown" href="#">
                            <select class="select-wrapper" id="">
                                <option value="">$ USD</option>
                                <option value="">$ USD</option>
                                <option value="">$ USD</option>
                            </select>
                        </a>
                    </li>
                    <li class="header-nav--desk__list-link">
                        <a class="dropdown-05 link-dropdown" href="#">
                            <img src="@/assets/icons/en.svg">
                            <select class="select-wrapper" id="">
                                <option value="">English</option>
                                <option value="">English</option>
                                <option value="">English</option>
                            </select>
                        </a>
                    </li>
                </ul>
            </div>
            <div class="header-search">
                <div class="header-search__logo">
                    <img src="@/assets/icons/desktop-logo.svg" alt="">
                </div>
                <a href="#" class="header-search__btn">
                    <img src="@/assets/icons/head-btn.svg" alt="">
                </a>
                <form action="">
                    <div class="header-search__form">
                        <input type="text" placeholder="Search in Turk">
                        <div class="header-search__form--select">
                            <select name="" id="">
                                <option value="">Everywhere</option>
                                <option value=""></option>
                                <option value=""></option>
                            </select>
                        </div>
                        <div class="header-search__form--btn">
                            <a href="#">Search</a>
                            <img src="@/assets/icons/search.svg" alt="">
                        </div>
                    </div>
                </form>
                <ul class="header-search__list">
                    <li class="header-search__list--item">
                        <img src="@/assets/icons/admin-desktop.svg" alt="">
                        <a href="#">Log in</a>
                    </li>
                    <li class="header-search__list--item">
                        <img src="@/assets/icons/orders.svg" alt="">
                        <a href="#">Orders</a>
                    </li>
                    <li class="header-search__list--item">
                        <img src="@/assets/icons/deffered.svg" alt="">
                        <a href="#">Deferred</a>
                    </li>
                    <li class="header-search__list--item">
                        <img src="@/assets/icons/cart.svg" alt="">
                        <a href="#">Shop cart</a>
                    </li>
                </ul>
            </div>
        </div>
    </header>
</template>

