## using local ipfs

It works

```
curl -i -s -X POST  -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/index.html;filename=index.html" -F "file=@/home/wighawag/dev/github/bug-reproduction/filebase-folder-upload/build/test/hello.txt;filename=test/hello.txt" "http://localhost:5001/api/v0/add?wrap-with-directory=true&cid-version=1&pin=true"
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
