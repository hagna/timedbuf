Timed Buffer
============

Implementation of a buffer that flushes its' contents immediately when it's full or at regular intervals. This is useful if you have data that you need to buffer but don't want the items to stay in the buffer for too long.

Please note that in some cases it might be more efficient to use the actual data type (and buffer pools).

Usage
-----
`go get github.com/charithe/timedbuf`


```go
// define a flush function that will be called whenever the buffer is full or the time period has elapsed
func flushFunc(items []string){
    // flush logic
}

// Initialize and use the buffer
tb := timedbuf.New(100, 10 * time.Second, flushFunc)
defer tb.Close()
tb.Put("foo", "bar")
tb.Put("baz")
...
```

