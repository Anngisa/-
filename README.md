var going = false
var nY = 0 // 实际计算出来
var nX = 0 // 实际计算出来

// container传css选择器
const mousemoveAn = function (sX, sY, container, ratioY = 0.02, ratioX = 0.015) {
  if (going) {
    return false
  }
  if (Math.abs(sX - nX) > 2) {
    nX += (sX - nX) / 6
  } else {
    nX = sX
  }

  if (Math.abs(sY - nY) > 2) {
    nY += (sY - nY) / 6
  } else {
    nY = sY
  }
  if (container instanceof Array) {
    container.forEach(item => {
      $(item).css({
        '-webkit-transition': 'all 0 linear',
        '-moz-transition': 'all 0 linear',
        '-o-transition': 'all 0 linear',
        '-ms-transition': 'all 0 linear',
        'transition': 'all 0 linear',
        '-webkit-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
        '-moz-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
        '-o-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
        '-ms-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
        'transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)'
      })
    })
  } else {
    $(container).css({
      '-webkit-transition': 'all 0 linear',
      '-moz-transition': 'all 0 linear',
      '-o-transition': 'all 0 linear',
      '-ms-transition': 'all 0 linear',
      'transition': 'all 0 linear',
      '-webkit-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
      '-moz-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
      '-o-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
      '-ms-transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)',
      'transform': 'perspective(3000px) rotateY(' + (nX * ratioY) + 'deg) rotateX(' + (-nY * ratioX) + 'deg)'
    })
  }
}
export default mousemoveAn

在调用的地方
$('body').on('mousemove', function (e) {
  sX = (e.clientX - win_w / 2)
  sY = (e.clientY - win_h / 2)
  mousemoveAn(sX, sY, '.role')
/*  mousemoveAn(sX, sY, '#banner-wrap', 0.001, 0.01)
  mousemoveAn(sX, sY, '.perspective-wrap-kv3', 0.009, 0.015)*/
})
