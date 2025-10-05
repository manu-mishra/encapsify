# Consultation Booking Template

## Template Overview

**Purpose**: Qualify prospects and schedule consultations  
**Complexity**: Low  
**Setup Time**: 1-2 days  
**Best For**: Coaches, consultants, service providers

## Use Case

This template streamlines the consultation booking process by qualifying prospects, educating them about your services, and enabling them to schedule meetings directly. It reduces back-and-forth communication while ensuring you meet with qualified, prepared prospects.

## Template Components

### 1. Service Overview and Positioning
**Purpose**: Communicate what you offer and who you help

**Content Elements**:
- Service description and approach
- Who you work with (ideal client profile)
- Problems you solve
- Your unique methodology or framework
- Credentials and experience

**Customization Required**:
- Write clear service description
- Define ideal client characteristics
- List specific problems you address
- Explain your unique approach
- Add credentials, certifications, experience

### 2. Qualification Assessment
**Purpose**: Ensure mutual fit before booking time

**Content Elements**:
- Current situation questions
- Goal and objective questions
- Budget and investment readiness
- Timeline and urgency
- Decision-making authority

**Customization Required**:
- Create qualification questions specific to your service
- Set up scoring or filtering logic
- Define what makes a qualified prospect
- Configure conditional paths based on responses
- Set up disqualification messaging

### 3. Service Explanation and Value
**Purpose**: Help prospects understand what they'll get

**Content Elements**:
- Service packages and options
- Process and methodology
- Expected outcomes and results
- Timeline and commitment
- Investment ranges

**Customization Required**:
- Detail your service packages
- Explain your process step-by-step
- Set realistic outcome expectations
- Clarify time commitments
- Provide pricing guidance

### 4. Social Proof and Credibility
**Purpose**: Build trust and demonstrate expertise

**Content Elements**:
- Client testimonials
- Case studies and results
- Media mentions or publications
- Professional credentials
- Awards and recognition

**Customization Required**:
- Add client testimonials with results
- Create brief case studies
- Include media features or publications
- List relevant credentials
- Add any awards or recognition

### 5. Calendar Integration and Booking
**Purpose**: Enable easy scheduling

**Content Elements**:
- Available time slots
- Meeting type selection (phone, video, in-person)
- Duration options
- Time zone handling
- Confirmation and reminder system

**Customization Required**:
- Connect calendar system
- Set availability rules
- Configure meeting types and durations
- Set up confirmation emails
- Configure reminder sequence

### 6. Pre-Consultation Questionnaire
**Purpose**: Gather information to make consultation valuable

**Content Elements**:
- Background information
- Specific challenges or goals
- Previous attempts or solutions tried
- Questions for the consultation
- Any materials to review

**Customization Required**:
- Create questionnaire specific to your service
- Determine what information you need in advance
- Set up automated delivery after booking
- Configure submission deadline
- Set up review process for your team

## AI Configuration

### Conversation Prompts

**Initial Greeting**:
```
Welcome! I'm here to help you understand how [Your Name/Company] can help you [achieve specific outcome].

I work with [ideal client description] to [solve specific problem] through [your approach].

To see if we're a good fit and schedule a consultation, I'll ask you a few questions about your situation and goals.

Ready to get started?
```

**Qualification Questions**:
```
Let me understand your situation better:

1. What's your biggest challenge with [problem area] right now?
2. What have you tried so far to address this?
3. What would success look like for you?
4. What's your timeline for making progress on this?
5. Are you ready to invest in solving this problem?
```

**Service Explanation**:
```
Based on what you've shared, here's how I typically work with clients in your situation:

[Process Step 1]: [Description]
[Process Step 2]: [Description]
[Process Step 3]: [Description]

Most clients see [specific results] within [timeframe].

The investment for this work is typically [range], depending on [factors].

Does this approach resonate with you?
```

**Booking Prompt**:
```
Great! It sounds like we could be a good fit to work together.

The next step is a [duration] consultation where we'll:
- Dive deeper into your specific situation
- Explore potential solutions and approaches
- Determine if and how we should work together
- Answer any questions you have

I have availability on [dates/times]. What works best for you?
```

**Disqualification Message**:
```
Thank you for your interest! Based on what you've shared, I don't think I'm the best fit for your needs right now because [specific reason].

However, I'd recommend:
[Alternative resource or referral]

I wish you the best in [their goal]!
```

### Customization Instructions
- Replace [Your Name/Company] with your actual name or business name
- Update ideal client description to match your target market
- Add your specific process steps and approach
- Configure qualification logic based on your criteria
- Create appropriate disqualification messages

## Integration Setup

### Calendar Integration
**Supported Systems**: Calendly, Acuity, Google Calendar, Outlook, Cal.com

**Configuration Steps**:
1. Connect your calendar system
2. Set availability rules and buffer times
3. Configure meeting types (discovery call, strategy session, etc.)
4. Set meeting durations
5. Enable time zone detection
6. Test booking flow

**Best Practices**:
- Limit availability to maintain scarcity
- Use buffer times between meetings
- Block personal time
- Set maximum advance booking window
- Enable automatic time zone conversion

### CRM Integration
**Supported Systems**: HubSpot, Salesforce, Pipedrive, Zoho, Airtable

**Configuration Steps**:
1. Connect CRM system
2. Map qualification fields to CRM
3. Set up contact creation rules
4. Configure deal/opportunity creation
5. Set up activity logging
6. Test data synchronization

### Email Integration
**Supported Systems**: Gmail, Outlook, SendGrid, Mailchimp

**Configuration Steps**:
1. Connect email system
2. Create confirmation email template
3. Set up reminder sequence (24 hours, 1 hour before)
4. Configure post-consultation follow-up
5. Set up no-show follow-up
6. Test all email triggers

### Payment Integration (Optional)
**Supported Systems**: Stripe, PayPal, Square

**Configuration Steps**:
1. Connect payment processor
2. Set consultation fee (if applicable)
3. Configure refund policy
4. Set up payment confirmation
5. Test payment flow

## Analytics Configuration

### Key Metrics to Track

**Qualification Metrics**:
- Qualification completion rate
- Qualification pass rate
- Average qualification score
- Disqualification reasons
- Time to complete qualification

**Booking Metrics**:
- Booking conversion rate (qualified → booked)
- Average time to book
- Preferred meeting times
- Meeting type selection
- Cancellation rate

**Consultation Metrics**:
- Show rate (% who attend)
- No-show rate
- Reschedule rate
- Consultation-to-client conversion
- Average deal size from consultations

**Quality Metrics**:
- Client satisfaction with consultation
- Qualification accuracy
- Time saved vs. traditional booking
- Revenue per consultation
- Client lifetime value by source

### Analytics Setup
1. Configure booking funnel tracking
2. Set up qualification scoring
3. Enable consultation outcome tracking
4. Configure revenue attribution
5. Set up automated reporting

## Content Requirements

### Must-Have Content
- [ ] Clear service description
- [ ] Ideal client profile
- [ ] Your unique approach or methodology
- [ ] 3-5 client testimonials
- [ ] Professional bio and credentials
- [ ] Service packages and pricing guidance
- [ ] Consultation process explanation
- [ ] Pre-consultation questionnaire

### Nice-to-Have Content
- [ ] Video introduction
- [ ] Case studies with results
- [ ] Published articles or media features
- [ ] FAQ section
- [ ] Service comparison chart
- [ ] Client success stories
- [ ] Your philosophy or approach document

### Content Specifications
- **Professional Photo**: High-quality headshot
- **Testimonials**: Include name, role, and specific results
- **Case Studies**: Problem, solution, results format
- **Videos**: 1-2 minutes, professional quality
- **Text**: Conversational, authentic tone

## Customization Workflow

### Phase 1: Content Preparation (Day 1 Morning)
1. Write service description and positioning
2. Define ideal client profile
3. Gather testimonials and case studies
4. Create qualification questions
5. Write pre-consultation questionnaire
6. Prepare professional photo and bio

### Phase 2: Template Setup (Day 1 Afternoon)
1. Select consultation booking template
2. Upload content and imagery
3. Configure branding
4. Set up qualification logic
5. Configure AI conversation flows
6. Add social proof elements

### Phase 3: Calendar Configuration (Day 2 Morning)
1. Connect calendar system
2. Set availability rules
3. Configure meeting types
4. Set up confirmation emails
5. Create reminder sequence
6. Test booking process

### Phase 4: Integration Setup (Day 2 Afternoon)
1. Connect CRM if applicable
2. Set up email automation
3. Configure analytics tracking
4. Test all integrations
5. Set up payment if applicable

### Phase 5: Testing and Launch (Day 2 End)
1. Complete test booking
2. Verify all emails send correctly
3. Test on mobile devices
4. Review AI conversation quality
5. Deploy and share

## Best Practices

### Qualification Best Practices
- Ask questions that reveal fit, not just interest
- Be transparent about who you work with
- Respectfully disqualify poor fits
- Use qualification to personalize consultation
- Keep qualification brief (5-7 questions max)

### Booking Best Practices
- Limit availability to create scarcity
- Offer multiple meeting type options
- Make booking process simple (3 clicks or less)
- Send immediate confirmation
- Include clear preparation instructions

### Consultation Best Practices
- Review qualification responses before meeting
- Start on time and respect scheduled duration
- Have clear agenda and outcomes
- Take notes during consultation
- End with clear next steps

### Follow-Up Best Practices
- Send follow-up within 24 hours
- Include personalized recommendations
- Provide clear proposal or next steps
- Set deadline for decision
- Have nurture sequence for "not now" prospects

## Success Benchmarks

### Qualification Targets
- **Completion Rate**: 70-85% should complete qualification
- **Pass Rate**: 60-75% should qualify
- **Accuracy**: 80%+ of qualified prospects should be good fits
- **Time to Complete**: Under 5 minutes average

### Booking Targets
- **Conversion Rate**: 60-80% of qualified prospects should book
- **Show Rate**: 75-85% of booked consultations attended
- **Reschedule Rate**: Under 15%
- **Cancellation Rate**: Under 10%

### Consultation Targets
- **Consultation-to-Client**: 30-50% should become clients
- **Average Deal Size**: Track and optimize over time
- **Satisfaction Score**: 4.5+ out of 5.0
- **Referral Rate**: 20%+ should refer others

## Troubleshooting

### Low Qualification Completion
**Symptoms**: Many start but don't finish qualification
**Solutions**:
- Reduce number of questions
- Make questions more engaging
- Show progress indicator
- Explain why you're asking

### Low Booking Rate
**Symptoms**: Qualified prospects not scheduling
**Solutions**:
- Simplify booking process
- Offer more time slot options
- Reduce perceived commitment
- Add more social proof

### High No-Show Rate
**Symptoms**: Many booked consultations not attended
**Solutions**:
- Send more reminders
- Require pre-consultation questionnaire
- Add booking fee (refundable if attended)
- Call to confirm 24 hours before

### Low Conversion to Client
**Symptoms**: Good consultations but few become clients
**Solutions**:
- Improve qualification criteria
- Better prepare for consultations
- Strengthen consultation process
- Improve follow-up and proposals

## Template Variations

### High-Ticket Services Version
- Add more extensive qualification
- Include video introduction
- Require application process
- Add testimonials with revenue results
- Include case studies

### Group Coaching Version
- Show cohort start dates
- Include group size and dynamics
- Add peer testimonials
- Show community aspects
- Include group call schedule

### Free Consultation Version
- Emphasize "no obligation"
- Focus on value of consultation itself
- Include what they'll learn
- Add FAQ about what to expect
- Reduce qualification depth

### Paid Consultation Version
- Explain consultation fee and why
- Show what's included
- Offer credit toward services
- Add refund/guarantee policy
- Include payment in booking flow

## Support Resources

### Documentation
- Consultation booking setup guide
- Qualification question templates
- Email sequence templates
- Best practices checklist

### Examples
- Live consultation booking demonstrations
- High-converting examples by industry
- Before-and-after optimization case studies

### Getting Help
- Email: templates@encaptio.com
- Community forum for questions
- Professional services for custom setup

## Next Steps

1. Review this template documentation
2. Gather testimonials and credentials
3. Create qualification questions
4. Follow customization workflow
5. Test booking process thoroughly
6. Launch and monitor performance

Ready to streamline your consultation booking? Begin with Phase 1: Content Preparation.
