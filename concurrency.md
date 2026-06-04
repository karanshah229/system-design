# How to scale a Thread per request backend ?

1. The problem with a thread per request backend is that it accepts all connections irrespective of the number instantly.
2. Threads consume memory - stack, heap, etc. So, if we have too many connections, we will run out of memory soon.
3. Also CPU will be around 100% because there will be pressure from all threads to get time to execute

-> So we can add a event loop based reverse proxy in front of this backend server so that this uncontrolled load is converted to controlled load by the event loop (Check nginx repo for full understanding)

# How do decide how much memory NGINX would require ?

High latency downstream creates a mandatory resource tax upstream (FDs, memory buffer, etc).
You must budget NGINX memory based on your worst-case backend latency, not your average.
