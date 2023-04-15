# NFT下的Metadata该如何撰写

Metadata是这个NFT的资料，例如图片，说明，特殊属性等等

他的格式是JSON，看起来像下面那样

```flow
{
  "description": "Friendly OpenSea Creature that enjoys long swims in the ocean.", 
  "external_url": "https://openseacreatures.io/3", 
  "image": "https://storage.googleapis.com/opensea-prod.appspot.com/puffs/3.png", 
  "name": "Dave Starbelly",
  "attributes": [ ... ]
}
```

例如"description"后面，放的就是关于"description"的资料

我们用Opensea的需求来举例，Opensea几乎可以说是NFT产业的公共标准，Opensea支援的Metadata通常有以下栏位

| image | NFT的图片以及预览图，可以使用http或是ipfs |
| --- | --- |
| image_data | 如果你的图片是生成式的，例如编码成Base64或是SVG的图片，就需要用image_data |
| external_url | 关于这个NFT的其他网址 |
| description | 这个NFT的文字说明 |
| name | NFT的名字，例如你的名字叫KOI，你编号第999，这里可以写KOI #999 |
| attributes | NFT的属性资料 |
| background_color | 这个NFT的背景色，例如你是放3D或是透明PNG时会需要使用 |
| animation_url | 如果你的NFT不是图片，而是动画，视频，3D，互动式程式码，音乐等等，就需要把资料连接放到这里 |
| youtube_url | Youtube的链接 |

属性的写法范例如下，trait_type是属性名称，value就是属性的资料

```flow
...
{
"attributes": [
    {
      "trait_type": "Base", 
      "value": "Starfish"
    }, 
    {
      "trait_type": "Eyes", 
      "value": "Big"
    }, 
    {
      "trait_type": "Mouth", 
      "value": "Surprised"
    }, 
    {
      "trait_type": "Level", 
      "value": 5
    }, 
    {
      "trait_type": "Stamina", 
      "value": 1.4
    }
  ]
}
```

属性还可以用display_type定义数据类型，例如如果是生日日期

```flow
{
      "display_type": "date", 
      "trait_type": "birthday", 
      "value": 1546360800
    }
```

上面只是比较常见的Metadata格式，如果你有额外的需求都是可以自己拓展的

例如在游戏为主的ENJIN链上，会有properties这个类型，这个Opensea也是支援的

```flow
{
    "properties": {
        "base": "starfish",
        "rich_property": {
            "name": "eyes",
            "value": "big",
            "display_value": "Big",
        }
                ...
    }
}
```