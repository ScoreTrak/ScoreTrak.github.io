# Server

The Scoretrak scoring server is a golang application responsible to executing or delegating checks of services.


## Modes

### Single Node Master, No Workers

In a small environment, you can run one instance of the scoring engine that will be responsible for executing checks on the services and responding to client requests.

### Single Node Master, 1+ Workers

In a medium environment, you can run one instance of the scoring engine that will be responsible for delegating checks to workers via a queue platform. While the single node master will also be responsible for responding to client requests.

### Multi Node Master, 1+ Workers

In a large environment, you can run multiple instances of the scoring engine that will be responsible for delegating checks to workers via a queue platform. While the multi node masters will also be responsible for responding to client requests.
