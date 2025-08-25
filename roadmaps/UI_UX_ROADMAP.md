# HexTrackr UI/UX Technical Roadmap
*Updated: August 25, 2025*

## 🎯 **CURRENT STATUS: TREND TRACKING IMPLEMENTATION PHASE**
**✅ CONFIRMED WORKING:**
- Modern Tabler.io vulnerability dashboard with real data ✅
- Statistics cards (109 Critical, 4,843 High, etc.) ✅
- AG Grid table with pagination (Page 1 of 200) ✅

**🔄 CRITICAL ISSUE IDENTIFIED:**
- **Problem**: CSV imports create duplicates instead of tracking changes over time
- **Solution**: Transform into time-series vulnerability management system

---

## 📋 **PHASE 1: Database Schema Migration** 
*Risk: HIGH | Impact: CRITICAL | Duration: 2-3 tasks*

### 1.1 Analyze Current Data Structure
- [ ] Audit existing vulnerability data patterns
- [ ] Identify unique vulnerability identifiers (CVE+hostname+date)
- [ ] Map current columns to time-series requirements

### 1.2 Design Time-Series Schema
- [ ] Create `vulnerability_master` table (static CVE data)
- [ ] Create `vulnerability_history` table (time-series: device+date+VPR)
- [ ] Add unique constraints: `(hostname, cve, scan_date)`
- [ ] Design indexes for latest-value queries

### 1.3 Create Migration Scripts
- [ ] Backup existing data
- [ ] Write migration script to reshape current data
- [ ] Test migration on sample data
- [ ] Create rollback procedures

---

## 📋 **PHASE 2: Smart CSV Import System**
*Risk: MEDIUM | Impact: HIGH | Duration: 2-3 tasks*

### 2.1 Redesign Import Logic
- [ ] Use date field as "last_updated" timestamp
- [ ] Implement UPSERT logic (UPDATE if exists, INSERT if new)
- [ ] Key on: `hostname + cve + scan_date`
- [ ] Track VPR changes over time

### 2.2 Data Validation & Integrity
- [ ] Validate date formats during import
- [ ] Ensure VPR score changes are logged
- [ ] Add data quality checks
- [ ] Handle malformed/duplicate entries gracefully

### 2.3 Import Analytics
- [ ] Track what changed during each import
- [ ] Report new/updated/unchanged vulnerabilities
- [ ] Log VPR trend changes per import

---

## 📋 **PHASE 3: Core Functionality Fixes** 
*Risk: MEDIUM | Impact: CRITICAL | Duration: 3-4 tasks*

### 3.1 Header & Navigation Cleanup
- [ ] Remove non-working "Import CSV Data" button from header
- [ ] Remove standalone "Settings" button (now in user dropdown)
- [ ] Clean up header layout for better visual balance
- [ ] Update navigation accessibility and keyboard support

### 3.2 CVE Link System Overhaul
- [ ] **CRITICAL BUG**: Fix CVE links opening ALL CVEs instead of clicked one
- [ ] Audit all CVE link implementations
- [ ] Create centralized CVE popup handler function
- [ ] Fix popup URL construction for multiple CVEs
- [ ] Implement 1200px wide popup standard
- [ ] Add error handling for blocked popups

### 3.3 Enhanced Vulnerability Details Modal
- [ ] **NEW FEATURE**: Click vulnerability description → modal
- [ ] Design vulnerability details modal (mirror of device modal)
- [ ] Show vulnerability details, totals, affected devices table
- [ ] Use 1200px width like device modal
- [ ] Add vulnerability metadata display (CVSS, VPR, timeline)
- [ ] Create vulnerability export functionality

### 3.4 Device Modal Export System
- [ ] **FIX**: CVE links in Active Vulnerabilities sub-table should open 1200px popup
- [ ] **IMPLEMENT**: Generate Report → PDF/HTML export of Device Overview
- [ ] **IMPLEMENT**: Export button → CSV export of Active Vulnerabilities table
- [ ] Replace HTML file generation with PDF creation
- [ ] Add professional PDF headers/footers with timestamps

---

## 📋 **PHASE 4: Enhanced Filtering & Display**
*Risk: LOW | Impact: HIGH | Duration: 3-4 tasks*

### 4.1 State Column Improvements & Default Filtering
- [ ] **DEFAULT**: Hide FIXED state by default in all filters (table, charts, totals)
- [ ] **STYLE**: Use different color scheme for STATE column (currently showing FIXED/Open)
- [ ] **FILTER**: Add State filter dropdown to table controls
- [ ] **CONSISTENCY**: Ensure state colors match across cards and table

### 4.2 Advanced Vendor Filtering System
- [ ] **FILTER**: Add Vendor filter dropdown (CISCO, Tenable, etc.)
- [ ] **UI**: Integrate with existing severity filter in clean layout
- [ ] **EXTEND**: Apply all table filters to card views (Devices/Vulnerabilities)
- [ ] **SYNC**: Keep filter state synchronized across view modes
- [ ] Extract vendor from plugin_name automatically
- [ ] Add vendor-specific vulnerability scoring

### 4.3 Interactive Statistics Cards
- [ ] Implement vendor filtering with flip animations
- [ ] Add historical trend integration
- [ ] Calculate vendor-specific statistics
- [ ] Show vendor comparison analytics

### 4.4 Layout & Navigation Improvements
- [ ] **REPOSITION**: Move search bar below charts and above table
- [ ] **CRITICAL FIX**: Fix non-functional "Clear Data" button in settings
- [ ] **UI**: Optimize layout flow for better user experience

### 4.5 Unified Header Design
- [ ] **HEADER UNIFICATION**: Remove purple bar from vulnerability dashboard
- [ ] **DARK HEADER**: Replace vuln dashboard top bar with tickets page dark header
- [ ] **TOGGLE INTEGRATION**: Move dark/light mode toggle into both page toolbars
- [ ] **MENU CONSISTENCY**: Add hamburger menu to both pages with same styling
- [ ] **BRANDING**: Ensure consistent HexTrackr branding across both dashboards

---

## 📋 **PHASE 5: Performance & Navigation**
*Risk: LOW | Impact: HIGH | Duration: 2-3 tasks*

### 5.1 Latest Values Display
- [ ] Modify `/api/vulnerabilities` to return latest values only
- [ ] Create efficient queries for most recent data per device+CVE
- [ ] Update vulnerability cards to show latest VPR
- [ ] Ensure tables reflect most recent scan data
- [ ] Add "last updated" timestamps to UI

### 5.2 Pagination Enhancement
- [ ] **OPTIMIZE**: Add pagination to card views (currently only table has it)
- [ ] **PERFORMANCE**: Reduce initial load by limiting cards per page
- [ ] **UX**: Consistent pagination controls across all views

### 5.3 Memory & Load Optimization
- [ ] **ANALYZE**: Current system loads 10,000+ records (Page 1 of 200)
- [ ] **OPTIMIZE**: Implement virtual scrolling or smaller page sizes
- [ ] **CACHE**: Better client-side data management

---

## 📋 **PHASE 6: Trend Visualization**
*Risk: LOW | Impact: HIGH | Duration: 3-4 tasks*

### 6.1 Historical Data API
- [ ] Create `/api/vulnerabilities/trends` endpoint
- [ ] Return VPR changes over time per vulnerability
- [ ] Support date range filtering

### 6.2 Chart Implementation
- [ ] Design Chart.js trend visualizations
- [ ] Show VPR score changes over time
- [ ] Display severity level migrations
- [ ] Add device-level trend analysis
- [ ] Implement interactive legend with line toggling

### 6.3 Dashboard Integration
- [ ] Add trend charts to vulnerability dashboard
- [ ] Create "trending up/down" indicators
- [ ] Show improvement/degradation analytics
- [ ] Add vendor filtering to historical trends

---

## 📋 **PHASE 7: Enhanced User Interactions**
*Risk: LOW | Impact: MEDIUM | Duration: 3-4 tasks*

### 7.1 Vulnerability Action Buttons
- [ ] **Edit Button (Pencil Icon)**: Create modal for editing vulnerability information
- [ ] **Refresh Button (Refresh Icon)**: Implement API data refresh for individual vulnerabilities
- [ ] **Button State Management**: Show appropriate tooltips and handle error states

### 7.2 Enhanced Table Interactions & Smart Filtering
- [ ] **Clickable Description Filtering**: Make vulnerability description column clickable to filter
- [ ] **Clickable CVE Filtering**: Make CVE Info column clickable to filter
- [ ] **Clickable Hostname Filtering**: Make hostname entries clickable to filter
- [ ] **Smart Info Icons**: Add info icons next to CVE entries, descriptions, hostnames
- [ ] **Enhanced Filter UI**: Show active filters as removable chips/badges

### 7.3 Device Security Modal Improvements
- [ ] **Remove "First Seen" Column**: Clean up modal table layout
- [ ] **Clickable Plugin Names**: Make Plugin Name column clickable links
- [ ] **Modal System Enhancements**: Create reusable vulnerability edit modal component

### 7.4 Modal Z-Index & CVE Bug Fixes
- [ ] **Fix Modal Layering**: Implement proper modal stacking system for nested modals
- [ ] **Fix CVE Link Behavior**: Ensure single CVE clicks open only that CVE popup
- [ ] **Fix HTML Report Artifacts**: Clean up character encoding issues in report titles

---

## 📋 **PHASE 8: API Integration Framework**
*Risk: MEDIUM | Impact: HIGH | Duration: 2-3 tasks*

### 8.1 API Supplement System
- [ ] Design hooks for real-time API data
- [ ] Create 30-day history pull mechanism
- [ ] Merge API data with CSV historical data

### 8.2 Data Source Management
- [ ] Support multiple data sources (CSV + API)
- [ ] Prioritize API data over CSV when available
- [ ] Maintain data source lineage
- [ ] Add API configuration status indicator to UI
- [ ] Implement API health checks

---

## 📋 **PHASE 9: Cross-Dashboard Integration**
*Risk: MEDIUM | Impact: HIGH | Duration: 4-5 tasks*

### 9.1 Tickets Page Redesign
- [ ] Audit current tickets.html design and functionality
- [ ] Apply Tabler.io framework to tickets page
- [ ] Implement consistent header and navigation design
- [ ] Update ticket cards to match vulnerability card styling
- [ ] Add VPR-style mini-cards for ticket priorities/statuses
- [ ] Update PDF generation to match new design

### 9.2 Ticket ↔ Vulnerability Cross-Reference
- [ ] **HOSTNAME LINKS**: Click hostname in tickets dashboard → opens vulnerability modal
- [ ] **DEVICE INTEGRATION**: Add "Open Ticket" button on vulnerability device cards
- [ ] **MODAL SHARING**: Share device modal component between dashboards
- [ ] **DATA INDEPENDENCE**: Maintain separate data storage for each dashboard

### 9.3 Authentication & Data Protection
- [ ] Implement simple login system with default credentials
- [ ] Add session management and timeout functionality
- [ ] Create user profile management interface
- [ ] Default credentials: `admin` / `hextrackr2025` (changeable)

---

## 📋 **PHASE 10: Advanced UI/UX Features**
*Risk: LOW | Impact: MEDIUM | Duration: 3-4 tasks*

### 10.1 Dark Mode Implementation
- [ ] Design dark mode color palette for Tabler.io integration
- [ ] Implement CSS custom properties for theme switching
- [ ] Add dark mode toggle in user dropdown
- [ ] Update all charts and graphs for dark mode compatibility
- [ ] Create automatic dark/light mode based on system preference

### 10.2 User Experience Refinements
- [ ] Add keyboard shortcuts for power users
- [ ] Implement context menus for quick actions
- [ ] Add drag-and-drop for bulk operations
- [ ] Create onboarding tour for new users
- [ ] Add accessibility improvements (ARIA labels, keyboard nav)

### 10.3 Advanced Dashboard Customization
- [ ] Implement drag-and-drop dashboard builder
- [ ] Add widget library (charts, tables, statistics)
- [ ] Create dashboard templates for different roles
- [ ] Add dashboard sharing and collaboration features

---

## 🎯 **IMMEDIATE NEXT STEPS**
1. **Start with Phase 1.1**: Analyze current data structure
2. **Fix Critical Issues**: Address CVE link bugs and modal layering
3. **Test thoroughly**: Each phase must be working before moving on
4. **Implement time-series**: Core architecture change for trend tracking

## 📊 **Success Criteria**
- ✅ Time-series data model implemented with no duplicates
- ✅ All CVE links open properly in 1200px popups
- ✅ Vulnerability modal shows comprehensive device list
- ✅ State filtering works with proper color coding
- ✅ Vendor filtering implemented across all views
- ✅ Page load time reduced by 50%
- ✅ Memory usage optimized for large datasets

## 🚀 **Estimated Timeline**
- **Phase 1-2 (Database)**: 1-2 weeks
- **Phase 3-5 (Core UX)**: 2-3 weeks
- **Phase 6-8 (Advanced Features)**: 2-3 weeks
- **Phase 9-10 (Integration & Polish)**: 1-2 weeks
- **Total Duration**: 6-10 weeks

---
*Last Updated: August 25, 2025 • Priority: HIGH - Critical trend tracking + UX improvements*
- [ ] **CONTEXT PASSING**: Pass hostname/device context between systems
- [ ] **STATE MANAGEMENT**: Maintain independent operation of each dashboard

---

## 📋 **PHASE 7: Enhanced Statistics Cards** 
*Risk: LOW | Impact: LOW | Duration: 2-3 tasks | Priority: VERY LOW*

### 7.1 VPR Calculation Improvements
- [ ] **CRITICAL LOGIC**: Exclude FIXED state from VPR total calculations  
- [ ] **ACCURACY**: Ensure cards only count active vulnerabilities
- [ ] **CONSISTENCY**: Match card totals with filtered table data

### 7.2 Enhanced Card Design & Micro-Charts
- [ ] **SIZING**: Make statistics cards larger for better visibility
- [ ] **MICRO-GRAPHS**: Add small historical trend graphs within cards
- [ ] **SPARKLINES**: Show 7-day or 30-day trend indicators
- [ ] **VISUAL**: Enhanced card styling with embedded chart.js mini-graphs

---

## 📋 **PHASE 6: User Authentication & Security**
*Risk: HIGH | Impact: CRITICAL | Duration: 5-6 tasks*

### 6.1 Authentication System
- [ ] **LOGIN PAGE**: Create secure login interface
- [ ] **SESSION MANAGEMENT**: Implement secure session handling
- [ ] **ROUTE PROTECTION**: Wrap both dashboards behind authentication
- [ ] **DATA SECURITY**: Protect all data endpoints with auth middleware

### 6.2 User Management
- [ ] **USER ACCOUNTS**: Basic user account system
- [ ] **PERMISSIONS**: Role-based access if needed
- [ ] **LOGOUT**: Secure logout and session cleanup
- [ ] **SESSION TIMEOUT**: Automatic logout after inactivity

---

## 🎯 **IMMEDIATE PRIORITIES**
1. **Phase 2.2** - Fix critical "Clear Data" button issue (urgent bug fix)
2. **Phase 7.1** - Fix VPR calculations to exclude FIXED state (data accuracy)
3. **Phase 2.4** - Unified header design (visual consistency)
4. **Phase 2.1** - Default hide FIXED state (immediate UX improvement)
5. **Phase 1.1** - Vulnerability Description Modal (high impact feature)
6. **Phase 2.2** - Search bar repositioning (layout improvement)

**Which phase should we tackle first? I recommend starting with Phase 1.1 for immediate user value! 🚀**
