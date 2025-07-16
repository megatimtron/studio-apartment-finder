# Content Strategy & Templates
## Scalable Content Framework for Building Portfolio

### Content Architecture Overview

The content strategy ensures consistency while allowing for building-specific customization. Each property page follows a standardized structure with modular components that can be adapted based on available data and unique features.

### Building Data Schema

```typescript
interface BuildingData {
  // Basic Information
  id: string;
  name: string;
  location: {
    address: string;
    city: string;
    state: string;
    zipCode: string;
    neighborhood: string;
    coordinates?: {
      lat: number;
      lng: number;
    };
  };
  
  // Overview Content
  overview: {
    tagline: string;
    description: string;
    keyFeatures: string[];
    uniqueSellingPoints: string[];
  };
  
  // Pricing & Availability
  pricing: {
    studioRange: string;
    oneBedRange?: string;
    twoBedRange?: string;
    threeBedRange?: string;
    currentSpecials: string[];
    moveInCosts: {
      deposit: string;
      fees: string[];
    };
  };
  
  // Floor Plans
  floorPlans: {
    type: 'studio' | '1bed' | '2bed' | '3bed';
    name: string;
    sqFt: number;
    price: string;
    availability: string;
    features: string[];
    imageUrl?: string;
  }[];
  
  // Amenities
  amenities: {
    category: string;
    items: {
      name: string;
      icon: string;
      description?: string;
    }[];
  }[];
  
  // Scoring System
  scores: {
    value: number; // 1-5 rating
    quiet: number; // 1-5 rating
    management: number; // 1-5 rating
    amenities: number; // 1-5 rating
    location: number; // 1-5 rating
    overall: number; // Calculated average
  };
  
  // Reviews & Feedback
  reviews: {
    pros: string[];
    cons: string[];
    managementFeedback: string;
    noiseLevels: string;
    overallLiving: string;
    petFriendliness: string;
  };
  
  // Contact & Leasing
  contact: {
    phone: string;
    email: string;
    officeHours: string;
    virtualTourUrl?: string;
    scheduleTourUrl?: string;
  };
  
  // Media
  media: {
    heroImage: string;
    galleryImages: string[];
    virtualTourUrl?: string;
    videoUrl?: string;
  };
  
  // SEO & Meta
  seo: {
    title: string;
    description: string;
    keywords: string[];
    canonicalUrl: string;
  };
}
```

### Content Templates

#### 1. Hero Section Template

```html
<!-- Hero Section Template -->
<section class="hero-section animate-fade-in">
  <div class="container mx-auto px-4 relative z-10">
    <h1 class="text-4xl md:text-6xl font-bold mb-4 leading-tight">
      {{building.name}} 
      <span class="block text-3xl md:text-5xl">{{building.location.neighborhood}}</span>
    </h1>
    <p class="text-xl md:text-2xl opacity-90 mb-8 max-w-2xl mx-auto">
      {{building.overview.tagline}}
    </p>
    <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
      <button class="btn-modern text-lg px-8 py-3" onclick="scrollToSection('comparison-section')">
        {{building.pricing.studioRange ? 'View Studio Options' : 'Explore Properties'}}
      </button>
      {{#if building.contact.virtualTourUrl}}
      <a href="{{building.contact.virtualTourUrl}}" class="btn-secondary text-lg px-8 py-3">
        Virtual Tour
      </a>
      {{/if}}
    </div>
  </div>
</section>
```

#### 2. Property Overview Template

```html
<!-- Property Overview Template -->
<section class="mb-20 animate-slide-up">
  <div class="text-center mb-12">
    <h2 class="text-4xl font-bold gradient-text mb-4">{{building.name}} Overview</h2>
    <p class="text-xl text-gray-600 max-w-2xl mx-auto">
      {{building.overview.description}}
    </p>
  </div>
  
  <div class="grid md:grid-cols-3 gap-6 mb-12">
    {{#each building.overview.keyFeatures}}
    <div class="card-modern p-6 text-center">
      <div class="feature-icon mx-auto">{{this.icon}}</div>
      <h3 class="text-xl font-semibold mb-2">{{this.title}}</h3>
      <p class="text-gray-600">{{this.description}}</p>
    </div>
    {{/each}}
  </div>
</section>
```

#### 3. Pricing & Availability Template

```html
<!-- Pricing & Availability Template -->
<section class="mb-20">
  <div class="text-center mb-12">
    <h2 class="text-4xl font-bold gradient-text mb-4">Floor Plans & Pricing</h2>
    <p class="text-xl text-gray-600 max-w-2xl mx-auto">
      Find the perfect space for your lifestyle
    </p>
  </div>
  
  <div class="grid lg:grid-cols-2 gap-8">
    {{#each building.floorPlans}}
    <div class="property-card">
      <div class="card-header">
        <div class="flex justify-between items-start">
          <div>
            <h3 class="text-2xl font-semibold">{{this.name}}</h3>
            <p class="text-gray-600">{{this.sqFt}} sq ft</p>
          </div>
          <div class="text-right">
            <p class="text-2xl font-bold text-purple-600">{{this.price}}</p>
            <p class="text-sm text-gray-500">{{this.availability}}</p>
          </div>
        </div>
      </div>
      <div class="card-body">
        <ul class="space-y-2">
          {{#each this.features}}
          <li class="flex items-center text-gray-700">
            <span class="text-green-500 mr-2">✓</span>
            {{this}}
          </li>
          {{/each}}
        </ul>
      </div>
      <div class="card-footer">
        <button class="btn btn-primary">Schedule Tour</button>
      </div>
    </div>
    {{/each}}
  </div>
  
  {{#if building.pricing.currentSpecials}}
  <div class="card-modern p-6 mt-8 bg-gradient-to-r from-purple-50 to-blue-50">
    <h3 class="text-xl font-semibold mb-4 text-center">Current Specials</h3>
    <div class="space-y-2">
      {{#each building.pricing.currentSpecials}}
      <p class="text-center text-gray-700">{{this}}</p>
      {{/each}}
    </div>
  </div>
  {{/if}}
</section>
```

#### 4. Amenities Template

```html
<!-- Amenities Template -->
<section class="mb-20">
  <div class="text-center mb-12">
    <h2 class="text-4xl font-bold gradient-text mb-4">Amenities & Features</h2>
    <p class="text-xl text-gray-600 max-w-2xl mx-auto">
      Discover what makes {{building.name}} special
    </p>
  </div>
  
  {{#each building.amenities}}
  <div class="card-modern p-8 mb-8">
    <h3 class="text-2xl font-semibold mb-6 text-center">{{this.category}}</h3>
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
      {{#each this.items}}
      <div class="flex items-center space-x-3">
        <div class="feature-icon icon-sm">{{this.icon}}</div>
        <div>
          <h4 class="font-semibold">{{this.name}}</h4>
          {{#if this.description}}
          <p class="text-sm text-gray-600">{{this.description}}</p>
          {{/if}}
        </div>
      </div>
      {{/each}}
    </div>
  </div>
  {{/each}}
</section>
```

#### 5. Location & Neighborhood Template

```html
<!-- Location & Neighborhood Template -->
<section class="mb-20">
  <div class="text-center mb-12">
    <h2 class="text-4xl font-bold gradient-text mb-4">Prime Location</h2>
    <p class="text-xl text-gray-600 max-w-2xl mx-auto">
      {{building.location.neighborhood}} convenience at your doorstep
    </p>
  </div>
  
  <div class="grid lg:grid-cols-2 gap-8">
    <div class="card-modern p-8">
      <h3 class="text-2xl font-semibold mb-4">Address</h3>
      <p class="text-gray-700 mb-4">
        {{building.location.address}}<br>
        {{building.location.city}}, {{building.location.state}} {{building.location.zipCode}}
      </p>
      
      <h4 class="text-lg font-semibold mb-2">Nearby Attractions</h4>
      <ul class="space-y-1 text-gray-600">
        {{#each building.location.nearbyAttractions}}
        <li>• {{this}}</li>
        {{/each}}
      </ul>
    </div>
    
    <div class="card-modern p-8">
      <h3 class="text-2xl font-semibold mb-4">Transportation</h3>
      <ul class="space-y-2 text-gray-700">
        {{#each building.location.transportation}}
        <li class="flex items-center">
          <span class="text-blue-500 mr-2">{{this.icon}}</span>
          {{this.description}}
        </li>
        {{/each}}
      </ul>
    </div>
  </div>
</section>
```

#### 6. Reviews & Insights Template

```html
<!-- Reviews & Insights Template -->
<section class="mb-20">
  <div class="text-center mb-12">
    <h2 class="text-4xl font-bold gradient-text mb-4">Resident Insights</h2>
    <p class="text-xl text-gray-600 max-w-2xl mx-auto">
      What residents love about {{building.name}}
    </p>
  </div>
  
  <div class="grid lg:grid-cols-2 gap-8">
    <div class="card-modern p-8">
      <h3 class="text-2xl font-semibold mb-4 text-green-600">Highlights</h3>
      <ul class="space-y-3">
        {{#each building.reviews.pros}}
        <li class="flex items-start">
          <span class="text-green-500 mr-2 mt-1">✓</span>
          <span class="text-gray-700">{{this}}</span>
        </li>
        {{/each}}
      </ul>
    </div>
    
    <div class="card-modern p-8">
      <h3 class="text-2xl font-semibold mb-4 text-orange-600">Considerations</h3>
      <ul class="space-y-3">
        {{#each building.reviews.cons}}
        <li class="flex items-start">
          <span class="text-orange-500 mr-2 mt-1">!</span>
          <span class="text-gray-700">{{this}}</span>
        </li>
        {{/each}}
      </ul>
    </div>
  </div>
  
  <div class="card-modern p-8 mt-8">
    <h3 class="text-2xl font-semibold mb-4">Living Experience</h3>
    <p class="text-gray-700 leading-relaxed">{{building.reviews.overallLiving}}</p>
  </div>
</section>
```

### Content Adaptation Guidelines

#### 1. Voice & Tone Standards

**Brand Voice Characteristics:**
- **Professional yet approachable**: Knowledgeable but not intimidating
- **Helpful and informative**: Focus on solving user problems
- **Confident but honest**: Highlight strengths while acknowledging considerations
- **Inclusive and welcoming**: Appeal to diverse audiences

**Tone Variations by Section:**
- **Hero Section**: Aspirational and exciting
- **Pricing**: Clear and transparent
- **Amenities**: Descriptive and benefit-focused
- **Reviews**: Balanced and authentic
- **Contact**: Encouraging and action-oriented

#### 2. Content Personalization

**Location-Specific Adaptations:**
```html
<!-- Urban locations -->
<p class="hero-tagline">
  Urban luxury in the heart of {{city}} - where convenience meets sophistication
</p>

<!-- Suburban locations -->
<p class="hero-tagline">
  Peaceful living with city access - your perfect {{neighborhood}} retreat
</p>

<!-- Waterfront locations -->
<p class="hero-tagline">
  Waterfront luxury living with stunning {{water_body}} views
</p>
```

**Demographic-Specific Content:**
```html
<!-- Young professionals -->
<div class="feature-highlight">
  <h3>Work-Life Balance</h3>
  <p>Modern co-working spaces and fitness facilities designed for your busy lifestyle</p>
</div>

<!-- Families -->
<div class="feature-highlight">
  <h3>Family-Friendly</h3>
  <p>Safe, spacious environments with playgrounds and family amenities</p>
</div>

<!-- Retirees -->
<div class="feature-highlight">
  <h3>Maintenance-Free Living</h3>
  <p>Enjoy your golden years with full-service amenities and community activities</p>
</div>
```

#### 3. SEO-Optimized Content Structure

**Title Templates:**
```html
<!-- Primary Template -->
<title>{{building.name}} - {{city}} {{property_type}} | {{company_name}}</title>

<!-- Location-focused -->
<title>{{city}} {{property_type}} at {{building.name}} | {{neighborhood}} Living</title>

<!-- Feature-focused -->
<title>{{building.name}} - {{key_amenity}} {{property_type}} in {{city}}</title>
```

**Meta Description Templates:**
```html
<!-- Standard Template -->
<meta name="description" content="Discover {{building.name}} in {{city}} - modern {{property_type}} with {{key_amenities}}. Starting at {{price_range}}. Schedule your tour today!">

<!-- Amenity-focused -->
<meta name="description" content="{{building.name}} offers luxury {{property_type}} living in {{city}} with {{premium_amenity}}. {{current_special}} Available now.">
```

#### 4. Content Modularity System

**Reusable Content Blocks:**
```html
<!-- Pricing CTA Block -->
<div class="pricing-cta-block">
  <h3>Ready to Make {{building.name}} Home?</h3>
  <p>{{building.pricing.studioRange}} studios available now</p>
  <div class="cta-buttons">
    <button class="btn-primary">Schedule Tour</button>
    <button class="btn-secondary">Download Brochure</button>
  </div>
</div>

<!-- Special Offers Block -->
<div class="special-offers-block">
  <h3>Limited-Time Offers</h3>
  {{#each building.pricing.currentSpecials}}
  <div class="special-offer">
    <span class="offer-badge">Special</span>
    <p>{{this}}</p>
  </div>
  {{/each}}
</div>

<!-- Contact Info Block -->
<div class="contact-info-block">
  <h3>Get in Touch</h3>
  <div class="contact-methods">
    <div class="contact-method">
      <span class="icon">📞</span>
      <a href="tel:{{building.contact.phone}}">{{building.contact.phone}}</a>
    </div>
    <div class="contact-method">
      <span class="icon">✉️</span>
      <a href="mailto:{{building.contact.email}}">{{building.contact.email}}</a>
    </div>
    <div class="contact-method">
      <span class="icon">🏢</span>
      <span>{{building.contact.officeHours}}</span>
    </div>
  </div>
</div>
```

### Content Management Workflow

#### 1. Content Creation Process

**Step 1: Data Collection**
- Gather building information and media
- Conduct resident interviews/surveys
- Analyze competitor properties
- Document unique features and amenities

**Step 2: Content Structure**
- Populate building data schema
- Create location-specific content variations
- Develop SEO-optimized metadata
- Generate image alt texts and captions

**Step 3: Review & Approval**
- Property manager review
- Legal compliance check
- Brand consistency audit
- Accessibility review

**Step 4: Publishing & Testing**
- Deploy to staging environment
- Cross-browser testing
- Mobile responsiveness check
- Performance optimization

#### 2. Content Maintenance Schedule

**Monthly Updates:**
- Pricing and availability refresh
- Special offers and promotions
- New resident review integration
- Image gallery updates

**Quarterly Reviews:**
- Content accuracy audit
- SEO performance analysis
- User engagement metrics review
- A/B testing of key sections

**Annual Overhauls:**
- Complete content refresh
- New photography sessions
- Comprehensive SEO audit
- User experience improvements

### Quality Assurance Checklist

#### Content Quality Standards
- [ ] All building data fields populated
- [ ] Consistent voice and tone throughout
- [ ] Location-specific content included
- [ ] SEO metadata optimized
- [ ] Images properly optimized and tagged
- [ ] Contact information current
- [ ] Pricing and availability accurate
- [ ] Legal disclaimers included
- [ ] Accessibility standards met
- [ ] Mobile-friendly formatting

#### Technical Standards
- [ ] All links functional
- [ ] Forms working properly
- [ ] Images loading correctly
- [ ] Page loading under 3 seconds
- [ ] Mobile responsive design
- [ ] Cross-browser compatibility
- [ ] Schema markup implemented
- [ ] Analytics tracking active
- [ ] SSL certificate valid
- [ ] Error handling in place

This content strategy framework ensures consistency across your building portfolio while maintaining the flexibility to highlight each property's unique characteristics and appeal to diverse tenant demographics.
