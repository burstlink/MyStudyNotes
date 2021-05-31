## bke项目elasticsearch7.1一些积累

* 匹配string的开头字符
```bash
{
    "from": 0,
    "size": 1000,
    "query": {
        "match_phrase_prefix": {
            "xxxx": xxxx
        }
    }
}
```
