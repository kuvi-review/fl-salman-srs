# Software Requirements Specification (SRS)
## Cohort Management System with Commercial Meeting Platform Integration

**Document Version:** 2.0  
**Date:** June 19, 2025  
**Prepared by:** Vishnu Prasad Kuntar
**Budget:** ₹20,000 - ₹30,000 INR

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Overall Description](#2-overall-description)
3. [Functional Requirements](#3-functional-requirements)
4. [Non-Functional Requirements](#4-non-functional-requirements)
5. [External Interface Requirements](#5-external-interface-requirements)
6. [System Architecture Overview](#6-system-architecture-overview)
7. [Meeting Platform Integration Strategy](#7-meeting-platform-integration-strategy)
8. [Budget Allocation and Cost Management](#8-budget-allocation-and-cost-management)
9. [Optional Enhancements](#9-optional-enhancements)
10. [Technology Stack and Tools](#10-technology-stack-and-tools)

---

## 1. Introduction

### 1.1 Purpose
This document specifies the requirements for a web-based Cohort Management System that integrates with commercial meeting platforms (Google Meet, Microsoft Teams, or Zoom) to manage students across multiple cohorts, schedule meetings, and handle recordings within a budget of ₹20,000-30,000 INR.

### 1.2 Scope
The system encompasses:
- Multi-tenant cohort and user management
- Integration with commercial meeting platforms
- Meeting scheduling with automated meeting creation
- Recording management through platform APIs
- Cost-optimized deployment within INR budget constraints
- Administrative dashboard and reporting

### 1.3 Definitions and Acronyms
- **CMS**: Cohort Management System
- **API**: Application Programming Interface
- **SRS**: Software Requirements Specification
- **RBAC**: Role-Based Access Control
- **INR**: Indian Rupees

### 1.4 References
- Google Meet API Documentation
- Microsoft Graph API (Teams) Documentation
- Zoom API Documentation
- IEEE Std 830-1998 (IEEE Recommended Practice for Software Requirements Specifications)

---

## 2. Overall Description

### 2.1 Product Perspective
The Cohort Management System is a web application that acts as a centralized hub for educational management while leveraging existing commercial meeting platforms for video conferencing. The system focuses on cohort administration, scheduling automation, and recording management through API integrations.

### 2.2 Product Functions
- **User Management**: Multi-role user authentication and authorization
- **Cohort Administration**: Creation, management, and assignment of student cohorts
- **Meeting Scheduling**: Automated meeting creation on chosen platform
- **Platform Integration**: Seamless integration with Google Meet, Teams, or Zoom
- **Recording Management**: Access and organization of platform-stored recordings
- **Notification System**: Email and in-app notifications for meeting reminders
- **Administrative Dashboard**: Usage analytics and user management interface

### 2.3 User Classes and Characteristics
- **System Administrators**: Full system access, platform configuration, user management
- **Teachers/Instructors**: Cohort management, meeting scheduling, recording access
- **Students**: Meeting participation, recording viewing, profile management
- **Institution Administrators**: Multi-cohort overview, reporting, budget monitoring

### 2.4 Operating Environment
- **Client Side**: Modern web browsers (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- **Server Side**: Shared hosting or low-cost VPS (₹500-1500/month)
- **Database**: MySQL/PostgreSQL on shared hosting or managed service
- **Meeting Platforms**: Google Workspace, Microsoft 365, or Zoom Pro plans
- **Storage**: Platform-native recording storage + minimal application storage

### 2.5 Design and Implementation Constraints
- **Budget Constraint**: Total monthly cost ≤ ₹2,500 
- **Platform Dependency**: Functionality dependent on chosen meeting platform capabilities
- **API Limitations**: Subject to rate limits and feature restrictions of meeting platforms
- **User Limits**: Platform-specific concurrent user limitations
- **Integration Complexity**: Varying API capabilities across different platforms

---

## 3. Functional Requirements

### 3.1 User Management System

#### 3.1.1 User Registration and Authentication
- **FR-001**: System shall support user registration with email verification
- **FR-002**: System shall authenticate users via email/password
- **FR-003**: System shall integrate with Google/Microsoft SSO when using their platforms
- **FR-004**: System shall implement password reset functionality
- **FR-005**: System shall sync user data with meeting platform when possible

#### 3.1.2 Role-Based Access Control
- **FR-006**: System shall implement four user roles: Admin, Teacher, Student, Viewer
- **FR-007**: System shall restrict functionality based on user roles
- **FR-008**: System shall allow role assignment and modification by administrators
- **FR-009**: System shall maintain audit logs of role changes

### 3.2 Cohort Management

#### 3.2.1 Cohort Creation and Configuration
- **FR-010**: System shall allow teachers to create and configure cohorts
- **FR-011**: System shall support cohort metadata (name, description, start/end dates)
- **FR-012**: System shall allow bulk import of students via CSV upload
- **FR-013**: System shall support cohort archiving and restoration
- **FR-014**: System shall track cohort-specific meeting platform settings

#### 3.2.2 Student Assignment
- **FR-015**: System shall allow assignment of students to multiple cohorts
- **FR-016**: System shall support student removal from cohorts
- **FR-017**: System shall track student enrollment history
- **FR-018**: System shall generate cohort rosters with meeting platform user mapping

### 3.3 Meeting Platform Integration

#### 3.3.1 Google Meet Integration
- **FR-019**: System shall create Google Meet meetings via Google Calendar API
- **FR-020**: System shall generate meeting links and add participants automatically
- **FR-021**: System shall retrieve meeting recordings from Google Drive
- **FR-022**: System shall sync meeting metadata with Google Calendar events

#### 3.3.2 Microsoft Teams Integration
- **FR-023**: System shall create Teams meetings via Microsoft Graph API
- **FR-024**: System shall manage meeting participants through Teams API
- **FR-025**: System shall access Teams meeting recordings via OneDrive API
- **FR-026**: System shall integrate with Outlook calendar for scheduling

#### 3.3.3 Zoom Integration
- **FR-027**: System shall create Zoom meetings via Zoom API
- **FR-028**: System shall manage Zoom meeting settings and participants
- **FR-029**: System shall retrieve Zoom cloud recordings via API
- **FR-030**: System shall handle Zoom webhook notifications for meeting events

### 3.4 Meeting Scheduling

#### 3.4.1 Schedule Management
- **FR-031**: System shall provide calendar interface for meeting scheduling
- **FR-032**: System shall support recurring meeting schedules
- **FR-033**: System shall handle timezone conversion automatically
- **FR-034**: System shall prevent scheduling conflicts for teachers
- **FR-035**: System shall automatically create meetings on chosen platform

#### 3.4.2 Meeting Configuration
- **FR-036**: System shall allow meeting configuration per platform capabilities
- **FR-037**: System shall support meeting templates for common configurations
- **FR-038**: System shall allow meeting cancellation and rescheduling
- **FR-039**: System shall generate platform-specific join links and meeting IDs

### 3.5 Recording Management

#### 3.5.1 Recording Access
- **FR-040**: System shall list all meeting recordings from integrated platform
- **FR-041**: System shall provide search and filtering capabilities for recordings
- **FR-042**: System shall link recordings to specific cohorts and sessions
- **FR-043**: System shall display recording metadata (duration, participants, date)

#### 3.5.2 Recording Organization
- **FR-044**: System shall organize recordings by cohort and date
- **FR-045**: System shall support recording tagging and categorization
- **FR-046**: System shall provide recording sharing controls
- **FR-047**: System shall track recording access and viewing analytics

### 3.6 Notification System

#### 3.6.1 Email Notifications
- **FR-048**: System shall send meeting reminders via email
- **FR-049**: System shall notify users of meeting changes/cancellations
- **FR-050**: System shall send digest emails of upcoming meetings
- **FR-051**: System shall support customizable email templates

#### 3.6.2 Platform Notifications
- **FR-052**: System shall leverage platform-native notifications when possible
- **FR-053**: System shall send calendar invitations through integrated platforms
- **FR-054**: System shall provide in-app notification dashboard
- **FR-055**: System shall support notification preferences per user

### 3.7 Administrative Dashboard

#### 3.7.1 Usage Analytics
- **FR-056**: System shall provide meeting attendance analytics
- **FR-057**: System shall track platform usage and costs
- **FR-058**: System shall generate cohort performance reports
- **FR-059**: System shall monitor API usage and rate limits
- **FR-083**: System shall track recording upload statistics and storage usage
- **FR-084**: System shall provide cost analysis for storage vs. platform subscriptions

### 3.8 Local Recording and Upload System ⭐ **NEW MODULE** - You can opt in for this option only and need not purchase Zoom or Google meet. Total cost of project would be 20,000 to 25000 INR 

#### 3.8.1 Local Recording Management
- **FR-064**: System shall provide recording guidelines and setup instructions
- **FR-065**: System shall support multiple recording methods (OBS, browser, mobile)
- **FR-066**: System shall provide recording quality recommendations
- **FR-067**: System shall offer recording templates and presets for instructors

#### 3.8.2 Video Upload System
- **FR-068**: System shall provide drag-and-drop video upload interface
- **FR-069**: System shall support multiple video formats (MP4, WebM, MOV, AVI)
- **FR-070**: System shall implement resumable upload for large video files
- **FR-071**: System shall automatically compress videos for storage optimization
- **FR-072**: System shall generate video thumbnails and metadata

#### 3.8.3 Recording Processing
- **FR-073**: System shall validate uploaded video files for corruption
- **FR-074**: System shall extract video metadata (duration, resolution, size)
- **FR-075**: System shall link uploaded recordings to specific meetings and cohorts
- **FR-076**: System shall support batch upload for multiple recordings
- **FR-077**: System shall provide upload progress tracking and status updates

#### 3.8.4 Free Platform Integration
- **FR-078**: System shall create meeting links for free tier services
- **FR-079**: System shall track meeting schedules within time limitations
- **FR-080**: System shall send reminders about meeting time limits
- **FR-081**: System shall provide meeting restart functionality for extended sessions
- **FR-082**: System shall integrate with free calendar services for scheduling

---

## 4. Non-Functional Requirements

### 4.1 Performance Requirements
- **NFR-001**: System shall support 100+ concurrent users
- **NFR-002**: Web interface shall load within 3 seconds on standard broadband
- **NFR-003**: Meeting creation shall complete within 10 seconds
- **NFR-004**: System shall handle 500+ registered users
- **NFR-005**: API calls to meeting platforms shall complete within 5 seconds

### 4.2 Scalability Requirements
- **NFR-006**: System shall support horizontal scaling within budget constraints
- **NFR-007**: Database shall efficiently handle growing user and meeting data
- **NFR-008**: System shall handle API rate limits gracefully
- **NFR-009**: Recording management shall scale with platform storage limits

### 4.3 Availability Requirements
- **NFR-010**: System shall maintain 99% uptime during business hours
- **NFR-011**: System shall provide graceful degradation when platform APIs are unavailable
- **NFR-012**: Database shall implement regular backups
- **NFR-013**: System shall recover from failures within 10 minutes

### 4.4 Security Requirements
- **NFR-014**: All data transmission shall use HTTPS encryption
- **NFR-015**: User passwords shall be hashed using bcrypt
- **NFR-016**: Platform API credentials shall be encrypted at rest
- **NFR-017**: System shall implement rate limiting for user actions
- **NFR-018**: Personal data shall comply with platform privacy policies

### 4.5 Usability Requirements
- **NFR-019**: Interface shall be responsive across desktop and mobile devices
- **NFR-020**: System shall provide intuitive meeting platform switching
- **NFR-021**: Error messages shall be user-friendly and actionable
- **NFR-022**: System shall maintain consistent UI regardless of integrated platform

### 4.6 Reliability Requirements
- **NFR-023**: System shall handle platform API failures gracefully
- **NFR-024**: Meeting data shall remain consistent across platform changes
- **NFR-025**: System shall log all critical operations for debugging
- **NFR-026**: Automated testing shall cover 70%+ of codebase

---

## 5. External Interface Requirements

### 5.1 User Interface Requirements
- **UI-001**: Web-based responsive interface compatible with modern browsers
- **UI-002**: Clean, intuitive design following modern web standards
- **UI-003**: Dashboard with platform-specific widgets and controls
- **UI-004**: Calendar view integrated with chosen meeting platform
- **UI-005**: Recording library with preview and playback capabilities

### 5.2 API Interface Requirements
- **API-001**: RESTful API for external system integration
- **API-002**: Webhook endpoints for platform event handling
- **API-003**: OAuth integration for platform authentication
- **API-004**: JSON-based data exchange with meeting platforms

### 5.3 Meeting Platform Interface Requirements
- **MPI-001**: Google Meet API integration for meeting management
- **MPI-002**: Microsoft Graph API integration for Teams functionality
- **MPI-003**: Zoom API integration for meeting and recording management
- **MPI-004**: Platform-specific webhook handling for real-time updates

### 5.4 Communication Interface Requirements
- **COM-001**: SMTP integration for email notifications
- **COM-002**: Platform-native notification systems integration
- **COM-003**: Calendar API integration for scheduling
- **COM-004**: File API integration for recording access

---

## 6. System Architecture Overview

### 6.1 High-Level Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Web Browser   │    │   Mobile Web    │    │  Admin Panel    │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          └──────────────────────┼──────────────────────┘
                                 │
                    ┌─────────────────┐
                    │  Web Application│
                    │   (React/Vue +  │
                    │   Node.js/PHP)  │
                    └─────────┬───────┘
                              │
                 ┌────────────┼────────────┐
                 │            │            │
        ┌─────────────────┐   │   ┌─────────────────┐
        │    Database     │   │   │  File Storage   │
        │ (MySQL/PostgreSQL)  │   │   (Minimal)     │
        └─────────────────┘   │   └─────────────────┘
                              │
         ┌────────────────────┼────────────────────┐
         │                   │                    │
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│  Google Meet/   │ │ Microsoft Teams │ │     Zoom        │
│  Workspace API  │ │   Graph API     │ │     API         │
└─────────────────┘ └─────────────────┘ └─────────────────┘
         │                   │                    │
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ Google Drive    │ │   OneDrive/     │ │ Zoom Cloud      │
│  (Recordings)   │ │  SharePoint     │ │  (Recordings)   │
└─────────────────┘ └─────────────────┘ └─────────────────┘
```

### 6.2 Component Architecture

#### 6.2.1 Frontend Layer
- **React/Vue.js Application**: Single-page application with responsive design
- **UI Framework**: Bootstrap or Tailwind CSS for cost-effective styling
- **State Management**: Context API or Vuex for application state
- **Platform Integrations**: JavaScript SDKs for seamless meeting joins

#### 6.2.2 Backend Layer
- **Web Framework**: Node.js with Express or PHP with Laravel
- **Authentication Service**: JWT-based with platform OAuth integration
- **Meeting Service**: Universal API wrapper for all meeting platforms
- **Recording Service**: Platform-agnostic recording management
- **Notification Service**: Email and platform notification handling

#### 6.2.3 Data Layer
- **Primary Database**: MySQL or PostgreSQL on shared hosting
- **File Storage**: Minimal local storage for app data only
- **Platform Storage**: Leveraging meeting platform native storage
- **Cache**: Simple file-based or Redis caching if available

---

## 7. Meeting Platform Integration Strategy

### 7.1 Platform Comparison and Selection

#### 7.1.1 Google Workspace (Google Meet)
**Monthly Cost**: ₹125-250 per user (Business Starter/Standard)
**Pros:**
- Excellent API integration capabilities
- Automatic recording to Google Drive
- Strong calendar integration
- Good mobile app support
- Familiar interface for most users

**Cons:**
- Recording limited to paid plans
- Meeting duration limits on basic plans
- Requires Google Workspace subscription

**Best For**: Organizations already using Google services, need strong integration

#### 7.1.2 Microsoft 365 (Teams)
**Monthly Cost**: ₹145-875 per user (Business Basic/Premium)
**Pros:**
- Comprehensive Graph API
- Excellent enterprise features
- Strong recording capabilities
- Good compliance and security features
- Integrated with Office suite

**Cons:**
- More complex API implementation
- Higher cost for full features
- Steeper learning curve

**Best For**: Enterprise environments, need advanced compliance features

#### 7.1.4 Free Tier Services (Zero-Cost Meeting Platform) ⭐ **NEW SCENARIO COST 20,000 INR Total**
**Monthly Cost**: ₹0 for meeting platform
**Pros:**
- **No subscription costs** for meeting platforms
- **Google Meet free**: 60 minutes for 3+ participants
- **Teams free**: 60 minutes for 3+ participants  
- **Zoom free**: 40 minutes for 3+ participants
- **Complete cost control** over recording and storage
- **Local recording flexibility** with multiple tools

**Cons:**
- **Time limitations** on meetings (40-60 minutes)
- **No cloud recording** from platforms
- **Manual recording management** required
- **Technical complexity** for recording setup
- **Quality dependent** on instructor's equipment and internet

**Best For**: **Budget-conscious institutions, short sessions, technical teams comfortable with recording setup**

**Recording Solutions:**
- **OBS Studio**: Professional recording software (free)
- **Browser-based recording**: MediaRecorder API integration
- **Screen recording tools**: Built-in OS tools or free software
- **Mobile recording**: Phone/tablet recording as backup

### 7.2 Implementation Strategy

#### 7.2.1 Multi-Platform Support Architecture
```javascript
// Platform abstraction layer
class MeetingPlatformAdapter {
  constructor(platform) {
    this.platform = platform;
    this.client = this.initializeClient(platform);
  }
  
  async createMeeting(meetingData) {
    switch(this.platform) {
      case 'google':
        return await this.createGoogleMeet(meetingData);
      case 'teams':
        return await this.createTeamsMeeting(meetingData);
      case 'zoom':
        return await this.createZoomMeeting(meetingData);
      case 'free': // NEW: Free tier implementation
        return await this.createFreeMeeting(meetingData);
    }
  }
  
  async getRecordings(meetingId) {
    // Platform-specific recording retrieval OR local upload handling
  }
  
  // NEW: Free platform specific methods
  async createFreeMeeting(meetingData) {
    return {
      googleMeetLink: `https://meet.google.com/${generateMeetingId()}`,
      teamsLink: `https://teams.microsoft.com/l/meetup-join/...`,
      zoomLink: `https://zoom.us/j/${generateMeetingId()}`,
      duration: 40, // Free tier limitation
      recordingMethod: 'local'
    };
  }
}
```

#### 7.2.2 Local Recording Integration Architecture
```javascript
// Recording upload and management system
class RecordingManager {
  async uploadRecording(file, meetingData) {
    // Validate file format and size
    const validation = await this.validateRecording(file);
    if (!validation.valid) throw new Error(validation.error);
    
    // Compress video for storage optimization
    const compressedFile = await this.compressVideo(file);
    
    // Generate thumbnail and metadata
    const metadata = await this.extractMetadata(compressedFile);
    
    // Upload to cloud storage with resumable upload
    const uploadResult = await this.resumableUpload(compressedFile);
    
    // Link to meeting and cohort
    return await this.linkRecordingToMeeting(uploadResult, meetingData);
  }
  
  async compressVideo(file) {
    // FFmpeg.js or similar for client-side compression
    // Or server-side processing depending on implementation
  }
}
```

#### 7.2.3 Configuration Management
- **Environment Variables**: Store API credentials securely
- **Platform Selection**: Runtime platform switching capability including free tier
- **Feature Flags**: Enable/disable platform-specific features
- **Fallback Mechanisms**: Handle API failures gracefully
- **Recording Modes**: Toggle between platform recording and local upload

---

## 8. Budget Allocation and Cost Management

### 8.1 Monthly Budget Breakdown (₹20,000-30,000)

#### 8.1.1 Meeting Platform Costs
| Platform | Users | Monthly Cost (INR) | Annual Cost (INR) |
|----------|-------|-------------------|-------------------|
| Google Workspace Business Starter | 20 users | ₹2,500 | ₹30,000 |
| Microsoft 365 Business Basic | 20 users | ₹2,900 | ₹34,800 |
| Zoom Pro | 5 licenses | ₹750 | ₹9,000 |
| **Free Tier Services** | Unlimited | ₹0 | ₹0 |

#### 8.1.2 Infrastructure Costs
| Component | Service | Monthly Cost (INR) |
|-----------|---------|-------------------|
| Web Hosting | Shared hosting/VPS | ₹500-1,500 |
| Domain & SSL | Domain + SSL certificate | ₹100-200 |
| Email Service | SMTP service | ₹200-500 |
| Database | Managed DB (optional) | ₹500-1,000 |
| CDN/Storage | For video recordings | ₹300-800 |
| **Video Storage** | **AWS S3/Google Cloud** | **₹500-1,500** |

#### 8.1.3 Total Cost Analysis
**Scenario 1: Google Workspace Focus**
- Google Workspace (20 users): ₹2,500
- Infrastructure: ₹1,000
- **Total: ₹3,500/month (₹42,000/year)**

**Scenario 2: Zoom + Basic Infrastructure**
- Zoom Pro (5 licenses): ₹750
- Infrastructure: ₹1,000
- Additional email hosting: ₹300
- **Total: ₹2,050/month (₹24,600/year)** ✅ **FITS BUDGET**

**Scenario 3: Hybrid Approach**
- Mix of platforms based on cohort needs
- Flexible licensing
- **Total: ₹2,200-2,800/month**

**Scenario 4: Zero-Cost Meeting Platform** ⭐ **NEW**
- **Free meeting services**: Google Meet (free), Teams (free), Zoom (free 40min)
- **Local recording**: OBS Studio, browser-based recording
- **Cloud storage**: ₹800-1,200 for video storage
- **Infrastructure**: ₹1,000
- **Total: ₹1,800-2,200/month (₹21,600-26,400/year)** ✅ **BEST BUDGET FIT**

### 8.2 Cost Optimization Strategies

#### 8.2.1 User Management
- **Shared Licenses**: Rotate licenses among teachers based on schedule
- **Student Access**: Use free participant access where possible
- **Flexible Scaling**: Add/remove licenses based on enrollment

#### 8.2.2 Infrastructure Optimization
- **Shared Hosting**: Start with cost-effective shared hosting
- **CDN Usage**: Minimize bandwidth costs
- **Database Optimization**: Use efficient queries and indexing
- **Monitoring**: Track usage to prevent overages

#### 8.2.3 Platform-Specific Savings
- **Google**: Leverage free Gmail accounts for students
- **Teams**: Use free tier for students, paid for instructors
- **Zoom**: Host meetings from licensed accounts, students join free

---

## 9. Optional Enhancements

### 9.1 Advanced Features (Phase 2)

#### 9.1.1 Mobile Application
- **Description**: Responsive web app optimized for mobile
- **Technology**: Progressive Web App (PWA)
- **Benefits**: Better mobile experience, offline capabilities
- **Cost**: No additional platform costs

#### 9.1.2 Advanced Analytics
- **Description**: Detailed usage analytics and reporting
- **Features**: Attendance tracking, engagement metrics, cost analysis
- **Implementation**: Platform APIs + custom analytics
- **Benefits**: Data-driven decision making, cost optimization

#### 9.1.3 Integration Hub
- **Description**: Connect with Learning Management Systems
- **Supported LMS**: Moodle, Canvas integration
- **Benefits**: Streamlined workflow, grade synchronization

### 9.2 Cost-Neutral Enhancements

#### 9.2.1 Automation Features
- **Description**: Automated meeting scheduling and reminders
- **Technology**: Cron jobs, platform webhooks
- **Benefits**: Reduced manual work, better user experience

#### 9.2.2 Custom Branding
- **Description**: White-label interface with institution branding
- **Implementation**: CSS customization, configurable themes
- **Benefits**: Professional appearance, brand consistency

### 9.3 Future Scalability Options

#### 9.3.1 Multi-Tenant Architecture
- **Description**: Support multiple institutions on single deployment
- **Benefits**: Cost sharing, scalable business model
- **Implementation**: Tenant isolation, platform quota management

#### 9.3.2 API Marketplace
- **Description**: Third-party integrations and plugins
- **Benefits**: Extended functionality, community contributions
- **Model**: Open-source with premium integrations

---

## 10. Technology Stack and Tools

### 10.1 Recommended Technology Stack

#### 10.1.1 Budget-Conscious Stack
```
Frontend:
├── React 18.x (free)
├── Bootstrap 5 (free)
├── Axios for API calls
└── React Router

Backend:
├── Node.js 18.x LTS
├── Express.js 4.x
├── JWT for authentication
├── Multer for file uploads
└── Node-cron for scheduling

Database:
├── MySQL 8.0 (shared hosting)
└── File-based caching

Meeting Integrations:
├── Google Calendar API
├── Microsoft Graph API
├── Zoom API v2
└── Platform-specific SDKs
```

#### 10.1.2 Alternative PHP Stack
```
Backend:
├── PHP 8.x
├── Laravel 9.x
├── MySQL/PostgreSQL
└── Composer for dependencies

Benefits:
├── Lower hosting costs
├── Wider hosting availability
├── Familiar to many developers
└── Good API integration capabilities
```

### 10.2 Development Tools

#### 10.2.1 Free Development Tools
- **VS Code**: Primary IDE
- **Git**: Version control
- **GitHub**: Code repository and CI/CD
- **Postman**: API testing
- **Chrome DevTools**: Frontend debugging

#### 10.2.2 Testing and Quality
- **Jest**: JavaScript testing (free)
- **PHPUnit**: PHP testing (free)
- **ESLint**: Code quality (free)
- **GitHub Actions**: CI/CD (free tier)

### 10.3 Monitoring and Maintenance

#### 10.3.1 Free Monitoring Tools
- **UptimeRobot**: Website uptime monitoring (free tier)
- **Google Analytics**: User behavior tracking
- **Platform Analytics**: Built-in meeting platform analytics
- **Error Logging**: Simple file-based logging

#### 10.3.2 Backup Strategy
- **Database Backups**: Daily automated backups
- **Code Repository**: Git-based version control
- **Configuration Backup**: Environment variable documentation
- **Recovery Plan**: Step-by-step restoration procedures

---

## Appendices

### Appendix A: Budget Scenarios Comparison

| Scenario | Platform | Monthly Cost | Users Supported | Recording Method | Best For |
|----------|----------|--------------|-----------------|------------------|----------|
| **A** | Zoom Pro Only | ₹2,050 | 100 participants | Platform cloud | Small institutions |
| **B** | Google Workspace | ₹3,500 | 20 host accounts | Google Drive | Google-integrated orgs |
| **C** | Hybrid Model | ₹2,500 | Mixed approach | Mixed | Flexible needs |
| **D** | **Free Tier + Local Recording** | **₹1,800-2,200** | **Unlimited** | **Local upload** | **Ultra budget-conscious** |

### Appendix B: Platform Feature Comparison

| Feature | Google Meet | Teams | Zoom | Free Tier Services |
|---------|-------------|-------|------|-------------------|
| Max Meeting Duration | 24 hours | 24 hours | 40 min (free) / Unlimited (pro) | **40-60 min** |
| Recording Storage | Google Drive | OneDrive | Zoom Cloud | **Manual/Local** |
| API Quality | Excellent | Good | Excellent | **Basic/None** |
| Mobile Support | Excellent | Good | Excellent | **Good** |
| Browser Support | Universal | Good | Universal | **Universal** |
| **Cost** | **₹125/user** | **₹145/user** | **₹150/license** | **₹0** |
| **Recording Cost** | **Included** | **Included** | **Included** | **Storage only** |

### Appendix C: Implementation Phases

| Phase | Duration | Features | Cost Impact | Recording Method |
|-------|----------|----------|------------|------------------|
| Phase 1 | 4-6 weeks | Core system, one platform | Initial setup | Platform or local |
| Phase 2 | 2-3 weeks | Multi-platform support | No additional cost | Both methods |
| Phase 3 | 3-4 weeks | **Local recording upload system** | **Storage costs only** | **Local focus** |
| Phase 4 | 2-3 weeks | Analytics and reporting | Better cost tracking | All methods |
| Phase 5 | 1-2 weeks | **Recording optimization & compression** | **Reduced storage costs** | **Enhanced local** |

### Appendix D: Recording Solutions Comparison

| Method | Setup Complexity | Quality Control | Cost | Storage | Best For |
|--------|------------------|-----------------|------|---------|----------|
| **Platform Recording** | Low | High | High (subscription) | Platform-managed | Paid subscriptions |
| **OBS Studio** | Medium | Very High | Free | Self-managed | Technical users |
| **Browser Recording** | Low | Medium | Free | Self-managed | Simple setup |
| **Mobile Recording** | Very Low | Medium | Free | Self-managed | Backup/emergency |
| **Screen Capture Tools** | Low | Medium | Free | Self-managed | Quick sessions |

### Appendix E: Free Tier Limitations and Workarounds

| Platform | Free Limit | Workaround Strategy | Implementation |
|----------|------------|-------------------|----------------|
| **Google Meet** | 60 min, 3+ people | Meeting restart, session splitting | Auto-restart functionality |
| **Teams** | 60 min, 3+ people | Multiple meeting rooms | Room rotation system |
| **Zoom** | 40 min, 3+ people | Back-to-back meetings | Quick rejoin system |
| **Recording** | No cloud recording | Local recording + upload | Upload management system |

### Appendix D: Risk Mitigation

| Risk | Impact | Probability | Mitigation Strategy |
|------|--------|-------------|-------------------|
| Platform API changes | High | Medium | Multi-platform support |
| Cost overruns | High | Low | Usage monitoring and alerts |
| User adoption issues | Medium | Medium | Training and documentation |
| Technical complexity | Medium | Medium | Phased implementation |

---

**Document Control**
- **Version**: 2.0
- **Budget Focus**: ₹20,000-30,000 INR annually
- **Platform Strategy**: Commercial meeting platform integration
- **Last Updated**: June 19, 2025
- **Status**: Ready for Implementation
- **Developer** : Vishnu Prasad Kuntar  - [https://vishnuprasadkuntar.me]
