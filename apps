// Load after DOM is fully loaded
document.addEventListener('DOMContentLoaded', function() {
    console.log("DOM fully loaded and parsed");
    
    // Set up all event listeners
    setupEventListeners();
});

// Guide Text Data from CSV
const guideTextData = [
    {
        "User Goal": "Strengthen my position",
        "IP Type": "Trade mark (registered)",
        "Guide Text": "Someone else is using a name very similar to my registered trade mark. I want to understand what steps I can take to protect it going forward."
    },
    {
        "User Goal": "Strengthen my position",
        "IP Type": "Patent",
        "Guide Text": "I think a competitor's product is similar to my patent, and I want to make sure I'm prepared if they try to copy it more directly."
    },
    {
        "User Goal": "Strengthen my position",
        "IP Type": "Design",
        "Guide Text": "A new product has a similar look to my registered design. I'm not sure if it's an issue, but I want to understand what I can do to protect my design."
    },
    {
        "User Goal": "Strengthen my position",
        "IP Type": "Unregistered brand or business name",
        "Guide Text": "I've been using my business name and logo for years, and now someone else is using something very similar. I want to know how to protect myself."
    },
    {
        "User Goal": "Strengthen my position",
        "IP Type": "Uncertain / mixed rights",
        "Guide Text": "I'm not sure what kind of IP this relates to, but I want to understand how to protect my position going forward."
    },
    {
        "User Goal": "Explore ways to reach an agreement",
        "IP Type": "Trade mark (registered)",
        "Guide Text": "Another business is using a trade mark that's similar to mine. I'd prefer to resolve it directly if possible—maybe through a licensing agreement or negotiation."
    },
    {
        "User Goal": "Explore ways to reach an agreement",
        "IP Type": "Patent",
        "Guide Text": "I believe another company is using my patented technology. I'd like to understand if there's a way to reach an agreement without going to court."
    },
    {
        "User Goal": "Explore ways to reach an agreement",
        "IP Type": "Design",
        "Guide Text": "Someone else is selling a product that looks like mine. I want to know if there's a way to come to an agreement before this escalates."
    },
    {
        "User Goal": "Explore ways to reach an agreement",
        "IP Type": "Unregistered brand or business name",
        "Guide Text": "We've both been using similar business names. I want to understand my options to avoid a long dispute and see if we can agree on something."
    },
    {
        "User Goal": "Explore ways to reach an agreement",
        "IP Type": "Uncertain / mixed rights",
        "Guide Text": "There's a disagreement about an idea or product, and I want to understand what kind of agreement might be possible to resolve it."
    },
    {
        "User Goal": "Prevent potential infringement",
        "IP Type": "Trade mark (registered)",
        "Guide Text": "We're launching a new product line and I want to be sure the branding won't lead to issues with similar trade marks."
    },
    {
        "User Goal": "Prevent potential infringement",
        "IP Type": "Patent",
        "Guide Text": "I'm about to launch something and want to be sure it doesn't infringe anyone else's patent."
    },
    {
        "User Goal": "Prevent potential infringement",
        "IP Type": "Design",
        "Guide Text": "I'm about to release a new product and want to make sure no one can copy the look of it once it's out."
    },
    {
        "User Goal": "Prevent potential infringement",
        "IP Type": "Unregistered brand or business name",
        "Guide Text": "I heard someone might be planning to launch a business with a name very close to mine. I want to know what I can do now to stop this before it happens."
    },
    {
        "User Goal": "Prevent potential infringement",
        "IP Type": "Uncertain / mixed rights",
        "Guide Text": "I want to take some steps to stop others from copying what we've created, but I'm not sure what kind of rights apply."
    },
    {
        "User Goal": "Get professional support",
        "IP Type": "Trade mark (registered)",
        "Guide Text": "I've seen someone using a logo that looks like mine, and I'd like to talk to a professional about whether that's an issue."
    },
    {
        "User Goal": "Get professional support",
        "IP Type": "Patent",
        "Guide Text": "I think my invention might be protected under a patent, but I don't know what to do next. I'd like help from someone who can guide me."
    },
    {
        "User Goal": "Get professional support",
        "IP Type": "Design",
        "Guide Text": "I've registered a design but someone's making something similar. I want to speak to someone who can help me understand if that matters."
    },
    {
        "User Goal": "Get professional support",
        "IP Type": "Unregistered brand or business name",
        "Guide Text": "I'm not sure how to protect my business name or branding. I'd like to speak with someone who can help me figure out what rights I might have."
    },
    {
        "User Goal": "Get professional support",
        "IP Type": "Uncertain / mixed rights",
        "Guide Text": "I'm not sure what kind of IP rights are involved but I need help understanding where to go from here."
    }
];

// IP Enforcement Options Data
const ipOptionsData = [
    {
        "Overtitle": "Patent opposition",
        "Main Title": "Challenge a new or amended patent",
        "Description": "Initiate a challenge to the validity of a new patent with IP Australia",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Patent"
    },
    {
        "Overtitle": "Patent re-examination",
        "Main Title": "Challenge a granted patent",
        "Description": "Request a re-examination with IP Australia, to revoke or amend a granted patent",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Patent"
    },
    {
        "Overtitle": "Court - Patent",
        "Main Title": "Seek binding, authoritative decisions",
        "Description": "Escalate a wide range of patent matters to court",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Patent"
    },
    {
        "Overtitle": "Trade mark opposition",
        "Main Title": "Challenge a new or amended trade mark",
        "Description": "Initiate a challenge to a trade mark application with IP Australia",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Trade mark"
    },
    {
        "Overtitle": "Non-use removal",
        "Main Title": "Challenge inactive trade marks",
        "Description": "Apply to remove a registered trade mark that is not being used",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Trade mark"
    },
    {
        "Overtitle": "Court - Trade mark",
        "Main Title": "Seek binding, authoritative decisions",
        "Description": "Escalate a wide range of trade mark matters to court",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Trade mark"
    },
    {
        "Overtitle": "Design opposition",
        "Main Title": "Challenge a design",
        "Description": "Initiate a challenge to the validity of a registered design with IP Australia",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Designs"
    },
    {
        "Overtitle": "Court - Design",
        "Main Title": "Seek binding, authoritative decisions",
        "Description": "Escalate a wide range of design matters to court",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "Designs"
    },
    {
        "Overtitle": "PBR opposition",
        "Main Title": "Challenge a plant breeder's right",
        "Description": "Initiate a challenge to the validity of a plant breeder's right with IP Australia",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "PBR"
    },
    {
        "Overtitle": "Court - PBR",
        "Main Title": "Seek binding, authoritative decisions",
        "Description": "Escalate a wide range of plant breeder's right matters to court",
        "Response Type": "Enforcement; Accused",
        "Right it applies to": "PBR"
    },
    {
        "Overtitle": "Representation services",
        "Main Title": "Get help from IP professionals",
        "Description": "Engage an attorney or lawyer for representation and advice",
        "Response Type": "Support",
        "Right it applies to": "Any"
    },
    {
        "Overtitle": "IP Australia",
        "Main Title": "Contact for general guidance",
        "Description": "Reach out for general information about IP rights and processes",
        "Response Type": "Support",
        "Right it applies to": "Any"
    },
    {
        "Overtitle": "Warning letter",
        "Main Title": "Send a formal notice",
        "Description": "Communicate concerns and request action through a formal letter",
        "Response Type": "Enforcement",
        "Right it applies to": "Any"
    },
    {
        "Overtitle": "Online platforms",
        "Main Title": "Report IP violations on digital platforms",
        "Description": "Use online platforms' reporting tools to address IP infringements",
        "Response Type": "Enforcement",
        "Right it applies to": "Trade mark; Copyright"
    },
    {
        "Overtitle": "Border measures",
        "Main Title": "Block import of infringing products",
        "Description": "Use customs notices to prevent importation of infringing goods",
        "Response Type": "Enforcement",
        "Right it applies to": "Trade mark"
    },
    {
        "Overtitle": "Licensing",
        "Main Title": "Authorise others to use your IP",
        "Description": "Create agreements that permit others to use your IP under specific terms",
        "Response Type": "Agreement",
        "Right it applies to": "Any"
    },
    {
        "Overtitle": "Settlement agreement",
        "Main Title": "Reach a formal resolution",
        "Description": "Create a binding agreement to resolve an IP dispute",
        "Response Type": "Agreement",
        "Right it applies to": "Any"
    },
    {
        "Overtitle": "Mediation",
        "Main Title": "Work with a neutral facilitator",
        "Description": "Engage a mediator to help parties reach agreement",
        "Response Type": "Agreement",
        "Right it applies to": "Any"
    }
];

// DOM Elements
const situationForm = document.getElementById('situationForm');
const promptContainer = document.getElementById('promptContainer');
const resultsContainer = document.getElementById('resultsContainer');
const resultsGrid = document.getElementById('resultsGrid');
const userDescription = document.getElementById('userDescription');
const editDescriptionBtn = document.getElementById('editDescription');
const backButton = document.getElementById('backButton');
const descriptionField = document.getElementById('description');

// Filter elements
const situationFilter = document.getElementById('situationFilter');
const focusFilter = document.getElementById('focusFilter');
const ipTypeFilter = document.getElementById('ipTypeFilter');

// Function to set up all event listeners
function setupEventListeners() {
    console.log("Setting up event listeners");
    
    // Get elements
    const situationSelect = document.getElementById('situation');
    const focusSelect = document.getElementById('focus');
    const ipTypeSelect = document.getElementById('ipType');
    const guideTextContainer = document.getElementById('guideTextContainer');
    const guideText = document.getElementById('guideText');
    
    // Edit description button
    editDescriptionBtn.addEventListener('click', function() {
        promptContainer.

          // Function to set up all event listeners
function setupEventListeners() {
    console.log("Setting up event listeners");
    
    // Get elements
    const situationSelect = document.getElementById('situation');
    const focusSelect = document.getElementById('focus');
    const ipTypeSelect = document.getElementById('ipType');
    const guideTextContainer = document.getElementById('guideTextContainer');
    const guideText = document.getElementById('guideText');
    
    // Edit description button
    editDescriptionBtn.addEventListener('click', function() {
        promptContainer.style.display = 'block';
        resultsContainer.style.display = 'none';
    });
    
    // Back button
    backButton.addEventListener('click', function() {
        promptContainer.style.display = 'block';
        resultsContainer.style.display = 'none';
    });
    
    // Filter change events - make cards update reactively
    situationFilter.addEventListener('change', function() {
        updateResults();
    });
    
    focusFilter.addEventListener('change', function() {
        updateResults();
    });
    
    ipTypeFilter.addEventListener('change', function() {
        updateResults();
    });
    
    // Handle input changes for guide text updates
    situationSelect.addEventListener('change', updateGuideText);
    focusSelect.addEventListener('change', updateGuideText);
    ipTypeSelect.addEventListener('change', updateGuideText);
    
    // Submit form event
    situationForm.addEventListener('submit', function(e) {
        e.preventDefault();
        showResults();
    });
    
    // Direct button click as a fallback
    document.getElementById('exploreBtn').addEventListener('click', function() {
        // Check form validity
        if (situationForm.checkValidity()) {
            showResults();
        } else {
            // Trigger form validation
            const submitEvent = new Event('submit', { cancelable: true });
            situationForm.dispatchEvent(submitEvent);
        }
    });
    
    // Function to update guide text based on selections
    function updateGuideText() {
        // Get current selections
        const focusValue = focusSelect.value;
        const ipTypeValue = ipTypeSelect.value;
        
        // Map focus dropdown values to User Goal values in the CSV
        const focusToGoalMap = {
            'strengthen': 'Strengthen my position',
            'agreement': 'Explore ways to reach an agreement',
            'prevent': 'Prevent potential infringement',
            'support': 'Get professional support'
        };
        
        const userGoal = focusToGoalMap[focusValue];
        
        // Find matching guide text
        let matchingGuideText = null;
        
        if (userGoal && ipTypeValue) {
            // Try to find exact match first
            matchingGuideText = guideTextData.find(item => 
                item["User Goal"] === userGoal && 
                item["IP Type"] === ipTypeValue
            );
            
            // If no exact match, try partial matches
            if (!matchingGuideText) {
                // Try to match on patterns like "Trade mark (registered or unregistered)"
                matchingGuideText = guideTextData.find(item => 
                    item["User Goal"] === userGoal && 
                    item["IP Type"].includes(ipTypeValue)
                );
            }
        }
        
        // Update the guide text
        if (matchingGuideText) {
            guideText.textContent = matchingGuideText["Guide Text"];
            guideTextContainer.classList.add('active');
            
            // Also update description placeholder
            descriptionField.placeholder = matchingGuideText["Guide Text"];
        } else {
            guideText.textContent = "Select options above to see relevant examples...";
            guideTextContainer.classList.remove('active');
            descriptionField.placeholder = "This helps us show you content that may be more relevant.";
        }
    }
}

// Function to show results page
function showResults() {
    // Get form values
    const situation = document.getElementById('situation').value;
    const focus = document.getElementById('focus').value;
    const ipType = document.getElementById('ipType').value;
    const description = document.getElementById('description').value;
    
    console.log("Showing results for:", { situation, focus, ipType });
    
    // Show results container, hide prompt container
    promptContainer.style.display = 'none';
    resultsContainer.style.display = 'block';
    
    // Set filters to match form values
    situationFilter.value = situation;
    focusFilter.value = focus;
    ipTypeFilter.value = ipType;
    
    // Display user description
    userDescription.textContent = description || "No description provided.";
    
    // Generate results
    generateResults(ipType);
}

// Update results when filters change
function updateResults() {
    const ipType = ipTypeFilter.value;
    
    // Add animation class to cards
    const cards = document.querySelectorAll('.card:not(:first-child)');
    cards.forEach(card => {
        card.classList.add('card-updating');
    });
    
    // Generate new results after a short delay for animation
    setTimeout(() => {
        generateResults(ipType);
    }, 300);
}

// Generate results based on IP type and filters
function generateResults(ipType) {
    // Clear previous results
    resultsGrid.innerHTML = '';
    
    // Map from dropdown value to data value
    const ipTypeMap = {
        'Trade mark (registered)': 'Trade mark',
        'Unregistered brand or business name': 'Trade mark',
        'Uncertain / mixed rights': 'Any'
    };
    
    // Get the mapped value or use the original if no mapping exists
    const mappedIpType = ipTypeMap[ipType] || ipType;
    
    // Filter options based on IP type
    const filteredOptions = ipOptionsData.filter(option => {
        // Check if the option applies to selected IP type or "Any" or "All types"
        return option["Right it applies to"] === mappedIpType || 
               option["Right it applies to"] === "Any" || 
               option["Right it applies to"] === "All types" ||
               option["Right it applies to"].includes(mappedIpType);
    });
    
    // Create cards for each filtered option with staggered animation
    filteredOptions.forEach((option, index) => {
        const card = createCard(option);
        
        // Add staggered animation
        card.style.animationDelay = `${index * 0.05}s`;
        card.classList.add('card-animated');
        
        resultsGrid.appendChild(card);
    });
    
    // If no results, show a message
    if (filteredOptions.length === 0) {
        const noResults = document.createElement('div');
        noResults.className = 'card';
        noResults.innerHTML = `
            <h3 class="card-title">No options found</h3>
            <p>We couldn't find any specific options matching your criteria. Try adjusting your filters or contact an IP professional for assistance.</p>
        `;
        resultsGrid.appendChild(noResults);
    }
}

// Create a card element for an IP option
function createCard(option) {
    const card = document.createElement('div');
    card.className = `card card-${option["Right it applies to"].split(';')[0].trim().replace(/\s+/g, '-')}`;
    
    // Determine tag classes based on right it applies to
    const rightTypes = option["Right it applies to"].split(';').map(type => type.trim());
    const tagHtml = rightTypes.map(type => 
        `<span class="feature-tag tag-${type.replace(/\s+/g, '-')}">${type}</span>`
    ).join('');
    
    card.innerHTML = `
        <div class="card-overtitle">${option.Overtitle}</div>
        <h3 class="card-title">${option["Main Title"]}</h3>
        <p>${option.Description}</p>
        <div class="card-tags">
            ${tagHtml}
        </div>
    `;
    
    return card;
}
