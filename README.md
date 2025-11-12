<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Nouva — Curated Conscious Fashion</title>
<meta name="description" content="Nouva - stylish and sustainable clothing. Shop by mood, see sustainability scores, track impact." />
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Playfair+Display:wght@500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#fffafc;
    --card:#ffffff;
    --muted:#7b7780;
    --dusty:#c56b8c; /* dusty rose */
    --lav:#b599d6;   /* lavender */
    --gold:#f0d69b;  /* soft gold */
    --accent:#f6f0f4;
    --shadow: 0 18px 50px rgba(2,6,23,0.08);
    --glass: rgba(255,255,255,0.65);
    --radius:14px;
    --maxw:1200px;
  }
  *{box-sizing:border-box}
  html,body{height:100%}
  body{
    margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;
    background:linear-gradient(180deg,#fffafc,#fffdfd);
    color:#0f1724;
    -webkit-font-smoothing:antialiased;-moz-osx-font-smoothing:grayscale;
  }
  .wrap{max-width:var(--maxw);margin:20px auto;padding:0 18px}

  /* HEADER */
  header{display:flex;align-items:center;justify-content:space-between;gap:12px;padding:14px 0}
  .brand{display:flex;align-items:center;gap:12px}
  .logo{width:64px;height:64px;border-radius:14px;background:linear-gradient(135deg,var(--dusty),var(--lav));display:flex;align-items:center;justify-content:center;box-shadow:var(--shadow)}
  .logo svg{width:44px;height:44px;animation:logoFloat 5s ease-in-out infinite}
  @keyframes logoFloat{0%{transform:translateY(0)}50%{transform:translateY(-6px)}100%{transform:translateY(0)}}
  .brand-title{font-family:'Playfair Display',serif;font-size:18px;font-weight:700}
  .brand-sub{font-size:12px;color:var(--muted);margin-top:3px}

  nav{display:flex;align-items:center;gap:10px}
  .mega{position:relative}
  .nav-links{display:flex;gap:8px;align-items:center}
  .nav-links button{background:transparent;border:0;padding:6px 10px;border-radius:8px;font-weight:600;cursor:pointer;color:var(--muted)}
  .nav-links button:hover{background:var(--accent)}

  /* mega panel */
  .mega-panel{position:absolute;left:0;top:58px;background:var(--card);padding:18px;border-radius:12px;box-shadow:var(--shadow);display:none;width:760px;z-index:60}
  .mega-panel.show{display:block}
  .mega-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
  .mega-item{padding:10px;border-radius:10px}

  /* search */
  .search{display:flex;align-items:center;gap:8px;background:var(--card);padding:8px 12px;border-radius:12px;box-shadow:0 8px 20px rgba(2,6,23,0.06);min-width:320px}
  .search input{border:0;outline:0;background:transparent;width:100%}

  /* hero carousel */
  .hero{margin-top:10px;border-radius:18px;padding:18px;display:grid;grid-template-columns:1fr 420px;gap:18px;align-items:center;
    background:radial-gradient(600px 200px at 10% 20%, rgba(197,107,140,0.04), transparent),
               radial-gradient(500px 180px at 90% 80%, rgba(181,153,214,0.03), transparent);
    box-shadow:var(--shadow)}
  .hero-left h1{font-family:'Playfair Display',serif;font-size:34px;margin:0}
  .hero-left p{color:var(--muted);margin-top:8px}
  .hero-slides{position:relative;overflow:hidden;border-radius:12px}
  .slide{min-height:260px;border-radius:12px;display:grid;grid-template-columns:1fr;align-items:center;padding:24px;background-size:cover;background-position:center;transition:transform .6s ease,opacity .6s ease}
  .slide-overlay{background:linear-gradient(180deg, rgba(0,0,0,0.0), rgba(0,0,0,0.12));border-radius:12px;padding:12px}
  .dots{display:flex;gap:8px;margin-top:12px}
  .dot{width:10px;height:10px;border-radius:999px;background:rgba(15,23,42,0.12);cursor:pointer}
  .dot.active{background:linear-gradient(90deg,var(--dusty),var(--lav));box-shadow:0 6px 16px rgba(197,107,140,0.12)}

  /* promo strips */
  .promo-strip{display:flex;gap:12px;align-items:center;padding:10px;border-radius:12px;background:linear-gradient(90deg,#fff7f9,#fffbf7);box-shadow:0 8px 20px rgba(2,6,23,0.04);margin-top:12px}

  /* controls */
  .controls{display:flex;gap:12px;align-items:center;flex-wrap:wrap;margin-top:18px}
  .chip{background:var(--card);padding:8px 12px;border-radius:999px;border:1px solid rgba(2,6,23,0.04);cursor:pointer;font-weight:600;color:var(--muted)}
  .filters{display:flex;gap:8px;align-items:center}

  /* grid */
  .content{display:flex;gap:18px;margin-top:18px}
  .sidebar{width:260px;background:var(--card);border-radius:12px;padding:12px;box-shadow:var(--shadow);height:fit-content}
  .sidebar h4{margin:0 0 8px 0}
  .grid{flex:1;display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
  .card{background:var(--card);border-radius:12px;padding:12px;box-shadow:0 18px 50px rgba(2,6,23,0.06);transition:transform .22s,box-shadow .22s}
  .card:hover{transform:translateY(-8px);box-shadow:0 30px 70px rgba(2,6,23,0.08)}
  .thumb{height:260px;border-radius:10px;overflow:hidden;display:flex;align-items:center;justify-content:center;background:#faf7fb}
  .thumb img{width:100%;height:100%;object-fit:cover}
  .meta{display:flex;justify-content:space-between;align-items:flex-start;margin-top:8px}
  .price{font-weight:800}
  .badge{display:inline-block;padding:6px 8px;border-radius:8px;font-weight:700;font-size:13px}

  .sustain{background:linear-gradient(90deg,#fff3e6,#f7f7ff);color:#7b5b4a;padding:6px 8px;border-radius:8px;font-weight:700}

  /* quick actions */
  .actions{display:flex;gap:8px;margin-top:12px}
  .btn{background:linear-gradient(90deg,var(--dusty),var(--lav));color:#fff;padding:10px 12px;border-radius:10px;border:0;cursor:pointer;font-weight:700;box-shadow:0 8px 30px rgba(197,107,140,0.12)}
  .ghost{background:transparent;border:1px solid rgba(15,23,42,0.06);padding:8px 10px;border-radius:10px;cursor:pointer}

  /* modal */
  .modal{position:fixed;inset:0;background:rgba(2,6,23,0.45);display:flex;align-items:center;justify-content:center;z-index:120}
  .modal-card{background:var(--card);border-radius:12px;padding:18px;width:min(920px,96%);display:flex;gap:18px;box-shadow:var(--shadow)}
  .gallery{width:52%;border-radius:10px;overflow:hidden}
  .gallery img{width:100%;height:420px;object-fit:cover;border-radius:10px}
  .modal-right{flex:1;display:flex;flex-direction:column;gap:10px}

  /* cart sidebar */
  .cart-side{position:fixed;right:18px;top:18px;bottom:18px;width:420px;background:linear-gradient(180deg,#fff,#fffaf8);border-radius:12px;padding:18px;box-shadow:0 40px 90px rgba(2,6,23,0.12);transform:translateX(120%);transition:transform .28s;z-index:110}
  .cart-side.open{transform:translateX(0)}
  .cart-item{display:flex;gap:12px;align-items:center;border-bottom:1px dashed #f6eef0;padding:12px 0}

  /* footer */
  footer{margin-top:28px;padding:24px 0;text-align:center;color:var(--muted)}

  /* responsive */
  @media(max-width:1100px){ .grid{grid-template-columns:repeat(2,1fr)} .hero{grid-template-columns:1fr 340px} .mega-panel{width:640px} }
  @media(max-width:780px){ header{flex-direction:column;align-items:flex-start;gap:12px} .hero{grid-template-columns:1fr} .grid{grid-template-columns:1fr} .sidebar{display:none} .mega-panel{position:static;width:100%;margin-top:8px} }
  @media(max-width:420px){ .search{min-width:160px} .modal-card{flex-direction:column} .gallery img{height:260px} .cart-side{width:92%} }

  /* utilities */
  .muted{color:var(--muted)}
  .small{font-size:13px}
  .row{display:flex;align-items:center;gap:8px}
  .float-cta{position:fixed;right:20px;bottom:20px;background:linear-gradient(90deg,var(--dusty),var(--lav));color:white;padding:12px 14px;border-radius:999px;box-shadow:0 18px 60px rgba(2,6,23,0.12);cursor:pointer;z-index:200}
  .rating{color:#ffb86b;font-weight:700}
  .pill{background:#fff;border-radius:999px;padding:6px 10px;border:1px solid rgba(0,0,0,0.04)}
  .pagination{display:flex;gap:8px;justify-content:center;margin-top:18px}
  .page-btn{padding:8px 10px;border-radius:8px;border:1px solid rgba(2,6,23,0.06);cursor:pointer}
</style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="logo" aria-hidden="true">
          <svg viewBox="0 0 100 100" xmlns="https://ibb.co/gZntMJ5q"><defs><linearGradient id="g" x1="0" x2="1"><stop offset="0" stop-color="#c56b8c"/><stop offset="1" stop-color="#b599d6"/></linearGradient></defs><rect x="8" y="8" width="84" height="84" rx="14" fill="url(#g)" opacity="0.12"/><text x="50" y="62" text-anchor="middle" font-size="42" font-weight="800" fill="url(#g)" style="font-family:Inter, sans-serif;">N</text></svg>
        </div>
        <div>
          <div class="brand-title">Nouva</div>
          <div class="brand-sub">Style · Ethics · Joy</div>
        </div>
      </div>

      <nav>
        <div class="nav-links">
          <div class="mega">
            <button id="shopBtn">Shop ▾</button>
            <div id="mega" class="mega-panel" role="dialog" aria-hidden="true">
              <div class="mega-grid">
                <div class="mega-item"><strong>Collections</strong><ul><li class="small muted">Soft Romance</li><li class="small muted">Urban Edge</li><li class="small muted">Timeless Aura</li></ul></div>
                <div class="mega-item"><strong>Materials</strong><ul><li class="small muted">Linen</li><li class="small muted">Organic Cotton</li><li class="small muted">Recycled</li></ul></div>
                <div class="mega-item"><strong>Explore</strong><ul><li class="small muted">Repair & Rewear</li><li class="small muted">Our Journal</li><li class="small muted">Sustainability</li></ul></div>
              </div>
            </div>
          </div>
          <button id="newBtn">New</button>
          <button id="bestBtn">Best Sellers</button>
          <button id="saleBtn">Sale</button>
        </div>

        <div class="search" role="search">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M21 21l-4.35-4.35" stroke="#9aa0ab" stroke-width="1.8" stroke-linecap="round"/></svg>
          <input id="search" placeholder="Search styles, moods, tags..." />
        </div>

        <div style="display:flex;align-items:center;gap:10px">
          <button class="ghost" id="wishlistBtn">♡ Wishlist</button>
          <div style="position:relative">
            <button class="btn" id="cartBtn">Cart</button>
            <div class="cart-count pill" id="miniCount" style="display:none;position:absolute;top:-10px;right:-10px;background:#ff6b6b;color:#fff;font-size:12px;padding:6px 8px;border-radius:999px"></div>
          </div>
        </div>
      </nav>
    </header>

    <!-- HERO -->
    <section class="hero">
      <div class="hero-left">
        <div class="muted">Consciously curated • beautifully made</div>
        <h1>Style with soul — pieces you'll love forever.</h1>
        <p class="muted">Nouva blends modern aesthetics with ethical craft. Shop by mood, discover impact data, and join a community of mindful style-lovers.</p>
        <div class="hero-cta" style="margin-top:12px">
          <button class="btn" id="shopNow">Shop Collection</button>
          <button class="ghost" onclick="document.getElementById('designerSection').scrollIntoView({behavior:'smooth'})">Design Your Own</button>
        </div>

        <div class="promo-strip" style="margin-top:12px">
          <div style="font-weight:700">Limited: Autumn Edit</div>
          <div class="muted">Handpicked linen pieces • Free repairs for 6 months</div>
          <div style="margin-left:auto"><button class="pill">Explore</button></div>
        </div>

        <div style="margin-top:12px">
          <div style="display:flex;gap:8px;align-items:center">
            <div style="font-weight:800">Trending moods</div>
            <div style="display:flex;gap:6px;margin-left:12px">
              <div class="chip">Soft Romance</div><div class="chip">Urban Edge</div><div class="chip">Timeless Aura</div>
            </div>
          </div>
        </div>
      </div>

      <div>
        <div class="hero-slides" id="heroSlides">
          <div class="slide" data-bg="https://i.pinimg.com/736x/32/aa/79/32aa798ae2c3ed4ee7d502d6af70667d.jpg" style="background-image:url('https://images.unsplash.com/photo-1503341455253-b2e723bb3dbb?auto=format&fit=crop&w=1400&q=80')">
            <div class="slide-overlay">
              <div style="font-weight:800;font-size:18px">Autumn Linen Edit</div>
              <div class="muted">Lightweight, crafted with love</div>
              <div style="margin-top:10px"><button class="btn">Shop Linen</button></div>
            </div>
          </div>
          <div class="slide" data-bg="https://images.unsplash.com/photo-1541099649105-f69ad21f3246?auto=format&fit=crop&w=1400&q=80" style="background-image:url('https://images.unsplash.com/photo-1541099649105-f69ad21f3246?auto=format&fit=crop&w=1400&q=80')">
            <div class="slide-overlay">
              <div style="font-weight:800;font-size:18px">Eco Essentials</div>
              <div class="muted">Organic cotton staples</div>
              <div style="margin-top:10px"><button class="btn">Shop Essentials</button></div>
            </div>
          </div>
          <div class="slide" data-bg="https://images.unsplash.com/photo-1542204165-9f28a0a6f9b9?auto=format&fit=crop&w=1400&q=80" style="background-image:url('https://images.unsplash.com/photo-1542204165-9f28a0a6f9b9?auto=format&fit=crop&w=1400&q=80')">
            <div class="slide-overlay">
              <div style="font-weight:800;font-size:18px">Recycled Knitwear</div>
              <div class="muted">Warm, conscious, cosy</div>
              <div style="margin-top:10px"><button class="btn">Shop Knitwear</button></div>
            </div>
          </div>
        </div>
        <div class="dots" id="dots"></div>
      </div>
    </section>

    <!-- controls -->
    <div class="controls">
      <div class="row">
        <select id="sort" class="pill">
          <option value="popular">Sort: Popular</option>
          <option value="price-asc">Price: Low → High</option>
          <option value="price-desc">Price: High → Low</option>
          <option value="new">Newest</option>
        </select>
      </div>
      <div style="margin-left:auto" class="row muted">
        Showing <strong id="count">0</strong> items
      </div>
    </div>

    <!-- main -->
    <div class="content">
      <aside class="sidebar">
        <h4>Filters</h4>
        <div style="margin-top:8px">
          <div class="small muted">Mood</div>
          <div style="display:flex;gap:8px;margin-top:8px;flex-wrap:wrap">
            <button class="chip filterMood" data-mood="all">All</button>
            <button class="chip filterMood" data-mood="romance">Soft Romance</button>
            <button class="chip filterMood" data-mood="urban">Urban Edge</button>
            <button class="chip filterMood" data-mood="timeless">Timeless Aura</button>
          </div>
        </div>

        <div style="margin-top:12px">
          <div class="small muted">Category</div>
          <div style="display:flex;flex-direction:column;gap:6px;margin-top:8px">
            <label><input type="checkbox" class="cat" value="linen" /> Linen</label>
            <label><input type="checkbox" class="cat" value="denim" /> Denim</label>
            <label><input type="checkbox" class="cat" value="organic" /> Organic</label>
            <label><input type="checkbox" class="cat" value="recycled" /> Recycled</label>
          </div>
        </div>

        <div style="margin-top:12px">
          <div class="small muted">Size</div>
          <div style="display:flex;gap:6px;margin-top:8px;flex-wrap:wrap">
            <button class="chip size" data-size="S">S</button>
            <button class="chip size" data-size="M">M</button>
            <button class="chip size" data-size="L">L</button>
            <button class="chip size" data-size="XL">XL</button>
          </div>
        </div>

        <div style="margin-top:12px">
          <div class="small muted">Color</div>
          <div style="display:flex;gap:6px;margin-top:8px;flex-wrap:wrap">
            <div class="swatch" data-color="#ffffff" style="background:#ffffff;border:1px solid #eee;width:28px;height:28px;border-radius:6px;cursor:pointer"></div>
            <div class="swatch" data-color="#fdeef5" style="background:#fdeef5;width:28px;height:28px;border-radius:6px;cursor:pointer"></div>
            <div class="swatch" data-color="#efe6ff" style="background:#efe6ff;width:28px;height:28px;border-radius:6px;cursor:pointer"></div>
            <div class="swatch" data-color="#f7ecd7" style="background:#f7ecd7;width:28px;height:28px;border-radius:6px;cursor:pointer"></div>
          </div>
        </div>

        <div style="margin-top:16px">
          <button class="btn" id="applyFilters">Apply</button>
          <button class="ghost" id="clearFilters">Clear</button>
        </div>
      </aside>

      <main style="flex:1">
        <div class="grid" id="grid"></div>

        <div class="pagination" id="pagination"></div>
      </main>
    </div>

    <!-- Design your own section -->
    <section id="designerSection" style="margin-top:28px;background:linear-gradient(180deg,#fff,#fffaf8);padding:16px;border-radius:12px;box-shadow:var(--shadow)">
      <h3>Design Your Own</h3>
      <div style="display:flex;gap:12px;align-items:center;flex-wrap:wrap">
        <div style="width:160px;height:160px;border-radius:8px;background:#fff;display:flex;align-items:center;justify-content:center;box-shadow:0 12px 30px rgba(2,6,23,0.06)">
          <div id="designPreview" style="width:140px;height:140px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-weight:800">NEW</div>
        </div>
        <div style="display:flex;flex-direction:column;gap:8px">
          <div style="display:flex;gap:8px">
            <div class="swatch des" data-color="#ffffff" style="width:36px;height:36px;border-radius:8px;border:1px solid #eee"></div>
            <div class="swatch des" data-color="#fdeef5" style="width:36px;height:36px;border-radius:8px"></div>
            <div class="swatch des" data-color="#efe6ff" style="width:36px;height:36px;border-radius:8px"></div>
            <div class="swatch des" data-color="#f7ecd7" style="width:36px;height:36px;border-radius:8px"></div>
          </div>
          <input id="designLabel" placeholder="Label (e.g., Aanya)" style="padding:8px;border-radius:8px;border:1px solid #eee;max-width:320px" />
          <div style="display:flex;gap:8px">
            <button class="btn" id="saveDesign">Save Design</button>
            <button class="ghost" id="viewDesigns">View Designs</button>
          </div>
        </div>
      </div>
    </section>

    <!-- Repair & Journal -->
    <section style="margin-top:22px;display:grid;grid-template-columns:1fr 1fr;gap:18px">
      <div style="background:var(--card);padding:14px;border-radius:12px;box-shadow:var(--shadow)">
        <h3>Repair & Rewear</h3>
        <p class="muted">Extend garment life with repairs and mending support.</p>
        <form id="repairForm" style="display:flex;flex-direction:column;gap:8px;margin-top:8px">
          <input id="r_name" placeholder="Your name" style="padding:8px;border-radius:8px;border:1px solid #eee" />
          <input id="r_item" placeholder="Item / Order ID" style="padding:8px;border-radius:8px;border:1px solid #eee" />
          <textarea id="r_msg" placeholder="Describe issue" rows="3" style="padding:8px;border-radius:8px;border:1px solid #eee"></textarea>
          <div style="display:flex;gap:8px">
            <button class="btn" id="sendRepair">Send Request</button>
            <button class="ghost" id="repairTips">Mending Tips</button>
          </div>
        </form>
      </div>

      <div style="background:var(--card);padding:14px;border-radius:12px;box-shadow:var(--shadow)">
        <h3>Nouva Journal</h3>
        <p class="muted">Short reads on mindful style, makers and craft.</p>
        <article style="margin-top:12px;padding:12px;border-radius:10px;background:linear-gradient(180deg,#fff,#fffaf8);">
          <h4 style="margin:0">Why slow fashion feels better</h4>
          <p class="muted" style="margin-top:8px">Small repairs, thoughtful buying and timeless pieces reduce waste and feel more meaningful.</p>
          <a href="#" class="muted" onclick="alert('Demo: open article')">Read more →</a>
        </article>
      </div>
    </section>

    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px">
        <div class="muted">© <span id="year"></span> Nouva — Wear what feels right</div>
        <div class="muted">Demo prototype • No payments</div>
      </div>
    </footer>
  </div>

  <!-- modals / cart -->
  <div id="modalRoot"></div>

  <aside id="cartSide" class="cart-side" aria-hidden="true">
    <div style="display:flex;justify-content:space-between;align-items:center">
      <div style="font-weight:800">Your Cart</div>
      <button class="ghost" id="closeCart">Close</button>
    </div>
    <div id="cartItems" style="margin-top:12px"></div>
    <div style="margin-top:12px;border-top:1px dashed #f6eef0;padding-top:12px">
      <div style="display:flex;justify-content:space-between"><div class="muted">Subtotal</div><div id="cartTotal" style="font-weight:800">₹0</div></div>
      <div style="margin-top:12px;display:flex;gap:8px">
        <button class="btn" id="checkout">Checkout</button>
        <button class="ghost" id="clearCart">Clear</button>
      </div>
      <div class="muted" style="margin-top:10px">Impact from items in cart will show above.</div>
    </div>
  </aside>

  <div id="newsletterModal" class="modal" style="display:none">
    <div class="modal-card" style="max-width:540px">
      <div style="flex:1">
        <h3>Join the Nouva Journal</h3>
        <p class="muted">Weekly stories, first access to drops, and repair guides.</p>
        <input id="newsEmail" placeholder="Enter email" style="padding:10px;border-radius:8px;border:1px solid #eee;width:100%" />
        <div style="display:flex;gap:8px;margin-top:12px">
          <button class="btn" id="subscribeNews">Subscribe</button>
          <button class="ghost" id="closeNews">Close</button>
        </div>
      </div>
    </div>
  </div>

  <div id="toast" style="position:fixed;left:50%;transform:translateX(-50%);bottom:22px;background:var(--dusty);color:white;padding:10px 14px;border-radius:10px;display:none;z-index:999"></div>

  <div class="float-cta" id="helpCta">Ask us 💬</div>

<script>
/* ------------------ Demo product dataset (richer) ------------------ */
const PRODUCTS = [
  { id:'p1', name:'Embroidered Dress', price:2199, tags:['linen','romance'], mood:'romance', category:['linen'], sizes:['S','M','L'], colors:['#ffffff','#fdeef5'], sustainable:true, src:'https://img.tatacliq.com/images/i11/437Wx649H/MP000000016925513_437Wx649H_202304290200591.jpeg', desc:'Lightweight linen made in small batches.', materials:{organic:0.9,recycled:0,water:12}, rating:4.6, reviews:24},
  { id:'p2', name:'Minimal Hemp Tee', price:999, tags:['organic','minimal'], mood:'timeless', category:['organic'], sizes:['S','M','L','XL'], colors:['#ffffff','#efe6ff'], sustainable:true, src:'https://i.etsystatic.com/26451652/r/il/11a60f/6258284787/il_1588xN.6258284787_mieu.jpg', desc:'Hemp tee with low-impact dyes.', materials:{organic:0.85,recycled:0.05,water:8}, rating:4.4, reviews:18},
  { id:'p3', name:'Everyday Denim', price:2599, tags:['denim','urban'], mood:'urban', category:['denim'], sizes:['M','L','XL'], colors:['#cfd8dc'], sustainable:false, src:'https://images.unsplash.com/photo-1520975979651-7b5d05f7f9dd?auto=format&fit=crop&w=900&q=60', desc:'Durable denim with long-life design.', materials:{organic:0,recycled:0,water:60}, rating:4.2, reviews:40},
  { id:'p4', name:'Recycled Knit Sweater', price:3299, tags:['winter','cozy'], mood:'timeless', category:['recycled'], sizes:['S','M','L'], colors:['#efe6ff','#f7ecd7'], sustainable:true, src:'https://m.media-amazon.com/images/I/81ANRIROzjL._AC_SX569_.jpg', desc:'Made from recycled yarn.', materials:{organic:0,recycled:0.95,water:6}, rating:4.8, reviews:51},
  { id:'p5', name:'Linen Summer Dress', price:2899, tags:['linen','romance'], mood:'romance', category:['linen'], sizes:['S','M','L'], colors:['#fdeef5','#ffffff'], sustainable:true, src:'https://images.unsplash.com/photo-1503341455253-b2e723bb3dbb?auto=format&fit=crop&w=900&q=60', desc:'Elegant, airy linen dress.', materials:{organic:0.85,recycled:0,water:14}, rating:4.5, reviews:32},
  { id:'p6', name:'Upcycled Denim Jacket', price:3499, tags:['denim','urban'], mood:'urban', category:['denim','recycled'], sizes:['M','L','XL'], colors:['#cfd8dc'], sustainable:true, src:'https://images.unsplash.com/photo-1541099649105-f69ad21f3246?auto=format&fit=crop&w=900&q=60', desc:'Stylish jacket from upcycled denim.', materials:{organic:0,recycled:0.9,water:30}, rating:4.7, reviews:14},
  { id:'p7', name:'Organic Cotton Hoodie', price:1999, tags:['comfort','cozy'], mood:'timeless', category:['organic'], sizes:['S','M','L','XL'], colors:['#ffffff','#f7ecd7'], sustainable:true, src:'https://www.bhumi-organic.com/cdn/shop/files/OliveWomensHoodieFront2.jpg?v=1746593224&width=990', desc:'Cozy hoodie from organic cotton.', materials:{organic:0.9,recycled:0,water:20}, rating:4.3, reviews:45},
  { id:'p8', name:'Recycled Joggers', price:1499, tags:['comfort','minimal'], mood:'timeless', category:['recycled'], sizes:['S','M','L'], colors:['#cfd8dc'], sustainable:true, src:'https://images.unsplash.com/photo-1520975942238-2b9f3f8d6d1a?auto=format&fit=crop&w=900&q=60', desc:'Comfort joggers from recycled fibers.', materials:{organic:0,recycled:0.9,water:10}, rating:4.1, reviews:9},
  { id:'p9', name:'Embroidery Blazer Co-Ord Set', price:899, tags:['accessory','romance'], mood:'romance', category:['accessory'], sizes:[], colors:['#f7ecd7','#fdeef5'], sustainable:false, src:'https://www.hatkay.com/cdn/shop/files/7506_bcbe9755-11e5-4d94-aec6-6fd26c32883d_1024x1024.jpg?v=1728733606', desc:'Soft scarf with subtle sheen.', materials:{organic:0,recycled:0,water:30}, rating:4.2, reviews:8}
];

/* ------------------ Utilities ------------------ */
const q = (s)=>document.querySelector(s);
const format = (n)=>'₹'+n.toLocaleString('en-IN');
const toast = (t)=>{ const el=q('#toast'); el.textContent=t; el.style.display='block'; clearTimeout(window._to); window._to=setTimeout(()=>el.style.display='none',2600); };

/* ------------------ State ------------------ */
let state = { q:'', mood:'all', cats:[], size:null, color:null, sort:'popular', page:1, per:6 };
let cart = JSON.parse(localStorage.getItem('nouva_cart')||'[]');
let wishlist = JSON.parse(localStorage.getItem('nouva_wishlist')||'[]');
let designs = JSON.parse(localStorage.getItem('nouva_designs')||'[]');

/* ------------------ Helper: sustainability score ------------------ */
function sustainabilityScore(p){
  const mat = p.materials || {organic:0,recycled:0,water:30};
  const materialScore = Math.round((mat.organic*0.7 + mat.recycled*0.3)*100);
  const waterAdj = Math.max(0, Math.round((60 - Math.min(mat.water,60))/60 * 10));
  const score = Math.max(15, Math.min(98, materialScore + (10 - waterAdj)));
  return score;
}

/* ------------------ Render hero dots and autoplay ------------------ */
(function heroInit(){
  const slides = Array.from(document.querySelectorAll('.slide'));
  const dots = q('#dots');
  slides.forEach((s,i)=>{ const d=document.createElement('div'); d.className='dot'; d.addEventListener('click',()=>goto(i)); dots.appendChild(d); });
  let idx=0;
  function show(i){ slides.forEach((s,a)=>{ s.style.opacity=(a===i?1:0); s.style.transform=(a===i?'translateX(0)':'translateX(6px)'); dots.querySelectorAll('.dot').forEach((d,di)=>d.classList.toggle('active',di===i)); } ) }
  function goto(i){ idx=i; show(idx); }
  function next(){ idx=(idx+1)%slides.length; show(idx); }
  show(0); setInterval(next,4500);
})();

/* ------------------ Render product grid with pagination ------------------ */
function filterProducts(){
  let list = PRODUCTS.slice();
  // mood
  if(state.mood && state.mood!=='all') list = list.filter(p=>p.mood===state.mood);
  // categories
  if(state.cats.length) list = list.filter(p=> state.cats.every(c=>p.category.includes(c)));
  // size
  if(state.size) list = list.filter(p=> p.sizes && p.sizes.includes(state.size));
  // color
  if(state.color) list = list.filter(p=> p.colors && p.colors.includes(state.color));
  // search
  if(state.q) list = list.filter(p=> (p.name + p.desc + (p.tags||[]).join(' ')).toLowerCase().includes(state.q.toLowerCase()));
  // sort
  if(state.sort==='price-asc') list.sort((a,b)=>a.price-b.price);
  if(state.sort==='price-desc') list.sort((a,b)=>b.price-a.price);
  if(state.sort==='new') list = list.slice().reverse();
  if(state.sort==='popular') list.sort((a,b)=> (b.rating||0) - (a.rating||0));
  return list;
}

function renderProducts(){
  const list = filterProducts();
  const total = list.length;
  const start = (state.page-1)*state.per;
  const pageItems = list.slice(start, start + state.per);
  const grid = q('#grid'); grid.innerHTML='';
  pageItems.forEach(p=>{
    const sc = sustainabilityScore(p);
    const el = document.createElement('article'); el.className='card';
    el.innerHTML = `
      <div class="thumb"><img loading="lazy" src="${p.src}" alt="${p.name}"></div>
      <div class="meta">
        <div>
          <div style="font-weight:800">${p.name}</div>
          <div class="muted small">${p.desc}</div>
          <div style="margin-top:8px"><span class="sustain">🌱 ${sc}%</span> <span style="margin-left:8px" class="rating">★ ${p.rating}</span></div>
        </div>
        <div style="text-align:right">
          <div class="price">${format(p.price)}</div>
          <div class="muted small">${p.reviews} reviews</div>
        </div>
      </div>
      <div class="actions">
        <button class="btn" data-add="${p.id}">Add to cart</button>
        <button class="ghost" data-view="${p.id}">Quick view</button>
        <button class="ghost" data-wish="${p.id}">${wishlist.some(w=>w.id===p.id)?'♥':'♡'}</button>
      </div>
    `;
    grid.appendChild(el);
  });
  q('#count').textContent = total;
  renderPagination(Math.ceil(total/state.per));
  updateCartUI();
}

/* ------------------ Pagination ------------------ */
function renderPagination(pages){
  const el = q('#pagination'); el.innerHTML='';
  for(let i=1;i<=pages;i++){
    const b=document.createElement('button'); b.className='page-btn'; b.textContent=i;
    b.addEventListener('click', ()=>{ state.page=i; renderProducts(); });
    if(state.page===i) b.style.background='linear-gradient(90deg,var(--dusty),var(--lav))', b.style.color='white';
    el.appendChild(b);
  }
}

/* ------------------ Cart functions ------------------ */
function saveCart(){ localStorage.setItem('nouva_cart', JSON.stringify(cart)); updateCartUI(); }
function saveWishlist(){ localStorage.setItem('nouva_wishlist', JSON.stringify(wishlist)); updateCartUI(); }
function updateCartUI(){
  const items = q('#cartItems'); const totalEl = q('#cartTotal'); const countBadge = q('#miniCount');
  items.innerHTML=''; if(cart.length===0){ items.innerHTML='<div class="muted">Your cart is empty</div>'; totalEl.textContent='₹0'; countBadge.style.display='none'; q('#impactText').textContent='No items yet — add products to see estimated water & carbon savings.'; return;}
  let total=0, waterSaved=0, carbonSaved=0;
  cart.forEach(it=>{
    const p = PRODUCTS.find(x=>x.id===it.id);
    const div=document.createElement('div'); div.className='cart-item';
    div.innerHTML = `<img src="${p.src}" style="width:64px;height:64px;object-fit:cover;border-radius:8px"/>
      <div style="flex:1"><div style="font-weight:700">${p.name}</div><div class="muted small">Qty: ${it.qty}</div>
      <div style="margin-top:8px;display:flex;gap:6px"><button class="ghost" data-minus="${it.id}">-</button><button class="ghost" data-plus="${it.id}">+</button><button class="ghost" data-remove="${it.id}">Remove</button></div></div>
      <div style="text-align:right">${format(p.price*it.qty)}</div>`;
    items.appendChild(div);
    total += p.price * it.qty;
    const est = estimatedImpactSavings(p); waterSaved += est.water * it.qty; carbonSaved += est.carbon * it.qty;
  });
  totalEl.textContent = format(total);
  countBadge.style.display='block'; countBadge.textContent = cart.reduce((s,i)=>s+i.qty,0);
  q('#impactText').textContent = `By choosing these items (demo), you may save approx ${Math.round(waterSaved)}L water and ${Math.round(carbonSaved*10)/10}kg CO₂ vs conventional alternatives.`;
}

/* ------------------ estimated impact ------------------ */
function estimatedImpactSavings(p){
  const defaultConventionalWater = 50;
  const water = p.materials?.water || 30;
  const waterSaved = Math.max(0, defaultConventionalWater - water);
  const carbonSaved = Math.round(waterSaved * 0.08 * 10)/10;
  return {water: waterSaved, carbon: carbonSaved};
}

/* ------------------ Events: click delegation ------------------ */
document.addEventListener('click',(e)=>{
  // add to cart
  const add = e.target.closest('[data-add]');
  if(add){ const id=add.getAttribute('data-add'); const item = cart.find(c=>c.id===id); if(item) item.qty++; else cart.push({id,qty:1}); saveCart(); toast('Added to cart'); renderProducts(); return; }
  // quick view
  const view = e.target.closest('[data-view]');
  if(view){ openModal(view.getAttribute('data-view')); return; }
  // wishlist
  const wish = e.target.closest('[data-wish]');
  if(wish){ const id=wish.getAttribute('data-wish'); const idx=wishlist.findIndex(w=>w.id===id); if(idx>-1){ wishlist.splice(idx,1); toast('Removed from wishlist'); } else { wishlist.push({id}); toast('Added to wishlist'); } saveWishlist(); renderProducts(); return; }
  // cart controls
  const minus = e.target.closest('[data-minus]'); if(minus){ const id=minus.getAttribute('data-minus'); const it=cart.find(i=>i.id===id); if(it){ it.qty=Math.max(1,it.qty-1); saveCart(); renderProducts(); } return; }
  const plus = e.target.closest('[data-plus]'); if(plus){ const id=plus.getAttribute('data-plus'); const it=cart.find(i=>i.id===id); if(it){ it.qty++; saveCart(); renderProducts(); } return; }
  const rem = e.target.closest('[data-remove]'); if(rem){ const id=rem.getAttribute('data-remove'); cart = cart.filter(i=>i.id!==id); saveCart(); renderProducts(); return; }

  // cart open/close
  if(e.target.id==='cartBtn' || e.target.id==='openCart'){ q('#cartSide').classList.add('open'); q('#cartSide').setAttribute('aria-hidden','false'); }
  if(e.target.id==='closeCart'){ q('#cartSide').classList.remove('open'); q('#cartSide').setAttribute('aria-hidden','true'); }

  // clear cart
  if(e.target.id==='clearCart'){ cart=[]; saveCart(); toast('Cart cleared'); renderProducts(); }

  // checkout
  if(e.target.id==='checkout'){ if(cart.length===0) return toast('Cart is empty'); const orderId = 'ORD-'+Math.random().toString(36).slice(2,9).toUpperCase(); const orders = JSON.parse(localStorage.getItem('nouva_orders')||'[]'); orders.unshift({orderId,items:cart,at:new Date().toISOString()}); localStorage.setItem('nouva_orders', JSON.stringify(orders)); cart=[]; saveCart(); toast('Order placed: ' + orderId); q('#cartSide').classList.remove('open'); renderProducts(); }

  // wishlist modal
  if(e.target.id==='wishlistBtn'){ const wl = wishlist.map(w=>PRODUCTS.find(p=>p.id===w.id)?.name).filter(Boolean); alert('Wishlist (demo):\\n' + (wl.length? wl.join('\\n') : 'No items')); }

  // shop now scroll
  if(e.target.id==='shopNow'){ document.querySelector('#grid').scrollIntoView({behavior:'smooth'}); }

  // save design
  if(e.target.id==='saveDesign'){ const color = document.querySelector('.des.active')?.getAttribute('data-color') || '#ffffff'; const label = q('#designLabel').value.trim() || 'NEW'; designs.unshift({color,label,at:new Date().toISOString()}); localStorage.setItem('nouva_designs', JSON.stringify(designs)); toast('Saved design'); }

  if(e.target.id==='viewDesigns'){ const ds = JSON.parse(localStorage.getItem('nouva_designs')||'[]'); if(!ds.length) return toast('No designs yet'); alert('Designs:\\n' + ds.map(d=>d.label+' • '+new Date(d.at).toLocaleString()).join('\\n')); }

  // repair send
  if(e.target.id==='sendRepair'){ e.preventDefault(); const name = q('#r_name').value.trim(); if(!name) return toast('Please add name'); const repairs = JSON.parse(localStorage.getItem('nouva_repairs')||'[]'); repairs.unshift({name, item:q('#r_item').value.trim(), msg:q('#r_msg').value.trim(), at:new Date().toISOString()}); localStorage.setItem('nouva_repairs', JSON.stringify(repairs)); q('#repairForm').reset(); toast('Repair request saved (demo)'); }

  // newsletter modal
  if(e.target.id==='closeNews'){ q('#newsletterModal').style.display='none'; }
  if(e.target.id==='subscribeNews'){ const em = q('#newsEmail').value.trim(); if(!em) return toast('Add email'); const subs = JSON.parse(localStorage.getItem('nouva_news')||'[]'); subs.unshift({email:em,at:new Date().toISOString()}); localStorage.setItem('nouva_news', JSON.stringify(subs)); q('#newsletterModal').style.display='none'; toast('Subscribed'); }

  // help cta
  if(e.target.id==='helpCta'){ alert('Hi! This is a demo prototype of Nouva. For real integration (payments, backend), request next steps.'); }

});

/* ------------------ Modal quick view ------------------ */
function openModal(id){
  const p = PRODUCTS.find(x=>x.id===id); if(!p) return;
  const sc = sustainabilityScore(p);
  q('#modalRoot').innerHTML = `<div class="modal" id="productModal"><div class="modal-card">
    <div class="gallery"><img src="${p.src}" alt="${p.name}" /></div>
    <div class="modal-right">
      <div style="display:flex;justify-content:space-between;align-items:start"><div style="font-weight:800">${p.name}</div><button class="ghost" id="closeModal">✕</button></div>
      <div class="muted small">${p.tags.join(' • ')}</div>
      <div style="font-size:20px;font-weight:800;margin-top:8px">${format(p.price)}</div>
      <div style="margin-top:8px" class="muted">${p.desc}</div>
      <div style="margin-top:8px"><span class="sustain">🌱 ${sc}%</span></div>
      <div style="margin-top:12px"><div class="small muted">Choose size</div><div style="display:flex;gap:8px;margin-top:8px" id="sizeOptions"></div></div>
      <div style="margin-top:12px"><div class="small muted">Choose color</div><div style="display:flex;gap:8px;margin-top:8px" id="colorOptions"></div></div>
      <div style="margin-top:12px;display:flex;gap:8px">
        <button class="btn" id="modalAddToCart">Add to cart</button>
        <button class="ghost" id="modalSaveWish">♡ Wishlist</button>
      </div>
      <div style="margin-top:12px" class="muted small">Rating: ${p.rating} • ${p.reviews} reviews</div>
    </div>
  </div></div>`;
  // close modal
  q('#closeModal').onclick = ()=>{ q('#modalRoot').innerHTML=''; };
  // populate size/color
  const sizeWrap = q('#sizeOptions');
  if(p.sizes && p.sizes.length){
    p.sizes.forEach(s=>{ const b=document.createElement('button'); b.className='chip'; b.textContent=s; b.addEventListener('click', ()=>{ document.querySelectorAll('#sizeOptions .chip').forEach(x=>x.classList.remove('active')); b.classList.add('active'); }); sizeWrap.appendChild(b); });
  } else sizeWrap.innerHTML = '<div class="muted small">One size</div>';
  const colorWrap = q('#colorOptions');
  if(p.colors && p.colors.length){
    p.colors.forEach(c=>{ const b=document.createElement('div'); b.className='swatch'; b.style.background=c; b.style.width='36px'; b.style.height='36px'; b.style.borderRadius='8px'; b.style.cursor='pointer'; b.addEventListener('click', ()=>{ document.querySelectorAll('#colorOptions .swatch').forEach(x=>x.classList.remove('active')); b.classList.add('active'); }); colorWrap.appendChild(b); });
  } else colorWrap.innerHTML = '<div class="muted small">Standard</div>';

  // add to cart from modal
  q('#modalAddToCart').onclick = ()=>{
    const size = q('#sizeOptions .chip.active')?.textContent || null;
    const color = q('#colorOptions .swatch.active')?.style.background || null;
    const item = cart.find(c=>c.id===p.id && c.size===size && c.color===color);
    if(item) item.qty++; else cart.push({id:p.id, qty:1, size, color});
    saveCart(); toast('Added to cart'); q('#modalRoot').innerHTML='';
  };
  q('#modalSaveWish').onclick = ()=>{ if(wishlist.some(w=>w.id===p.id)) { wishlist = wishlist.filter(w=>w.id!==p.id); toast('Removed from wishlist'); } else { wishlist.push({id:p.id}); toast('Added to wishlist'); } saveWishlist(); q('#modalRoot').innerHTML=''; renderProducts(); };
}

/* ------------------ Filters UI handlers ------------------ */
q('#search').addEventListener('input',(e)=>{ state.q=e.target.value; state.page=1; renderProducts(); });
document.querySelectorAll('.filterMood').forEach(b=> b.addEventListener('click',(e)=>{ document.querySelectorAll('.filterMood').forEach(x=>x.style.opacity=0.6); e.target.style.opacity=1; state.mood=e.target.getAttribute('data-mood'); state.page=1; renderProducts(); }));

document.querySelectorAll('.cat').forEach(cb=> cb.addEventListener('change', ()=>{
  const checked = Array.from(document.querySelectorAll('.cat:checked')).map(x=>x.value); state.cats=checked; state.page=1; renderProducts();
}));
document.querySelectorAll('.size').forEach(b=> b.addEventListener('click',(e)=>{ document.querySelectorAll('.size').forEach(x=>x.style.opacity=1); e.target.style.opacity=0.6; state.size=e.target.getAttribute('data-size'); state.page=1; renderProducts(); }));
document.querySelectorAll('.swatch').forEach(s=> s.addEventListener('click',(e)=>{ document.querySelectorAll('.swatch').forEach(x=>x.style.outline=''); e.target.style.outline='2px solid rgba(11,132,255,0.12)'; state.color=e.target.getAttribute('data-color'); state.page=1; renderProducts(); }));

q('#applyFilters').addEventListener('click', ()=>{ state.page=1; renderProducts(); });
q('#clearFilters').addEventListener('click', ()=>{ state={...state, mood:'all', cats:[], size:null, color:null}; document.querySelectorAll('.cat').forEach(x=>x.checked=false); document.querySelectorAll('.size').forEach(x=>x.style.opacity=1); document.querySelectorAll('.swatch').forEach(x=>x.style.outline=''); renderProducts(); });

q('#sort').addEventListener('change',(e)=>{ state.sort=e.target.value; state.page=1; renderProducts(); });

/* ------------------ Designer swatches ------------------ */
document.querySelectorAll('.des').forEach(s=> s.addEventListener('click', (e)=>{ document.querySelectorAll('.des').forEach(x=>x.classList.remove('active')); s.classList.add('active'); q('#designPreview').style.background = s.getAttribute('data-color'); q('#designPreview').style.color = (s.getAttribute('data-color')==='#ffffff')? '#0f1724':'#fff'; }));

/* ------------------ Save / hydrate ------------------ */
function hydrate(){ renderProducts(); updateCartUI(); q('#year').textContent = new Date().getFullYear(); }
hydrate();

/* ------------------ Mega menu toggle ------------------ */
q('#shopBtn').addEventListener('mouseenter', ()=>{ q('#mega').classList.add('show'); q('#mega').setAttribute('aria-hidden','false'); });
q('#shopBtn').addEventListener('mouseleave', ()=>{ setTimeout(()=>{ if(!document.querySelector(':hover')?.classList?.contains('mega-panel')) q('#mega').classList.remove('show'); },300) });
q('#mega').addEventListener('mouseleave', ()=> q('#mega').classList.remove('show'));

/* ------------------ simple newsletter pop after 8s ------------------ */
setTimeout(()=>{ if(!localStorage.getItem('nouva_news_seen')) q('#newsletterModal').style.display='flex'; },8000);

/* ------------------ keyboard accessibility: close modals on Esc ------------------ */
document.addEventListener('keydown', (e)=>{ if(e.key==='Escape'){ q('#modalRoot').innerHTML=''; q('#newsletterModal').style.display='none'; q('#cartSide').classList.remove('open'); } });

</script>
</body>
</html>
