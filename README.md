`pnpm dev & sleep 5 && kill %1`
3/4 of the time:

```
uv loop at [0x7f729f9ff988] has open handles:
[0x7f6d6c1f0120] timer (active)
        Close callback: (nil)
        Data: 0x7f6d6c1f0030
        (First field): 0x7f6a9ac6c110
[0x7f6d6c1f0030] udp (active)
        Close callback: (nil)
        Data: 0x7f6a9ac6c110
uv loop at [0x7f729f9ff988] has 2 open handles in total

  #  /usr/bin/node[34579]: void node::CheckedUvLoopClose(uv_loop_t*) at ../src/debug_utils.cc:352
  #  Assertion failed: "Unreachable code reached" ": " "uv_loop_close() while having open handles"

----- Native stack trace -----

 1: 0x59a177f83e11 node::Assert(node::AssertionInfo const&) [/usr/bin/node]
 2: 0x59a177ebd909 node::CheckedUvLoopClose(uv_loop_s*) [/usr/bin/node]
 3: 0x59a1780dae6a node::worker::WorkerThreadData::~WorkerThreadData() [/usr/bin/node]
 4: 0x59a1780d98f4 node::worker::Worker::Run() [/usr/bin/node]
 5: 0x59a1780d9a2b  [/usr/bin/node]
 6: 0x7f72b00a339d  [/usr/lib/libc.so.6]
 7: 0x7f72b012849c  [/usr/lib/libc.so.6]
```
