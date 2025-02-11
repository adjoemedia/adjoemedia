@extends('system.user.publisher.iframe.master')

@push('style')
    <style>
        .menu-close {
            width: 34px;
            height: 34px;
            background: #fff;
            border-radius: 50%;
            position: absolute;
            right: 10px;
            ;
            top: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .top-header {
            background: #F6F6F6;
            width: 100%;
            position: relative;
            border-radius: 0;
            padding: 0 1rem;
        }

        .top-header #menu-toggle {
            cursor: pointer;
        }

        .top-header #menu-toggle i {
            font-size: 20px;
        }

        .top-header .inner-content {
            display: flex;
            font-style: normal;
            align-items: center;
            justify-content: space-between;
            padding-top: 2.5rem;
            padding-bottom: 2.5rem;
        }

        .top-header .inner-content .history-icon i {
            font-size: 26px;
        }

        .top-header .inner-content .white-box {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: #fff;
            display: flex;
            align-items: center;
            justify-content: center
        }



        .top-header .image img {
            width: 100px;
        }

        .top-header .nav-tabs.top-offers {
            border-radius: 20px;
            background: #fff;
            gap: 0;
            padding: 2px;
            overflow: hidden;
            width: 100%;
            max-width: 100%;
        }

        .top-header .nav-tabs.top-offers .nav-link {
            border: none;
            color: #000;
            background: transparent;
            border-radius: 20px;
            padding: 6px;
            font-size: .9rem;
            font-weight: 400;
            display: block;
        }

        .top-header .nav-tabs.top-offers .nav-link.active {
            color: #fff;
            background: #8338EC
        }

        .offers-list {
            width: 95%;
            margin: auto;
            margin-top: 26px
        }


        body .offers-list .wannads-wrapper .card {
            background-color: #fff !important
        }

        body .offers-list .wannads-wrapper .card .titleoffer {
            font-size: 0.9rem;
            font-weight: 600;
            color: #000;
            word-break: break-all
        }

        body .offers-list .wannads-wrapper .card .titleoffer+p {
            font-size: 0.8rem;
            font-weight: 400;
            margin-bottom: 10px;
            color: #444;
        }

        /* new design */
        .wannads-wrapper .offer-content {
            width: 100%;
            display: flex;
            align-items: center;
            gap: 10px
        }

        .wannads-wrapper .offer-content .left-part {
            align-self: flex-start
        }

        .wannads-wrapper .offer-content .right-part {
            display: flex;
            align-items: center;
            justify-content: space-between;
            width: 100%;
        }

        .wannads-wrapper .offer-content .right-part .content-part {
            width: 100%
        }

        .wannads-wrapper .offer-content .right-part .content-part .inner-part {
            display: flex;
            align-items: center;
            width: 100%;
            justify-content: space-between;
        }

        .wannads-wrapper .offer-wrapper .start-offer-wrapper {
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: #F27332;
            color: #fff;
            text-transform: uppercase;
            padding: 9px;
            border-radius: 10px;
            margin-top: 10px;
            font-weight: 500;
            font-size: .95rem;
            position: relative;
        }

        .wannads-wrapper .offer-wrapper .reward {
            position: absolute;
            left: 0px;
            background: #FCAC78;
            padding: 9px;
            border-top-left-radius: 9px;
            border-bottom-left-radius: 9px;
        }

        .wannads-wrapper .offer-wrapper .start-offer-wrapper a {
            color: #fff;
            padding-left: 20%
        }

        .wannads-wrapper .offer-wrapper .start-offer-wrapper a:hover {
            color: #fff;
            text-decoration: none
        }

        #sidebar {
            position: fixed;
            top: 0;
            right: 0;
            height: 100vh;
            background: #FCFAFA;
            width: 250px;
            max-width: 100%;
            transform: translateX(250px);
            transition: all .5s;
        }

        #sidebar.active-sidebar {
            transform: translateX(0)
        }

        #sidebar .logo-part {
            text-align: center;
        }

        #sidebar .logo-part img {

            width: 200px;
            display: block;
            margin-top: 15px;
            margin-left: 15px;
        }


        #sidebar .nav-links {
            display: block;
            padding: 0;
            margin-top: 21px;
        }

        #sidebar .nav-links a {
            display: block;
            padding: 8px 10px;
            color: #444;
            margin-bottom: 6px;
            font-size: 14px;
        }
    </style>
@endpush


@section('content')
    <div class="d-flex justify-content-center">
        <div class="top-header">
            <div class="inner-content">
                <a href="javascript:void(0);" data-bs-toggle="modal" data-bs-target="#user_history_modal" class="history-icon">
                    <div class="white-box">
                        <svg width="27" height="27" viewBox="0 0 27 27" fill="none"
                            xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <rect width="27" height="27" fill="url(#pattern0)" />
                            <defs>
                                <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1"
                                    height="1">
                                    <use xlink:href="#image0_23_1411" transform="scale(0.0025)" />
                                </pattern>
                                <image id="image0_23_1411" width="400" height="400"
                                    xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZAAAAGQCAYAAACAvzbMAAAgAElEQVR4Aey9B1iVZ7b2P6d958xMZtITjTGJvSMg2AAFsfeGHTv2rthFbNgRQVBURFFQSY+Tpkk00Rhjxa6JMT1Gjcmc8535n+/MTFz/617Ps973ed+9MSbfN2dmyJPreq692WzKXtm8P+91r/KLX9j/bARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBGwEbARsBMpOBIjoH/bv3//Pe/bs+VVeXt5vCgsL7y/atOnR/OzsctvWrXtwx44dv83Nzf1VcXHx/8Jzy84rt6/ERsBGwEbARuAHI1BcXPxP+fn59+Xl5dXYtXVr651bCyfsLNieviM/f1dB3pYD2zbnXdq2Ke+L/E2bv96yadM3ebkbv8vL3fj7vA25t/I25F7flJP75ab1uVc25+Qe2ZS94bm8dRvW5WZnz9y4bn23rKysepmZmQ8Xp6b+rx/8RewTbARsBGwEbAT+tiMAtbAzb+djRdu3t91dWLiweEfh60UF26/s2Lr1Pwryt36/dXMe5W/aTFtyN1LehlzatH49bczOUScnh3LXZdOGrHWUk5lJ2Rlr+azLWEt81mTQujUZlJW+hrLSM25npWf8YV16xmdZGRnvZa1ek7l2ZXqf7KXpVdPT039pFcvf9vvE/nY2AjYCNgIc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AVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU8AUMAVMAVPAFDAFTAFTwBQwBUwBU+DUVOD/ABconGIB05xJAAAAAElFTkSuQmCC" />
                            </defs>
                        </svg>
                    </div>
                </a>
                <div class="image">
                    <img src="{{ asset('asset/home_1/img/adjoemedialogo.svg') }}" alt="">
                </div>
                <div id="menu-toggle">
                    <div class="white-box">
                        <svg width="16" height="16" viewBox="0 0 18 18" fill="none"
                            xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M0 1C0 0.447715 0.447715 0 1 0H7C7.55228 0 8 0.447715 8 1V7C8 7.55228 7.55228 8 7 8H1C0.447715 8 0 7.55228 0 7V1ZM0 11C0 10.4477 0.447715 10 1 10H7C7.55228 10 8 10.4477 8 11V17C8 17.5523 7.55228 18 7 18H1C0.447715 18 0 17.5523 0 17V11ZM10 1C10 0.447715 10.4477 0 11 0H17C17.5523 0 18 0.447715 18 1V7C18 7.55228 17.5523 8 17 8H11C10.4477 8 10 7.55228 10 7V1ZM10 11C10 10.4477 10.4477 10 11 10H17C17.5523 10 18 10.4477 18 11V17C18 17.5523 17.5523 18 17 18H11C10.4477 18 10 17.5523 10 17V11Z"
                                fill="#3A3A3A" />
                        </svg>
                    </div>
                </div>
            </div>



            <ul class="nav nav-tabs top-offers" id="myTab" role="tablist">
                @if (set('enable_trends_offers'))
                    <li class="nav-item" role="presentation">
                        <a class="offer-nav nav-link active" id="first_offer-tab" data-bs-toggle="tab" href="#first_offer"
                            role="tab" aria-controls="first_offer" aria-selected="true">Offers</a>
                    </li>
                    <li class="nav-item" role="presentation">
                        <a class="offer-nav nav-link" id="surveys-tab" data-bs-toggle="tab" href="#surveys" role="tab"
                            aria-controls="surveys" aria-selected="true">Surveys</a>
                    </li>
                @endif
            </ul>
        </div>
    </div>
    <div class="offers-list">
        @php
            $i = 1;
        @endphp

        <div class="tab-content" id="myTabContent">
            @if (set('enable_top_trends'))
                <div class="offer-tap tab-pane fade " id="ads_offers" role="tabpanel" aria-labelledby="first_offer-tab">
                    <div id="load_ads_offers"></div>
                </div>
            @endif
            @if (set('enable_trends_offers'))
                <div class="offer-tap tab-pane fade active show" id="first_offer" role="tabpanel"
                    aria-labelledby="first_offer-tab">
                    <div id="load_custom_offers"></div>
                    <div id="load_bitlabs"></div>
                    <div id="load_lootably"></div>
                    <div id="load_hangmyads"></div>
                    <div id="load_notik"></div>
                    <div id="load_revlum"></div>
                    <div id="load_adscendmedia"></div>
                    <div id="load_adgatemedia"></div>
                    <div id="load_wannads"></div>
                    <div id="load_adgem"></div>
                    <div id="load_offertoro"></div>
                </div>

                <div class="offer-tap tab-pane fade active show" id="surveys">
                    <div id="load_notik_surveys"></div>
                </div>
            @endif
            @forelse($offers as $offer)
                <div class="offer-tap tab-pane fade " id="{{ $offer->name }}" role="tabpanel"
                    aria-labelledby="{{ $offer->name }}-tab">
                    <iframe src="{{ \Str::replace('subId', $user . '_' . $site->id, $offer->iframe_url) }}" height="700px"
                        width="100%"></iframe>
                </div>
            @empty
                <p></p>
            @endforelse

            @foreach ($builtin_offers->useIframe as $offer)
                @switch ($offer->id)
                    @case('3')
                        <div class="offer-tap tab-pane fade " id="tab_{{ $offer->id }}" role="tabpanel"
                            aria-labelledby="{{ $offer->id }}-tab">
                            <iframe
                                src="https://wall.wannads.com/wall?apiKey={{ $offer->public_key }}&userId={{ $user . '_' . $site->id }}"
                                height="700px" width="100%"></iframe>
                        </div>
                    @case('4')
                        <div class="offer-tap tab-pane fade " id="tab_{{ $offer->id }}" role="tabpanel"
                            aria-labelledby="{{ $offer->id }}-tab">
                            <iframe
                                src="https://api.adgem.com/v1/wall?appid={{ $offer->public_key }}&playerid={{ $user . '_' . $site->id }}"
                                height="700px" width="100%"></iframe>
                        </div>
                    @case('5')
                        <div class="offer-tap tab-pane fade " id="tab_{{ $offer->id }}" role="tabpanel"
                            aria-labelledby="{{ $offer->id }}-tab">
                            <iframe
                                src="https://www.offertoro.com/ifr/show/{{ $offer->public_key }}/{{ $user . '_' . $site->id }}/{{ $offer->secret_key }}"
                                height="700px" width="100%"></iframe>
                        </div>
                    @break
                @endswitch
            @endforeach
        </div>
    </div>
    </div>


    <div id="sidebar">

        <a href="javascript:void(0);" id="menu-close" class="menu-close">
            <svg width="24px" height="24px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
                <g id="SVGRepo_iconCarrier">
                    <rect width="24" height="24" fill="white"></rect>
                    <path d="M7 17L16.8995 7.10051" stroke="#000000" stroke-linecap="round" stroke-linejoin="round">
                    </path>
                    <path d="M7 7.00001L16.8995 16.8995" stroke="#000000" stroke-linecap="round" stroke-linejoin="round">
                    </path>
                </g>
            </svg>
        </a>

        <div class="nav-links">
            <a href="/privacy-policy"><img src="/asset/home_1/img/policysidebar.svg" style="width:21px;"> Privacy</a>
            <a href="/tos"><img src="/asset/home_1/img/termssidebar.svg" style="width:21px;"> Terms</a>
            <a href="mailto:support@adjoemedia.com"><img src="/asset/home_1/img/supportsidebar.svg" style="width:21px;">
                Support</a>
            <a href="mailto:support@adjoemedia.com"><img src="/asset/home_1/img/advertisesidebar.svg"
                    style="width:21px;"> Advertise</a>

        </div>
    </div>
@endsection
@push('style')
    <style>
        img.brand-img {
            height: 56px;
            width: 213px;
        }

        .collapse .navbar-nav a.nav-link {
            margin-right: 19px;
        }

        .navbar-light .navbar-toggler-icon {
            background-color: #bd9243;
            background-image: url("data:image/png;base64,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");
            margin-right: 15px;
            box-shadow: none !important;
            height: 30px;
            width: 30px;
        }

        button#user_history {

            font-weight: 600;
            margin-left: 5px;
            margin-right: 15px;
        }

        .nav-tabs {
            background: #23211b;
            border: none;
            border-radius: 12px;
            padding: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            max-width: 420px;
            padding: 0;
            margin: 10px auto;
            overflow-y: auto;
        }

        .nav-tabs .nav-link {
            color: #fff;
            font-weight: 300;
            border-radius: 0px;
            font-size: 1rem;
            background: #23211b;
            border-radius: 0px;
            padding: 12px 25px;
        }

        .nav-tabs .nav-item {
            margin-bottom: 0 !important;
            display: block !important;
            width: 50% !important;
            text-align: center !important;
        }

        .nav-tabs .nav-item.show .nav-link,
        .nav-tabs .nav-link.active {
            background-color: #bd9243;
            border: none;
            color: #ffffff;
            border-radius: 6px;
        }

        .wannads-wrapper .card {
            box-shadow: none;
            margin-bottom: 10px;
            border-radius: 10px
        }

        .wannads-wrapper .card .btn {

            padding: 7px 0;
            font-size: 17px;
            width: 210px;
            float: right;
        }

        @media (max-width:780px) {
            .wannads-wrapper .card .btn {

                font-size: 12px;
            }
        }

        img.offer-image {
            width: 80px;
            border-radius: 10px;
            object-fit: contain;
        }

        @media screen and (max-width:830px) {
            img.offer-image {
                width: 60px;
            }
        }

        img.we-artwork__image.ember334656 {
            height: 100px;
            border-radius: 10px
        }
    </style>
@endpush

@push('script')
    <script>
        $(document).ready(function() {
            $.ajax({
                type: 'GET',
                url: '{{ route('publish.iframe.custom-offer') }}',
                data: {
                    user: "{{ $user }}",
                    key: "{{ $site->st_key }}"
                },
                success: function(response) {
                    console.log(response)
                    $('#load_custom_offers').html(response.views);
                }
            });

            @if (set('enable_top_trends'))
                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.ads-offers') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_ads_offers').html(response);
                    }
                });
            @endif
            @if (set('enable_trends_offers'))


                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.hangmyads') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_hangmyads').html(response);
                    }
                });


                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.lootably') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_lootably').html(response);
                    }
                });

                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.bitlabs') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_bitlabs').html(response);
                    }
                });


                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.notik') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_notik').html(response);
                    }

                });

                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.notik.surveys') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_notik_surveys').html(response);
                    }

                });


                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.revlum') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_revlum').html(response);
                    }

                });


                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.wannads') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_wannads').html(response);
                    }
                });

                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.adgem') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_adgem').html(response);
                    }
                });

                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.offertoro') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_offertoro').html(response);
                    }
                });
                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.adgatemedia') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_adgatemedia').html(response);
                    }
                });
                $.ajax({
                    type: 'GET',
                    url: '{{ route('publish.iframe.offer.adscendmedia') }}',
                    data: {
                        user: "{{ $user }}",
                        site: "{{ $site->id }}"
                    },
                    success: function(response) {
                        $('#load_adscendmedia').html(response);
                    }
                });
            @endif


            $("#menu-toggle").on("click", function() {
                $("#sidebar").toggleClass('active-sidebar')
            });

            $("#menu-close").on("click", function() {
                $("#sidebar").removeClass('active-sidebar')
            });

        });

        $(document).ready(function() {
            $(document).on('click', 'a.start-offer-callback', function(e) {
                e.preventDefault();

                let siteid = $(this).data('siteid');
                let url = $(this).data('url');

                $.ajax({
                    method: "GET",
                    url: "{{ route('offer.navigate') }}",
                    data: {
                        siteid: siteid,
                    }
                });

                window.open(url, '_blank');

            });
        });
    </script>
@endpush
