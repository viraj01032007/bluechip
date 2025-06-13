<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BluechipProperty - Premium Property Solutions</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <style>
        body { 
            font-family: 'Inter', sans-serif; 
            overflow-x: hidden;
            padding-bottom: 120px;
        }
        
        .bluechip-gradient { 
            background: linear-gradient(135deg, #2563eb, #1d4ed8); 
        }
        
        .hero-overlay {
            background: linear-gradient(135deg, rgba(37, 99, 235, 0.8), rgba(29, 78, 216, 0.9));
        }
        
        .btn-primary { 
            background: #2563eb; 
            color: white; 
            padding: 0.875rem 2rem; 
            border-radius: 0.75rem; 
            transition: all 0.3s ease; 
            border: none; 
            cursor: pointer; 
            font-weight: 600; 
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
            font-size: 1rem;
            text-decoration: none;
        }
        
        .btn-primary:hover { 
            background: #1d4ed8; 
            transform: translateY(-2px);
            box-shadow: 0 10px 25px -5px rgba(37, 99, 235, 0.4);
        }

        .btn-secondary { 
            background: #f8fafc; 
            color: #334155; 
            padding: 0.875rem 2rem; 
            border-radius: 0.75rem; 
            transition: all 0.3s ease; 
            border: 2px solid #e2e8f0; 
            cursor: pointer; 
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }
        
        .btn-secondary:hover { 
            background: #f1f5f9; 
            border-color: #cbd5e1;
            transform: translateY(-1px);
        }

        .nav-link {
            position: relative;
            transition: all 0.3s ease;
            padding: 0.5rem 0;
            text-decoration: none;
            cursor: pointer;
        }
        
        .nav-link:hover {
            color: #2563eb;
        }
        
        .nav-link.active {
            color: #2563eb;
            font-weight: 600;
        }
        
        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #2563eb, #3b82f6);
            border-radius: 2px;
        }

        .property-card {
            transition: all 0.3s ease;
            border: 2px solid transparent;
            cursor: pointer;
        }
        
        .property-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            border-color: #e2e8f0;
        }

        .modal { 
            display: none; 
            position: fixed; 
            z-index: 1000; 
            left: 0; 
            top: 0; 
            width: 100%; 
            height: 100%; 
            background-color: rgba(0,0,0,0.6); 
            overflow-y: auto;
            padding: 1rem;
            backdrop-filter: blur(4px);
        }
        
        .modal.show { 
            display: flex; 
            align-items: center; 
            justify-content: center; 
        }
        
        .modal-content { 
            background: white; 
            border-radius: 1rem; 
            padding: 2rem; 
            max-width: 900px; 
            width: 100%; 
            max-height: 90vh; 
            overflow-y: auto;
            position: relative;
            animation: slideIn 0.3s ease-out;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .page-section {
            display: none;
        }

        .page-section.active {
            display: block;
        }

        .transparent-pricing {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(135deg, #8b5cf6, #7c3aed);
            backdrop-filter: blur(10px);
            z-index: 50;
            padding: 1rem;
            border-top: 1px solid rgba(255, 255, 255, 0.2);
        }

        .pricing-item {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 0.75rem;
            padding: 1rem;
            text-align: center;
            color: white;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .pricing-item:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .form-input {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 2px solid #e2e8f0;
            border-radius: 0.5rem;
            transition: all 0.3s ease;
            font-size: 1rem;
        }

        .form-input:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #374151;
        }

        .masked-info {
            background: #fef3c7;
            border: 1px solid #f59e0b;
            border-radius: 0.5rem;
            padding: 0.75rem;
            margin: 0.5rem 0;
            position: relative;
        }

        .unlock-btn {
            background: #f59e0b;
            color: white;
            border: none;
            border-radius: 0.25rem;
            padding: 0.25rem 0.5rem;
            font-size: 0.75rem;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .unlock-btn:hover {
            background: #d97706;
        }

        .contact-agent-btn {
            background: #10b981;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 1rem 0;
            width: 100%;
        }

        .contact-agent-btn:hover {
            background: #059669;
            transform: translateY(-1px);
        }

        .bed-selector {
            display: inline-block;
            width: 60px;
            height: 60px;
            background: white;
            border: 2px solid #e2e8f0;
            border-radius: 0.5rem;
            margin: 0.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .bed-selector:hover {
            border-color: #2563eb;
            background: #eff6ff;
        }

        .bed-selector.occupied {
            background: #fee2e2;
            border-color: #ef4444;
            cursor: not-allowed;
        }

        .bed-selector.selected {
            background: #dbeafe;
            border-color: #2563eb;
        }

        .virtual-room {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 1rem;
            max-width: 300px;
            margin: 2rem auto;
            padding: 2rem;
            background: #f8fafc;
            border-radius: 1rem;
            border: 2px solid #e2e8f0;
        }

        .virtual-room.four-bed {
            grid-template-columns: repeat(2, 1fr);
        }

        .image-upload-area {
            border: 2px dashed #9ca3af;
            border-radius: 0.75rem;
            padding: 2rem;
            text-align: center;
            background: #f8fafc;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .image-upload-area:hover {
            border-color: #2563eb;
            background: #eff6ff;
        }

        .loading-spinner {
            border: 2px solid #f3f4f6;
            border-top: 2px solid #2563eb;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 0.5rem;
            padding: 1rem;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.2);
            z-index: 1001;
            transform: translateX(100%);
            transition: transform 0.3s ease;
        }

        .toast.show {
            transform: translateX(0);
        }

        .toast.success {
            border-left: 4px solid #10b981;
        }

        .toast.error {
            border-left: 4px solid #ef4444;
        }

        .sign-in-btn {
            background: #4285f4;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            border-radius: 0.5rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 0.5rem 0;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .sign-in-btn:hover {
            background: #3367d6;
            transform: translateY(-1px);
        }

        .sign-in-btn.twitter {
            background: #1da1f2;
        }

        .sign-in-btn.twitter:hover {
            background: #0d8bd9;
        }

        .footer {
            background: #1f2937;
            color: white;
            padding: 3rem 0 1rem;
            margin-top: 4rem;
        }

        .footer h3 {
            color: white;
            font-weight: 600;
            margin-bottom: 1rem;
        }

        .footer a {
            color: #d1d5db;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer a:hover {
            color: white;
        }

        .footer-divider {
            border-top: 1px solid #374151;
            margin: 2rem 0 1rem;
        }

        .social-icon {
            width: 40px;
            height: 40px;
            background: #374151;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #d1d5db;
            transition: all 0.3s ease;
        }

        .social-icon:hover {
            background: #2563eb;
            color: white;
            transform: translateY(-2px);
        }

        .divider {
            position: relative;
            text-align: center;
            margin: 24px 0;
        }

        .divider::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 0;
            right: 0;
            height: 1px;
            background: #e2e8f0;
        }

        .divider span {
            background: white;
            padding: 0 16px;
            color: #64748b;
            font-size: 14px;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Header -->
    <header class="bg-white shadow-lg sticky top-0 z-40 backdrop-blur-md bg-white/95">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-18">
                <div class="flex items-center space-x-4 cursor-pointer py-2" onclick="showPage('home')">
                    <div class="w-12 h-12 bluechip-gradient rounded-xl flex items-center justify-center shadow-lg">
                        <i class="fas fa-building text-white text-xl"></i>
                    </div>
                    <div>
                        <h1 class="text-2xl font-bold text-gray-900">BluechipProperty</h1>
                        <p class="text-sm text-gray-500 font-medium">Premium Solutions</p>
                    </div>
                </div>
                
                <!-- Mobile Menu Button -->
                <button class="md:hidden p-3 rounded-lg hover:bg-gray-100 transition-colors" onclick="toggleMobileMenu()">
                    <i id="menuIcon" class="fas fa-bars text-gray-700 text-xl"></i>
                </button>
                
                <!-- Desktop Navigation -->
                <nav class="hidden md:flex items-center space-x-8">
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600 active" onclick="showPage('home')" data-page="home">Home</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('sale')" data-page="sale">Sale Properties</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('rentals')" data-page="rentals">Rentals</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('pg')" data-page="pg">PG Listings</a>
                    <a href="#" class="nav-link font-medium text-gray-700 hover:text-blue-600" onclick="showPage('list')" data-page="list">List Property</a>
                    
                    <!-- Sign In Button -->
                    <button onclick="openSignInModal()" class="btn-primary ml-4">
                        <i class="fas fa-user mr-2"></i>
                        Sign In
                    </button>
                </nav>
            </div>
            
            <!-- Mobile Navigation -->
            <div id="mobileMenu" class="md:hidden hidden bg-white border-t border-gray-200">
                <div class="px-4 py-4 space-y-3">
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('home'); toggleMobileMenu()">Home</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('sale'); toggleMobileMenu()">Sale Properties</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('rentals'); toggleMobileMenu()">Rentals</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('pg'); toggleMobileMenu()">PG Listings</a>
                    <a href="#" class="block py-3 font-medium text-gray-700 hover:text-blue-600" onclick="showPage('list'); toggleMobileMenu()">List Property</a>
                    <button onclick="openSignInModal(); toggleMobileMenu()" class="btn-primary w-full mt-4">
                        <i class="fas fa-user mr-2"></i>
                        Sign In
                    </button>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main>
        <!-- Home Page -->
        <div id="home" class="page-section active">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <!-- Hero Section -->
                <div class="relative rounded-2xl overflow-hidden mb-12">
                    <div class="hero-overlay absolute inset-0 z-10"></div>
                    <img 
                        src="https://images.unsplash.com/photo-1486406146926-c627a92ad1ab?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2000&h=800" 
                        alt="Modern city skyline with glass buildings" 
                        class="w-full h-96 object-cover" 
                    />
                    
                    <div class="absolute inset-0 z-20 flex items-center justify-center text-center text-white">
                        <div class="max-w-4xl px-6">
                            <h2 class="text-5xl md:text-6xl font-bold mb-6">Find Your Dream Property</h2>
                            <p class="text-xl md:text-2xl mb-8 text-gray-100">
                                Discover premium properties, PG accommodations, and rental spaces with transparent pricing
                            </p>
                            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                                <button onclick="showPage('sale')" class="btn-primary text-lg px-8 py-4">
                                    <i class="fas fa-home mr-2"></i>
                                    Browse Properties
                                </button>
                                <button onclick="showPage('pg')" class="btn-secondary text-lg px-8 py-4 bg-white/20 border-white/30 text-white hover:bg-white/30 hover:text-white">
                                    <i class="fas fa-bed mr-2"></i>
                                    Find PG
                                </button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Featured Properties Section -->
                <div class="mb-12">
                    <h3 class="text-3xl font-bold text-gray-900 mb-8 text-center">Featured Properties</h3>
                    <div id="featuredProperties" class="grid md:grid-cols-3 gap-8">
                        <!-- Featured properties will be loaded here -->
                    </div>
                </div>

                <!-- Services Section -->
                <div class="grid md:grid-cols-3 gap-8 mb-12">
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-all duration-300">
                        <div class="w-16 h-16 bluechip-gradient rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-home text-white text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-4">Property Sales</h3>
                        <p class="text-gray-600">Find your perfect home with our curated selection of premium properties.</p>
                    </div>
                    
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-all duration-300">
                        <div class="w-16 h-16 bg-green-500 rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-key text-white text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-4">Rental Properties</h3>
                        <p class="text-gray-600">Flexible rental options for short-term and long-term stays.</p>
                    </div>
                    
                    <div class="bg-white rounded-xl p-8 shadow-lg hover:shadow-xl transition-all duration-300">
                        <div class="w-16 h-16 bg-purple-500 rounded-xl flex items-center justify-center mb-6">
                            <i class="fas fa-bed text-white text-2xl"></i>
                        </div>
                        <h3 class="text-xl font-bold text-gray-900 mb-4">PG Accommodations</h3>
                        <p class="text-gray-600">Comfortable paying guest accommodations with modern amenities.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Properties Page -->
        <div id="sale" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-3xl font-bold text-gray-900 mb-8">Properties for Sale</h2>
                <div id="saleProperties" class="grid md:grid-cols-3 gap-8">
                    <!-- Sale properties will be loaded here -->
                </div>
            </div>
        </div>

        <div id="rentals" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-3xl font-bold text-gray-900 mb-8">Rental Properties</h2>
                <div id="rentalProperties" class="grid md:grid-cols-3 gap-8">
                    <!-- Rental properties will be loaded here -->
                </div>
            </div>
        </div>

        <div id="pg" class="page-section">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                <h2 class="text-3xl font-bold text-gray-900 mb-8">PG Accommodations</h2>
                <div id="pgProperties" class="grid md:grid-cols-3 gap-8">
                    <!-- PG properties will be loaded here -->
                </div>
            </div>
        </div>

        <!-- List Property Page -->
        <div id="list" class="page-section">
            <div class="max-w-xl mx-auto px-4 sm:px-6 lg:px-4 py-8">
                <div class="bg-white rounded-lg shadow-lg p-8">
                    <h2 class="text-sm font-bold text-gray-900 mb-8 text-center">List Your Property</h2>
                    
                    <div class="bg-amber-50 border border-amber-200 rounded-lg p-4 mb-6">
                        <div class="flex items-center">
                            <i class="fas fa-upload text-amber-600 mr-3"></i>
                            <span class="text-amber-800 font-medium">Listing Fee: ₹999 (One-time payment)</span>
                        </div>
                    </div>

                    <form id="listPropertyForm" class="space-y-6">
                        <div class="form-group">
                            <label class="form-label">Property Title</label>
                            <input type="text" name="title" class="form-input" placeholder="Enter property title" required>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Property Type</label>
                            <select name="type" class="form-input" required>
                                <option value="">Select property type</option>
                                <option value="sale">For Sale</option>
                                <option value="rent">For Rent</option>
                                <option value="pg">PG Accommodation</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Price (₹)</label>
                            <input type="number" name="price" class="form-input" placeholder="Enter price" required>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Location </label>
                            <input type="text" name="location" class="form-input" placeholder="e.g., Sec 15, Belapur" required>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Exact Location </label>
                            <input type="text" name="exactLocation" class="form-input" placeholder="Enter full address with plot/building details" required>
                        </div>

                        <div class="grid grid-cols-3 gap-4">
                            <div class="form-group">
                                <label class="form-label">Bedrooms</label>
                                <input type="number" name="bedrooms" class="form-input" min="1" value="1" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Bathrooms</label>
                                <input type="number" name="bathrooms" class="form-input" min="1" value="1" required>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Area (sq ft)</label>
                                <input type="number" name="area" class="form-input" min="1" value="500" required>
                            </div>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Description</label>
                            <textarea name="description" class="form-input" rows="4" placeholder="Describe your property" required></textarea>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Property Images</label>
                            <div class="image-upload-area" onclick="document.getElementById('imageInput').click()">
                                <i class="fas fa-cloud-upload-alt text-gray-400 text-4xl mb-4"></i>
                                <p class="text-gray-600">Click to upload images</p>
                                <input type="file" id="imageInput" multiple accept="image/*" style="display: none;" onchange="handleImageUpload(event)">
                            </div>
                            <div id="imagePreviews" class="mt-4 grid grid-cols-3 gap-4"></div>
                        </div>

                        <div class="form-group">
                            <label class="form-label">Contact Number</label>
                            <input type="tel" name="contact" class="form-input" placeholder="Enter contact number" required>
                        </div>

                        <button type="submit" class="btn-primary w-full py-4 text-lg">
                            <i class="fas fa-upload mr-2"></i>
                            List Property for ₹999
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </main>

    <!-- Footer -->
    <footer class="footer">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-4 gap-8">
                <!-- Company Info -->
                <div>
                    <div class="flex items-center space-x-3 mb-4">
                        <div class="w-10 h-10 bluechip-gradient rounded-lg flex items-center justify-center">
                            <i class="fas fa-building text-white"></i>
                        </div>
                        <h3 class="text-xl font-bold">BluechipProperty</h3>
                    </div>
                    <p class="text-gray-400 mb-4">Premium property solutions with transparent pricing. Find your dream home or list your property with us.</p>
                    <div class="flex space-x-3">
                        <a href="#" class="social-icon">
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="#" class="social-icon">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                </div>

                <!-- Quick Links -->
                <div>
                    <h3>Quick Links</h3>
                    <ul class="space-y-2">
                        <li><a href="#" onclick="showPage('home')">Home</a></li>
                        <li><a href="#" onclick="showPage('sale')">Properties for Sale</a></li>
                        <li><a href="#" onclick="showPage('rentals')">Rental Properties</a></li>
                        <li><a href="#" onclick="showPage('pg')">PG Listings</a></li>
                        <li><a href="#" onclick="showPage('list')">List Property</a></li>
                    </ul>
                </div>

                <!-- Services -->
                <div>
                    <h3>Services</h3>
                    <ul class="space-y-2">
                        <li><a href="#">Property Valuation</a></li>
                        <li><a href="#">Home Loans</a></li>
                        <li><a href="#">Legal Services</a></li>
                        <li><a href="#">Property Management</a></li>
                        <li><a href="#">Investment Consulting</a></li>
                    </ul>
                </div>

                <!-- Contact Info -->
                <div>
                    <h3>Contact Us</h3>
                    <ul class="space-y-2">
                        <li class="flex items-center">
                            <i class="fas fa-phone mr-2 text-blue-500"></i>
                            <span>+91 98765 43210</span>
                        </li>
                        <li class="flex items-center">
                            <i class="fas fa-envelope mr-2 text-blue-500"></i>
                            <span>info@bluechipproperty.com</span>
                        </li>
                        <li class="flex items-center">
                            <i class="fas fa-map-marker-alt mr-2 text-blue-500"></i>
                            <span>Navi Mumbai, Maharashtra</span>
                        </li>
                        <li class="flex items-center">
                            <i class="fas fa-clock mr-2 text-blue-500"></i>
                            <span>Mon - Sat: 9AM - 7PM</span>
                        </li>
                    </ul>
                </div>
            </div>

            <div class="footer-divider"></div>
            
            <div class="flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-400 text-sm">
                    &copy; 2024 BluechipProperty. All rights reserved.
                </p>
                <div class="flex space-x-6 mt-2 md:mt-0">
                    <a href="#" class="text-gray-400 hover:text-white text-sm">Privacy Policy</a>
                    <a href="#" class="text-gray-400 hover:text-white text-sm">Terms of Service</a>
                    <a href="#" class="text-gray-400 hover:text-white text-sm">Cookie Policy</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- Sign In Modal -->
    <div id="signInModal" class="modal">
        <div class="modal-content" style="max-width: 400px;">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold">Sign In</h2>
                <button onclick="closeSignInModal()" class="text-gray-500 hover:text-gray-700 text-2xl">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="space-y-4">
                <button onclick="signInWithGoogle()" class="sign-in-btn">
                    <i class="fab fa-google mr-2"></i>
                    Continue with Google
                </button>
                
                <button onclick="signInWithTwitter()" class="sign-in-btn twitter">
                    <i class="fab fa-twitter mr-2"></i>
                    Continue with Twitter
                </button>
                
                <div class="divider">
                    <span class="bg-white px-4 text-gray-500">or</span>
                </div>
                
                <form id="emailSignInForm" class="space-y-4">
                    <div class="form-group">
                        <label class="form-label">Email</label>
                        <input type="email" name="email" class="form-input" placeholder="Enter your email" required>
                    </div>
                    
                    <div class="form-group">
                        <label class="form-label">Password</label>
                        <input type="password" name="password" class="form-input" placeholder="Enter your password" required>
                    </div>
                    
                    <button type="submit" class="btn-primary w-full">
                        <i class="fas fa-sign-in-alt mr-2"></i>
                        Sign In
                    </button>
                </form>
                
                <div class="text-center">
                    <p class="text-gray-600 text-sm">
                        Don't have an account? 
                        <a href="#" class="text-blue-600 hover:underline" onclick="switchToSignUp()">Sign up here</a>
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- Property Modal -->
    <div id="propertyModal" class="modal">
        <div class="modal-content">
            <div class="flex justify-between items-center mb-6">
                <h2 id="modalTitle" class="text-2xl font-bold"></h2>
                <button onclick="closeModal()" class="text-gray-500 hover:text-gray-700 text-2xl">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="grid md:grid-cols-2 gap-6">
                <div>
                    <img id="modalImage" src="" alt="" class="w-full h-64 object-cover rounded-lg mb-4">
                    
                    <div class="grid grid-cols-3 gap-4 mb-6">
                        <div class="text-center p-3 bg-gray-50 rounded-lg">
                            <i class="fas fa-bed text-blue-600 text-xl mb-2"></i>
                            <div class="text-sm text-gray-600">Bedrooms</div>
                            <div id="modalBedrooms" class="font-bold"></div>
                        </div>
                        <div class="text-center p-3 bg-gray-50 rounded-lg">
                            <i class="fas fa-bath text-blue-600 text-xl mb-2"></i>
                            <div class="text-sm text-gray-600">Bathrooms</div>
                            <div id="modalBathrooms" class="font-bold"></div>
                        </div>
                        <div class="text-center p-3 bg-gray-50 rounded-lg">
                            <i class="fas fa-expand-arrows-alt text-blue-600 text-xl mb-2"></i>
                            <div class="text-sm text-gray-600">Area</div>
                            <div id="modalArea" class="font-bold"></div>
                        </div>
                    </div>
                </div>
                
                <div>
                    <div id="modalPrice" class="text-3xl font-bold text-blue-600 mb-4"></div>
                    
                    <div id="locationInfo" class="masked-info mb-4">
                        <div class="flex items-center justify-between">
                            <span class="flex items-center">
                                <i class="fas fa-map-marker-alt mr-2"></i>
                                <span id="locationText"></span>
                            </span>
                            <button id="unlockLocationBtn" class="unlock-btn" onclick="unlockLocation()">
                                ₹49
                            </button>
                        </div>
                    </div>
                    
                    <div id="contactInfo" class="masked-info mb-6">
                        <div class="flex items-center justify-between">
                            <span class="flex items-center">
                                <i class="fas fa-phone mr-2"></i>
                                <span id="contactText"></span>
                            </span>
                            <button id="unlockContactBtn" class="unlock-btn" onclick="unlockContact()">
                                ₹99
                            </button>
                        </div>
                    </div>
                    
                    <div class="mb-6">
                        <h4 class="text-lg font-bold text-gray-900 mb-2">Description</h4>
                        <p id="modalDescription" class="text-gray-600"></p>
                    </div>
                    
                    <button class="contact-agent-btn" onclick="contactAgent()">
                        <i class="fas fa-user mr-2"></i>
                        Contact Agent
                    </button>
                    
                    <div id="virtualRoomSection" class="mt-6" style="display: none;">
                        <h4 class="text-lg font-bold text-gray-900 mb-4">Virtual Room View</h4>
                        <div id="virtualRoom" class="virtual-room">
                            <!-- Virtual room beds will be populated here -->
                        </div>
                        <div class="flex items-center justify-center mt-4 text-sm text-gray-600">
                            <div class="flex items-center mr-6">
                                <div class="w-4 h-4 bg-white border-2 border-gray-300 rounded mr-2"></div>
                                <span>Available</span>
                            </div>
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-red-100 border-2 border-red-400 rounded mr-2"></div>
                                <span>Occupied</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Bed Booking Modal -->
    <div id="bedBookingModal" class="modal">
        <div class="modal-content" style="max-width: 500px;">
            <div class="flex justify-between items-center mb-6">
                <h2 id="bedBookingTitle" class="text-xl font-bold">Book Bed #1</h2>
                <button onclick="closeBedBookingModal()" class="text-gray-500 hover:text-gray-700 text-2xl">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <form id="bedBookingForm" class="space-y-4">
                <div class="form-group">
                    <label class="form-label">Your Name</label>
                    <input type="text" name="name" class="form-input" placeholder="Enter your name" required>
                </div>
                
                <div class="form-group">
                    <label class="form-label">Contact Number</label>
                    <input type="tel" name="contact" class="form-input" placeholder="Enter your contact number" required>
                </div>
                
                <div class="form-group">
                    <label class="form-label">Check-in Date</label>
                    <input type="date" name="checkin" class="form-input" required>
                </div>
                
                <div class="form-group">
                    <label class="form-label">Duration</label>
                    <select name="duration" class="form-input" required>
                        <option value="">Select duration</option>
                        <option value="1">1 Month</option>
                        <option value="3">3 Months</option>
                        <option value="6">6 Months</option>
                        <option value="12">12 Months</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label class="form-label">Additional Details</label>
                    <textarea name="details" class="form-input" rows="3" placeholder="Any special requirements or notes"></textarea>
                </div>
                
                <button type="submit" class="btn-primary w-full">
                    <i class="fas fa-paper-plane mr-2"></i>
                    Submit Booking Request
                </button>
            </form>
        </div>
    </div>




    <!-- Toast Container -->
    <div id="toastContainer"></div>

    <script>
        // Sample Property Data
        const properties = [
            {
                id: 1,
                title: "Luxury 3BHK Apartment",
                type: "sale",
                price: 12500000,
                maskedLocation: "Sec 15, Belapur",
                exactLocation: "Sector 15, Plot 23, Belapur, Navi Mumbai - 400614",
                maskedContact: "99XXXXXXX",
                fullContact: "9987654321",
                description: "Spacious 3BHK apartment with modern amenities, parking, and 24/7 security. Prime location with easy access to schools, hospitals, and shopping centers.",
                image: "https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 3,
                bathrooms: 2,
                area: 1250,
                isPG: false,
                virtualRoom: null,
                status: "active"
            },
            {
                id: 2,
                title: "Modern 2BHK Rental",
                type: "rent",
                price: 25000,
                maskedLocation: "Sec 7, Vashi",
                exactLocation: "Sector 7, Building A-301, Vashi, Navi Mumbai - 400703",
                maskedContact: "98XXXXXXX",
                fullContact: "9876543210",
                description: "Well-furnished 2BHK apartment for rent with all modern amenities. Ideal for families and working professionals.",
                image: "https://images.unsplash.com/photo-1502672260266-1c1ef2d93688?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 2,
                bathrooms: 1,
                area: 900,
                isPG: false,
                virtualRoom: null,
                status: "active"
            },
            {
                id: 3,
                title: "Premium PG for Students",
                type: "pg",
                price: 12000,
                maskedLocation: "Sec 12, Kharghar",
                exactLocation: "Sector 12, Near Railway Station, Kharghar, Navi Mumbai - 410210",
                maskedContact: "97XXXXXXX",
                fullContact: "9765432109",
                description: "Comfortable PG accommodation with AC rooms, WiFi, meals, and housekeeping. Perfect for students and working professionals.",
                image: "https://images.unsplash.com/photo-1555854877-bab0e460b527?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 4,
                bathrooms: 2,
                area: 200,
                isPG: true,
                virtualRoom: {
                    beds: 4,
                    occupancy: [false, true, false, false]
                },
                status: "active"
            },
            {
                id: 4,
                title: "Cozy 1BHK Studio",
                type: "rent",
                price: 18000,
                maskedLocation: "Sec 20, CBD Belapur",
                exactLocation: "Sector 20, Tower B-1205, CBD Belapur, Navi Mumbai - 400614",
                maskedContact: "96XXXXXXX",
                fullContact: "9654321098",
                description: "Modern studio apartment perfect for singles or couples. Fully furnished with balcony and city view.",
                image: "https://images.unsplash.com/photo-1522708323590-d24dbb6b0267?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 1,
                bathrooms: 1,
                area: 650,
                isPG: false,
                virtualRoom: null,
                status: "active"
            },
            {
                id: 5,
                title: "Executive PG - AC Rooms",
                type: "pg",
                price: 15000,
                maskedLocation: "Sec 8, Airoli",
                exactLocation: "Sector 8, Opposite Metro Station, Airoli, Navi Mumbai - 400708",
                maskedContact: "95XXXXXXX",
                fullContact: "9543210987",
                description: "Premium PG with AC rooms, gym, common area, and 24/7 security. All meals included with housekeeping service.",
                image: "https://images.unsplash.com/photo-1586023492125-27b2c045efd7?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 2,
                bathrooms: 2,
                area: 150,
                isPG: true,
                virtualRoom: {
                    beds: 2,
                    occupancy: [true, false]
                },
                status: "active"
            },
            {
                id: 6,
                title: "Spacious 4BHK Villa",
                type: "sale",
                price: 28500000,
                maskedLocation: "Sec 22, Kamothe",
                exactLocation: "Sector 22, Villa Complex, Kamothe, Navi Mumbai - 410209",
                maskedContact: "94XXXXXXX",
                fullContact: "9432109876",
                description: "Independent villa with garden, parking for 2 cars, and premium fittings. Quiet residential area with excellent connectivity.",
                image: "https://images.unsplash.com/photo-1449844908441-8829872d2607?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&h=600",
                bedrooms: 4,
                bathrooms: 3,
                area: 2200,
                isPG: false,
                virtualRoom: null,
                status: "active"
            }
        ];

        // Global variables
        let currentProperty = null;
        let selectedBed = null;
        let uploadedImages = [];

        // Utility Functions
        function formatPrice(price, type) {
            if (type === 'sale') {
                return `₹${(price / 100000).toFixed(1)} Lakhs`;
            } else {
                return `₹${price.toLocaleString()}/month`;
            }
        }

        function showToast(message, type = 'success') {
            const toast = document.createElement('div');
            toast.className = `toast ${type}`;
            toast.innerHTML = `
                <div class="flex items-center justify-between">
                    <span>${message}</span>
                    <button onclick="this.parentElement.parentElement.remove()" class="ml-4 text-gray-500 hover:text-gray-700">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
            `;
            
            document.getElementById('toastContainer').appendChild(toast);
            
            setTimeout(() => {
                toast.classList.add('show');
            }, 100);
            
            setTimeout(() => {
                toast.classList.remove('show');
                setTimeout(() => toast.remove(), 300);
            }, 5000);
        }

        // Navigation Functions
        function showPage(page) {
            // Hide all pages
            const pages = document.querySelectorAll('.page-section');
            pages.forEach(p => p.classList.remove('active'));
            
            // Show selected page
            document.getElementById(page).classList.add('active');
            
            // Update nav links
            const navLinks = document.querySelectorAll('.nav-link');
            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('data-page') === page || 
                   (page === 'sale' && link.getAttribute('data-page') === 'sale') ||
                   (page === 'rentals' && link.getAttribute('data-page') === 'rentals') ||
                   (page === 'pg' && link.getAttribute('data-page') === 'pg') ||
                   (page === 'list' && link.getAttribute('data-page') === 'list') ||
                   (page === 'home' && link.getAttribute('data-page') === 'home')) {
                    link.classList.add('active');
                }
            });
            
            // Load properties based on page
            if (page === 'home') {
                loadFeaturedProperties();
            } else if (page === 'sale') {
                loadPropertiesByType('sale', 'saleProperties');
            } else if (page === 'rentals') {
                loadPropertiesByType('rent', 'rentalProperties');
            } else if (page === 'pg') {
                loadPropertiesByType('pg', 'pgProperties');
            }
        }

        function toggleMobileMenu() {
            const mobileMenu = document.getElementById('mobileMenu');
            const menuIcon = document.getElementById('menuIcon');
            
            if (mobileMenu.classList.contains('hidden')) {
                mobileMenu.classList.remove('hidden');
                menuIcon.className = 'fas fa-times text-gray-700 text-xl';
            } else {
                mobileMenu.classList.add('hidden');
                menuIcon.className = 'fas fa-bars text-gray-700 text-xl';
            }
        }

        // Property Loading Functions
        function loadFeaturedProperties() {
            const container = document.getElementById('featuredProperties');
            const featuredProps = properties.slice(0, 3);
            container.innerHTML = featuredProps.map(property => createPropertyCard(property)).join('');
        }

        function loadPropertiesByType(type, containerId) {
            const container = document.getElementById(containerId);
            const filteredProps = properties.filter(p => p.type === type);
            
            if (filteredProps.length === 0) {
                container.innerHTML = `
                    <div class="col-span-full text-center py-12">
                        <p class="text-gray-600 text-lg">No properties found for this category.</p>
                    </div>
                `;
            } else {
                container.innerHTML = filteredProps.map(property => createPropertyCard(property)).join('');
            }
        }

        function createPropertyCard(property) {
            const priceText = property.type === 'sale' 
                ? `₹${(property.price / 100000).toFixed(1)}L`
                : `₹${property.price.toLocaleString()}/month`;

            return `
                <div class="property-card bg-white rounded-xl shadow-lg overflow-hidden" onclick="openPropertyModal(${property.id})">
                    <div class="relative">
                        <img src="${property.image}" alt="${property.title}" class="w-full h-48 object-cover">
                        <div class="absolute top-4 right-4 bg-blue-600 text-white px-3 py-1 rounded-full text-sm font-semibold">
                            ${property.type.toUpperCase()}
                        </div>
                    </div>
                    
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-gray-900 mb-2">${property.title}</h3>
                        
                        <div class="flex items-center text-gray-600 mb-2">
                            <i class="fas fa-map-marker-alt mr-2"></i>
                            <span>${property.maskedLocation}</span>
                        </div>
                        
                        <div class="flex items-center justify-between mb-4">
                            <div class="text-2xl font-bold text-blue-600">${priceText}</div>
                            <div class="flex items-center text-gray-500 text-sm">
                                <i class="fas fa-bed mr-1"></i>
                                <span class="mr-3">${property.bedrooms} bed</span>
                                <i class="fas fa-bath mr-1"></i>
                                <span>${property.bathrooms} bath</span>
                            </div>
                        </div>
                        
                        <button class="btn-primary w-full">
                            <i class="fas fa-eye mr-2"></i>
                            View Details
                        </button>
                    </div>
                </div>
            `;
        }

        // Modal Functions
        function openPropertyModal(propertyId) {
            currentProperty = properties.find(p => p.id === propertyId);
            if (!currentProperty) return;

            // Populate modal content
            document.getElementById('modalTitle').textContent = currentProperty.title;
            document.getElementById('modalImage').src = currentProperty.image;
            document.getElementById('modalImage').alt = currentProperty.title;
            document.getElementById('modalBedrooms').textContent = currentProperty.bedrooms;
            document.getElementById('modalBathrooms').textContent = currentProperty.bathrooms;
            document.getElementById('modalArea').textContent = currentProperty.area + ' sq ft';
            document.getElementById('modalPrice').textContent = formatPrice(currentProperty.price, currentProperty.type);
            document.getElementById('modalDescription').textContent = currentProperty.description;
            
            // Location info
            document.getElementById('locationText').textContent = currentProperty.maskedLocation;
            document.getElementById('unlockLocationBtn').style.display = 'block';
            
            // Contact info
            document.getElementById('contactText').textContent = currentProperty.maskedContact;
            document.getElementById('unlockContactBtn').style.display = 'block';
            
            // Virtual room for PG properties
            if (currentProperty.isPG && currentProperty.virtualRoom) {
                document.getElementById('virtualRoomSection').style.display = 'block';
                createVirtualRoom(currentProperty.virtualRoom);
            } else {
                document.getElementById('virtualRoomSection').style.display = 'none';
            }

            // Show modal
            document.getElementById('propertyModal').classList.add('show');
        }

        function closeModal() {
            document.getElementById('propertyModal').classList.remove('show');
            currentProperty = null;
        }

        function createVirtualRoom(virtualRoom) {
            const container = document.getElementById('virtualRoom');
            container.className = `virtual-room ${virtualRoom.beds === 4 ? 'four-bed' : 'two-bed'}`;
            
            container.innerHTML = virtualRoom.occupancy.map((occupied, index) => `
                <div class="bed-selector ${occupied ? 'occupied' : ''}" 
                     onclick="selectBed(${index}, ${occupied})"
                     title="${occupied ? 'Occupied' : 'Available'}">
                    <div class="absolute inset-0 flex items-center justify-center">
                        <i class="fas fa-bed text-gray-400"></i>
                    </div>
                    <div class="absolute bottom-1 right-1 text-xs font-bold">
                        ${index + 1}
                    </div>
                </div>
            `).join('');
        }

        function selectBed(bedIndex, isOccupied) {
            if (isOccupied) return;
            
            selectedBed = bedIndex;
            document.getElementById('bedBookingTitle').textContent = `Book Bed #${bedIndex + 1}`;
            document.getElementById('bedBookingModal').classList.add('show');
        }

        function closeBedBookingModal() {
            document.getElementById('bedBookingModal').classList.remove('show');
            selectedBed = null;
        }

        // Payment Functions
        function unlockLocation() {
            if (!currentProperty) return;
            
            const btn = document.getElementById('unlockLocationBtn');
            btn.innerHTML = '<div class="loading-spinner"></div>';
            btn.disabled = true;
            
            // Simulate payment processing
            setTimeout(() => {
                document.getElementById('locationText').textContent = currentProperty.exactLocation;
                btn.style.display = 'none';
                showToast('Location unlocked successfully!');
            }, 1500);
        }

        function unlockContact() {
            if (!currentProperty) return;
            
            const btn = document.getElementById('unlockContactBtn');
            btn.innerHTML = '<div class="loading-spinner"></div>';
            btn.disabled = true;
            
            // Simulate payment processing
            setTimeout(() => {
                document.getElementById('contactText').textContent = currentProperty.fullContact;
                btn.style.display = 'none';
                
                // Add call button
                const contactInfo = document.getElementById('contactInfo');
                contactInfo.innerHTML = `
                    <div class="flex items-center justify-between">
                        <span class="flex items-center">
                            <i class="fas fa-phone mr-2"></i>
                            <span>${currentProperty.fullContact}</span>
                        </span>
                        <button onclick="window.open('tel:${currentProperty.fullContact}', '_blank')" class="btn-primary text-sm px-3 py-1">
                            <i class="fas fa-phone mr-1"></i>
                            Call Now
                        </button>
                    </div>
                `;
                
                showToast('Contact details unlocked successfully!');
            }, 1500);
        }

        function contactAgent() {
            if (!currentProperty) return;
            
            const message = `Hi, I'm interested in ${currentProperty.title} located at ${currentProperty.maskedLocation}. Can you provide more details?`;
            const whatsappUrl = `https://wa.me/919876543210?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        }

        function handlePricingClick(type) {
            switch(type) {
                case 'location':
                    showToast('Click on any property to unlock exact location for ₹49', 'info');
                    break;
                case 'contact':
                    showToast('Click on any property to unlock full contact details for ₹99', 'info');
                    break;
                case 'listing':
                    showPage('list');
                    break;
            }
        }

        // Sign In Functions
        function openSignInModal() {
            document.getElementById('signInModal').classList.add('show');
        }

        function closeSignInModal() {
            document.getElementById('signInModal').classList.remove('show');
        }

        function signInWithGoogle() {
            showToast('Google Sign In successful! Welcome back.');
            closeSignInModal();
            updateSignInState('Google User');
        }

        function signInWithTwitter() {
            showToast('Twitter Sign In successful! Welcome back.');
            closeSignInModal();
            updateSignInState('Twitter User');
        }

        function updateSignInState(userName) {
            const signInBtn = document.querySelector('nav button[onclick="openSignInModal()"]');
            const mobileSignInBtn = document.querySelector('#mobileMenu button[onclick*="openSignInModal"]');
            
            if (signInBtn) {
                signInBtn.innerHTML = `
                    <i class="fas fa-user-circle mr-2"></i>
                    ${userName}
                `;
                signInBtn.setAttribute('onclick', 'showUserMenu()');
            }
            
            if (mobileSignInBtn) {
                mobileSignInBtn.innerHTML = `
                    <i class="fas fa-user-circle mr-2"></i>
                    ${userName}
                `;
                mobileSignInBtn.setAttribute('onclick', 'showUserMenu(); toggleMobileMenu()');
            }
        }

        function showUserMenu() {
            showToast('User menu functionality coming soon!');
        }

        function switchToSignUp() {
            showToast('Sign up functionality coming soon!');
        }

        // Form Handling
        function handleImageUpload(event) {
            const files = Array.from(event.target.files);
            const previewContainer = document.getElementById('imagePreviews');
            
            files.forEach((file, index) => {
                if (file.type.startsWith('image/') && file.size <= 5 * 1024 * 1024) {
                    uploadedImages.push(file);
                    
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const div = document.createElement('div');
                        div.className = 'relative';
                        div.innerHTML = `
                            <img src="${e.target.result}" alt="Property ${uploadedImages.length}" class="w-full h-24 object-cover rounded-lg">
                            <button type="button" onclick="removeImage(${uploadedImages.length - 1})" 
                                    class="absolute top-1 right-1 bg-red-500 text-white rounded-full w-6 h-6 flex items-center justify-center text-xs hover:bg-red-600">
                                <i class="fas fa-times"></i>
                            </button>
                        `;
                        previewContainer.appendChild(div);
                    };
                    reader.readAsDataURL(file);
                } else {
                    showToast(`Invalid file: ${file.name}. Please upload images under 5MB.`, 'error');
                }
            });
        }

        function removeImage(index) {
            uploadedImages.splice(index, 1);
            document.getElementById('imagePreviews').innerHTML = '';
            
            // Rebuild previews
            uploadedImages.forEach((file, i) => {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const div = document.createElement('div');
                    div.className = 'relative';
                    div.innerHTML = `
                        <img src="${e.target.result}" alt="Property ${i + 1}" class="w-full h-24 object-cover rounded-lg">
                        <button type="button" onclick="removeImage(${i})" 
                                class="absolute top-1 right-1 bg-red-500 text-white rounded-full w-6 h-6 flex items-center justify-center text-xs hover:bg-red-600">
                            <i class="fas fa-times"></i>
                        </button>
                    `;
                    document.getElementById('imagePreviews').appendChild(div);
                };
                reader.readAsDataURL(file);
            });
        }

        // Event Listeners
        document.addEventListener('DOMContentLoaded', function() {
            // Load initial content
            loadFeaturedProperties();
            
            // Property listing form
            document.getElementById('listPropertyForm').addEventListener('submit', function(e) {
                e.preventDefault();
                
                if (uploadedImages.length === 0) {
                    showToast('Please upload at least one image', 'error');
                    return;
                }
                
                const formData = new FormData(this);
                const propertyData = Object.fromEntries(formData);
                
                // Simulate form submission
                const submitBtn = this.querySelector('button[type="submit"]');
                const originalText = submitBtn.innerHTML;
                submitBtn.innerHTML = '<div class="loading-spinner mr-2"></div>Processing...';
                submitBtn.disabled = true;
                
                setTimeout(() => {
                    showToast('Property listed successfully! It will be reviewed and published within 24 hours.');
                    this.reset();
                    uploadedImages = [];
                    document.getElementById('imagePreviews').innerHTML = '';
                    submitBtn.innerHTML = originalText;
                    submitBtn.disabled = false;
                }, 2000);
            });
            
            // Bed booking form
            document.getElementById('bedBookingForm').addEventListener('submit', function(e) {
                e.preventDefault();
                
                const formData = new FormData(this);
                const bookingData = Object.fromEntries(formData);
                
                // Simulate booking submission
                const submitBtn = this.querySelector('button[type="submit"]');
                const originalText = submitBtn.innerHTML;
                submitBtn.innerHTML = '<div class="loading-spinner mr-2"></div>Submitting...';
                submitBtn.disabled = true;
                
                setTimeout(() => {
                    showToast('Booking request submitted! You will be contacted soon.');
                    this.reset();
                    closeBedBookingModal();
                    submitBtn.innerHTML = originalText;
                    submitBtn.disabled = false;
                }, 1500);
            });
            
            // Email sign in form
            document.getElementById('emailSignInForm').addEventListener('submit', function(e) {
                e.preventDefault();
                
                const formData = new FormData(this);
                const email = formData.get('email');
                
                showToast('Email sign in successful! Welcome back.');
                closeSignInModal();
                updateSignInState(email.split('@')[0]);
                this.reset();
            });
            
            // Close modals when clicking outside
            document.getElementById('propertyModal').addEventListener('click', function(e) {
                if (e.target === this) {
                    closeModal();
                }
            });
            
            document.getElementById('bedBookingModal').addEventListener('click', function(e) {
                if (e.target === this) {
                    closeBedBookingModal();
                }
            });
            
            document.getElementById('signInModal').addEventListener('click', function(e) {
                if (e.target === this) {
                    closeSignInModal();
                }
            });
        });
    </script>
</body>
</html>
