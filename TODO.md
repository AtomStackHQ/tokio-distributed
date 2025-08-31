# Roadmap

## **Phase 1: Foundation (Weeks 1-2)**
**Goal**: Basic local functionality that mirrors tokio's API

### **1.1 Core Traits & Types**
- [ ] `DistributedRuntime` trait (generic over Transport, Security, Observability)
- [ ] `DistributedHandle` trait
- [ ] `JoinHandle` that wraps tokio's JoinHandle
- [ ] Basic error types
- [ ] `#[distributed::function]` proc macro (skeleton)

### **1.2 Local-Only Implementation**
- [ ] `LocalRuntime` - pure tokio wrapper
- [ ] Working local runtime that passes tokio compatibility tests
- [ ] `distributed::spawn_fn()` works locally
- [ ] All tokio Runtime/Handle methods work
- [ ] Integration tests proving API compatibility

## **Phase 2: Function Registry (Weeks 3-4)**
**Goal**: Compile-time function registration and basic serialization

### **2.1 Function Registration System**
- [ ] `#[distributed::function]` macro fully implemented
- [ ] Compile-time function ID generation
- [ ] Type-safe serialization/deserialization
- [ ] Function registry with static dispatch
- [ ] Unit tests for all function signature types

### **2.2 Message Protocol**
- [ ] Message format specification
- [ ] Efficient binary serialization
- [ ] Message versioning strategy
- [ ] Protocol documentation

## **Phase 3: Transport Layer (Weeks 5-7)**
**Goal**: Multiple transport implementations

### **3.1 Transport Abstraction**
- [ ] `Transport` trait design
- [ ] Memory transport (for testing)
- [ ] Process transport (Unix sockets)
- [ ] Basic network transport (TCP)
- [ ] Transport abstraction tests

### **3.2 Basic Distributed Runtime**
- [ ] Two-node function execution working
- [ ] Remote function calls with results
- [ ] Basic error handling and timeouts
- [ ] Integration tests with multiple transports

**MVP Milestone**: End of Phase 3 - basic distributed function execution across 2+ nodes

## **Phase 4: Node Discovery & Coordination (Weeks 8-10)**
**Goal**: Multi-node cluster formation

### **4.1 Node Discovery**
- [ ] `Discovery` trait design
- [ ] Static node list configuration
- [ ] DNS-based discovery
- [ ] Peer-to-peer gossip discovery

### **4.2 Cluster State Management**
- [ ] Node topology tracking
- [ ] Health checking and failure detection
- [ ] Basic cluster formation
- [ ] Multi-node integration tests

## **Phase 5: Scheduling & Placement (Weeks 11-13)**
**Goal**: Smart task placement with tags/taints/tolerations

### **5.1 Node Metadata**
- [ ] Node tags, taints, tolerations implementation
- [ ] Node selector logic with flexible string references
- [ ] Basic load-balancing scheduler
- [ ] Affinity-based placement

### **5.2 Advanced Placement APIs**
- [ ] Full placement API (`with_node_selector`, `with_tolerations`)
- [ ] Builder patterns for placement config
- [ ] Extension traits for ergonomics (`on_gpu_nodes()`, `in_zone()`)
- [ ] Comprehensive placement tests

## **Phase 6: Security (Weeks 14-16)**
**Goal**: Secure communication between nodes

### **6.1 Security Abstraction**
- [ ] `SecurityProvider` trait
- [ ] Plaintext provider (dev/testing)
- [ ] Basic mTLS implementation
- [ ] Certificate management

### **6.2 Authentication & Authorization**
- [ ] Node authentication working
- [ ] Certificate rotation
- [ ] Authorization policies
- [ ] Security integration tests

## **Phase 7: Observability (Weeks 17-19)**
**Goal**: Complete metrics and monitoring

### **7.1 Metrics Collection**
- [ ] `MetricsProvider` trait
- [ ] Runtime metrics collection
- [ ] Task execution metrics
- [ ] Network/transport metrics
- [ ] Prometheus export

### **7.2 Distributed Tracing**
- [ ] Cross-node trace correlation
- [ ] Task execution tracing
- [ ] Performance monitoring
- [ ] Debug tooling

## **Phase 8: Production Readiness (Weeks 20-24)**
**Goal**: Performance, reliability, and ecosystem integration

### **8.1 Performance Optimization**
- [ ] Zero-copy serialization where possible
- [ ] Connection pooling
- [ ] Batch message processing
- [ ] Memory usage optimization
- [ ] Comprehensive benchmarking

### **8.2 Fault Tolerance**
- [ ] Node failure detection and recovery
- [ ] Task migration on node failure
- [ ] Graceful shutdown procedures
- [ ] Split-brain prevention
- [ ] Chaos engineering tests

### **8.3 Ecosystem Integration**
- [ ] Tokio ecosystem compatibility tests
- [ ] Documentation and examples
- [ ] Production deployment guides
- [ ] Community feedback integration

# **Development Priorities**

## **Immediate Next Steps (Week 1)**
1. Set up basic project structure and module layout
2. Define core traits (`DistributedRuntime`, `DistributedHandle`)
3. Implement `LocalRuntime` as pure tokio wrapper
4. Create basic `JoinHandle` wrapper
5. Write initial integration tests

## **Success Criteria by Phase**
- **Phase 1**: Local distributed runtime works identically to tokio
- **Phase 3**: MVP - basic distributed execution across nodes
- **Phase 5**: Full scheduling with tags/taints/tolerations
- **Phase 8**: Production-ready distributed runtime

## **Risk Mitigation**
- Start simple and iterate (local-first approach)
- Extensive testing at each phase
- Performance regression testing
- Security review before Phase 6 completion
- Community feedback integration throughout

This roadmap ensures we build a solid foundation while incrementally adding distributed capabilities, keeping the API tokio-compatible throughout the entire development process.
