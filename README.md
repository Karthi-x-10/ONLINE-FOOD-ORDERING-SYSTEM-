# ONLINE-FOOD-ORDERING-SYSTEM-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FoodSavvy India | Compare Food Delivery Prices on Swiggy, Zomato, Magicpin, EatClub & ONDC</title>
  <meta name="description" content="Compare live food delivery prices and coupons in India across Swiggy, Zomato, Magicpin, EatClub, and ONDC. Guaranteed lowest price and maximum savings on every meal in INR (₹).">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="/css/style.css">
</head>
<body>

  <!-- Top Announcement Bar / Deal Radar Ticker -->
  <aside class="deal-ticker" aria-label="Live Flash Deals India">
    <div class="ticker-badge">
      <span class="pulse-dot"></span> LIVE DEAL RADAR INDIA
    </div>
    <div class="ticker-wrapper">
      <div class="ticker-content" id="dealTickerContent">
        <span>🔥 <strong>Swiggy:</strong> 50% OFF up to ₹100 with code <code>SWIGGYIT</code></span>
        <span>⚡ <strong>Zomato:</strong> Gold Free Delivery + 20% OFF with <code>ZOMATOGOLD</code></span>
        <span>✨ <strong>Magicpin:</strong> Flat ₹80 OFF with <code>MAGICPIN50</code></span>
        <span>🛵 <strong>EatClub:</strong> ₹0 Delivery Fee + Flat ₹100 OFF with <code>EATCLUB0</code></span>
        <span>🇮🇳 <strong>ONDC:</strong> Flat ₹60 Govt Network Subsidy with <code>ONDCDEAL</code></span>
        <span>🎉 <strong>Universal:</strong> Extra ₹50 OFF any platform with <code>INDIAEATS</code></span>
      </div>
    </div>
  </aside>

  <!-- Navigation Bar -->
  <header class="navbar" id="mainNavbar">
    <div class="nav-container">
      <a href="#" class="brand-logo" id="brandLogo">
        <div class="logo-icon">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M18 8h1a4 4 0 0 1 0 8h-1"></path>
            <path d="M2 8h16v9a4 4 0 0 1-4 4H6a4 4 0 0 1-4-4V8z"></path>
            <line x1="6" y1="1" x2="6" y2="4"></line>
            <line x1="10" y1="1" x2="10" y2="4"></line>
            <line x1="14" y1="1" x2="14" y2="4"></line>
          </svg>
        </div>
        <div class="logo-text">
          <span class="logo-title">Food<span class="highlight">Savvy</span> <span style="font-size:0.75rem; background:linear-gradient(90deg, #ff9933, #ffffff, #138808); -webkit-background-clip:text; -webkit-text-fill-color:transparent; font-weight:900;">INDIA 🇮🇳</span></span>
          <span class="logo-tagline">CROSS-PLATFORM ARBITRAGE</span>
        </div>
      </a>

      <!-- City / Micro-Location Selector -->
      <div class="location-picker" id="locationPicker">
        <button class="location-btn" id="locationBtn" title="Switch Delivery City or Area">
          <span class="loc-pin">📍</span>
          <span class="loc-text" id="activeLocationText">Indiranagar, Bengaluru</span>
          <span class="loc-arrow">▾</span>
        </button>
        <div class="location-dropdown" id="locationDropdown" style="display:none;">
          <div class="loc-dropdown-header">Select Delivery City in India</div>
          <div class="loc-options-list" id="locationOptionsList">
            <!-- Rendered dynamically -->
          </div>
        </div>
      </div>

      <!-- Search Input -->
      <div class="search-box">
        <svg class="search-icon" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="11" cy="11" r="8"></circle>
          <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
        </svg>
        <input type="text" id="searchInput" placeholder="Search biryani, dosa, butter chicken, momos, sweets..." autocomplete="off">
        <button class="search-clear-btn" id="searchClearBtn" title="Clear search" style="display:none;">&times;</button>
      </div>

      <!-- Nav Actions -->
      <div class="nav-actions">
        <button class="nav-btn savings-pill-btn" id="savingsDashboardBtn" title="View Lifetime Savings & Orders">
          <span class="icon">💰</span>
          <span class="btn-text">Saved: <strong id="navLifetimeSavings" style="color:var(--emerald);">₹322</strong></span>
        </button>

        <button class="nav-btn" id="dealsModalBtn" title="Browse Active Indian Vouchers">
          <span class="icon">🎟️</span>
          <span class="btn-text">Vouchers</span>
        </button>

        <button class="nav-btn" id="orderHistoryBtn" title="Live Delivery Status">
          <span class="icon">🛵</span>
          <span class="btn-text">Orders</span>
          <span class="active-badge" id="activeOrdersBadge" style="display:none;">1</span>
        </button>

        <button class="cart-btn" id="cartToggleBtn" title="View Cart & Price Comparison">
          <div class="cart-icon-wrapper">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <circle cx="9" cy="21" r="1"></circle>
              <circle cx="20" cy="21" r="1"></circle>
              <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path>
            </svg>
            <span class="cart-count" id="cartCount">0</span>
          </div>
          <span class="cart-total" id="cartNavTotal">₹0</span>
        </button>
      </div>
    </div>
  </header>

  <!-- Hero Section -->
  <main>
    <section class="hero-section">
      <div class="hero-bg-glow"></div>
      <div class="hero-content">
        <div class="hero-pill">
          <span class="pill-sparkle">🇮🇳</span> Compare Live Food Delivery Prices in India & Save up to ₹150 per meal!
        </div>
        <h1 class="hero-title">
          Never Overpay on Food Delivery in India <br>
          <span class="gradient-text">Swiggy • Zomato • Magicpin • EatClub • ONDC</span>
        </h1>
        <p class="hero-subtitle">
          Restaurant dish prices, platform fees (₹3-₹6), surge charges, and coupons vary drastically across Indian apps. FoodSavvy continuously audits all 5 platforms to guarantee you pay the absolute lowest price.
        </p>

        <!-- Supported Platforms Bar -->
        <div class="platform-strip">
          <span class="strip-label">MONITORED REAL-TIME:</span>
          <div class="platform-chips">
            <div class="platform-chip swig" data-platform="SWIGGY">
              <span class="plat-dot"></span> Swiggy
            </div>
            <div class="platform-chip zoma" data-platform="ZOMATO">
              <span class="plat-dot"></span> Zomato
            </div>
            <div class="platform-chip magic" data-platform="MAGICPIN">
              <span class="plat-dot"></span> Magicpin
            </div>
            <div class="platform-chip club" data-platform="EATCLUB">
              <span class="plat-dot"></span> EatClub
            </div>
            <div class="platform-chip ondc" data-platform="ONDC">
              <span class="plat-dot"></span> ONDC Food
            </div>
          </div>
        </div>

        <!-- Metric Badges -->
        <div class="hero-metrics">
          <div class="metric-card">
            <span class="metric-num">₹110+</span>
            <span class="metric-label">Average Savings per Order</span>
          </div>
          <div class="metric-card">
            <span class="metric-num">5 Apps</span>
            <span class="metric-label">Live Price Parity Audit</span>
          </div>
          <div class="metric-card">
            <span class="metric-num">Instant UPI</span>
            <span class="metric-label">GPay, PhonePe, Paytm, COD</span>
          </div>
          <div class="metric-card">
            <span class="metric-num">100% Free</span>
            <span class="metric-label">Zero Hidden Platform Fees</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Filters & Category Navigation -->
    <section class="controls-section">
      <div class="controls-container">
        <!-- Cuisine Chips -->
        <div class="cuisine-scroll" id="cuisineFilters">
          <button class="chip-btn active" data-category="ALL">🇮🇳 All Cuisines</button>
          <button class="chip-btn" data-category="Biryani">🍗 Biryani & Andhra</button>
          <button class="chip-btn" data-category="Dosa">🥞 South Indian Tiffins</button>
          <button class="chip-btn" data-category="Curries">🍛 North Indian & Tandoor</button>
          <button class="chip-btn" data-category="Chaat">🥟 Delhi Chaat & Sweets</button>
          <button class="chip-btn" data-category="Burgers">🍔 Indian Fusion Burgers</button>
          <button class="chip-btn" data-category="Desserts">🍨 Theobroma & Shakes</button>
        </div>

        <!-- Sorting & Dietary Filters -->
        <div class="filters-row">
          <div class="dietary-tags" id="dietaryFilters">
            <button class="diet-btn active" data-diet="ALL">All Dietary</button>
            <button class="diet-btn" data-diet="Veg">🥬 Pure Veg</button>
            <button class="diet-btn" data-diet="Non-Veg">🍗 Non-Veg</button>
            <button class="diet-btn" data-diet="Vegan">🌱 100% Vegan</button>
          </div>

          <div class="sort-wrapper">
            <label for="sortBySelect" class="sort-label">Sort by:</label>
            <select id="sortBySelect" class="sort-select">
              <option value="best-savings">💰 Highest ₹ Savings</option>
              <option value="rating">★ Highest Rated</option>
              <option value="speed">⚡ Fastest Delivery</option>
              <option value="price-asc">💵 Price: Low to High</option>
            </select>
          </div>
        </div>
      </div>
    </section>

    <!-- Restaurant & Menu Feed -->
    <section class="catalog-section">
      <div class="catalog-container">
        <div class="section-header">
          <div>
            <h2 class="section-title">Verified Indian Restaurants & Menus</h2>
            <p class="section-desc">Click any dish to inspect real-time pricing and fees across Swiggy, Zomato, Magicpin, EatClub & ONDC</p>
          </div>
          <div class="deal-guarantee-badge">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
            </svg>
            Lowest Price Guaranteed in India
          </div>
        </div>

        <!-- Restaurant Grid -->
        <div class="restaurant-grid" id="restaurantGrid">
          <!-- Populated dynamically by app.js -->
        </div>
      </div>
    </section>
  </main>

  <!-- Side-by-Side Platform Comparison Modal -->
  <div class="modal-overlay" id="compareModal" style="display:none;">
    <div class="modal-box compare-modal-box">
      <div class="modal-header">
        <div>
          <span class="modal-eyebrow">LIVE INDIAN PLATFORM ARBITRAGE</span>
          <h3 class="modal-title" id="compareModalItemName">Dish Name</h3>
          <p class="modal-sub" id="compareModalItemDesc">Comparing total cost across 5 Indian delivery apps including 5% GST and platform fees</p>
        </div>
        <button class="modal-close-btn" id="closeCompareModalBtn">&times;</button>
      </div>

      <!-- Best Value Alert Box -->
      <div class="best-value-banner" id="bestValueBanner">
        <div class="banner-icon">🏆</div>
        <div class="banner-text">
          <strong id="bestPlatformWinner">Platform Name</strong> gives you the best deal at <span class="highlight-price" id="bestPlatformPrice">₹0</span>.
          <span class="savings-pill" id="bestPlatformSavings">Save ₹0!</span>
        </div>
      </div>

      <!-- Platform Comparison Cards Container -->
      <div class="platform-cards-grid" id="platformComparisonGrid">
        <!-- Rendered dynamically -->
      </div>

      <div class="modal-footer">
        <button class="btn btn-secondary" id="compareCloseBtn">Close</button>
        <button class="btn btn-primary" id="compareAddToCartBtn">
          <span>Add Winning Deal to Cart</span> ⚡
        </button>
      </div>
    </div>
  </div>

  <!-- Voucher Vault Modal -->
  <div class="modal-overlay" id="dealsModal" style="display:none;">
    <div class="modal-box deals-modal-box">
      <div class="modal-header">
        <div>
          <span class="modal-eyebrow">VOUCHER RADAR INDIA</span>
          <h3 class="modal-title">Active Food Promo Codes</h3>
          <p class="modal-sub">Verified real-time coupons automatically tested and applied at checkout</p>
        </div>
        <button class="modal-close-btn" id="closeDealsModalBtn">&times;</button>
      </div>

      <div class="deals-tabs" id="dealsPlatformTabs">
        <button class="deals-tab-btn active" data-filter="ALL">All Platforms</button>
        <button class="deals-tab-btn" data-filter="SWIGGY">Swiggy</button>
        <button class="deals-tab-btn" data-filter="ZOMATO">Zomato</button>
        <button class="deals-tab-btn" data-filter="MAGICPIN">Magicpin</button>
        <button class="deals-tab-btn" data-filter="EATCLUB">EatClub</button>
        <button class="deals-tab-btn" data-filter="ONDC">ONDC Food</button>
      </div>

      <div class="deals-grid" id="dealsGrid">
        <!-- Rendered dynamically -->
      </div>
    </div>
  </div>

  <!-- Smart Cart Drawer -->
  <div class="cart-backdrop" id="cartBackdrop" style="display:none;"></div>
  <aside class="cart-drawer" id="cartDrawer">
    <div class="cart-header">
      <div class="cart-header-title">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="9" cy="21" r="1"></circle>
          <circle cx="20" cy="21" r="1"></circle>
          <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path>
        </svg>
        <h3>Your Smart Cart</h3>
      </div>
      <button class="cart-close-btn" id="closeCartBtn">&times;</button>
    </div>

    <!-- Multi-Platform Smart Selector Box -->
    <div class="cart-platform-optimizer" id="cartOptimizerBox" style="display:none;">
      <div class="optimizer-header">
        <span class="ai-sparkle">🤖</span>
        <strong>Multi-Platform Deal Analyzer</strong>
      </div>
      <p class="optimizer-summary" id="optimizerSummary">
        Analyzing Swiggy, Zomato, Magicpin, EatClub & ONDC for lowest total...
      </p>
      <div class="cart-platform-pills" id="cartPlatformPills">
        <!-- Rendered dynamically -->
      </div>
      <button class="auto-switch-btn" id="autoSwitchDealBtn" style="display:none;">
        ⚡ Auto-Switch to Best Deal (Save <span id="autoSwitchSaveAmount">₹0</span>)
      </button>
    </div>

    <!-- Cart Items List -->
    <div class="cart-items" id="cartItemsList">
      <div class="cart-empty-state">
        <div class="empty-icon">🍛</div>
        <p>Your cart is empty.</p>
        <small>Pick delicious Indian dishes to compare platform savings!</small>
      </div>
    </div>

    <!-- Promo Code Section -->
    <div class="cart-coupon-section" id="cartCouponSection" style="display:none;">
      <label for="couponInput" class="coupon-label">Have a promo code?</label>
      <div class="coupon-input-group">
        <input type="text" id="couponInput" placeholder="e.g. SWIGGYIT, ZOMATOGOLD, INDIAEATS" uppercase>
        <button id="applyCouponBtn" class="coupon-apply-btn">Apply</button>
      </div>
      <div class="coupon-feedback" id="couponFeedback"></div>
    </div>

    <!-- Cart Summary Breakdown -->
    <div class="cart-summary" id="cartSummary" style="display:none;">
      <div class="summary-line">
        <span>Food Subtotal</span>
        <span id="sumSubtotal">₹0</span>
      </div>
      <div class="summary-line">
        <span>Delivery Fee (<span id="sumPlatformName">Swiggy</span>)</span>
        <span id="sumDeliveryFee">₹0</span>
      </div>
      <div class="summary-line">
        <span>Platform Fee</span>
        <span id="sumServiceFee">₹0</span>
      </div>
      <div class="summary-line">
        <span>Restaurant GST (5%)</span>
        <span id="sumTaxes">₹0</span>
      </div>
      <div class="summary-line discount" id="sumDiscountRow" style="display:none;">
        <span>Promo Discount (<span id="sumCouponCode">NONE</span>)</span>
        <span id="sumDiscount">-₹0</span>
      </div>
      <div class="summary-separator"></div>
      <div class="summary-line total">
        <span>Total Payable</span>
        <span class="total-amount" id="sumGrandTotal">₹0</span>
      </div>
      <div class="savings-callout" id="sumSavingsCallout">
        🎉 You are saving <strong id="sumTotalSaved">₹0</strong> compared to highest delivery app!
      </div>

      <button class="checkout-btn" id="checkoutBtn">
        Proceed to Checkout ❯
      </button>
    </div>
  </aside>

  <!-- Checkout & Live Tracking Modal -->
  <div class="modal-overlay" id="checkoutModal" style="display:none;">
    <div class="modal-box checkout-modal-box">
      <!-- Checkout Form View -->
      <div id="checkoutFormView">
        <div class="modal-header">
          <div>
            <span class="modal-eyebrow">FAST & SECURE CHECKOUT</span>
            <h3 class="modal-title">Finalize Delivery in India</h3>
            <p class="modal-sub">Order will be placed on <strong id="checkoutPlatformBadge">Swiggy</strong> with highest savings</p>
          </div>
          <button class="modal-close-btn" id="closeCheckoutBtn">&times;</button>
        </div>

        <form id="checkoutForm" class="checkout-form">
          <div class="form-row">
            <div class="form-group">
              <label for="custName">Full Name</label>
              <input type="text" id="custName" value="Vikram Malhotra" required>
            </div>
            <div class="form-group">
              <label for="custPhone">Mobile Number (India)</label>
              <input type="tel" id="custPhone" value="+91 98765 43210" required>
            </div>
          </div>

          <div class="form-group">
            <label for="custAddress">Delivery Address</label>
            <input type="text" id="custAddress" value="Flat 402, Lotus Residency, 100ft Road, Indiranagar, Bengaluru - 560038" required>
          </div>

          <div class="form-group">
            <label for="custNotes">Delivery Instructions (Optional)</label>
            <input type="text" id="custNotes" placeholder="e.g. Ring bell twice, leave with security at main gate">
          </div>

          <div class="form-group">
            <label>Payment Method</label>
            <div class="payment-options">
              <label class="pay-option">
                <input type="radio" name="paymentMethod" value="upi" checked>
                <span>⚡ UPI (GPay / PhonePe / Paytm)</span>
              </label>
              <label class="pay-option">
                <input type="radio" name="paymentMethod" value="card">
                <span>💳 RuPay / Cards</span>
              </label>
              <label class="pay-option">
                <input type="radio" name="paymentMethod" value="cod">
                <span>💵 Cash on Delivery</span>
              </label>
            </div>
          </div>

          <div class="checkout-order-summary">
            <div class="checkout-summary-line">
              <span>Platform Selected:</span>
              <strong id="chkPlatformName">Swiggy</strong>
            </div>
            <div class="checkout-summary-line">
              <span>Your Net Savings:</span>
              <strong class="savings-text" id="chkSavings">₹0</strong>
            </div>
            <div class="checkout-summary-line total">
    