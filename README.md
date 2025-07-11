# WordPress-website
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ApnaStore - The Everything Store</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <!-- Google Fonts: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Custom Styles -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* Dropdown styles */
        .dropdown:hover .dropdown-menu {
            display: block;
        }

        /* Modal styles */
        .modal {
            transition: opacity 0.25s ease;
        }

        /* Slider Styles */
        .slider-container {
            position: relative;
            max-width: 100%;
            height: 60vh;
            /* Adjust height as needed */
            margin: auto;
            overflow: hidden;
        }

        .slide {
            display: none;
            width: 100%;
            height: 100%;
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .slide-content {
            position: absolute;
            bottom: 10%;
            left: 5%;
            color: white;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 8px;
        }

        .prev,
        .next {
            cursor: pointer;
            position: absolute;
            top: 50%;
            width: auto;
            padding: 16px;
            margin-top: -22px;
            color: white;
            font-weight: bold;
            font-size: 24px;
            transition: 0.6s ease;
            border-radius: 0 3px 3px 0;
            user-select: none;
            background-color: rgba(0, 0, 0, 0.3);
        }

        .next {
            right: 0;
            border-radius: 3px 0 0 3px;
        }

        .prev:hover,
        .next:hover {
            background-color: rgba(0, 0, 0, 0.8);
        }

        .dots-container {
            text-align: center;
            position: absolute;
            bottom: 20px;
            width: 100%;
        }

        .dot {
            cursor: pointer;
            height: 15px;
            width: 15px;
            margin: 0 2px;
            background-color: #bbb;
            border-radius: 50%;
            display: inline-block;
            transition: background-color 0.6s ease;
        }

        .dot.active,
        .dot:hover {
            background-color: #717171;
        }

        /* Equal height product cards */
        .product-card {
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .product-card .card-content {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }

        .product-card .card-footer {
            margin-top: auto;
        }

        /* Deal badge */
        .deal-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: #CC0C39;
            color: white;
            padding: 3px 8px;
            border-radius: 3px;
            font-size: 12px;
            font-weight: bold;
        }
    </style>
</head>

<body class="bg-gray-200">

    <!-- Header Section -->
    <header class="bg-gray-900 text-white sticky top-0 z-50">
        <!-- Top Nav -->
        <div class="container mx-auto px-4 py-2 flex justify-between items-center">
            <a href="#" class="text-3xl font-bold" onclick="showPage('home')">Apna<span
                    class="text-orange-400">Store</span></a>
            <div class="hidden md:flex flex-grow max-w-2xl mx-4">
                <input type="text" placeholder="Search ApnaStore..."
                    class="w-full px-4 py-2 rounded-l-md text-gray-800 focus:outline-none">
                <button class="bg-orange-400 hover:bg-orange-500 text-white px-5 rounded-r-md"><i
                        class="fa fa-search"></i></button>
            </div>
            <div class="flex items-center space-x-4">
                <div class="relative dropdown"><button class="flex items-center space-x-1 hover:text-orange-400"><i
                            class="fa fa-globe text-xl"></i><span class="hidden lg:inline">EN</span><i
                            class="fa fa-caret-down text-xs"></i></button>
                    <ul
                        class="dropdown-menu absolute hidden bg-white text-gray-800 rounded-md shadow-lg mt-2 py-1 w-32 right-0">
                        <li><a href="#" class="block px-4 py-2 text-sm hover:bg-gray-100">English</a></li>
                        <li><a href="#" class="block px-4 py-2 text-sm hover:bg-gray-100">اردو</a></li>
                    </ul>
                </div>
                <button id="signInBtn" class="hover:text-orange-400">
                    <div class="text-xs">Hello, sign in</div>
                    <div class="font-bold flex items-center">Account & Lists <i
                            class="fa fa-caret-down text-xs ml-1"></i></div>
                </button>
                <a href="#" class="hidden sm:block hover:text-orange-400">
                    <div class="text-xs">Returns</div>
                    <div class="font-bold">& Orders</div>
                </a>
                <a href="#" class="relative flex items-end hover:text-orange-400"><i
                        class="fa fa-shopping-cart text-3xl"></i><span
                        class="absolute -top-1 -right-2 bg-orange-400 text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">3</span><span
                        class="hidden lg:inline font-bold ml-2">Cart</span></a>
                <button id="mobile-menu-button" class="md:hidden text-white focus:outline-none ml-2"><i
                        class="fa fa-bars text-xl"></i></button>
            </div>
        </div>
        <!-- Bottom Nav -->
        <nav class="bg-gray-800 text-white">
            <div class="container mx-auto px-4 flex items-center space-x-6 py-2">
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('home')">Home</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('shop')">Today's Deals</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('contact')">Customer
                    Service</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('messages')">Messages</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('giftcards')">Gift Cards</a>
                <a href="#" class="font-semibold hover:text-orange-400" onclick="showPage('sell')">Sell</a>
            </div>
        </nav>
        <div id="mobile-menu" class="hidden md:hidden bg-gray-800 px-4 pb-3"></div>
    </header>

    <main>
        <!-- Home Page -->
        <div id="home" class="page active">
            <!-- Image Slider -->
            <div class="slider-container">
                <div class="slide">
                    <img src="https://placehold.co/1600x600/334155/FFFFFF?text=Latest+in+Electronics" alt="Electronics">
                    <div class="slide-content">
                        <h2>Discover Cutting-Edge Gadgets</h2>
                        <p>Shop the newest phones, laptops, and accessories.</p>
                    </div>
                </div>
                <div class="slide">
                    <img src="https://placehold.co/1600x600/7c2d12/FFFFFF?text=Shop+Fashion+Trends" alt="Fashion">
                    <div class="slide-content">
                        <h2>Upgrade Your Wardrobe</h2>
                        <p>Find the latest trends in clothing for all seasons.</p>
                    </div>
                </div>
                <div class="slide">
                    <img src="https://placehold.co/1600x600/166534/FFFFFF?text=Beautify+Your+Home" alt="Home Decor">
                    <div class="slide-content">
                        <h2>Transform Your Living Space</h2>
                        <p>Explore stylish furniture and home decor.</p>
                    </div>
                </div>
                <a class="prev">&#10094;</a>
                <a class="next">&#10095;</a>
            </div>
            <div class="dots-container"></div>

            <!-- Product Grid -->
            <div class="container mx-auto px-6 py-12">
                <h2 class="text-3xl font-bold text-center text-gray-800 mb-10">Top Picks for You</h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                    <!-- Product 1: Kitchen Knife -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="kitchenknife.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">6 Inch Kitchen Knife</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 7,899</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 2: Wooden Cutting Board -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="wood-cutting-board.avif" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Wooden Cutting Board</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 4,499</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 3: Non-Stick Frying Pan -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="pan.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Non-Stick Frying Pan</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 9,120</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Product 4: Measuring Spoon Set -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card">
                        <img src="spoonset.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Measuring Spoon Set</h3>
                            <p class="text-orange-500 font-bold text-xl">PKR 2,750</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Today's Deals Page -->
        <div id="shop" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Today's Deals</h1>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
                    <!-- Deal 1 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">30% OFF</span>
                        <img src="airbuds.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Wireless Earbuds Pro</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 4,999</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 7,142</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 2,143</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 2 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">50% OFF</span>
                        <img src="watch.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Smart Watch Series 5</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 8,999</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 17,999</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 9,000</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 3 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">25% OFF</span>
                        <img src="blender.webp" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">3-in-1 Blender</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 5,625</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 7,500</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 1,875</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>

                    <!-- Deal 4 -->
                    <div class="bg-white rounded-lg shadow-lg overflow-hidden product-card relative">
                        <span class="deal-badge">40% OFF</span>
                        <img src="bag.jpg" class="w-full h-56 object-cover">
                        <div class="p-6 card-content">
                            <h3 class="text-lg font-semibold text-gray-800 mb-2">Premium Travel Backpack</h3>
                            <div class="flex items-center">
                                <p class="text-orange-500 font-bold text-xl">PKR 3,600</p>
                                <p class="text-gray-500 line-through ml-2 text-sm">PKR 6,000</p>
                            </div>
                            <p class="text-green-600 text-sm mt-1">Save PKR 2,400</p>
                            <div class="card-footer">
                                <button
                                    class="w-full mt-4 bg-gray-800 text-white py-2 rounded-lg hover:bg-orange-500">Add
                                    to Cart</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Categories Page -->
        <div id="categories" class="page">
            <div class="container mx-auto px-6 py-12">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Categories</h1>
                <p class="text-center">Categories page content goes here.</p>
            </div>
        </div>

        <!-- About Page -->
        <div id="about" class="page">
            <div class="container mx-auto px-6 py-16">
                <h1 class="text-4xl font-bold text-gray-800 mb-6 text-center">About Us</h1>
                <div class="bg-white p-8 rounded-lg shadow-lg max-w-4xl mx-auto">
                    <p class="text-lg text-gray-700 leading-relaxed">'ApnaStore' was launched in 2024 with the mission
                        to provide high-quality products at affordable prices to customers across Pakistan. We leverage
                        technology and superior customer service to make your online shopping experience easy and
                        enjoyable.</p>
                </div>
            </div>
        </div>

        <!-- Contact Page -->
        <div id="contact" class="page">
            <div class="container mx-auto px-6 py-16">
                <h1 class="text-4xl font-bold text-gray-800 mb-8 text-center">Customer Service</h1>
                <div class="max-w-2xl mx-auto bg-white p-8 rounded-lg shadow-lg">
                    <form>
                        <div class="mb-4"><label for="name"
                                class="block text-gray-700 font-semibold mb-2">Name</label><input type="text" id="name"
                                class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500">
                        </div>
                        <div class="mb-4"><label for="email"
                                class="block text-gray-700 font-semibold mb-2">Email</label><input type="email"
                                id="email"
                                class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500">
                        </div>
                        <div class="mb-4"><label for="message"
                                class="block text-gray-700 font-semibold mb-2">Message</label><textar
