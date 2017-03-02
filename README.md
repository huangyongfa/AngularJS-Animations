# AngularJS-Animations
Angular动画的语法实例，通过ng指令结合JavaScript来实现
指令事件集
 ![此处输入图片的描述][1]
  JavaScript动画基本的框架
  

    angular.module('coursesApp').animation('.name-of-animation', function(<injectables>) {
      return {
        event: function(elem, done){
          //logic of animation
          done();
        }
      };
    });

**ng-view动画**

触发 `<div ng-view class="view-slide-in"></div>`
脚本：

        courseAppAnimations.animation('.view-slide-in', function () {
          return {
            enter: function(element, done) {
              element.css({
                opacity: 0.5,
                position: "relative",
                top: "10px",
                left: "20px"
              })
              .animate({
                top: 0,
                left: 0,
                opacity: 1
                }, 1000, done);
            }
          };
    
    });

**ng-repeat 动画**

    courseAppAnimations.animation('.repeat-animation', function () {
      return {
        enter : function(element, done) {
          console.log("entering...");
          var width = element.width();
          element.css({
            position: 'relative',
            left: -10,
            opacity: 0
          });
          element.animate({
            left: 0,
            opacity: 1
          }, done);
        },
        leave : function(element, done) {
          element.css({
            position: 'relative',
            left: 0,
            opacity: 1
          });
          element.animate({
            left: -10,
            opacity: 0
          }, done);
        },
        move : function(element, done) {
          element.css({
            left: "2px",
            opacity: 0.5
          });
          element.animate({
            left: "0px",
            opacity: 1
          }, done);
        }
      };
    });

**Ng-hide动画**

    courseAppAnimations.animation('.hide-animation', function () {
      return {
        beforeAddClass : function(element, className, done) {
          if (className === 'ng-hide') {
            element.animate({
              opacity: 0
            },500, done);
          } else {
            done();
          }
        },
        removeClass : function(element, className, done) {
          if (className === 'ng-hide') {
          element.css('opacity',0);
          element.animate({
              opacity: 1
            }, 500, done);
          } else {
            done();
          }
        }
      };
    });


  [1]: http://thumbnail0.baidupcs.com/thumbnail/6df518bb03c285c911ae1d5b0ec64767?fid=3944337783-250528-295890824823393&time=1488416400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-htmUc4ugJBOy2KI7emry/E2cDE4=&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=1401100974761465644&dp-callid=0&size=c710_u400&quality=100
