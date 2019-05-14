// pages/list/list.js
const app = getApp()
Page({
    data: {
        navData: [{
                text: '首页'
            },
            {
                text: '健康'
            },
            {
                text: '情感'
            },
            {
                text: '职场'
            }
        ],
        currentTab: 0,
        navScrollLeft: 0,
        theight: '',
        toView: '',
        alltop: [],
    },
    //事件处理函数
    onLoad: function() {

        wx.getSystemInfo({
            success: (res) => {
                console.log('res', res)
                this.setData({
                    pixelRatio: res.pixelRatio,
                    theight: res.windowHeight,
                    windowWidth: res.windowWidth
                })
            },
        })
    },

    switchNav(event) {
        console.log(event)
        var cur = event.currentTarget.dataset.current;
        //每个tab选项宽度占1/5
        var singleNavWidth = this.data.windowWidth / 5;
        //tab选项居中                            
        this.setData({
            navScrollLeft: (cur - 2) * singleNavWidth
        })
        if (this.data.currentTab == cur) {
            return false;
        } else {
            this.setData({
                currentTab: cur
            })
        }
    },
    scroll(event) {
        let cur
        let atop = event.detail.scrollTop;
        let alltop = this.data.alltop
        console.log(atop)
        console.log(alltop[0])
        if (atop < alltop[1] - 40) cur = 0
        else if (atop < alltop[2] - 40) cur = 1
        else if (atop > alltop[1] - 40 && atop < alltop[2]) cur = 2
        else if (atop > alltop[2] && atop < alltop[3]) cur = 3
        this.setData({
                currentTab: cur
            })
            // else if(atopalltop[1])
            // if (atop) {}
    },
    onShow: function() {
        let id
        let that = this
        for (let i in that.data.navData) {
            id = '#t' + i
            const query = wx.createSelectorQuery()
            query.select(id).boundingClientRect()
            query.selectViewport().scrollOffset()
            query.exec(function(res) {
                console.log(i, res[0].top)
                that.data.alltop.push(res[0].top)
                console.log(that.data.alltop)
                res[0].top // #id节点的上边界坐标
                res[1].scrollTop // 显示区域的竖直滚动位置

            })
        }


    },
})
