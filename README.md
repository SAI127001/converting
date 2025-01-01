# Social Media Analytics Platform
## Complete Technical Documentation

## Table of Contents
1. [Deployment](#deployment)
2. [Project Overview](#project-overview)
3. [System Architecture](#system-architecture)
4. [Frontend Implementation](#frontend-implementation)
5. [Backend Implementation](#backend-implementation)
6. [LangFlow Integration](#langflow-integration)
7. [Technical Specifications](#technical-specifications)
8. [API Documentation](#api-documentation)
9. [Data Structure](#data-structure)

## Deployment

### Live Application
- Production URL: https://socialanalytics-client.onrender.com/
- Platform: Render
- Status: Active

### Deployment Infrastructure
- Frontend: Render Web Services
- Database: DataStax Astra DB
- AI Integration: Langflow & OpenAI

## Project Overview

### Objective
Build an analytics module that analyzes engagement data from mock social media accounts using Langflow and DataStax integration.

### Core Components
- DataStax Astra DB for database operations
- Langflow for workflow creation and GPT integration
- React-based frontend
- Node.js proxy backend
- OpenAI GPT integration

### Key Features
- Real-time social media analytics
- GPT-powered insights generation
- AI Powered Chat Bot
- Custom metric tracking
- Data visualization
- Post performance analysis
- Engagement metrics calculation

## System Architecture

### Frontend Layer
1. **Landing Page**
   - Header with navigation
   - Features showcase
   - Team information
   - Call-to-action elements

2. **Analytics Dashboard**
   - Performance overview cards
   - Data visualization section
   - Analytics insights panel
   - Data grid for detailed view

### Backend Layer
1. **Proxy Server**
   - WebSocket connections
   - Request handling
   - Response streaming
   - Error management

2. **Data Processing**
   - Text splitting and chunking
   - Data parsing
   - Vector store implementation
   - GPT integration

## Frontend Implementation

### Dashboard Components

#### Performance Overview Cards
```typescript
interface EngagementMetrics {
  totalEngagement: number;
  engagementRate: number;
  performanceScore: number;
}
```

#### Data Visualization Section
- Post Performance Chart
- Post Type Comparison
- Engagement Summary Card

#### Data Grid
- Sortable columns
- Filtering capabilities
- Pagination (50 items/page)
- Search functionality

### State Management
```typescript
interface DashboardState {
  posts: PostData[];
  dateRange: [Date, Date];
  selectedPostTypes: string[];
  sortBy: string;
  sortOrder: 'asc' | 'desc';
  currentPage: number;
  filters: {
    search: string;
    minEngagement?: number;
    maxEngagement?: number;
  };
}
```

## Backend Implementation

### Server Setup
```javascript
const express = require('express');
const http = require('http');
const WebSocket = require('ws');
const cors = require('cors');

const app = express();
const server = http.createServer(app);
const wss = new WebSocket.Server({ server });
```

### WebSocket Management
- Unique requestId assignment
- Connection tracking
- Real-time data streaming
- Error handling

### API Endpoints
1. **Chat Endpoint**
   - Handles client requests
   - Forwards to Langflow API
   - Streams responses
   - Error management

## LangFlow Integration

### Pipeline Components

1. **File Input**
   - Loads CSV data
   - Path: `mock_social_media_data.csv`

2. **Text Processing**
   - Chunk size: 1000
   - Overlap: 200
   - Custom separators

3. **Astra DB Integration**
   - Database: `davedb`
   - Collection: `engagement`
   - Embedding Model: Astra Vectorize
   - Provider: OpenAI
   - Model: `text-embedding-3-small`

4. **OpenAI Integration**
   - Model: `gpt-4o-mini`
   - Temperature: 0.1
   - Streaming enabled

## Technical Specifications

### Design Guidelines
1. **Color Palette**
   - Primary: #2563EB
   - Secondary: #3B82F6
   - Accent: #EAB308
   - Background: #F8FAFC
   - Text: #1E293B

2. **Typography**
   - Headings: Inter
   - Body: Roboto
   - Monospace: Source Code Pro

3. **Responsive Design**
   - Mobile: 320px - 480px
   - Tablet: 481px - 768px
   - Desktop: 769px+

### Performance Optimizations
1. **Frontend**
   - Virtual scrolling
   - Response caching
   - Lazy loading
   - Asset optimization

2. **Backend**
   - Connection pooling
   - Request batching
   - Response streaming
   - Error handling

### Testing Strategy
1. **Unit Testing**
   - Component testing
   - Function testing
   - State management testing

2. **Integration Testing**
   - API endpoint testing
   - WebSocket testing
   - Data flow testing

3. **End-to-End Testing**
   - User flow testing
   - Performance testing
   - Error handling testing

## API Documentation

### Endpoints

1. **Chat API**
```javascript
POST /chat
{
  "input_value": string,
  "requestId": string
}
```

2. **Analytics API**
```javascript
GET /api/posts
Query Parameters:
- startDate: ISO date string
- endDate: ISO date string
- postTypes: string[]
- page: number
- limit: number
- sort: string
- order: 'asc' | 'desc'
```

## Data Structure

### Post Data Model
```typescript
interface PostData {
  Post_ID: string;
  Post_Type: 'Reel' | 'Carousel' | 'Static Image';
  Likes: number;
  Shares: number;
  Comments: number;
  Date_Posted: string;
}
```

### Analytics Data Model
```typescript
interface AnalyticsData {
  totalEngagement: number;
  engagementRate: number;
  performanceScore: number;
  postTypeDistribution: {
    [key: string]: number;
  };
  timeSeriesData: {
    date: string;
    engagement: number;
    postType: string;
  }[];
}
```

This documentation provides a comprehensive overview of the Social Media Analytics Platform. For specific implementation details or clarification, please refer to the individual sections or contact the development team.
