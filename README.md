## using local ipfs

It works

```
curl -i -s -X POST  -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/index.html;filename=index.html" -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/test/hello.txt;filename=test/hello.txt" "http://localhost:5001/api/v0/add?wrap-with-directory=true&cid-version=1&pin=true"
```

I get

```
{"Name":"index.html","Hash":"bafkreifjjcie6lypi6ny7amxnfftagclbuxndqonfipmb64f2km2devei4","Size":"12"}
{"Name":"test/hello.txt","Hash":"bafkreiga3xlcy5yxdahh764kcw5zm5gt5sjfslqlpld5dvjita3livj34i","Size":"3"}
{"Name":"test","Hash":"bafybeierkfrhdzvoiqr767h5zt5tooubhm4hfy4gjqn7edqte66yglaute","Size":"60"}
{"Name":"","Hash":"bafybeigd7frj3wbcqboo4nqh5w26dfrcmklpcpjcv67wqvm4btlm3x3b5e","Size":"178"}
```

## using filebase

It fails:

```
curl -i -s -X POST -H "Authorization: Bearer $FILEBASE_API_KEY" -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/index.html;filename=index.html" -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/test/hello.txt;filename=test/hello.txt" "https://rpc.filebase.io/api/v0/add?wrap-with-directory=true&cid-version=1&pin=true"
```

but weirdly if we post an empty folder it works:

```
curl -i -s -X POST -H "Authorization: Bearer $FILEBASE_API_KEY" -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build" "https://rpc.filebase.io/api/v0/add?wrap-with-directory=true&cid-version=1&pin=true"
```

I get

```
{"Name":"build","Hash":"bafkreihdwdcefgh4dqkjv67uzcmw7ojee6xedzdetojuzjevtenxquvyku","Size":"0"}
{"Name":"","Hash":"bafybeigv2dhrtowlohjhbksvn3q3vqtncw4k5nrilpgzkajy4qcareppgm","Size":"53"}
```
