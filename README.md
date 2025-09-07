# PokéFactory Legends

A comprehensive Minecraft server ecosystem that integrates Cobblemon gameplay with advanced analytics and database tracking. This meta-repository links three interconnected components that work together to provide enhanced Pokemon gameplay experiences.

## 🎮 Architecture Overview

```
Players ↔ Minecraft Server (Mod) ↔ Go API ↔ PostgreSQL Database ↔ Web Analytics
```

**Security Model**: Minecraft server and backend API communicate over localhost only. Public analytics served via separate port with no PII exposure.

---

## 📦 Component Repositories

### [PokéFactory Legends Minecraft Mod](https://github.com/diamondoughnut/pokefactory-legends)
**Status: Ready for Field Testing** 🟢

**NeoForge 1.21.1 mod with Cobblemon integration**

- **Event Detection**: Automatically captures Pokemon catch events from Cobblemon
- **Batched Sync**: 30-second intervals with deduplication and crash recovery
- **Development Mode**: Single-player testing with simulated multiplayer
- **Bidirectional Sync**: Full backup/restore between local and database
- **Test Commands**: `/pftest` and `/pfsync` for comprehensive testing

**Dependencies**: Cobblemon, KotlinForForge, NeoForge 1.21.1

### [PokéFactory Legends Backend Server](https://github.com/diamondoughnut/pokefactory-server)
**Status: Testing Phase 1** 🟡

**Dockerized Go API with PostgreSQL database**

#### Port 8080 (Localhost Only)
- **Server Authentication**: JWT-based Minecraft server auth
- **Data Management**: Player registration, Pokédex updates, statistics
- **Admin Operations**: Manual sync, rollback recovery, data management
- **Security**: No external access, PII-safe communication

#### Port 8081 (Public Analytics)
- **Leaderboards**: Regional/National Pokédex completion rankings  
- **Statistics**: Pokemon popularity, recent captures, completion rates
- **Server Status**: Real-time health monitoring and uptime tracking
- **Public Data Only**: No personally identifiable information exposed

**Tech Stack**: Go, PostgreSQL, Docker, Goose migrations

### [PokéFactory Legends WebApp](https://github.com/diamondoughnut/pokefactory-webapp)
**Status: Early Development** 🔴

**React-Vite frontend for public analytics**

- **Real-time Analytics**: Live server statistics and player achievements
- **Leaderboards**: Regional completion tracking and rankings
- **Server Status**: Health monitoring with configurable status pages
- **Future Features**: Player authentication, admin panels, potential e-commerce integration

**Tech Stack**: React, Vite, URL-parameter based queries

---

## 🚀 Deployment Strategy

### **Minecraft Server + Backend** (Same Hardware)
- **Location**: Local server hardware
- **Communication**: localhost:8080 (no external exposure)
- **Security**: JWT authentication, PII isolation
- **Data Flow**: Minecraft → API → Database (30-second batches)

### **WebApp** (External Hosting)
- **Location**: Third-party hosting service
- **Communication**: Public IP:8081 (analytics only)
- **Failover**: Configurable status pages during server downtime
- **Recovery**: Automatic restoration on successful API calls

---

## 🎯 Current Status & Roadmap

### **Phase 1: Core Infrastructure** ✅
- [x] Cobblemon event integration
- [x] API authentication and data flow
- [x] Database schema and migrations
- [x] Test command framework
- [x] Development environment setup

### **Phase 2: Field Testing** 🔄
- [ ] Multi-player stress testing
- [ ] Rollback scenario validation
- [ ] Production deployment testing
- [ ] Performance optimization

### **Phase 3: Analytics Platform** 📋
- [ ] WebApp development completion
- [ ] Real-time dashboard implementation
- [ ] Advanced analytics features
- [ ] Public beta testing

### **Phase 4: Enhanced Features** 🔮
- [ ] Legendary Pokemon summoning items
- [ ] Pokédex checking blocks with certificates
- [ ] Additional gameplay mechanics (TBA)

---

## 🛠️ Quick Start

### **For Server Administrators**
1. Deploy backend: `docker-compose up -d` in backend repository
2. Install mod on Minecraft server with Cobblemon
3. Configure `pokefactory_legends-common.toml` with API endpoint
4. Use `/pftest` commands to verify integration

### **For Developers**
1. Clone all three repositories
2. Set `dev_mode = true` in mod configuration
3. Use `/pftest cobblemon` to verify Cobblemon integration
4. Test API endpoints with `/pftest` command suite

### **For Players**
- Join participating Minecraft servers
- Catch Pokemon normally in Cobblemon
- View your progress on the server's analytics website
- Compete in regional completion leaderboards

---

## 📞 Support & Community

- **Issues**: Open issues in the relevant component repository
- **Questions**: Contact via GitHub or [portfolio website](https://diamondoughnut.dev)
- **Server Community**: Discord link available when server goes live

---

## 📄 License & Credits

**MIT License** - Fork freely with attribution to DiamonDoughnut

**Special Thanks**:
- **NeoForged Team**: Minecraft mod development framework
- **Cobblemon Team**: Pokemon integration platform  
- **Community Contributors**: Testing and feedback

---

*Ready to transform your Minecraft Pokemon experience with data-driven gameplay and community competition.*
