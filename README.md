# 🛤️ Onboarding Journey Builder

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Active](https://img.shields.io/badge/Status-Active-success.svg)](https://github.com/aakarsh-hub/onboarding-journey-builder)

A powerful visual workflow builder for creating and optimizing user onboarding journeys. Design multi-step onboarding flows, track user progress, and improve activation rates with data-driven insights.

## ✨ Key Features

- **Visual Workflow Builder**: Drag-and-drop interface for designing onboarding flows
- **Multi-Step Journeys**: Create complex branching onboarding paths
- **Progress Tracking**: Monitor user completion rates at each step
- **A/B Testing**: Test different onboarding variations
- **Analytics Dashboard**: Visualize drop-off points and completion funnels
- **Template Library**: Pre-built onboarding templates for common scenarios
- **Export/Import**: Share workflows as JSON templates
- **REST API**: Programmatic workflow management
- **Event Triggers**: Automated actions based on user behavior

## 🏗️ Architecture

```
Workflow Designer → Journey Engine → Event Tracker → Analytics → Dashboard
                       ↓
                User State Manager
```

## 🚦 Quick Start

### Prerequisites
- Python 3.8+
- Flask for backend API
- React/HTML for UI (optional)

### Installation

```bash
git clone https://github.com/aakarsh-hub/onboarding-journey-builder.git
cd onboarding-journey-builder
pip install -r requirements.txt
```

### Run the Application

```bash
# Start the backend API
python src/journey_api.py

# Open the visual builder
open http://localhost:7000
```

## 📊 Sample Usage

### Create a Journey

```python
from journey_builder import OnboardingJourney, Step

# Define onboarding journey
journey = OnboardingJourney(
    name="SaaS Product Onboarding",
    description="New user activation flow"
)

# Add steps
journey.add_step(Step(
    id="welcome",
    type="message",
    title="Welcome!",
    content="Let's get you started in 3 easy steps",
    next_step="profile_setup"
))

journey.add_step(Step(
    id="profile_setup",
    type="form",
    title="Complete Your Profile",
    fields=["name", "company", "role"],
    required=True,
    next_step="feature_tour"
))

journey.add_step(Step(
    id="feature_tour",
    type="interactive_tour",
    title="Quick Tour",
    highlights=["dashboard", "analytics", "settings"],
    next_step="first_action"
))

journey.add_step(Step(
    id="first_action",
    type="task",
    title="Create Your First Project",
    description="Let's create your first project together",
    completion_criteria="project_created",
    next_step="complete"
))

# Save journey
journey.save()
print(f"Journey created: {journey.id}")
```

### Track User Progress

```python
import requests

# Start user journey
response = requests.post('http://localhost:7000/api/journey/start', json={
    'journey_id': 'saas_onboarding_v1',
    'user_id': 'user_12345'
})

session = response.json()
print(f"Current step: {session['current_step']}")

# Complete a step
requests.post('http://localhost:7000/api/journey/complete_step', json={
    'session_id': session['id'],
    'step_id': 'profile_setup',
    'data': {
        'name': 'John Doe',
        'company': 'Acme Inc',
        'role': 'Product Manager'
    }
})
```

### Analyze Journey Performance

```python
from journey_builder import JourneyAnalytics

analytics = JourneyAnalytics(journey_id='saas_onboarding_v1')
stats = analytics.get_stats()

print(f"Total users started: {stats['total_started']}")
print(f"Completion rate: {stats['completion_rate']:.1%}")
print(f"Average time to complete: {stats['avg_completion_time']}")
print(f"\nStep-by-step breakdown:")
for step in stats['steps']:
    print(f"  {step['name']}: {step['completion_rate']:.1%} completed")
```

## 🧪 Running Tests

```bash
pytest tests/ -v --cov=src
```

Test coverage: **88%**

## 📁 Project Structure

```
onboarding-journey-builder/
├── src/
│   ├── journey_api.py        # REST API server
│   ├── journey_builder.py    # Core journey logic
│   ├── step_manager.py       # Step definitions
│   ├── user_state.py         # User progress tracking
│   ├── analytics.py          # Journey analytics
│   └── templates.py          # Pre-built templates
├── ui/
│   ├── index.html            # Visual workflow builder
│   ├── builder.js            # Drag-and-drop interface
│   └── styles.css
├── templates/
│   ├── saas_onboarding.json
│   ├── ecommerce_onboarding.json
│   └── mobile_app_onboarding.json
├── tests/
│   ├── test_journey.py
│   ├── test_steps.py
│   └── test_analytics.py
├── examples/
│   └── complete_journey_example.py
├── requirements.txt
└── README.md
```

## 🔧 Key Technologies

- **Backend**: Python, Flask, SQLAlchemy
- **Frontend**: HTML5, JavaScript, CSS
- **Database**: SQLite/PostgreSQL
- **Visualization**: D3.js, Chart.js
- **Testing**: Pytest

## 🎯 Step Types

### 1. Message Steps
Display information or welcome messages

### 2. Form Steps
Collect user information

### 3. Interactive Tours
Guided product tours with highlights

### 4. Task Steps
Require user to complete specific actions

### 5. Video/Tutorial Steps
Embedded video or tutorial content

### 6. Conditional Branches
Different paths based on user responses

### 7. Wait/Delay Steps
Time-based or event-based delays

## 📊 Pre-built Templates

1. **SaaS Product Onboarding**: Profile setup, feature tour, first action
2. **E-commerce**: Account creation, preferences, first purchase incentive
3. **Mobile App**: Permissions, tutorial, personalization
4. **B2B Platform**: Company setup, team invites, integration
5. **Content Platform**: Profile, interests, content recommendations

## 🎯 Use Cases

- **Product Teams**: Optimize new user activation
- **Growth Teams**: Improve conversion funnels
- **UX Designers**: Prototype onboarding flows
- **Customer Success**: Reduce time-to-value
- **Marketing**: Guide users to "aha" moments

## 📊 Analytics Features

- **Funnel Visualization**: See drop-off at each step
- **Time-to-Complete**: Track how long each step takes
- **Completion Rates**: Overall and per-step
- **User Segmentation**: Compare different user groups
- **A/B Test Results**: Statistical analysis of variants
- **Heatmaps**: Interaction patterns (when UI integrated)

## 🚀 Advanced Features

### Conditional Logic
Branch journeys based on:
- User attributes
- Previous responses
- External data
- Time/date conditions

### Event Triggers
Automate actions on:
- Step completion
- Journey abandonment
- Milestone achievements
- Time delays

### Personalization
Customize content based on:
- User role
- Industry
- Previous behavior
- Company size

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

MIT License - see LICENSE file for details

## 👤 Author

**Aakarsh**
- GitHub: [@aakarsh-hub](https://github.com/aakarsh-hub)

---

⭐ Star this repository if you're passionate about great user onboarding!
