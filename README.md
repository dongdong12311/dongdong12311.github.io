<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=100%, initial-scale=1">
        <title>与江叔叔聊天中</title>
        <link href="css/main.min.css" rel="stylesheet" type="text/css">
        <link rel="Shortcut Icon" href="favicon.ico"/>
        <link rel="preload" href="img/love-the-girl.jpg" as="image">
        <link rel="preload" href="img/news-wuhanfeiyan.jpg" as="image">
        <link rel="preload" href="img/separate.jpeg" as="image">
        <link rel="preload" href="img/in-sichuan.jpeg" as="image">
        <link rel="preload" href="img/lucky-me.jpg" as="image">
        <link rel="preload" href="img/breakfast.jpg" as="image">
        <link rel="preload" href="img/exercise-together.jpg" as="image">
        <link rel="preload" href="img/travel.jpg" as="image">
        <link rel="preload" href="img/foot.jpg" as="image">
        <link rel="preload" href="img/marry-me.png" as="image">
        <link rel="preload" href="img/kiss-my-princess.png" as="image">
    </head>
    <body>
        <div id="mobile" :class="{ 'has-prompt': hasPrompt }">
            <div id="mobile-head">
                <div id="mobile-head-title">与江叔叔聊天中</div>
            </div>
            <div id="mobile-body">
                <div id="mobile-body-bg"></div>
                <div id="mobile-body-content">
                    <div id="mock-msg-row" class="msg-row">
                        <div id="mock-msg" class="msg" v-html="latestMsgContent"></div>
                    </div>
                    <div class="msg-row"
                        v-for="(msg, index) in messages"
                        :key="index"
                        :class="msg.author === 'author' ? 'msg-author' : 'msg-me'">
                        <div class="msg"
                            :class="'msg-bounce-in-' + (msg.author === 'author' ? 'left': 'right')"
                            :style="msg.width && msg.height && {width: msg.width - 26 + 'px', height: msg.height - 18 + 'px'}"
                            v-html="msg.content"></div>
                    </div>
                </div>
            </div>
            <div id="mobile-foot">
                <div id="prompt">
                    <div id="prompt-head">
                        <div class="say-something">我想说……</div>
                        <a href="javascript:;" class="close-btn"
                            v-on:click="togglePrompt(false)"></a>
                    </div>
                    <div id="prompt-body">
                        <ul class="responses" v-if="lastDialog">
                            <li v-for="res in lastDialog.responses">
                                <a href="javascript:;" v-on:click="respond(res)">{{ res.content }}</a>
                            </li>
                        </ul>
                        <div class="next-topic"
                            v-if="!lastDialog || !lastDialog.responses">
                            <ul class="topics">
                                <li v-for="topic in nextTopics">
                                    <a href="javascript:;" v-on:click="ask(topic)">{{ topic.brief }}</a>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div id="input-hint" class="say-something"
                    v-on:click="togglePrompt(true)"
                    :class="{'clickable': !isTyping }">
                    <span v-if="!isTyping">我想说……</span>
                    <span v-if="isTyping">江叔叔正在输入中</span>
                </div>
            </div>
            <div id="prompt-bg" v-on:click="togglePrompt(false)"></div>
        </div>

        <div class="extra-link" id="meta-link">
            <a class="letters" href="https://github.com/wongjohn/for-my-love" target="_blank">
                源码
            </a>
        </div>

        <script src="//cdn.bootcss.com/zepto/1.2.0/zepto.min.js"></script>
        <script src="//cdn.bootcss.com/vue/2.2.6/vue.min.js"></script>

        <script src="js/index-min.js"></script>
    </body>
</html>
