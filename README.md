基于vue的dom复制功能，可以将dom复制为png图片到剪贴板
import copy2clipboard from 'copy2clipboard'
Vue.use(copy2clipboard)

demo:
```
// <div class="png-wrap" ref="pngWrap">
//    <img width="600px" :src="require('../assets/shuiku.jpg')" alt="">
// </div>
<canvas ref="pngWrap"> ... </canvas>
<button v-copy2clipboard="copypng()">复制图片</button>

copypng() {
    return {
        target: 'pngWrap',
        scale: 1,
        handler: (param) => {
            console.log(param);
        },
    }
}
```

简单实现，主要是提供思路，目前还存在较严重的兼容问题，以后会逐步提代execCommand
- npm 不允许发布外部依赖项，所以上述 dome 使用 html2canvas 无法直接注入  小伙伴先生成canvas再使用复制