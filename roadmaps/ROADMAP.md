# HexTrackr Project Roadmap & Task List

## 🎯 Project Overview
HexTrackr is a dual-purpose cybersecurity management system providing:
- **Ticket Management**: Hexagon security workflow management
- **Vulnerability Management**: Multi-vendor vulnerability data analysis

---

## 🟢 COMPLETED FEATURES

### Core Infrastructure ✅
- [x] **Dual-app architecture** (tickets.html + vulnerabilities.html)
- [x] **Time-series database** with dimensional schema migration (97% data reduction)
- [x] **Modern AG Grid** with responsive configuration
- [x] **Bootstrap 5 + Tabler.io UI** with responsive design
- [x] **PDF generation** with jsPDF + auto-bundling capabilities
- [x] **Device management** with smart auto-increment naming
- [x] **CSV import/export** with UPSERT logic for time-series
- [x] **Pagination & filtering** across all views
- [x] **JavaScript architecture** with dedicated files per page pattern

### Chart & Visualization System ✅
- [x] **ApexCharts integration** with historical VPR trends
- [x] **Metric toggle functionality** (Count ↔ VPR Sum modes)
- [x] **Multi-severity visualization** (Critical, High, Medium, Low)
- [x] **Real-time chart updates** based on user selections
- [x] **Responsive chart configuration** for mobile/desktop

### Recent Critical Fixes ✅
- [x] **VPR Toggle Bug Fix** - Fixed JavaScript DOM selector issue in chart metric switching
- [x] **Database Schema Migration** - Complete time-series implementation with optimized queries
- [x] **Data Quality Improvement** - Eliminated 97% duplicates, maintained historical accuracy

### Cisco API Integration ✅
- [x] **OAuth2 authentication** with real Cisco endpoints
- [x] **AES-256 credential encryption** for secure local storage
- [x] **Live API testing** with connection validation
- [x] **Vulnerability synchronization** from Cisco PSIRT API
- [x] **Error handling & progress tracking**

---

## 🟡 IN PROGRESS

### Chart Timeline Enhancement 🔄 **NEXT PRIORITY**
- [ ] **Timeline Extension Feature** - Extend chart to current date with flat lines for data continuity
  - [ ] Calculate gap between last data point and current date (August 25, 2025)
  - [ ] Add synthetic data points to extend timeline with flat lines
  - [ ] Update API to support date range extension
  - [ ] Improve UX to show system is current and up-to-date

### Performance Optimization 🔄
- [ ] **Large CSV file handling** (50-100MB files)
  - [ ] Implement streaming CSV parser for memory efficiency
  - [ ] Add column filtering to ignore unnecessary data
  - [ ] Progress indicators for large file processing
  - [ ] Web Workers for non-blocking file processing
  - [ ] Chunk-based processing with IndexedDB batching

---

## 🔴 PLANNED FEATURES

### API Integrations Roadmap 📋

#### Cisco Extensions
- [ ] **Security Advisories Sync** (partially stubbed)
  - [ ] Complete `syncCiscoAdvisories()` implementation
  - [ ] Advisory correlation with existing vulnerabilities
  - [ ] Risk scoring integration

#### Palo Alto Networks Integration
- [ ] **Prisma Cloud API** integration
- [ ] **Cortex API** for threat intelligence
- [ ] **PAN-OS API** for firewall management
- [ ] **WildFire API** for malware analysis
- [ ] OAuth2 authentication framework
- [ ] Multi-product configuration management

#### Additional Vendor APIs
- [ ] **Tenable.io** vulnerability scanner integration
- [ ] **Qualys** VMDR API connectivity
- [ ] **Rapid7** InsightVM integration
- [ ] **CrowdStrike** Falcon endpoint data

### Network Infrastructure Features 📋

#### SNMP Network Polling
- [ ] **SNMPv2/v3 implementation**
  - [ ] Real-time device status monitoring
  - [ ] Hardware health monitoring  
  - [ ] Firmware version detection
  - [ ] Network interface analysis
  - [ ] Vulnerability correlation by device type
- [ ] **Docker containerization**
  - [ ] Node.js backend with net-snmp library
  - [ ] RESTful API for browser integration
  - [ ] Scalable multi-network support

#### Network Discovery & Mapping
- [ ] **Automated asset discovery**
- [ ] **Network topology visualization**
- [ ] **Device fingerprinting**
- [ ] **Service enumeration**

### Automation & Orchestration 📋

#### Ansible Integration
- [ ] **AWX/Tower API connectivity**
- [ ] **Automated patch deployment**
- [ ] **Configuration compliance enforcement**
- [ ] **Vulnerability remediation playbooks**
- [ ] **Bulk system updates and hardening**
- [ ] **Secure credential vault management**
- [ ] **Playbook execution monitoring**

#### Docker Implementation
- [ ] **Container architecture**
  - [ ] SNMP polling service containerization
  - [ ] API gateway container
  - [ ] Database container (if moving from browser storage)
  - [ ] Docker Compose orchestration

### Advanced Analytics & Intelligence 📋

#### Threat Intelligence & Priority Enhancement
- [ ] **CISA KEV Integration** 🚨 **HIGH PRIORITY**
  - [ ] Non-API CSV download implementation (user-friendly, no API key required)
  - [ ] API-based real-time sync (for users with access)
  - [ ] Automatic KEV flagging in vulnerability tables
  - [ ] KEV priority boost in VPR calculations (auto-assign 10.0 VPR)
  - [ ] Visual KEV indicators in dashboard cards and tables
  - [ ] Historical KEV trend tracking in time-series data
- [ ] **EPSS Scoring Integration**
  - [ ] Daily EPSS CSV download and processing
  - [ ] VPR calculation enhancement with exploit prediction
  - [ ] Non-API implementation for maximum accessibility
- [ ] **MITRE ATT&CK framework mapping**
- [ ] **CVE enrichment from NVD**
- [ ] **Exploit prediction modeling**
- [ ] **Enhanced risk scoring algorithms** (CVSS + EPSS + KEV + time-series trends)

#### Reporting & Visualization
- [ ] **Executive dashboards**
- [ ] **Compliance reporting** (SOC2, ISO27001, NIST)
- [ ] **Trend analysis** with ApexCharts expansion
- [ ] **Custom report builder**

### Enterprise Features 📋

#### Multi-tenancy & Access Control
- [ ] **User authentication system**
- [ ] **Role-based access control (RBAC)**
- [ ] **Organization/site isolation**
- [ ] **Audit logging**

#### Data Management
- [ ] **Backend database** option (PostgreSQL/MongoDB)
- [ ] **Data retention policies**
- [ ] **Backup & restore functionality**
- [ ] **Data encryption at rest**

---

## 🚀 IMMEDIATE PRIORITIES (Next Sprint)

### High Priority
1. **KEV Integration Implementation** 🚨 **NEW ADDITION**
   - Target: One-click KEV flagging for existing vulnerabilities
   - Non-API CSV download + API option for premium users
   - Visual indicators and automatic VPR boosting

2. **Large CSV Import Optimization** 
   - Target: 50-100MB file handling
   - Web Workers + streaming parser
   - Column filtering for data reduction

3. **Cisco API Completion**
   - Finish Security Advisories sync
   - Enhanced error handling

### Medium Priority  
3. **Performance Improvements**
   - IndexedDB query optimization
   - UI responsiveness during large operations
   - Memory usage optimization

4. **User Experience**
   - Better progress indicators
   - Improved error messages
   - Mobile responsiveness testing

---

## 📊 TECHNICAL DEBT

### Code Quality
- [ ] **ESLint configuration** for JavaScript standardization
- [ ] **Unit testing framework** setup (Jest)
- [ ] **End-to-end testing** with Playwright
- [ ] **Documentation improvements**

### Security Hardening
- [ ] **Content Security Policy (CSP)** implementation
- [ ] **API key rotation** mechanisms
- [ ] **Input validation** strengthening
- [ ] **XSS prevention** auditing

### Performance Monitoring
- [ ] **Performance metrics** collection
- [ ] **Memory leak detection**
- [ ] **Bundle size optimization**
- [ ] **Lighthouse score** improvements

---

## 🎯 **CRITICAL PRIORITY: Trend Tracking Implementation**
**Problem**: CSV imports create duplicates instead of tracking changes over time  
**Solution**: Transform into time-series vulnerability management system

### 📋 **PHASE 1: Database Schema Migration** 
*Risk: HIGH | Impact: CRITICAL | Duration: 2-3 tasks*

#### 1.1 Analyze Current Data Structure
- [ ] Audit existing vulnerability data patterns
- [ ] Identify unique vulnerability identifiers (CVE+hostname+date)
- [ ] Map current columns to time-series requirements

#### 1.2 Design Time-Series Schema
- [ ] Create `vulnerability_master` table (static CVE data)
- [ ] Create `vulnerability_history` table (time-series: device+date+VPR)
- [ ] Add unique constraints: `(hostname, cve, scan_date)`
- [ ] Design indexes for latest-value queries

#### 1.3 Create Migration Scripts
- [ ] Backup existing data
- [ ] Write migration script to reshape current data
- [ ] Test migration on sample data
- [ ] Create rollback procedures

### 📋 **PHASE 2: Smart CSV Import System**
*Risk: MEDIUM | Impact: HIGH | Duration: 2-3 tasks*

#### 2.1 Redesign Import Logic
- [ ] Use date field as "last_updated" timestamp
- [ ] Implement UPSERT logic (UPDATE if exists, INSERT if new)
- [ ] Key on: `hostname + cve + scan_date`
- [ ] Track VPR changes over time

#### 2.2 Data Validation & Integrity
- [ ] Validate date formats during import
- [ ] Ensure VPR score changes are logged
- [ ] Add data quality checks
- [ ] Handle malformed/duplicate entries gracefully

#### 2.3 Import Analytics
- [ ] Track what changed during each import
- [ ] Report new/updated/unchanged vulnerabilities
- [ ] Log VPR trend changes per import

### 📋 **PHASE 3: Latest Values Display**
*Risk: LOW | Impact: MEDIUM | Duration: 2 tasks*

#### 3.1 Update API Endpoints
- [ ] Modify `/api/vulnerabilities` to return latest values only
- [ ] Create efficient queries for most recent data per device+CVE
- [ ] Ensure cards/tables show current state

#### 3.2 Frontend Display Updates
- [ ] Update vulnerability cards to show latest VPR
- [ ] Ensure tables reflect most recent scan data
- [ ] Add "last updated" timestamps to UI

### 📋 **PHASE 4: Trend Visualization**
*Risk: LOW | Impact: HIGH | Duration: 3-4 tasks*

#### 4.1 Historical Data API
- [ ] Create `/api/vulnerabilities/trends` endpoint
- [ ] Return VPR changes over time per vulnerability
- [ ] Support date range filtering

#### 4.2 Chart Implementation
- [ ] Design Chart.js trend visualizations
- [ ] Show VPR score changes over time
- [ ] Display severity level migrations
- [ ] Add device-level trend analysis

#### 4.3 Dashboard Integration
- [ ] Add trend charts to vulnerability dashboard
- [ ] Create "trending up/down" indicators
- [ ] Show improvement/degradation analytics

### 📋 **PHASE 5: API Integration Framework**
*Risk: MEDIUM | Impact: HIGH | Duration: 2-3 tasks*

#### 5.1 API Supplement System
- [ ] Design hooks for real-time API data
- [ ] Create 30-day history pull mechanism
- [ ] Merge API data with CSV historical data

#### 5.2 Data Source Management
- [ ] Support multiple data sources (CSV + API)
- [ ] Prioritize API data over CSV when available
- [ ] Maintain data source lineage

---

## 🔧 DEVELOPMENT WORKFLOW

### Current Stack
- **Frontend**: Vanilla JavaScript, Bootstrap 5, ApexCharts
- **Storage**: localStorage, IndexedDB via LocalForage
- **Build**: No build process (direct file serving)
- **Dependencies**: CDN-based (Bootstrap, jQuery-less)

### Proposed Enhancements
- **Build System**: Webpack/Vite for optimization
- **Package Management**: npm/yarn for dependency management
- **Testing**: Jest + Playwright test suite
- **CI/CD**: GitHub Actions for automated testing

---

## 📋 MAINTENANCE SCHEDULE

### Regular Tasks
- **Weekly**: Dependency security updates
- **Monthly**: Performance monitoring review
- **Quarterly**: Feature roadmap review and prioritization
- **Annually**: Security audit and penetration testing

---

*Last Updated: August 24, 2025*
*Maintainer: HexTrackr Development Team*
