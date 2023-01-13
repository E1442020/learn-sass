--install with .scss not sass

--when we make .scss file global to transform into main sass ... add _ before naming that file , and don't forget to import it in fileUsing such as main.scss or other file

--in import we use @use better than @import

--when we need use file.scss that we store variable in it ... we use @use also but adding (as *) at the end

--global var strong than local var to in global styling
--local var strong than global var to in local styling

--when we need to convert global to local ... add after local  !global

--using condition like this 

                        $theme:'dark';

                        .section{
                            @if $theme=='dark' {
                                background-color: black;
                                color: #000;
                            } @else{
                                background-color: antiquewhite;
                                color: black;
                            }
                        }

--we also can use condition inside proprity like this

                    .parent{
                        background-color:if($theme=='dark',red,null)
                    }



--we can use variable with naming any thing such classes and
propirty-naming and through comment like that...

                        $position:'left';

                        .po#{$position}{
                            margin-#{$position}: 5px; /*jjjj*/
                        }

--comment like /* */ appear in main.css file
--comment like // don't appear in main.css file

--@mixin and @include is important thing is like @extend but better than it , with it we can pass proparity to any class with different vaule like that...

                            @mixin hh($vv){
                                background-color: $vv;

                            }
                            .ll{
                                @include hh(red)
                            }
                            .ff{
                            @include hh(black)
                            }

--using foR loop is very important we can use it such


                        @for $i from 1 through 100{
                            .class-#{$i}{
                                font-size: #{$i} +100;
                            }
                        }
                        ;


                        $dimensions:0;
                        @for $i from 1 through 10{
                            .circle-#{$dimensions+100}{
                                width: #{$dimensions+100};
                            }
                            $dimensions:$dimensions+100;
                        }



--Each Map in loop

(each such..)

                        $themes:red,blue;
                        @each $theme in $themes{
                            .#{$theme}{
                                .uu{
                                    background-color: $theme;

                                }
                            }
                        }


        ---another example---

                        $social:(
                    'facebook':blue,
                    'twitter':red,
                );

                @each $namee,$colorr in $social{
                    .#{$namee}{
                        background-color: $colorr;
                    }
                }
                لاحظي هنا انك استخدمتي ال key و value


--while loop ,, don't forget break that loop

                        $start:1;
                        @while $start<=10 {
                            .width-#{$start*100}{
                                width: $start*100px;
                                height: ($start*100px)/2;
                            }
                            $start:$start+1
                        }


 --grid col in bootstrap--using percentages fun--

                                $col:12;
                        @for $i from 1 through $col {
                            .col#{$i}{
                                width: percentage($i/ $col);
                            }
                        }


---function such----

                        @function half($size){
                        @return $size/2
                        };
                        $wid:800px;
                        .xx{
                        width: $wid;
                        height: half($wid);
                        }


  --mixins with media queries such as --

                    @mixin breakpoints($point){
                        @if $point==mobile{
                            @media (min-width:767px) {
                                @content;
                            }
                        }@else if $point==small{
                            @media (min-width:768px) and (max-width:991px){
                                @content;
                            }
                        }@else if $point==medium{
                            @media (min-width:992px) and (max-width:991px){
                                @content
                            }
                        }}
                                
                         -- and use it such--

                            .media{
                                @include breakpoints(small){
                                    font-size: 40px;
                                }
                            }                      