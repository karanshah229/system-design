What are the caching mechanisms at every level ?

Assuming standard SAAS:

- client device
    - browser cache
        - Service workers
        - local cache - images, styles, etc
        - storage - local storage, indexdb, session storage, cookies, etc
- client router (DNS queries)
- CDN
    - cache static request responses
- Edge
    - cloudfront, router 53 etc
- ALB
    - cache health status etc - slow pods, etc
- K8s
    - NodePlane, DNS caching, Container registry caching, etc.
- BE Pods
    - thread local storage
    - app specific cached values in memory ex - simple hashmap
    - disk level caching - prevents expensive N/W call
- Cache layer - redis
    - app layer caching
- DB Layer
    - materialized views
    - reading colocated to respond faster
    - MVCC
- Message systems
    - kafka - OS level caching
- Workers
    - cache responses
