```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Science & Spirituality Commentary</title>
    <style>
        /* ==========================================
           PREMIUM ACADEMIC DARK MODE STYLES
           ========================================== */
        :root {
            --bg-color: #0d0d0d;
            --bg-card: #161614;
            --bg-card-hover: #1c1c1a;
            --text-main: #e0e0d8;
            --text-muted: #8a8a82;
            --text-cream: #f0e6d2;
            --accent: #d4af37; /* Muted gold */
            --accent-dim: #8a7028;
            --border: #2a2a28;
            --border-light: #3a3a38;
            --font-serif: 'Georgia', 'Times New Roman', serif;
            --font-sans: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            font-family: var(--font-sans);
            line-height: 1.7;
            font-size: 17px;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* --- EDITABLE SECTIONS (Hidden from view) --- */
        #article-source, #cards-source {
            display: none;
        }

        /* --- LAYOUT --- */
        .container {
            max-width: 720px;
            margin: 0 auto;
            padding: 40px 20px 80px;
        }

        header {
            text-align: center;
            margin-bottom: 60px;
            padding-bottom: 30px;
            border-bottom: 1px solid var(--border);
        }

        header h1 {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            color: var(--text-cream);
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        header p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-top: 5px;
            font-style: italic;
        }

        /* --- ARTICLE STYLING --- */
        article {
            font-family: var(--font-serif);
        }

        article h2 {
            font-size: 2rem;
            color: var(--text-cream);
            line-height: 1.3;
            margin-bottom: 20px;
        }

        .meta {
            font-family: var(--font-sans);
            color: var(--text-muted);
            font-size: 0.85rem;
            margin-bottom: 40px;
            display: block;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            border-left: 2px solid var(--accent);
            padding-left: 10px;
        }

        article p {
            margin-bottom: 30px;
        }

        article p:first-of-type::first-letter {
            float: left;
            font-size: 3.5rem;
            line-height: 0.8;
            padding-right: 10px;
            padding-top: 5px;
            color: var(--accent);
            font-weight: bold;
        }

        /* --- INLINE CITATION LINKS --- */
        .inline-card {
            color: var(--accent);
            text-decoration: none;
            border-bottom: 1px dotted var(--accent-dim);
            cursor: pointer;
            transition: all 0.2s ease;
            font-weight: bold;
        }

        .inline-card:hover {
            color: var(--text-cream);
            background: rgba(212, 175, 55, 0.1);
            border-bottom: 1px solid var(--accent);
        }

        /* --- OVERLAY CARD DRAWER --- */
        #card-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(8px);
            z-index: 1000;
            display: none;
            justify-content: center;
            align-items: flex-end;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        #card-overlay.active {
            display: flex;
            opacity: 1;
        }

        .profile-card {
            background: var(--bg-card);
            width: 100%;
            max-width: 500px;
            border-top: 1px solid var(--accent);
            border-left: 1px solid var(--border-light);
            border-right: 1px solid var(--border-light);
            border-radius: 4px 4px 0 0;
            transform: translateY(100%);
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            max-height: 85vh;
            overflow-y: auto;
        }

        #card-overlay.active .profile-card {
            transform: translateY(0);
        }

        @media (min-width: 768px) {
            #card-overlay {
                align-items: center;
            }
            .profile-card {
                border-radius: 4px;
                border: 1px solid var(--border-light);
                transform: scale(0.9);
                opacity: 0;
            }
            #card-overlay.active .profile-card {
                transform: scale(1);
                opacity: 1;
            }
        }

        .card-close {
            position: absolute;
            top: 15px;
            right: 15px;
            background: rgba(0,0,0,0.5);
            border: 1px solid var(--border-light);
            color: var(--text-main);
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 1.2rem;
            z-index: 10;
            transition: all 0.2s;
        }

        .card-close:hover {
            background: var(--accent);
            color: #000;
            border-color: var(--accent);
        }

        .card-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-bottom: 1px solid var(--border);
            background: #000;
        }

        .card-content {
            padding: 30px;
        }

        .card-date {
            font-family: var(--font-sans);
            color: var(--accent);
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
            display: block;
        }

        .card-title {
            font-family: var(--font-serif);
            font-size: 1.8rem;
            color: var(--text-cream);
            margin-bottom: 20px;
            line-height: 1.2;
        }

        .card-summary {
            font-family: var(--font-serif);
            color: var(--text-main);
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 30px;
            border-left: 2px solid var(--border-light);
            padding-left: 15px;
        }

        .card-btn {
            display: block;
            width: 100%;
            padding: 15px;
            background: transparent;
            color: var(--accent);
            border: 1px solid var(--accent);
            text-align: center;
            text-decoration: none;
            font-family: var(--font-sans);
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.85rem;
            font-weight: bold;
            transition: all 0.2s;
            border-radius: 2px;
        }

        .card-btn:hover {
            background: var(--accent);
            color: #000;
        }

        /* --- COMMENT & REVIEW SECTION --- */
        #comments-section {
            margin-top: 80px;
            padding-top: 40px;
            border-top: 1px solid var(--border);
        }

        .section-header {
            font-family: var(--font-serif);
            font-size: 1.5rem;
            color: var(--text-cream);
            margin-bottom: 30px;
        }

        .rating-widget {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 30px;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 4px;
            margin-bottom: 40px;
        }

        .rating-widget p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 15px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .stars {
            display: flex;
            gap: 10px;
        }

        .star {
            font-size: 2rem;
            color: var(--border-light);
            cursor: pointer;
            transition: color 0.2s;
        }

        .star.active {
            color: var(--accent);
        }

        .comment-form {
            margin-bottom: 40px;
        }

        .comment-form textarea {
            width: 100%;
            background: var(--bg-card);
            border: 1px solid var(--border);
            color: var(--text-main);
            padding: 15px;
            border-radius: 4px;
            font-family: var(--font-sans);
            font-size: 1rem;
            min-height: 100px;
            resize: vertical;
            margin-bottom: 10px;
        }

        .comment-form textarea:focus {
            outline: none;
            border-color: var(--accent-dim);
        }

        .btn-submit {
            background: var(--accent);
            color: #000;
            border: none;
            padding: 12px 25px;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-size: 0.85rem;
            cursor: pointer;
            border-radius: 2px;
            transition: background 0.2s;
        }

        .btn-submit:hover {
            background: var(--text-cream);
        }

        .comment-thread {
            list-style: none;
        }

        .comment {
            border-left: 2px solid var(--border);
            padding-left: 20px;
            margin-bottom: 25px;
            position: relative;
        }

        .comment.reply {
            margin-left: 30px;
            margin-top: 20px;
            border-left-color: var(--border-light);
        }

        .comment-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .comment-author {
            font-weight: bold;
            color: var(--text-cream);
            font-size: 0.95rem;
        }

        .comment-date {
            color: var(--text-muted);
            font-size: 0.8rem;
        }

        .comment-body {
            color: var(--text-main);
            font-size: 0.95rem;
            margin-bottom: 10px;
        }

        .btn-reply {
            background: none;
            border: none;
            color: var(--text-muted);
            font-size: 0.8rem;
            cursor: pointer;
            text-decoration: underline;
            padding: 0;
        }

        .btn-reply:hover {
            color: var(--accent);
        }

        .reply-form {
            margin-top: 15px;
            display: none;
        }

        .reply-form.active {
            display: block;
        }

        .reply-form textarea {
            width: 100%;
            background: var(--bg-color);
            border: 1px solid var(--border);
            color: var(--text-main);
            padding: 10px;
            border-radius: 2px;
            font-family: var(--font-sans);
            font-size: 0.9rem;
            min-height: 60px;
            margin-bottom: 5px;
        }

        /* --- EXTERNAL SCRIPT PLACEHOLDER --- */
        #giscus-container {
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px dashed var(--border);
        }
    </style>
</head>
<body>

<!-- ==================================================================
     EDITABLE AREA 1: ARTICLE CONTENT
     (Edit the text below directly. It will update on your site.)
     To create a popup card link, use this format:
     <a class="inline-card" data-key="UNIQUE_KEY">Clickable Text</a>
     ================================================================== -->
<div id="article-source">
    <span class="meta">Thread 7 · Research Commentary</span>
    <h2>The Limits of Indexing: Monastic Preservation in the Digital Age</h2>

    <p>In the modern quest to bridge empirical science and esoteric spirituality, we frequently rely on AI-driven academic search engines to validate historical claims. Yet, as demonstrated in recent searches for the historical writings of Saint Germaine, these engines hit a hard epistemological boundary. Consensus AI, while powerful, primarily indexes peer-reviewed academic journals. It does not encompass the vast wealth of historical, esoteric, or religious texts that exist outside modern institutional databases.</p>

    <p>This limitation forces us to ask: how has spiritual and historical knowledge survived outside the modern academic matrix? The answer lies in the desert and the monastery. Consider the legacy of <a class="inline-card" data-key="anthony">Saint Anthony the Great</a>, a figure whose ascetic life in the Egyptian desert became the foundational blueprint for Christian monasticism. The sayings attributed to him—such as "I saw all the snares of the enemy spread over the earth... Humility"—were not published in journals, but passed down orally and preserved in manuscript form by early communities.</p>

    <p>These communities did more than pray; they were the intellectual bedrock of their eras. Monks preserved manuscripts, cultivated land, and helped shape the intellectual development of entire societies. Figures such as <a class="inline-card" data-key="benedict">Benedict of Nursia</a>, the mystic <a class="inline-card" data-key="hildegard">Hildegard of Bingen</a>, and modern contemplatives like <a class="inline-card" data-key="merton">Thomas Merton</a> continued this legacy. They prove that the pursuit of divine mystery and the preservation of earthly knowledge are inextricably linked, transcending any single search engine's index.</p>
</div>

<!-- ==================================================================
     EDITABLE AREA 2: POPUP CARD DATA
     (Create or edit cards here. Ensure the 'data-key' matches the link above.)
     ================================================================== -->
<div id="cards-source">
    <!-- CARD 1 -->
    <div class="card-data" data-key="anthony">
        <div class="card-title">Saint Anthony the Great</div>
        <div class="card-date">c. 251 – 356 AD</div>
        <div class="card-image">https://images.unsplash.com/photo-1585338447937-7082f8fc763d?q=80&w=1000&auto=format&fit=crop</div>
        <div class="card-summary">Saint Anthony was a Christian monk from Egypt, revered as the founder of Christian monasticism. His ascetic life in the desert served as a foundational model for subsequent monastic traditions. The Sayings of the Desert Fathers attributes numerous teachings to him, emphasizing humility and spiritual resilience.</div>
        <div class="card-link">https://en.wikipedia.org/wiki/Anthony_the_Great</div>
    </div>

    <!-- CARD 2 -->
    <div class="card-data" data-key="benedict">
        <div class="card-title">Benedict of Nursia</div>
        <div class="card-date">c. 480 – 547 AD</div>
        <div class="card-image">https://images.unsplash.com/photo-1532104173441-d3d1d2e6c0fc?q=80&w=1000&auto=format&fit=crop</div>
        <div class="card-summary">Benedict was a monastic reformer whose "Rule of Saint Benedict" became the foundational guide for Western monasticism. He established the monastery of Monte Cassino, creating a structured community life based on prayer and manual labor. His influence standardized monastic practice across medieval Europe.</div>
        <div class="card-link">https://en.wikipedia.org/wiki/Benedict_of_Nursia</div>
    </div>

    <!-- CARD 3 -->
    <div class="card-data" data-key="hildegard">
        <div class="card-title">Hildegard of Bingen</div>
        <div class="card-date">1098 – 1179 AD</div>
        <div class="card-image">https://images.unsplash.com/photo-1465778893808-5b8a05b6f7b5?q=80&w=1000&auto=format&fit=crop</div>
        <div class="card-summary">Hildegard was a German Benedictine abbess, mystic, and polymath renowned for her theological, musical, and scientific writings. She produced major visionary works, composed liturgical songs, and wrote extensively on natural history and medicine. Her legacy bridges the gap between medieval spirituality and early scientific observation.</div>
        <div class="card-link">https://en.wikipedia.org/wiki/Hildegard_of_Bingen</div>
    </div>

    <!-- CARD 4 -->
    <div class="card-data" data-key="merton">
        <div class="card-title">Thomas Merton</div>
        <div class="card-date">1915 – 1968 AD</div>
        <div class="card-image">https://images.unsplash.com/photo-1518107554-eb1c1c4d8b0a?q=80&w=1000&auto=format&fit=crop</div>
        <div class="card-summary">Thomas Merton was a Trappist monk, theologian, and prolific writer who popularized contemplative spirituality in the modern era. His autobiography, "The Seven Storey Mountain," remains a classic of religious literature. In his later life, he became a prominent advocate for social justice and interfaith dialogue.</div>
        <div class="card-link">https://en.wikipedia.org/wiki/Thomas_Merton</div>
    </div>
</div>


<!-- ======================== RENDERED WEBSITE BELOW ======================== -->

<header>
    <h1>Science & Spirituality</h1>
    <p>A Premium Research Commentary</p>
</header>

<div class="container">
    <main id="article-render"></main>

    <section id="comments-section">
        <h3 class="section-header">Review & Community Discussion</h3>
        
        <div class="rating-widget">
            <p>Rate this research piece</p>
            <div class="stars">
                <span class="star" data-value="1">★</span>
                <span class="star" data-value="2">★</span>
                <span class="star" data-value="3">★</span>
                <span class="star" data-value="4">★</span>
                <span class="star" data-value="5">★</span>
            </div>
        </div>

        <div class="comment-form">
            <textarea placeholder="Share your thoughts or insights on this thread..."></textarea>
            <button class="btn-submit" onclick="postComment()">Post Comment</button>
        </div>

        <ul class="comment-thread" id="commentThread">
            <!-- Mock Existing Comment -->
            <li class="comment">
                <div class="comment-header">
                    <span class="comment-author">Dr. Aris Thorne</span>
                    <span class="comment-date">2 days ago</span>
                </div>
                <div class="comment-body">
                    Fascinating breakdown of the Consensus AI limits. It reminds me that much of human knowledge is still analog and deeply personal. The connection to Desert Fathers is a brilliant pivot.
                </div>
                <button class="btn-reply" onclick="toggleReply(this)">Reply</button>
                <div class="reply-form">
                    <textarea placeholder="Write a reply..."></textarea>
                    <button class="btn-submit" style="font-size: 0.75rem; padding: 8px 15px;" onclick="postReply(this)">Submit Reply</button>
                </div>
                
                <!-- Nested Reply -->
                <ul class="comment-thread" style="margin-top: 20px;">
                    <li class="comment reply">
                        <div class="comment-header">
                            <span class="comment-author">Elena R.</span>
                            <span class="comment-date">1 day ago</span>
                        </div>
                        <div class="comment-body">
                            Agreed. I'd love to see a follow-up thread on how manuscript preservation actually worked mechanically in those monasteries.
                        </div>
                        <button class="btn-reply" onclick="toggleReply(this)">Reply</button>
                        <div class="reply-form">
                            <textarea placeholder="Write a reply..."></textarea>
                            <button class="btn-submit" style="font-size: 0.75rem; padding: 8px 15px;" onclick="postReply(this)">Submit Reply</button>
                        </div>
                    </li>
                </ul>
            </li>
        </ul>

        <!-- ==================================================================
             GISCUS / DISQUS PLACEHOLDER
             Paste your Giscus or Disqus embed code directly inside this div 
             to activate a live, persistent database comment system.
             ================================================================== -->
        <div id="giscus-container">
            <!-- <script src="https://giscus.app/client.js"
                    data-repo="YOUR_REPO/YOUR_REPO"
                    data-repo-id="YOUR_REPO_ID"
                    data-category="Announcements"
                    data-category-id="YOUR_CATEGORY_ID"
                    data-mapping="pathname"
                    data-strict="0"
                    data-reactions-enabled="1"
                    data-emit-metadata="0"
                    data-input-position="bottom"
                    data-theme="dark_dimmed"
                    data-lang="en"
                    crossorigin="anonymous"
                    async>
            </script> -->
        </div>

    </section>
</div>

<!-- POPUP OVERLAY CARD STRUCTURE -->
<div id="card-overlay">
    <div class="profile-card">
        <div class="card-close" onclick="closeCard()">✕</div>
        <img id="overlay-image" class="card-image" src="" alt="Profile Image">
        <div class="card-content">
            <span class="card-date" id="overlay-date"></span>
            <h2 class="card-title" id="overlay-title"></h2>
            <p class="card-summary" id="overlay-summary"></p>
            <a href="#" id="overlay-btn" class="card-btn" target="_blank">Read Full Source</a>
        </div>
    </div>
</div>

<script>
    // ==========================================
    // CORE LOGIC: INJECTING CONTENT
    // ==========================================
    document.addEventListener('DOMContentLoaded', () => {
        // Inject article text from the hidden source div
        document.getElementById('article-render').innerHTML = document.getElementById('article-source').innerHTML;

        // Attach click listeners to all inline cards
        document.querySelectorAll('.inline-card').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                openCard(link.getAttribute('data-key'));
            });
        });
    });

    // ==========================================
    // OVERLAY CARD MECHANICS
    // ==========================================
    function openCard(key) {
        // Find the corresponding card data in the hidden source
        const dataElement = document.querySelector(`#cards-source .card-data[data-key="${key}"]`);
        if (!dataElement) return;

        // Extract text content from the plain text divs
        const title = dataElement.querySelector('.card-title').textContent;
        const date = dataElement.querySelector('.card-date').textContent;
        const image = dataElement.querySelector('.card-image').textContent.trim();
        const summary = dataElement.querySelector('.card-summary').textContent;
        const link = dataElement.querySelector('.card-link').textContent.trim();

        // Populate the visible overlay
        document.getElementById('overlay-title').innerText = title;
        document.getElementById('overlay-date').innerText = date;
        document.getElementById('overlay-summary').innerText = summary;
        document.getElementById('overlay-btn').href = link;
        document.getElementById('overlay-image').src = image;

        // Show overlay
        document.getElementById('card-overlay').classList.add('active');
        document.body.style.overflow = 'hidden';
    }

    function closeCard() {
        document.getElementById('card-overlay').classList.remove('active');
        document.body.style.overflow = 'auto';
    }

    // Close if clicking outside the card
    document.getElementById('card-overlay').addEventListener('click', function(e) {
        if (e.target === this) {
            closeCard();
        }
    });

    // ==========================================
    // STAR RATING MECHANICS
    // ==========================================
    const stars = document.querySelectorAll('.star');
    stars.forEach((star, index) => {
        star.addEventListener('click', () => {
            stars.forEach((s, i) => {
                if (i <= index) s.classList.add('active');
                else s.classList.remove('active');
            });
        });
    });

    // ==========================================
    // MOCK COMMENT MECHANICS (Frontend Only)
    // ==========================================
    function toggleReply(button) {
        const form = button.nextElementSibling;
        form.classList.toggle('active');
    }

    function postComment() {
        const textarea = document.querySelector('.comment-form > textarea');
        const text = textarea.value.trim();
        if (text) {
            const thread = document.getElementById('commentThread');
            const newComment = document.createElement('li');
            newComment.className = 'comment';
            newComment.innerHTML = `
                <div class="comment-header">
                    <span class="comment-author">You (Guest)</span>
                    <span class="comment-date">Just now</span>
                </div>
                <div class="comment-body">${text}</div>
                <button class="btn-reply" onclick="toggleReply(this)">Reply</button>
                <div class="reply-form">
                    <textarea placeholder="Write a reply..."></textarea>
                    <button class="btn-submit" style="font-size: 0.75rem; padding: 8px 15px;" onclick="postReply(this)">Submit Reply</button>
                </div>
            `;
            thread.prepend(newComment);
            textarea.value = '';
        }
    }

    function postReply(button) {
        const form = button.parentElement;
        const textarea = form.querySelector('textarea');
        const text = textarea.value.trim();
        if (text) {
            const parentComment = form.parentElement;
            let replyThread = parentComment.querySelector('.comment-thread');
            
            // Create a nested thread if it doesn't exist
            if (!replyThread) {
                replyThread = document.createElement('ul');
                replyThread.className = 'comment-thread';
                replyThread.style.marginTop = '20px';
                parentComment.appendChild(replyThread);
            }

            const newReply = document.createElement('li');
            newReply.className = 'comment reply';
            newReply.innerHTML = `
                <div class="comment-header">
                    <span class="comment-author">You (Guest)</span>
                    <span class="comment-date">Just now</span>
                </div>
                <div class="comment-body">${text}</div>
                <button class="btn-reply" onclick="toggleReply(this)">Reply</button>
                <div class="reply-form">
                    <textarea placeholder="Write a reply..."></textarea>
                    <button class="btn-submit" style="font-size: 0.75rem; padding: 8px 15px;" onclick="postReply(this)">Submit Reply</button>
                </div>
            `;
            replyThread.appendChild(newReply);
            textarea.value = '';
            form.classList.remove('active');
        }
    }
</script>

</body>
</html>
```