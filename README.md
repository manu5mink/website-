<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daily News Hub</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            line-height: 1.6;
            color: #333;
            background-color: #f8f9fa;
        }

        header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 2.5rem;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .date {
            font-size: 1rem;
            opacity: 0.9;
        }

        nav {
            background-color: #fff;
            padding: 1rem 0;
            border-bottom: 3px solid #e9ecef;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            flex-wrap: wrap;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 600;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            transition: all 0.3s ease;
        }

        .nav-links a:hover, .nav-links a.active {
            background-color: #2a5298;
            color: white;
            transform: translateY(-2px);
        }

        main {
            padding: 2rem 0;
        }

        .news-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .featured-article {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }

        .featured-article:hover {
            transform: translateY(-5px);
        }

        .article-image {
            width: 100%;
            height: 300px;
            background: linear-gradient(45deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
            font-weight: bold;
        }

        .article-content {
            padding: 1.5rem;
        }

        .article-title {
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #2c3e50;
        }

        .article-meta {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .article-excerpt {
            color: #555;
            line-height: 1.7;
        }

        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .sidebar-section {
            background: white;
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 2px 15px rgba(0,0,0,0.08);
        }

        .sidebar-title {
            font-size: 1.3rem;
            font-weight: bold;
            margin-bottom: 1rem;
            color: #2c3e50;
            border-bottom: 2px solid #2a5298;
            padding-bottom: 0.5rem;
        }

        .trending-item {
            padding: 0.8rem 0;
            border-bottom: 1px solid #eee;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .trending-item:hover {
            background-color: #f8f9fa;
            border-radius: 6px;
            padding-left: 0.5rem;
        }

        .trending-item:last-child {
            border-bottom: none;
        }

        .trending-title {
            font-weight: 600;
            color: #333;
            margin-bottom: 0.3rem;
        }

        .trending-time {
            font-size: 0.8rem;
            color: #666;
        }

        .articles-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .news-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 3px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .news-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 25px rgba(0,0,0,0.15);
        }

        .card-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(45deg, #f093fb 0%, #f5576c 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .card-content {
            padding: 1.2rem;
        }

        .card-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #2c3e50;
        }

        .card-excerpt {
            color: #666;
            font-size: 0.9rem;
            line-height: 1.6;
        }

        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }

        @media (max-width: 768px) {
            .news-grid {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                text-align: center;
                gap: 1rem;
            }
            
            .logo {
                font-size: 2rem;
            }
            
            .nav-links {
                justify-content: center;
                gap: 1rem;
            }
            
            .articles-section {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <h1 class="logo">Daily News Hub</h1>
                <div class="date" id="current-date"></div>
            </div>
        </div>
    </header>

    <nav>
        <div class="container">
            <ul class="nav-links">
                <li><a href="#" class="active">Home</a></li>
                <li><a href="#">World</a></li>
                <li><a href="#">Politics</a></li>
                <li><a href="#">Technology</a></li>
                <li><a href="#">Sports</a></li>
                <li><a href="#">Business</a></li>
                <li><a href="#">Health</a></li>
            </ul>
        </div>
    </nav>

    <main>
        <div class="container">
            <div class="news-grid">
                <article class="featured-article">
                    <div class="article-image">Featured News Image</div>
                    <div class="article-content">
                        <h2 class="article-title">Breaking: Major Development in Global Climate Summit</h2>
                        <div class="article-meta">By Sarah Johnson | 2 hours ago | World News</div>
                        <p class="article-excerpt">
                            World leaders gather to discuss unprecedented climate action plans as new scientific data reveals urgent need for immediate intervention. The summit promises to deliver concrete solutions and binding commitments from participating nations, marking a potential turning point in global environmental policy.
                        </p>
                    </div>
                </article>

                <aside class="sidebar">
                    <div class="sidebar-section">
                        <h3 class="sidebar-title">Trending Now</h3>
                        <div class="trending-item">
                            <div class="trending-title">Tech Giants Announce AI Partnership</div>
                            <div class="trending-time">1 hour ago</div>
                        </div>
                        <div class="trending-item">
                            <div class="trending-title">Stock Market Reaches New Heights</div>
                            <div class="trending-time">3 hours ago</div>
                        </div>
                        <div class="trending-item">
                            <div class="trending-title">Olympic Games Preparation Update</div>
                            <div class="trending-time">5 hours ago</div>
                        </div>
                        <div class="trending-item">
                            <div class="trending-title">Healthcare Innovation Breakthrough</div>
                            <div class="trending-time">7 hours ago</div>
                        </div>
                    </div>

                    <div class="sidebar-section">
                        <h3 class="sidebar-title">Weather</h3>
                        <p>Today: Partly cloudy, 22°C</p>
                        <p>Tomorrow: Sunny, 25°C</p>
                        <p>Weekend: Light rain expected</p>
                    </div>
                </aside>
            </div>

            <section class="articles-section">
                <article class="news-card">
                    <div class="card-image">Technology News</div>
                    <div class="card-content">
                        <h3 class="card-title">Revolutionary Smartphone Technology Unveiled</h3>
                        <p class="card-excerpt">Leading tech company reveals groundbreaking battery technology that could extend phone life to a full week on single charge.</p>
                    </div>
                </article>

                <article class="news-card">
                    <div class="card-image">Sports Update</div>
                    <div class="card-content">
                        <h3 class="card-title">Championship Finals Set for This Weekend</h3>
                        <p class="card-excerpt">Two powerhouse teams prepare for the ultimate showdown in what promises to be the most exciting match of the season.</p>
                    </div>
                </article>

                <article class="news-card">
                    <div class="card-image">Business News</div>
                    <div class="card-content">
                        <h3 class="card-title">Global Markets Show Strong Recovery</h3>
                        <p class="card-excerpt">Economic indicators suggest sustained growth as international trade relations improve and consumer confidence rises.</p>
                    </div>
                </article>

                <article class="news-card">
                    <div class="card-image">Health & Science</div>
                    <div class="card-content">
                        <h3 class="card-title">New Medical Research Shows Promise</h3>
                        <p class="card-excerpt">Scientists report significant progress in treatment development, offering hope for millions of patients worldwide.</p>
                    </div>
                </article>

                <article class="news-card">
                    <div class="card-image">Local News</div>
                    <div class="card-content">
                        <h3 class="card-title">City Announces Infrastructure Improvements</h3>
                        <p class="card-excerpt">Major urban development project set to begin next month, promising better transportation and public services.</p>
                    </div>
                </article>

                <article class="news-card">
                    <div class="card-image">Entertainment</div>
                    <div class="card-content">
                        <h3 class="card-title">Film Festival Announces Award Winners</h3>
                        <p class="card-excerpt">Independent filmmakers take center stage at prestigious international festival, celebrating diverse storytelling.</p>
                    </div>
                </article>
            </section>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2025 Daily News Hub. All rights reserved. | Contact: news@dailynewshub.com</p>
        </div>
    </footer>

    <script>
        // Set current date
        function setCurrentDate() {
            const now = new Date();
            const options = { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            };
            document.getElementById('current-date').textContent = now.toLocaleDateString('en-US', options);
        }

        // Navigation functionality
        function initNavigation() {
            const navLinks = document.querySelectorAll('.nav-links a');
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    navLinks.forEach(l => l.classList.remove('active'));
                    this.classList.add('active');
                });
            });
        }

        // Trending items click functionality
        function initTrendingItems() {
            const trendingItems = document.querySelectorAll('.trending-item');
            trendingItems.forEach(item => {
                item.addEventListener('click', function() {
                    alert('This would navigate to: ' + this.querySelector('.trending-title').textContent);
                });
            });
        }

        // News cards click functionality
        function initNewsCards() {
            const newsCards = document.querySelectorAll('.news-card, .featured-article');
            newsCards.forEach(card => {
                card.addEventListener('click', function() {
                    const title = this.querySelector('.card-title, .article-title').textContent;
                    alert('This would open article: ' + title);
                });
            });
        }

        // Initialize all functionality
        document.addEventListener('DOMContentLoaded', function() {
            setCurrentDate();
            initNavigation();
            initTrendingItems();
            initNewsCards();
        });

        // Update date every minute
        setInterval(setCurrentDate, 60000);
    </script>
</body>
</html> 
