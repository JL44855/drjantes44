<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>DR Jantes – Jantes & Services</title>
  <style>
    *{margin:0;padding:0;box-sizing:border-box}
    :root{
      --gold:#c9a84c;--gold-light:#e8c96a;--dark:#0a0a0a;
      --dark2:#111;--dark3:#1a1a1a;--dark4:#222;
      --text:#eee;--text-muted:#888;--radius:10px;
    }
    html{scroll-behavior:smooth}
    body{font-family:'Segoe UI',sans-serif;background:var(--dark);color:var(--text)}
    nav{
      position:fixed;top:0;width:100%;z-index:1000;
      background:rgba(10,10,10,0.97);backdrop-filter:blur(10px);
      border-bottom:1px solid #2a2a2a;
      display:flex;align-items:center;justify-content:space-between;
      padding:0 40px;height:70px;
    }
    .logo{font-size:1.6rem;font-weight:800;letter-spacing:2px;color:var(--gold);text-decoration:none;cursor:pointer}
    .logo span{color:var(--text)}
    .nav-links{display:flex;gap:28px;list-style:none}
    .nav-links a{
      color:var(--text-muted);text-decoration:none;font-size:.85rem;
      letter-spacing:1px;text-transform:uppercase;transition:color .3s;cursor:pointer;
    }
    .nav-links a:hover,.nav-links a.active{color:var(--gold)}
    .nav-cta{
      background:var(--gold);color:#000;padding:10px 22px;border-radius:6px;
      font-weight:700;font-size:.85rem;letter-spacing:1px;
      border:none;cursor:pointer;transition:background .3s;
    }
    .nav-cta:hover{background:var(--gold-light)}
    .burger{display:none;flex-direction:column;gap:5px;cursor:pointer;background:none;border:none;padding:4px}
    .burger span{display:block;width:24px;height:2px;background:var(--text);transition:all .3s}
    .page{display:none;padding-top:70px;min-height:100vh}
    .page.active{display:block}
    /* HERO */
    .hero{
      min-height:calc(100vh - 70px);
      background:linear-gradient(135deg,#0a0a0a 0%,#1a1100 50%,#0a0a0a 100%);
      display:flex;align-items:center;justify-content:center;
      text-align:center;padding:60px 20px;position:relative;overflow:hidden;
    }
    .hero::before{
      content:'';position:absolute;inset:0;
      background:radial-gradient(ellipse at center,rgba(201,168,76,.15) 0%,transparent 70%);
    }
    .hero-content{position:relative;z-index:1;max-width:700px}
    .hero-badge{
      display:inline-block;border:1px solid var(--gold);color:var(--gold);
      font-size:.75rem;letter-spacing:3px;text-transform:uppercase;
      padding:6px 18px;border-radius:50px;margin-bottom:24px;
    }
    .hero h1{font-size:clamp(2.2rem,6vw,4.5rem);font-weight:900;line-height:1.1;margin-bottom:20px}
    .hero h1 span{color:var(--gold)}
    .hero p{font-size:1.05rem;color:var(--text-muted);margin:0 auto 40px;line-height:1.7}
    .hero-btns{display:flex;gap:16px;justify-content:center;flex-wrap:wrap}
    .btn-primary{
      background:var(--gold);color:#000;padding:14px 32px;border-radius:8px;
      font-weight:700;font-size:.95rem;border:none;cursor:pointer;
      transition:all .3s;letter-spacing:.5px;
    }
    .btn-primary:hover{background:var(--gold-light);transform:translateY(-2px)}
    .btn-secondary{
      border:1px solid #444;color:var(--text);padding:14px 32px;border-radius:8px;
      font-weight:600;font-size:.95rem;background:transparent;cursor:pointer;transition:all .3s;
    }
    .btn-secondary:hover{border-color:var(--gold);color:var(--gold)}
    .stats{display:flex;gap:50px;justify-content:center;margin-top:60px;flex-wrap:wrap}
    .stat{text-align:center}
    .stat strong{display:block;font-size:2rem;font-weight:800;color:var(--gold)}
    .stat span{font-size:.78rem;color:var(--text-muted);letter-spacing:1px;text-transform:uppercase}
    section{padding:80px 20px}
    .section-label{display:block;color:var(--gold);font-size:.73rem;letter-spacing:3px;text-transform:uppercase;margin-bottom:10px;text-align:center}
    .section-title{font-size:clamp(1.7rem,4vw,2.6rem);font-weight:800;text-align:center;margin-bottom:12px}
    .section-sub{text-align:center;color:var(--text-muted);max-width:540px;margin:0 auto 50px;line-height:1.7;font-size:.95rem}
    .container{max-width:1200px;margin:0 auto}
    /* SERVICES */
    .services-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px}
    .service-card{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);
      padding:28px 24px;transition:border-color .3s,transform .3s;
    }
    .service-card:hover{border-color:var(--gold);transform:translateY(-4px)}
    .service-icon{font-size:2rem;margin-bottom:16px;display:block}
    .service-card h3{font-size:1rem;margin-bottom:8px;font-weight:700}
    .service-card p{color:var(--text-muted);font-size:.85rem;line-height:1.6}
    /* PROMO CARDS */
    .promos-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:24px}
    .promo-card{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);
      overflow:hidden;transition:transform .3s,border-color .3s;position:relative;cursor:pointer;
    }
    .promo-card:hover{transform:translateY(-6px);border-color:var(--gold)}
    .promo-img{width:100%;height:170px;display:flex;align-items:center;justify-content:center;position:relative}
    .jante-bg{background:linear-gradient(135deg,#1a1500,#2a2200)}
    .pneu-bg{background:linear-gradient(135deg,#0a0f0a,#152015)}
    .pack-bg{background:linear-gradient(135deg,#100018,#200030)}
    .acc-bg{background:linear-gradient(135deg,#001212,#002020)}
    .badge-promo{
      position:absolute;top:10px;left:10px;background:#e53;color:#fff;
      font-size:.68rem;font-weight:800;padding:3px 10px;border-radius:50px;
    }
    .badge-new{
      position:absolute;top:10px;left:10px;background:var(--gold);color:#000;
      font-size:.68rem;font-weight:800;padding:3px 10px;border-radius:50px;
    }
    .promo-info{padding:18px}
    .promo-info h3{font-size:.97rem;font-weight:700;margin-bottom:6px}
    .price-row{display:flex;align-items:center;gap:8px;margin-bottom:10px;flex-wrap:wrap}
    .price-new{color:var(--gold);font-weight:800;font-size:1.05rem}
    .price-old{color:var(--text-muted);font-size:.82rem;text-decoration:line-through}
    .discount{background:rgba(229,85,51,.15);color:#e55;font-size:.7rem;font-weight:700;padding:2px 8px;border-radius:50px}
    .promo-tags{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:12px}
    .tag{background:rgba(201,168,76,.1);border:1px solid rgba(201,168,76,.2);color:var(--gold);font-size:.7rem;padding:3px 9px;border-radius:50px}
    .btn-devis{
      width:100%;background:transparent;border:1px solid var(--gold);color:var(--gold);
      padding:9px;border-radius:6px;font-weight:600;font-size:.83rem;cursor:pointer;transition:all .3s;
    }
    .btn-devis:hover{background:var(--gold);color:#000}
    /* CATALOGUE TABS */
    .cat-tabs{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-bottom:40px}
    .cat-tab{
      background:transparent;border:1px solid #333;color:var(--text-muted);
      padding:9px 22px;border-radius:50px;font-size:.83rem;cursor:pointer;transition:all .3s;
    }
    .cat-tab.active,.cat-tab:hover{border-color:var(--gold);color:var(--gold);background:rgba(201,168,76,.08)}
    .cat-section{display:none}
    .cat-section.active{display:block}
    /* PRODUCT CARDS */
    .products-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:24px}
    .product-card{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);
      overflow:hidden;transition:transform .3s,border-color .3s;
    }
    .product-card:hover{transform:translateY(-5px);border-color:var(--gold)}
    .product-img{width:100%;height:180px;display:flex;align-items:center;justify-content:center;position:relative}
    .prod-jante{background:linear-gradient(135deg,#1a1500,#2a2200)}
    .prod-pneu{background:linear-gradient(135deg,#0a0f0a,#152015)}
    .prod-pack{background:linear-gradient(135deg,#100018,#200030)}
    .prod-acc{background:linear-gradient(135deg,#001212,#002020)}
    .product-badge{
      position:absolute;top:10px;right:10px;background:var(--gold);color:#000;
      font-size:.68rem;font-weight:700;padding:3px 9px;border-radius:50px;
    }
    .product-badge.sale{background:#e53;color:#fff}
    .product-info{padding:20px}
    .product-info h3{font-size:.97rem;font-weight:700;margin-bottom:6px}
    .product-meta{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px}
    .product-size{color:var(--text-muted);font-size:.8rem}
    .product-price{color:var(--gold);font-weight:800;font-size:1.05rem}
    .product-tags{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:14px}
    /* RDV */
    .rdv-wrapper{display:grid;grid-template-columns:1fr 1.6fr;gap:50px;align-items:start}
    .rdv-info h2{font-size:1.7rem;font-weight:800;margin-bottom:14px}
    .rdv-info p{color:var(--text-muted);line-height:1.7;margin-bottom:28px;font-size:.93rem}
    .rdv-steps{display:flex;flex-direction:column;gap:18px}
    .step{display:flex;gap:14px;align-items:flex-start}
    .step-num{
      background:var(--gold);color:#000;width:30px;height:30px;border-radius:50%;
      display:flex;align-items:center;justify-content:center;font-weight:800;font-size:.82rem;flex-shrink:0;
    }
    .step-text h4{font-size:.92rem;margin-bottom:3px}
    .step-text p{color:var(--text-muted);font-size:.83rem}
    .rdv-form{background:var(--dark3);border:1px solid #2a2a2a;border-radius:14px;padding:32px}
    .form-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
    .form-group{margin-bottom:16px}
    .form-group label{display:block;font-size:.75rem;letter-spacing:.5px;color:var(--text-muted);margin-bottom:6px;text-transform:uppercase}
    .form-group input,.form-group select,.form-group textarea{
      width:100%;background:var(--dark4);border:1px solid #333;color:var(--text);
      border-radius:8px;padding:11px 13px;font-size:.88rem;transition:border-color .3s;
      outline:none;font-family:inherit;
    }
    .form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--gold)}
    .form-group select option{background:var(--dark4)}
    .form-group textarea{height:80px;resize:vertical}
    .time-slots{display:grid;grid-template-columns:repeat(4,1fr);gap:7px;margin-bottom:18px}
    .slot{
      background:var(--dark4);border:1px solid #333;color:var(--text-muted);
      border-radius:6px;padding:8px 4px;font-size:.76rem;text-align:center;cursor:pointer;transition:all .3s;
    }
    .slot:hover,.slot.selected{border-color:var(--gold);color:var(--gold);background:rgba(201,168,76,.08)}
    .slot.unavailable{opacity:.3;cursor:not-allowed;pointer-events:none}
    .slot-label{font-size:.72rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;margin-bottom:9px;display:block}
    .btn-submit{
      width:100%;background:var(--gold);color:#000;border:none;padding:14px;
      border-radius:8px;font-weight:800;font-size:.97rem;cursor:pointer;transition:all .3s;
    }
    .btn-submit:hover{background:var(--gold-light);transform:translateY(-2px)}
    /* CONTACT */
    .contact-grid{display:grid;grid-template-columns:1fr 1fr;gap:50px;align-items:start}
    .contact-info h2{font-size:1.7rem;font-weight:800;margin-bottom:20px}
    .contact-item{display:flex;gap:14px;margin-bottom:22px}
    .contact-icon{
      font-size:1.2rem;width:44px;height:44px;
      background:rgba(201,168,76,.1);border:1px solid rgba(201,168,76,.2);
      border-radius:10px;display:flex;align-items:center;justify-content:center;flex-shrink:0;
    }
    .contact-item h4{font-size:.8rem;color:var(--text-muted);margin-bottom:3px}
    .contact-item p{font-size:.92rem;font-weight:600}
    .map-box{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);
      height:280px;display:flex;align-items:center;justify-content:center;
      flex-direction:column;gap:10px;color:var(--gold);font-size:2.8rem;
    }
    .map-box p{font-size:.87rem;color:var(--text-muted)}
    /* REVIEWS */
    .reviews-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:22px}
    .review-card{background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);padding:26px}
    .stars{color:var(--gold);font-size:1rem;margin-bottom:12px}
    .review-card p{color:var(--text-muted);font-size:.88rem;line-height:1.7;margin-bottom:18px}
    .reviewer{display:flex;align-items:center;gap:10px}
    .avatar{width:38px;height:38px;border-radius:50%;background:var(--gold);color:#000;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:.85rem}
    .reviewer-info h4{font-size:.88rem;font-weight:700}
    .reviewer-info span{font-size:.76rem;color:var(--text-muted)}
    /* FOOTER */
    footer{background:var(--dark2);border-top:1px solid #222;padding:50px 40px 28px}
    .footer-grid{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:36px;max-width:1200px;margin:0 auto 36px}
    .footer-brand p{color:var(--text-muted);font-size:.85rem;line-height:1.6;margin-top:12px}
    footer h4{font-size:.75rem;text-transform:uppercase;letter-spacing:1.5px;color:var(--gold);margin-bottom:14px}
    footer ul{list-style:none;display:flex;flex-direction:column;gap:9px}
    footer ul a{color:var(--text-muted);text-decoration:none;font-size:.85rem;transition:color .3s;cursor:pointer}
    footer ul a:hover{color:var(--gold)}
    .footer-bottom{
      max-width:1200px;margin:0 auto;padding-top:22px;border-top:1px solid #222;
      display:flex;justify-content:space-between;align-items:center;
      font-size:.79rem;color:var(--text-muted);flex-wrap:wrap;gap:10px;
    }
    /* LOGIN PIN */
    .login-page{
      min-height:100vh;display:flex;align-items:center;justify-content:center;
      background:var(--dark);padding:20px;
    }
    .login-box{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:16px;
      padding:44px 36px;width:100%;max-width:360px;text-align:center;
    }
    .login-box .logo-lg{font-size:2rem;font-weight:900;color:var(--gold);letter-spacing:2px;margin-bottom:6px}
    .login-box .logo-lg span{color:var(--text)}
    .login-box .subtitle{color:var(--text-muted);font-size:.88rem;margin-bottom:32px}
    .pin-display{display:flex;gap:14px;justify-content:center;margin-bottom:28px}
    .pin-dot{width:14px;height:14px;border-radius:50%;border:2px solid #444;background:transparent;transition:all .3s}
    .pin-dot.filled{background:var(--gold);border-color:var(--gold)}
    .pin-pad{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:16px}
    .pin-btn{
      background:var(--dark4);border:1px solid #333;color:var(--text);
      height:56px;border-radius:10px;font-size:1.25rem;font-weight:600;
      cursor:pointer;transition:all .3s;
    }
    .pin-btn:hover{border-color:var(--gold);color:var(--gold);background:rgba(201,168,76,.08)}
    .pin-btn:active{transform:scale(.95)}
    .pin-btn.del{font-size:1rem;color:var(--text-muted)}
    .pin-error{color:#e55;font-size:.83rem;margin-top:10px;min-height:20px;transition:all .3s}
    .pin-hint{color:var(--text-muted);font-size:.75rem;margin-top:16px}
    /* ADMIN */
    .admin-layout{display:flex;min-height:calc(100vh - 70px)}
    .admin-sidebar{
      width:230px;flex-shrink:0;background:var(--dark2);
      border-right:1px solid #222;padding:28px 0;
      display:flex;flex-direction:column;position:sticky;top:70px;height:calc(100vh - 70px);overflow-y:auto;
    }
    .admin-sidebar-logo{padding:0 22px 22px;border-bottom:1px solid #222;margin-bottom:16px}
    .admin-sidebar-logo span{font-size:.72rem;color:var(--text-muted);letter-spacing:1.5px;text-transform:uppercase}
    .admin-nav-group{margin-bottom:8px}
    .admin-nav-label{font-size:.65rem;color:#444;letter-spacing:2px;text-transform:uppercase;padding:8px 22px 4px}
    .admin-nav-item{
      display:flex;align-items:center;gap:10px;padding:11px 22px;
      cursor:pointer;transition:all .3s;font-size:.87rem;color:var(--text-muted);
      border-left:3px solid transparent;
    }
    .admin-nav-item:hover,.admin-nav-item.active{color:var(--gold);background:rgba(201,168,76,.06);border-left-color:var(--gold)}
    .admin-nav-item .icon{font-size:1rem;width:20px;text-align:center}
    .admin-main{flex:1;padding:36px;overflow-y:auto;background:var(--dark)}
    .admin-page{display:none}
    .admin-page.active{display:block}
    .admin-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:32px;flex-wrap:wrap;gap:14px}
    .admin-header h2{font-size:1.4rem;font-weight:800}
    .admin-header p{color:var(--text-muted);font-size:.85rem;margin-top:3px}
    .add-btn{
      background:var(--gold);color:#000;border:none;padding:10px 22px;
      border-radius:8px;font-weight:700;font-size:.83rem;cursor:pointer;transition:background .3s;
    }
    .add-btn:hover{background:var(--gold-light)}
    /* STAT CARDS */
    .admin-stats{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:18px;margin-bottom:36px}
    .admin-stat-card{
      background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);
      padding:22px;display:flex;flex-direction:column;gap:6px;
    }
    .admin-stat-card .icon{font-size:1.6rem}
    .admin-stat-card .val{font-size:1.7rem;font-weight:800;color:var(--gold)}
    .admin-stat-card .lbl{font-size:.75rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px}
    /* TABLE */
    .table-wrap{background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);overflow:hidden;overflow-x:auto}
    .table-head{display:flex;justify-content:space-between;align-items:center;padding:18px 22px;border-bottom:1px solid #2a2a2a;flex-wrap:wrap;gap:10px}
    .table-head h3{font-size:.97rem;font-weight:700}
    .search-input{
      background:var(--dark4);border:1px solid #333;color:var(--text);
      padding:8px 14px;border-radius:8px;font-size:.83rem;outline:none;width:220px;
    }
    .search-input:focus{border-color:var(--gold)}
    table{width:100%;border-collapse:collapse;min-width:600px}
    th{background:var(--dark4);padding:11px 15px;text-align:left;font-size:.73rem;letter-spacing:.8px;text-transform:uppercase;color:var(--text-muted)}
    td{padding:13px 15px;border-top:1px solid #1e1e1e;font-size:.86rem}
    tr:hover td{background:rgba(201,168,76,.02)}
    .status-badge{display:inline-block;padding:3px 10px;border-radius:50px;font-size:.7rem;font-weight:700;letter-spacing:.5px}
    .s-pending{background:rgba(255,165,0,.15);color:orange}
    .s-confirmed{background:rgba(0,200,100,.15);color:#0c6}
    .s-done{background:rgba(100,100,255,.15);color:#99f}
    .s-cancelled{background:rgba(229,85,51,.15);color:#e55}
    .action-btns{display:flex;gap:5px}
    .action-btn{background:none;border:1px solid #2a2a2a;color:var(--text-muted);padding:4px 10px;border-radius:5px;font-size:.73rem;cursor:pointer;transition:all .2s}
    .action-btn:hover{border-color:var(--gold);color:var(--gold)}
    .action-btn.del:hover{border-color:#e55;color:#e55}
    /* ADMIN PRODUITS */
    .admin-prod-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:18px}
    .admin-prod-card{background:var(--dark3);border:1px solid #2a2a2a;border-radius:var(--radius);overflow:hidden}
    .admin-prod-img{height:120px;display:flex;align-items:center;justify-content:center;font-size:2.8rem;position:relative}
    .admin-prod-info{padding:14px}
    .admin-prod-info h4{font-size:.93rem;font-weight:700;margin-bottom:3px}
    .admin-prod-info .cat-tag{font-size:.7rem;color:var(--text-muted);margin-bottom:6px}
    .admin-prod-info .price{color:var(--gold);font-weight:800;margin-bottom:12px;font-size:.97rem}
    .admin-prod-actions{display:flex;gap:7px}
    .btn-edit{flex:1;background:rgba(201,168,76,.1);border:1px solid rgba(201,168,76,.3);color:var(--gold);padding:7px;border-radius:6px;font-size:.78rem;cursor:pointer;transition:all .2s}
    .btn-edit:hover{background:rgba(201,168,76,.2)}
    .btn-del{background:rgba(229,85,51,.1);border:1px solid rgba(229,85,51,.3);color:#e55;padding:7px 10px;border-radius:6px;font-size:.78rem;cursor:pointer;transition:all .2s}
    .btn-del:hover{background:rgba(229,85,51,.2)}
    /* MODAL */
    .modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.88);z-index:3000;display:none;align-items:center;justify-content:center;padding:20px}
    .modal-overlay.open{display:flex}
    .modal{background:var(--dark3);border:1px solid #2a2a2a;border-radius:14px;padding:32px;max-width:480px;width:100%;position:relative;max-height:88vh;overflow-y:auto}
    .modal-close{position:absolute;top:14px;right:18px;background:none;border:none;color:var(--text-muted);font-size:1.3rem;cursor:pointer;transition:color .2s}
    .modal-close:hover{color:var(--gold)}
    .modal h3{font-size:1.2rem;margin-bottom:20px;font-weight:800}
    /* TOAST */
    .toast{position:fixed;bottom:28px;right:28px;background:var(--dark3);border:1px solid var(--gold);color:var(--text);padding:14px 22px;border-radius:10px;font-size:.88rem;transform:translateY(100px);opacity:0;transition:all .4s;z-index:9999;max-width:300px}
    .toast.show{transform:translateY(0);opacity:1}
    .toast strong{color:var(--gold)}
    /* PROMO SECTION */
    .promo-section-head{display:flex;align-items:center;gap:12px;margin-bottom:24px;flex-wrap:wrap}
    .promo-section-head h3{font-size:1.1rem;font-weight:700}
    .promo-count-badge{background:rgba(229,85,51,.15);color:#e55;font-size:.72rem;font-weight:700;padding:3px 10px;border-radius:50px}
    /* TOGGLE PROMO */
    .toggle-promo{display:flex;align-items:center;gap:8px;font-size:.83rem;color:var(--text-muted);cursor:pointer;margin-bottom:14px}
    .toggle-switch{width:36px;height:20px;background:#333;border-radius:50px;position:relative;transition:background .3s;flex-shrink:0}
    .toggle-switch::after{content:'';position:absolute;width:14px;height:14px;background:#fff;border-radius:50%;top:3px;left:3px;transition:left .3s}
    .toggle-switch.on{background:var(--gold)}
    .toggle-switch.on::after{left:19px}
    @media(max-width:900px){
      .rdv-wrapper,.contact-grid{grid-template-columns:1fr}
      .footer-grid{grid-template-columns:1fr 1fr}
      .admin-sidebar{width:100%;height:auto;position:relative;top:0;flex-direction:row;flex-wrap:wrap;padding:8px}
      .admin-nav-label{display:none}
      .admin-nav-item{border-left:none;border-bottom:3px solid transparent;padding:10px 14px}
      .admin-nav-item.active{border-bottom-color:var(--gold);border-left-color:transparent}
      nav{padding:0 18px}
      .nav-links{display:none}
      .burger{display:flex}
    }
    @media(max-width:600px){
      .form-row{grid-template-columns:1fr}
      .time-slots{grid-template-columns:repeat(3,1fr)}
      .stats{gap:24px}
      .footer-grid{grid-template-columns:1fr}
      .admin-main{padding:20px}
    }
  </style>
</head>
<body>
<!-- ═══════════ NAV ═══════════ -->
<nav>
  <div class="logo" onclick="showPage('accueil')">DR<span>Jantes</span></div>
  <ul class="nav-links" id="navLinks">
    <li><a onclick="showPage('accueil')" id="nav-accueil" class="active">Accueil</a></li>
    <li><a onclick="showPage('catalogue')" id="nav-catalogue">Catalogue</a></li>
    <li><a onclick="showPage('rdv')" id="nav-rdv">Rendez-vous</a></li>
    <li><a onclick="showPage('contact')" id="nav-contact">Contact</a></li>
    <li><a onclick="showPage('admin-gate')" id="nav-admin">Admin ⚙️</a></li>
  </ul>
  <button class="nav-cta" onclick="showPage('rdv')">Prendre RDV</button>
  <button class="burger" onclick="toggleMenu()" id="burger">
    <span></span><span></span><span></span>
  </button>
</nav>
<!-- TOAST -->
<div class="toast" id="toast"></div>
<!-- ═══════════ PAGE ACCUEIL ═══════════ -->
<div class="page active" id="page-accueil">
  <!-- HERO -->
  <div class="hero">
    <div class="hero-content">
      <span class="hero-badge">⚡ Spécialiste Jantes & Pneus</span>
      <h1>L'excellence<br><span>au bout de vos roues</span></h1>
      <p>Jantes alu, pneus, équilibrage, géométrie — tout pour sublimer votre véhicule avec les meilleurs produits du marché.</p>
      <div class="hero-btns">
        <button class="btn-primary" onclick="showPage('catalogue')">Voir le catalogue</button>
        <button class="btn-secondary" onclick="showPage('rdv')">Prendre rendez-vous</button>
      </div>
      <div class="stats">
        <div class="stat"><strong>500+</strong><span>Clients satisfaits</span></div>
        <div class="stat"><strong>200+</strong><span>Modèles de jantes</span></div>
        <div class="stat"><strong>10+</strong><span>Ans d'expérience</span></div>
        <div class="stat"><strong>4.9★</strong><span>Note moyenne</span></div>
      </div>
    </div>
  </div>
  <!-- SERVICES -->
  <section style="background:var(--dark2)">
    <div class="container">
      <span class="section-label">Ce que nous faisons</span>
      <h2 class="section-title">Nos Services</h2>
      <p class="section-sub">Une gamme complète de services pour votre véhicule, réalisés par des experts passionnés.</p>
      <div class="services-grid">
        <div class="service-card"><span class="service-icon">🔧</span><h3>Montage de Jantes</h3><p>Installation professionnelle sur tous types de véhicules.</p></div>
        <div class="service-card"><span class="service-icon">⚖️</span><h3>Équilibrage</h3><p>Équilibrage précis pour un confort de conduite optimal.</p></div>
        <div class="service-card"><span class="service-icon">📐</span><h3>Géométrie</h3><p>Réglage 3D pour une tenue de route parfaite.</p></div>
        <div class="service-card"><span class="service-icon">🛞</span><h3>Remplacement Pneus</h3><p>Large choix toutes saisons, été, hiver des meilleures marques.</p></div>
        <div class="service-card"><span class="service-icon">✨</span><h3>Rénovation Jantes</h3><p>Réparation et remise en état de vos jantes abîmées.</p></div>
        <div class="service-card"><span class="service-icon">🚗</span><h3>Diagnostic Roues</h3><p>Contrôle complet avec rapport détaillé et recommandations.</p></div>
      </div>
    </div>
  </section>
  <!-- PROMOS ACCUEIL -->
  <section style="background:var(--dark)">
    <div class="container">
      <span class="section-label">Offres limitées</span>
      <h2 class="section-title">Promotions en cours</h2>
      <p class="section-sub">Profitez de nos meilleures offres sur une sélection de jantes, pneus et packs.</p>
      <div class="promos-grid" id="home-promos"></div>
    </div>
  </section>
  <!-- AVIS -->
  <section style="background:var(--dark2)">
    <div class="container">
      <span class="section-label">Ils nous font confiance</span>
      <h2 class="section-title">Avis Clients</h2>
      <p class="section-sub">La satisfaction de nos clients est notre priorité absolue.</p>
      <div class="reviews-grid">
        <div class="review-card"><div class="stars">★★★★★</div><p>"Service impeccable, jantes montées en moins d'une heure. Ma voiture a l'air neuve !"</p><div class="reviewer"><div class="avatar">JM</div><div class="reviewer-info"><h4>Jean-Marc L.</h4><span>BMW Série 5</span></div></div></div>
        <div class="review-card"><div class="stars">★★★★★</div><p>"Prix imbattables, équipe professionnelle et conseil de qualité. Je recommande !"</p><div class="reviewer"><div class="avatar">SC</div><div class="reviewer-info"><h4>Sophie C.</h4><span>Audi A4</span></div></div></div>
        <div class="review-card"><div class="stars">★★★★☆</div><p>"Très bon accueil, explications claires. Géométrie faite avec soin. Merci !"</p><div class="reviewer"><div class="avatar">KD</div><div class="reviewer-info"><h4>Karim D.</h4><span>Mercedes C220</span></div></div></div>
      </div>
    </div>
  </section>
  <!-- CONTACT RAPIDE -->
  <section style="background:var(--dark)">
    <div class="container" style="text-align:center">
      <span class="section-label">Nous joindre</span>
      <h2 class="section-title">Contactez-nous</h2>
      <p class="section-sub">Une question ? Un devis ? Notre équipe répond rapidement.</p>
      <div style="display:flex;gap:20px;justify-content:center;flex-wrap:wrap;margin-top:10px">
        <div class="service-card" style="max-width:220px;text-align:center">
          <span class="service-icon">📞</span>
          <h3>Téléphone</h3>
          <p style="color:var(--gold);font-weight:700">+33 1 23 45 67 89</p>
        </div>
        <div class="service-card" style="max-width:220px;text-align:center">
          <span class="service-icon">✉️</span>
          <h3>Email</h3>
          <p style="color:var(--gold);font-weight:700">contact@drjantes.fr</p>
        </div>
        <div class="service-card" style="max-width:220px;text-align:center">
          <span class="service-icon">🕐</span>
          <h3>Horaires</h3>
          <p>Lun–Sam : 8h–19h</p>
        </div>
      </div>
      <button class="btn-primary" style="margin-top:36px" onclick="showPage('contact')">Voir la page contact</button>
    </div>
  </section>
  <!-- FOOTER -->
  <footer>
    <div class="footer-grid">
      <div class="footer-brand">
        <div class="logo">DR<span>Jantes</span></div>
        <p>Votre spécialiste jantes et pneus depuis plus de 10 ans. Qualité, expertise et passion au service de votre véhicule.</p>
      </div>
      <div>
        <h4>Navigation</h4>
        <ul>
          <li><a onclick="showPage('accueil')">Accueil</a></li>
          <li><a onclick="showPage('catalogue')">Catalogue</a></li>
          <li><a onclick="showPage('rdv')">Rendez-vous</a></li>
          <li><a onclick="showPage('contact')">Contact</a></li>
        </ul>
      </div>
      <div>
        <h4>Services</h4>
        <ul>
          <li><a>Montage Jantes</a></li>
          <li><a>Équilibrage</a></li>
          <li><a>Géométrie 3D</a></li>
          <li><a>Rénovation</a></li>
        </ul>
      </div>
      <div>
        <h4>Contact</h4>
        <ul>
          <li><a>+33 1 23 45 67 89</a></li>
          <li><a>contact@drjantes.fr</a></li>
          <li><a>12 Rue des Jantes, Paris</a></li>
          <li><a>Lun–Sam 8h–19h</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2025 DR Jantes — Tous droits réservés</span>
      <span>Fait avec ❤️ pour nos clients</span>
    </div>
  </footer>
</div>
<!-- ═══════════ PAGE CATALOGUE ═══════════ -->
<div class="page" id="page-catalogue">
  <section style="background:var(--dark);min-height:calc(100vh - 70px)">
    <div class="container">
      <span class="section-label">Notre gamme complète</span>
      <h2 class="section-title">Catalogue</h2>
      <p class="section-sub">Découvrez l'ensemble de nos produits : jantes, pneus, packs et accessoires.</p>
      <div class="cat-tabs">
        <button class="cat-tab active" onclick="switchCat('jantes',this)">🔵 Jantes</button>
        <button class="cat-tab" onclick="switchCat('pneus',this)">⚫ Pneus</button>
        <button class="cat-tab" onclick="switchCat('packs',this)">📦 Packs</button>
        <button class="cat-tab" onclick="switchCat('accessoires',this)">🔩 Accessoires</button>
        <button class="cat-tab" onclick="switchCat('promos-cat',this)">🔥 Promotions</button>
      </div>
      <!-- JANTES -->
      <div class="cat-section active" id="cat-jantes">
        <div class="products-grid" id="grid-jantes"></div>
      </div>
      <!-- PNEUS -->
      <div class="cat-section" id="cat-pneus">
        <div class="products-grid" id="grid-pneus"></div>
      </div>
      <!-- PACKS -->
      <div class="cat-section" id="cat-packs">
        <div class="products-grid" id="grid-packs"></div>
      </div>
      <!-- ACCESSOIRES -->
      <div class="cat-section" id="cat-accessoires">
        <div class="products-grid" id="grid-accessoires"></div>
      </div>
      <!-- PROMOS -->
      <div class="cat-section" id="cat-promos-cat">
        <div class="promo-section-head">
          <h3>🔥 Toutes les promotions</h3>
          <span class="promo-count-badge" id="promo-count-badge">0 offres</span>
        </div>
        <div class="products-grid" id="grid-promos-cat"></div>
      </div>
    </div>
  </section>
</div>
<!-- ═══════════ PAGE RDV ═══════════ -->
<div class="page" id="page-rdv">
  <section style="background:var(--dark2);min-height:calc(100vh - 70px)">
    <div class="container">
      <span class="section-label">Réservation en ligne</span>
      <h2 class="section-title">Prendre Rendez-vous</h2>
      <p class="section-sub">Réservez votre créneau en quelques secondes. Confirmation immédiate par email.</p>
      <div class="rdv-wrapper">
        <div class="rdv-info">
          <h2>Pourquoi choisir DR Jantes ?</h2>
          <p>Notre équipe de professionnels s'occupe de tout. Déposez votre véhicule et repartez avec des roues parfaites.</p>
          <div class="rdv-steps">
            <div class="step"><div class="step-num">1</div><div class="step-text"><h4>Choisissez votre service</h4><p>Montage, géométrie, pneus ou diagnostic.</p></div></div>
            <div class="step"><div class="step-num">2</div><div class="step-text"><h4>Sélectionnez une date</h4><p>Créneaux disponibles du lundi au samedi.</p></div></div>
            <div class="step"><div class="step-num">3</div><div class="step-text"><h4>Confirmez vos infos</h4><p>Nom, véhicule et coordonnées.</p></div></div>
            <div class="step"><div class="step-num">4</div><div class="step-text"><h4>C'est confirmé !</h4><p>Vous recevez une confirmation immédiate.</p></div></div>
          </div>
        </div>
        <div class="rdv-form">
          <form onsubmit="submitRdv(event)">
            <div class="form-row">
              <div class="form-group"><label>Prénom *</label><input type="text" id="rdv-prenom" placeholder="Jean" required></div>
              <div class="form-group"><label>Nom *</label><input type="text" id="rdv-nom" placeholder="Dupont" required></div>
            </div>
            <div class="form-row">
              <div class="form-group"><label>Téléphone *</label><input type="tel" id="rdv-tel" placeholder="06 12 34 56 78" required></div>
              <div class="form-group"><label>Email</label><input type="email" id="rdv-email" placeholder="jean@email.com"></div>
            </div>
            <div class="form-group">
              <label>Véhicule *</label>
              <input type="text" id="rdv-vehicule" placeholder="Ex: Renault Clio 2020" required>
            </div>
            <div class="form-group">
              <label>Service souhaité *</label>
              <select id="rdv-service" required>
                <option value="">Choisir un service...</option>
                <option>Montage de jantes</option>
                <option>Équilibrage</option>
                <option>Géométrie 3D</option>
                <option>Remplacement de pneus</option>
                <option>Rénovation de jantes</option>
                <option>Diagnostic roues</option>
                <option>Pack complet</option>
              </select>
            </div>
            <div class="form-row">
              <div class="form-group"><label>Date souhaitée *</label><input type="date" id="rdv-date" required></div>
              <div class="form-group"><label>Préférence</label>
                <select id="rdv-periode">
                  <option>Matin (8h–12h)</option>
                  <option>Après-midi (13h–17h)</option>
                  <option>Fin de journée (17h–19h)</option>
                </select>
              </div>
            </div>
            <span class="slot-label">Créneaux disponibles</span>
            <div class="time-slots">
              <div class="slot" onclick="selectSlot(this)">08h00</div>
              <div class="slot" onclick="selectSlot(this)">09h00</div>
              <div class="slot unavailable">10h00</div>
              <div class="slot" onclick="selectSlot(this)">11h00</div>
              <div class="slot unavailable">13h00</div>
              <div class="slot" onclick="selectSlot(this)">14h00</div>
              <div class="slot" onclick="selectSlot(this)">15h00</div>
              <div class="slot unavailable">16h00</div>
              <div class="slot" onclick="selectSlot(this)">17h00</div>
              <div class="slot" onclick="selectSlot(this)">18h00</div>
            </div>
            <div class="form-group"><label>Message / Précisions</label><textarea id="rdv-message" placeholder="Informations supplémentaires..."></textarea></div>
            <button type="submit" class="btn-submit">✅ Confirmer le rendez-vous</button>
          </form>
        </div>
      </div>
    </div>
  </section>
</div>
<!-- ═══════════ PAGE CONTACT ═══════════ -->
<div class="page" id="page-contact">
  <section style="background:var(--dark);min-height:calc(100vh - 70px)">
    <div class="container">
      <span class="section-label">Nous joindre</span>
      <h2 class="section-title">Contact</h2>
      <p class="section-sub">Notre équipe est disponible du lundi au samedi pour répondre à toutes vos questions.</p>
      <div class="contact-grid">
        <div class="contact-info">
          <h2>Parlons de votre projet</h2>
          <div class="contact-item">
            <div class="contact-icon">📞</div>
            <div><h4>Téléphone</h4><p>+33 1 23 45 67 89</p></div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">✉️</div>
            <div><h4>Email</h4><p>contact@drjantes.fr</p></div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">📍</div>
            <div><h4>Adresse</h4><p>12 Rue des Jantes, 75001 Paris</p></div>
          </div>
          <div class="contact-item">
            <div class="contact-icon">🕐</div>
            <div><h4>Horaires</h4><p>Lun–Ven : 8h–19h | Sam : 9h–17h</p></div>
          </div>
          <div style="margin-top:30px">
            <button class="btn-primary" onclick="showPage('rdv')">📅 Prendre un RDV</button>
          </div>
        </div>
        <div>
          <div class="map-box">
            <span>📍</span>
            <p>12 Rue des Jantes, Paris</p>
            <p style="font-size:.78rem;color:#555">Intégrez votre Google Maps ici</p>
          </div>
          <div class="rdv-form" style="margin-top:24px">
            <h3 style="font-size:1rem;font-weight:700;margin-bottom:18px">Envoyer un message</h3>
            <form onsubmit="submitContact(event)">
              <div class="form-row">
                <div class="form-group"><label>Nom</label><input type="text" placeholder="Votre nom" required></div>
                <div class="form-group"><label>Email</label><input type="email" placeholder="email@exemple.fr" required></div>
              </div>
              <div class="form-group"><label>Sujet</label><input type="text" placeholder="Objet de votre message"></div>
              <div class="form-group"><label>Message</label><textarea placeholder="Votre message..." style="height:100px" required></textarea></div>
              <button type="submit" class="btn-submit">📨 Envoyer</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</div>
<!-- ═══════════ PAGE ADMIN LOGIN ═══════════ -->
<div class="page" id="page-admin-gate">
  <div class="login-page">
    <div class="login-box">
      <div class="logo-lg">DR<span style="color:var(--text)">Jantes</span></div>
      <p class="subtitle">Espace Administration<br>Entrez votre code à 6 chiffres</p>
      <div class="pin-display" id="pinDisplay">
        <div class="pin-dot" id="dot0"></div>
        <div class="pin-dot" id="dot1"></div>
        <div class="pin-dot" id="dot2"></div>
        <div class="pin-dot" id="dot3"></div>
        <div class="pin-dot" id="dot4"></div>
        <div class="pin-dot" id="dot5"></div>
      </div>
      <div class="pin-pad">
        <button class="pin-btn" onclick="pinPress('1')">1</button>
        <button class="pin-btn" onclick="pinPress('2')">2</button>
        <button class="pin-btn" onclick="pinPress('3')">3</button>
        <button class="pin-btn" onclick="pinPress('4')">4</button>
        <button class="pin-btn" onclick="pinPress('5')">5</button>
        <button class="pin-btn" onclick="pinPress('6')">6</button>
        <button class="pin-btn" onclick="pinPress('7')">7</button>
        <button class="pin-btn" onclick="pinPress('8')">8</button>
        <button class="pin-btn" onclick="pinPress('9')">9</button>
        <button class="pin-btn" onclick="pinPress('0')">0</button>
        <button class="pin-btn del" onclick="pinDel()">⌫</button>
      </div>
      <div class="pin-error" id="pinError"></div>
      <p class="pin-hint">Code par défaut : 123456</p>
    </div>
  </div>
</div>
<!-- ═══════════ PAGE ADMIN ═══════════ -->
<div class="page" id="page-admin">
  <div class="admin-layout">
    <!-- SIDEBAR -->
    <div class="admin-sidebar">
      <div class="admin-sidebar-logo">
        <div class="logo" style="font-size:1.2rem">DR<span>Jantes</span></div>
        <span>Administration</span>
      </div>
      <div class="admin-nav-group">
        <div class="admin-nav-label">Tableau de bord</div>
        <div class="admin-nav-item active" onclick="showAdminPage('dashboard',this)">
          <span class="icon">📊</span> Dashboard
        </div>
      </div>
      <div class="admin-nav-group">
        <div class="admin-nav-label">Gestion</div>
        <div class="admin-nav-item" onclick="showAdminPage('rdvs',this)">
          <span class="icon">📅</span> Rendez-vous
        </div>
        <div class="admin-nav-item" onclick="showAdminPage('produits',this)">
          <span class="icon">🛞</span> Produits
        </div>
        <div class="admin-nav-item" onclick="showAdminPage('promos',this)">
          <span class="icon">🔥</span> Promotions
        </div>
      </div>
      <div class="admin-nav-group">
        <div class="admin-nav-label">Catalogue</div>
        <div class="admin-nav-item" onclick="showAdminPage('cat-jantes',this)">
          <span class="icon">⭕</span> Jantes
        </div>
        <div class="admin-nav-item" onclick="showAdminPage('cat-pneus',this)">
          <span class="icon">⚫</span> Pneus
        </div>
        <div class="admin-nav-item" onclick="showAdminPage('cat-packs',this)">
          <span class="icon">📦</span> Packs
        </div>
        <div class="admin-nav-item" onclick="showAdminPage('cat-accessoires',this)">
          <span class="icon">🔩</span> Accessoires
        </div>
      </div>
      <div class="admin-nav-group" style="margin-top:auto;padding-top:20px;border-top:1px solid #222">
        <div class="admin-nav-item" onclick="adminLogout()" style="color:#e55">
          <span class="icon">🚪</span> Déconnexion
        </div>
      </div>
    </div>
    <!-- MAIN -->
    <div class="admin-main">
      <!-- DASHBOARD -->
      <div class="admin-page active" id="admin-dashboard">
        <div class="admin-header">
          <div><h2>Tableau de bord</h2><p>Bienvenue dans votre espace de gestion DR Jantes</p></div>
        </div>
        <div class="admin-stats">
          <div class="admin-stat-card"><span class="icon">📅</span><span class="val" id="stat-rdv">0</span><span class="lbl">Rendez-vous</span></div>
          <div class="admin-stat-card"><span class="icon">⏳</span><span class="val" id="stat-pending">0</span><span class="lbl">En attente</span></div>
          <div class="admin-stat-card"><span class="icon">🛞</span><span class="val" id="stat-prod">0</span><span class="lbl">Produits</span></div>
          <div class="admin-stat-card"><span class="icon">🔥</span><span class="val" id="stat-promo">0</span><span class="lbl">En promo</span></div>
        </div>
        <!-- Derniers RDV -->
        <div class="table-wrap">
          <div class="table-head"><h3>Derniers rendez-vous</h3></div>
          <table>
            <thead><tr><th>Client</th><th>Service</th><th>Date</th><th>Statut</th><th>Actions</th></tr></thead>
            <tbody id="dash-rdv-tbody"></tbody>
          </table>
        </div>
      </div>
      <!-- RDV -->
      <div class="admin-page" id="admin-rdvs">
        <div class="admin-header">
          <div><h2>Rendez-vous</h2><p>Gérez tous vos rendez-vous clients</p></div>
        </div>
        <div class="table-wrap">
          <div class="table-head">
            <h3>Tous les rendez-vous</h3>
            <input class="search-input" placeholder="🔍 Rechercher..." oninput="filterRdv(this.value)">
          </div>
          <table>
            <thead><tr><th>Client</th><th>Téléphone</th><th>Service</th><th>Date</th><th>Heure</th><th>Véhicule</th><th>Statut</th><th>Actions</th></tr></thead>
            <tbody id="rdv-tbody"></tbody>
          </table>
        </div>
      </div>
      <!-- PRODUITS (vue globale) -->
      <div class="admin-page" id="admin-produits">
        <div class="admin-header">
          <div><h2>Tous les produits</h2><p>Gérez l'ensemble de votre catalogue</p></div>
          <button class="add-btn" onclick="openAddProduct()">+ Ajouter un produit</button>
        </div>
        <div class="admin-prod-grid" id="admin-all-prod"></div>
      </div>
      <!-- PROMOS -->
      <div class="admin-page" id="admin-promos">
        <div class="admin-header">
          <div><h2>Promotions</h2><p>Activez ou désactivez les promotions sur vos produits</p></div>
        </div>
        <div class="admin-prod-grid" id="admin-promo-grid"></div>
      </div>
      <!-- CAT JANTES -->
      <div class="admin-page" id="admin-cat-jantes">
        <div class="admin-header">
          <div><h2>⭕ Jantes</h2><p>Gérez votre catalogue de jantes</p></div>
          <button class="add-btn" onclick="openAddProduct('Jantes')">+ Ajouter</button>
        </div>
        <div class="admin-prod-grid" id="admin-grid-jantes"></div>
      </div>
      <!-- CAT PNEUS -->
      <div class="admin-page" id="admin-cat-pneus">
        <div class="admin-header">
          <div><h2>⚫ Pneus</h2><p>Gérez votre catalogue de pneus</p></div>
          <button class="add-btn" onclick="openAddProduct('Pneus')">+ Ajouter</button>
        </div>
        <div class="admin-prod-grid" id="admin-grid-pneus"></div>
      </div>
      <!-- CAT PACKS -->
      <div class="admin-page" id="admin-cat-packs">
        <div class="admin-header">
          <div><h2>📦 Packs</h2><p>Gérez vos packs combinés</p></div>
          <button class="add-btn" onclick="openAddProduct('Packs')">+ Ajouter</button>
        </div>
        <div class="admin-prod-grid" id="admin-grid-packs"></div>
      </div>
      <!-- CAT ACCESSOIRES -->
      <div class="admin-page" id="admin-cat-accessoires">
        <div class="admin-header">
          <div><h2>🔩 Accessoires</h2><p>Gérez vos accessoires</p></div>
          <button class="add-btn" onclick="openAddProduct('Accessoires')">+ Ajouter</button>
        </div>
        <div class="admin-prod-grid" id="admin-grid-accessoires"></div>
      </div>
    </div>
  </div>
</div>
<!-- ═══════════ MODAL PRODUIT ═══════════ -->
<div class="modal-overlay" id="modalProduct">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('modalProduct')">✕</button>
    <h3 id="modal-prod-title">Ajouter un produit</h3>
    <form onsubmit="saveProduct(event)">
      <input type="hidden" id="prod-id">
      <div class="form-row">
        <div class="form-group"><label>Nom *</label><input type="text" id="prod-nom" required></div>
        <div class="form-group"><label>Catégorie *</label>
          <select id="prod-cat" required>
            <option value="Jantes">Jantes</option>
            <option value="Pneus">Pneus</option>
            <option value="Packs">Packs</option>
            <option value="Accessoires">Accessoires</option>
          </select>
        </div>
      </div>
      <div class="form-row">
        <div class="form-group"><label>Prix (€) *</label><input type="number" id="prod-prix" step="0.01" required></div>
        <div class="form-group"><label>Prix barré (€)</label><input type="number" id="prod-prix-old" step="0.01" placeholder="Laisser vide si aucun"></div>
      </div>
      <div class="form-row">
        <div class="form-group"><label>Taille / Spec</label><input type="text" id="prod-taille" placeholder="Ex: 18 pouces"></div>
        <div class="form-group"><label>Badge</label><input type="text" id="prod-badge" placeholder="Ex: Nouveau, -20%"></div>
      </div>
      <div class="form-group"><label>Description courte</label><textarea id="prod-desc" style="height:70px" placeholder="Description du produit..."></textarea></div>
      <div class="form-group">
        <label>Tags (séparés par virgule)</label>
        <input type="text" id="prod-tags" placeholder="Ex: Aluminium, 5 trous, Sport">
      </div>
      <div class="form-group" style="display:flex;align-items:center;gap:12px">
        <label style="margin:0">En promotion</label>
        <div class="toggle-switch" id="prod-promo-toggle" onclick="this.classList.toggle('on')"></div>
      </div>
      <button type="submit" class="btn-submit" style="margin-top:10px">💾 Enregistrer</button>
    </form>
  </div>
</div>
<!-- ═══════════ MODAL RDV DETAIL ═══════════ -->
<div class="modal-overlay" id="modalRdv">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('modalRdv')">✕</button>
    <h3>Détail du rendez-vous</h3>
    <div id="rdv-detail-content"></div>
    <div style="margin-top:20px">
      <label style="font-size:.78rem;color:var(--text-muted);text-transform:uppercase;letter-spacing:.5px;display:block;margin-bottom:8px">Changer le statut</label>
      <div style="display:flex;gap:8px;flex-wrap:wrap">
        <button class="action-btn" onclick="changeStatus('En attente')">⏳ En attente</button>
        <button class="action-btn" onclick="changeStatus('Confirmé')">✅ Confirmé</button>
        <button class="action-btn" onclick="changeStatus('Terminé')">🏁 Terminé</button>
        <button class="action-btn del" onclick="changeStatus('Annulé')">❌ Annulé</button>
      </div>
    </div>
  </div>
</div>
<script>
// ══════════════════════════════════════════════
//  DONNÉES
// ══════════════════════════════════════════════
let products = [
  // JANTES
  {id:1,nom:"Jante Sport RS",cat:"Jantes",prix:189,prixOld:240,taille:"17 pouces",badge:"-21%",desc:"Jante aluminium sport légère",tags:["Aluminium","5 trous","Sport"],promo:true},
  {id:2,nom:"Jante Classic Silver",cat:"Jantes",prix:149,prixOld:null,taille:"16 pouces",badge:"Nouveau",desc:"Design classique intemporel",tags:["Aluminium","4 trous"],promo:false},
  {id:3,nom:"Jante GT Black",cat:"Jantes",prix:229,prixOld:280,taille:"18 pouces",badge:"-18%",desc:"Look racing mat profond",tags:["Noir mat","5 trous","Racing"],promo:true},
  {id:4,nom:"Jante Flow 19\"",cat:"Jantes",prix:299,prixOld:null,taille:"19 pouces",badge:"Premium",desc:"Jante à rayons coulants",tags:["Chromé","5 trous"],promo:false},
  {id:5,nom:"Jante Evo Carbon",cat:"Jantes",prix:349,prixOld:420,taille:"20 pouces",badge:"-17%",desc:"Finition carbone ultra légère",tags:["Carbone","5 trous","Léger"],promo:true},
  {id:6,nom:"Jante Classic Steel",cat:"Jantes",prix:89,prixOld:null,taille:"15 pouces",badge:null,desc:"Jante acier robuste et économique",tags:["Acier","4 trous"],promo:false},
  // PNEUS
  {id:7,nom:"Michelin Pilot Sport 4",cat:"Pneus",prix:129,prixOld:155,taille:"225/45 R17",badge:"-17%",desc:"Performance route et circuit",tags:["Été","Sport","A"],promo:true},
  {id:8,nom:"Continental Premium",cat:"Pneus",prix:99,prixOld:null,taille:"205/55 R16",badge:"Bestseller",desc:"Confort et longévité au quotidien",tags:["Été","Comfort"],promo:false},
  {id:9,nom:"Bridgestone Blizzak",cat:"Pneus",prix:119,prixOld:140,taille:"215/55 R17",badge:"-15%",desc:"Pneu hiver haute performance",tags:["Hiver","Grip","AAA"],promo:true},
  {id:10,nom:"Goodyear All Season",cat:"Pneus",prix:109,prixOld:null,taille:"205/60 R16",badge:"4 Saisons",desc:"Polyvalent toute l'année",tags:["Toutes saisons"],promo:false},
  // PACKS
  {id:11,nom:"Pack Sport 17\"",cat:"Packs",prix:549,prixOld:720,taille:"4 jantes + 4 pneus",badge:"-24%",desc:"Jantes RS + Michelin Sport inclus",tags:["Complet","Sport","Montage inclus"],promo:true},
  {id:12,nom:"Pack Hiver Complet",cat:"Packs",prix:479,prixOld:580,taille:"4 jantes + 4 pneus hiver",badge:"-17%",desc:"Prêt pour l'hiver, montage offert",tags:["Hiver","Montage offert"],promo:true},
  {id:13,nom:"Pack Économique",cat:"Packs",prix:349,prixOld:null,taille:"4 jantes acier + pneus",badge:"Bon plan",desc:"Le meilleur rapport qualité-prix",tags:["Économique","Acier"],promo:false},
  // ACCESSOIRES
  {id:14,nom:"Kit Boulons Sport",cat:"Accessoires",prix:29,prixOld:40,taille:"20 pièces M14",badge:"-27%",desc:"Boulons acier traité anti-corrosion",tags:["Acier","M14"],promo:true},
  {id:15,nom:"Valve TPMS",cat:"Accessoires",prix:49,prixOld:null,taille:"Lot de 4",badge:"Connecté",desc:"Capteurs pression pneus bluetooth",tags:["Bluetooth","TPMS"],promo:false},
  {id:16,nom:"Écrous Antivol",cat:"Accessoires",prix:39,prixOld:55,taille:"4 écrous + clé",badge:"-29%",desc:"Protégez vos jantes du vol",tags:["Sécurité","Universel"],promo:true},
  {id:17,nom:"Cache-moyeu Logo",cat:"Accessoires",prix:19,prixOld:null,taille:"Lot de 4 - 60mm",badge:null,desc:"Finition parfaite pour vos jantes",tags:["Déco"],promo:false},
];
let rdvs = [
  {id:1,prenom:"Alexandre",nom:"Martin",tel:"06 12 34 56 78",email:"a.martin@email.fr",vehicule:"BMW X5 2021",service:"Montage de jantes",date:"2025-07-28",heure:"09h00",message:"Jantes 19 pouces",statut:"Confirmé"},
  {id:2,prenom:"Lucie",nom:"Bernard",tel:"07 23 45 67 89",email:"lucie.b@email.fr",vehicule:"Peugeot 308",service:"Géométrie 3D",date:"2025-07-29",heure:"14h00",message:"",statut:"En attente"},
  {id:3,prenom:"Marc",nom:"Dubois",tel:"06 34 56 78 90",email:"",vehicule:"Renault Megane RS",service:"Équilibrage",date:"2025-07-30",heure:"11h00",message:"Vibrations à 120km/h",statut:"En attente"},
  {id:4,prenom:"Emma",nom:"Petit",tel:"06 45 67 89 01",email:"emma@email.fr",vehicule:"Volkswagen Golf 8",service:"Pack complet",date:"2025-08-02",heure:"08h00",message:"Pack sport souhaité",statut:"Terminé"},
];
let nextProdId = 18;
let nextRdvId = 5;
let currentRdvId = null;
let selectedSlot = null;
const PIN = "123456";
let pinEntry = "";
// ══════════════════════════════════════════════
//  NAVIGATION
// ══════════════════════════════════════════════
function showPage(name){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('active'));
  if(name==='admin-gate'){
    if(sessionStorage.getItem('drj_auth')==='1'){
      document.getElementById('page-admin').classList.add('active');
      refreshAdmin();
    } else {
      document.getElementById('page-admin-gate').classList.add('active');
    }
  } else {
    const pg = document.getElementById('page-'+name);
    if(pg) pg.classList.add('active');
  }
  const nav = document.getElementById('nav-'+name);
  if(nav) nav.classList.add('active');
  window.scrollTo(0,0);
  if(name==='accueil') renderHomePromos();
  if(name==='catalogue') renderCatalogue();
}
function toggleMenu(){
  const nl = document.getElementById('navLinks');
  nl.style.display = nl.style.display==='flex'?'none':'flex';
  nl.style.flexDirection='column';
  nl.style.position='absolute';
  nl.style.top='70px';
  nl.style.left='0';
  nl.style.width='100%';
  nl.style.background='rgba(10,10,10,.98)';
  nl.style.padding='20px';
  nl.style.gap='16px';
  nl.style.borderBottom='1px solid #222';
}
// ══════════════════════════════════════════════
//  SVG JANTE
// ══════════════════════════════════════════════
function janteSVG(size=110, color="#c9a84c"){
  const r=size/2, cx=r, cy=r, outer=r-4, inner=r*0.38, hub=r*0.12;
  const spokes=5;
  let paths='';
  for(let i=0;i<spokes;i++){
    const a=(i/spokes)*Math.PI*2 - Math.PI/2;
    const a1=a-0.18, a2=a+0.18;
    const x1=cx+inner*Math.cos(a1), y1=cy+inner*Math.sin(a1);
    const x2=cx+inner*Math.cos(a2), y2=cy+inner*Math.sin(a2);
    const x3=cx+outer*Math.cos(a2), y3=cy+outer*Math.sin(a2);
    const x4=cx+outer*Math.cos(a1), y4=cy+outer*Math.sin(a1);
    paths+=`<path d="M${x1},${y1} L${x4},${y4} A${outer},${outer} 0 0,1 ${x3},${y3} L${x2},${y2} A${inner},${inner} 0 0,0 ${x1},${y1}Z" fill="${color}" opacity="0.9"/>`;
  }
  return `<svg width="${size}" height="${size}" viewBox="0 0 ${size} ${size}" xmlns="[w3.org](http://www.w3.org/2000/svg)">
    <circle cx="${cx}" cy="${cy}" r="${outer}" fill="none" stroke="${color}" stroke-width="5"/>
    <circle cx="${cx}" cy="${cy}" r="${r*0.28}" fill="${color}" opacity="0.15"/>
    ${paths}
    <circle cx="${cx}" cy="${cy}" r="${hub}" fill="${color}"/>
    <circle cx="${cx}" cy="${cy}" r="${hub*0.5}" fill="#111"/>
  </svg>`;
}
function productEmoji(cat){
  if(cat==='Jantes') return `<div style="display:flex;align-items:center;justify-content:center;width:100%;height:100%">${janteSVG(100)}</div>`;
  if(cat==='Pneus') return '🛞';
  if(cat==='Packs') return '📦';
  return '🔩';
}
function bgClass(cat){
  if(cat==='Jantes') return 'prod-jante';
  if(cat==='Pneus') return 'prod-pneu';
  if(cat==='Packs') return 'prod-pack';
  return 'prod-acc';
}
// ══════════════════════════════════════════════
//  RENDU PRODUIT CARD
// ══════════════════════════════════════════════
function renderProductCard(p){
  const tags = p.tags.map(t=>`<span class="tag">${t}</span>`).join('');
  const badgeHtml = p.badge ? `<span class="product-badge ${p.promo?'sale':''}">${p.badge}</span>` : '';
  const oldPrice = p.prixOld ? `<span class="price-old">${p.prixOld}€</span>` : '';
  const isJante = p.cat==='Jantes';
  return `<div class="product-card">
    <div class="product-img ${bgClass(p.cat)}">
      ${isJante ? janteSVG(100) : `<span style="font-size:3.2rem">${productEmojiChar(p.cat)}</span>`}
      ${badgeHtml}
    </div>
    <div class="product-info">
      <h3>${p.nom}</h3>
      <div class="product-meta">
        <span class="product-size">${p.taille}</span>
        <span class="product-price">${p.prix}€</span>
      </div>
      ${oldPrice ? `<div style="margin-bottom:8px">${oldPrice}</div>` : ''}
      <div class="product-tags">${tags}</div>
      <button class="btn-devis" onclick="demanderDevis('${p.nom}')">Demander un devis</button>
    </div>
  </div>`;
}
function productEmojiChar(cat){
  if(cat==='Pneus') return '🛞';
  if(cat==='Packs') return '📦';
  return '🔩';
}
// ══════════════════════════════════════════════
//  PROMOS ACCUEIL
// ══════════════════════════════════════════════
function renderHomePromos(){
  const promos = products.filter(p=>p.promo);
  const grid = document.getElementById('home-promos');
  if(!grid) return;
  grid.innerHTML = promos.length === 0
    ? '<p style="color:var(--text-muted);text-align:center;grid-column:1/-1">Aucune promotion en cours.</p>'
    : promos.map(p=>{
      const bgC = p.cat==='Jantes'?'jante-bg':p.cat==='Pneus'?'pneu-bg':p.cat==='Packs'?'pack-bg':'acc-bg';
      const disc = p.prixOld ? Math.round((1-p.prix/p.prixOld)*100) : null;
      const isJante = p.cat==='Jantes';
      return `<div class="promo-card">
        <div class="promo-img ${bgC}">
          ${isJante ? janteSVG(100) : `<span style="font-size:3.2rem">${productEmojiChar(p.cat)}</span>`}
          <span class="badge-promo">${p.badge||'PROMO'}</span>
        </div>
        <div class="promo-info">
          <h3>${p.nom}</h3>
          <div class="price-row">
            <span class="price-new">${p.prix}€</span>
            ${p.prixOld?`<span class="price-old">${p.prixOld}€</span><span class="discount">-${disc}%</span>`:''}
          </div>
          <div class="promo-tags">${p.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>
          <button class="btn-devis" onclick="demanderDevis('${p.nom}')">Voir l'offre</button>
        </div>
      </div>`;
    }).join('');
}
// ══════════════════════════════════════════════
//  CATALOGUE
// ══════════════════════════════════════════════
function renderCatalogue(){
  ['Jantes','Pneus','Packs','Accessoires'].forEach(cat=>{
    const key = cat.toLowerCase();
    const grid = document.getElementById('grid-'+key);
    if(!grid) return;
    const items = products.filter(p=>p.cat===cat);
    grid.innerHTML = items.length===0
      ? '<p style="color:var(--text-muted);grid-column:1/-1">Aucun produit dans cette catégorie.</p>'
      : items.map(p=>renderProductCard(p)).join('');
  });
  // Promos
  const promos = products.filter(p=>p.promo);
  const g = document.getElementById('grid-promos-cat');
  if(g) g.innerHTML = promos.length===0
    ? '<p style="color:var(--text-muted);grid-column:1/-1">Aucune promotion en cours.</p>'
    : promos.map(p=>renderProductCard(p)).join('');
  const badge = document.getElementById('promo-count-badge');
  if(badge) badge.textContent = promos.length+' offre'+(promos.length>1?'s':'');
}
function switchCat(name,btn){
  document.querySelectorAll('.cat-tab').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.cat-section').forEach(s=>s.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('cat-'+name).classList.add('active');
}
// ══════════════════════════════════════════════
//  RDV FORM
// ══════════════════════════════════════════════
function selectSlot(el){
  document.querySelectorAll('.slot').forEach(s=>s.classList.remove('selected'));
  el.classList.add('selected');
  selectedSlot = el.textContent;
}
function submitRdv(e){
  e.preventDefault();
  const rdv = {
    id: nextRdvId++,
    prenom: document.getElementById('rdv-prenom').value,
    nom: document.getElementById('rdv-nom').value,
    tel: document.getElementById('rdv-tel').value,
    email: document.getElementById('rdv-email').value,
    vehicule: document.getElementById('rdv-vehicule').value,
    service: document.getElementById('rdv-service').value,
    date: document.getElementById('rdv-date').value,
    heure: selectedSlot || document.getElementById('rdv-periode').value,
    message: document.getElementById('rdv-message').value,
    statut: 'En attente'
  };
  rdvs.unshift(rdv);
  e.target.reset();
  document.querySelectorAll('.slot').forEach(s=>s.classList.remove('selected'));
  selectedSlot = null;
  showToast('✅ <strong>Rendez-vous confirmé !</strong><br>Nous vous contacterons rapidement.');
}
function submitContact(e){
  e.preventDefault();
  e.target.reset();
  showToast('📨 <strong>Message envoyé !</strong><br>Nous vous répondrons dans les 24h.');
}
function demanderDevis(nom){
  showPage('rdv');
  setTimeout(()=>{
    const s = document.getElementById('rdv-service');
    s.value = 'Pack complet';
    const m = document.getElementById('rdv-message');
    m.value = 'Intéressé par : '+nom;
    showToast('💬 <strong>Produit sélectionné</strong><br>Complétez le formulaire pour votre devis.');
  },400);
}
// ══════════════════════════════════════════════
//  PIN LOGIN
// ══════════════════════════════════════════════
function pinPress(d){
  if(pinEntry.length>=6) return;
  pinEntry += d;
  updateDots();
  if(pinEntry.length===6){
    setTimeout(()=>{
      if(pinEntry===PIN){
        sessionStorage.setItem('drj_auth','1');
        pinEntry='';
        updateDots();
        document.getElementById('page-admin-gate').classList.remove('active');
        document.getElementById('page-admin').classList.add('active');
        refreshAdmin();
      } else {
        document.getElementById('pinError').textContent='❌ Code incorrect, réessayez.';
        pinEntry='';
        updateDots();
        setTimeout(()=>document.getElementById('pinError').textContent='',2000);
      }
    },150);
  }
}
function pinDel(){
  pinEntry = pinEntry.slice(0,-1);
  updateDots();
  document.getElementById('pinError').textContent='';
}
function updateDots(){
  for(let i=0;i<6;i++){
    const d=document.getElementById('dot'+i);
    if(d) d.classList.toggle('filled',i<pinEntry.length);
  }
}
// ══════════════════════════════════════════════
//  ADMIN
// ══════════════════════════════════════════════
function showAdminPage(name,el){
  document.querySelectorAll('.admin-page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.admin-nav-item').forEach(n=>n.classList.remove('active'));
  const pg = document.getElementById('admin-'+name);
  if(pg) pg.classList.add('active');
  if(el) el.classList.add('active');
  refreshAdmin();
}
function adminLogout(){
  sessionStorage.removeItem('drj_auth');
  pinEntry='';
  updateDots();
  showPage('accueil');
  showToast('👋 <strong>Déconnecté</strong> avec succès.');
}
function refreshAdmin(){
  // Stats
  const pending = rdvs.filter(r=>r.statut==='En attente').length;
  const promoCount = products.filter(p=>p.promo).length;
  const sv=document.getElementById('stat-rdv'); if(sv) sv.textContent=rdvs.length;
  const sp=document.getElementById('stat-pending'); if(sp) sp.textContent=pending;
  const spd=document.getElementById('stat-prod'); if(spd) spd.textContent=products.length;
  const spr=document.getElementById('stat-promo'); if(spr) spr.textContent=promoCount;
  // Dash RDV
  const dt=document.getElementById('dash-rdv-tbody');
  if(dt) dt.innerHTML=rdvs.slice(0,5).map(r=>rdvRow(r,true)).join('');
  // Full RDV
  const rt=document.getElementById('rdv-tbody');
  if(rt) rt.innerHTML=rdvs.map(r=>rdvRow(r,false)).join('');
  // All products
  const ap=document.getElementById('admin-all-prod');
  if(ap) ap.innerHTML=products.map(p=>adminProdCard(p)).join('');
  // By cat
  ['Jantes','Pneus','Packs','Accessoires'].forEach(cat=>{
    const g=document.getElementById('admin-grid-'+cat.toLowerCase());
    if(g) g.innerHTML=products.filter(p=>p.cat===cat).map(p=>adminProdCard(p)).join('');
  });
  // Promos panel
  const pg=document.getElementById('admin-promo-grid');
  if(pg) pg.innerHTML=products.map(p=>adminPromoCard(p)).join('');
}
function rdvRow(r,short){
  const sc={'En attente':'s-pending','Confirmé':'s-confirmed','Terminé':'s-done','Annulé':'s-cancelled'};
  const fmt=r.date?new Date(r.date).toLocaleDateString('fr-FR'):'—';
  if(short){
    return `<tr>
      <td><strong>${r.prenom} ${r.nom}</strong></td>
      <td>${r.service}</td>
      <td>${fmt}</td>
      <td><span class="status-badge ${sc[r.statut]||'s-pending'}">${r.statut}</span></td>
      <td><div class="action-btns">
        <button class="action-btn" onclick="openRdvDetail(${r.id})">👁 Voir</button>
      </div></td>
    </tr>`;
  }
  return `<tr>
    <td><strong>${r.prenom} ${r.nom}</strong></td>
    <td>${r.tel}</td>
    <td>${r.service}</td>
    <td>${fmt}</td>
    <td>${r.heure||'—'}</td>
    <td>${r.vehicule}</td>
    <td><span class="status-badge ${sc[r.statut]||'s-pending'}">${r.statut}</span></td>
    <td><div class="action-btns">
      <button class="action-btn" onclick="openRdvDetail(${r.id})">👁</button>
      <button class="action-btn del" onclick="deleteRdv(${r.id})">🗑</button>
    </div></td>
  </tr>`;
}
function openRdvDetail(id){
  currentRdvId = id;
  const r = rdvs.find(x=>x.id===id);
  if(!r) return;
  const fmt = r.date?new Date(r.date).toLocaleDateString('fr-FR'):'—';
  document.getElementById('rdv-detail-content').innerHTML=`
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px">
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Client</span><p style="font-weight:700;margin-top:3px">${r.prenom} ${r.nom}</p></div>
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Téléphone</span><p style="font-weight:700;margin-top:3px">${r.tel}</p></div>
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Service</span><p style="margin-top:3px">${r.service}</p></div>
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Véhicule</span><p style="margin-top:3px">${r.vehicule}</p></div>
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Date</span><p style="margin-top:3px">${fmt}</p></div>
      <div><span style="font-size:.75rem;color:var(--text-muted);text-transform:uppercase">Heure</span><p style="margin-top:3px">${r.heure||'—'}</p></div>
    </div>
    ${r.message?`<div style="background:var(--dark4);border-radius:8px;padding:12px;font-size:.87rem;color:var(--text-muted)">💬 ${r.message}</div>`:''}
  `;
  document.getElementById('modalRdv').classList.add('open');
}
function changeStatus(s){
  const r=rdvs.find(x=>x.id===currentRdvId);
  if(r){ r.statut=s; refreshAdmin(); showToast(`✅ Statut mis à jour : <strong>${s}</strong>`); }
  closeModal('modalRdv');
}
function deleteRdv(id){
  if(!confirm('Supprimer ce rendez-vous ?')) return;
  rdvs = rdvs.filter(r=>r.id!==id);
  refreshAdmin();
  showToast('🗑 Rendez-vous supprimé.');
}
function filterRdv(q){
  const rows = document.querySelectorAll('#rdv-tbody tr');
  rows.forEach(r=>{
    r.style.display = r.textContent.toLowerCase().includes(q.toLowerCase())?'':'none';
  });
}
// ══════════════════════════════════════════════
//  ADMIN PRODUIT CARDS
// ══════════════════════════════════════════════
function adminProdCard(p){
  const isJante=p.cat==='Jantes';
  const imgContent = isJante
    ? `<div style="display:flex;align-items:center;justify-content:center;width:100%;height:100%">${janteSVG(80)}</div>`
    : `<span style="font-size:2.6rem">${productEmojiChar(p.cat)}</span>`;
  return `<div class="admin-prod-card">
    <div class="admin-prod-img ${bgClass(p.cat)}">${imgContent}
      ${p.promo?'<span class="badge-promo" style="position:absolute;top:8px;left:8px">PROMO</span>':''}
    </div>
    <div class="admin-prod-info">
      <h4>${p.nom}</h4>
      <div class="cat-tag">${p.cat} · ${p.taille}</div>
      <div class="price">${p.prix}€${p.prixOld?` <span style="color:var(--text-muted);font-size:.82rem;text-decoration:line-through">${p.prixOld}€</span>`:''}</div>
      <div class="admin-prod-actions">
        <button class="btn-edit" onclick="openEditProduct(${p.id})">✏️ Modifier</button>
        <button class="btn-del" onclick="deleteProduct(${p.id})">🗑</button>
      </div>
    </div>
  </div>`;
}
function adminPromoCard(p){
  const isJante=p.cat==='Jantes';
  const imgContent = isJante
    ? `<div style="display:flex;align-items:center;justify-content:center;width:100%;height:100%">${janteSVG(70)}</div>`
    : `<span style="font-size:2.4rem">${productEmojiChar(p.cat)}</span>`;
  return `<div class="admin-prod-card" style="border-color:${p.promo?'rgba(201,168,76,.4)':'#2a2a2a'}">
    <div class="admin-prod-img ${bgClass(p.cat)}">${imgContent}</div>
    <div class="admin-prod-info">
      <h4>${p.nom}</h4>
      <div class="cat-tag">${p.cat} · ${p.taille}</div>
      <div class="price">${p.prix}€</div>
      <label class="toggle-promo" onclick="togglePromo(${p.id})">
        <div class="toggle-switch ${p.promo?'on':''}"></div>
        <span>${p.promo?'En promotion':'Hors promotion'}</span>
      </label>
    </div>
  </div>`;
}
function togglePromo(id){
  const p=products.find(x=>x.id===id);
  if(p){
    p.promo=!p.promo;
    refreshAdmin();
    showToast(p.promo?`🔥 <strong>${p.nom}</strong> mis en promotion.`:`✅ <strong>${p.nom}</strong> retiré des promos.`);
  }
}
// ══════════════════════════════════════════════
//  MODAL PRODUIT
// ══════════════════════════════════════════════
function openAddProduct(cat){
  document.getElementById('modal-prod-title').textContent='Ajouter un produit';
  document.getElementById('prod-id').value='';
  document.getElementById('prod-nom').value='';
  document.getElementById('prod-cat').value=cat||'Jantes';
  document.getElementById('prod-prix').value='';
  document.getElementById('prod-prix-old').value='';
  document.getElementById('prod-taille').value='';
  document.getElementById('prod-badge').value='';
  document.getElementById('prod-desc').value='';
  document.getElementById('prod-tags').value='';
  document.getElementById('prod-promo-toggle').classList.remove('on');
  document.getElementById('modalProduct').classList.add('open');
}
function openEditProduct(id){
  const p=products.find(x=>x.id===id);
  if(!p) return;
  document.getElementById('modal-prod-title').textContent='Modifier le produit';
  document.getElementById('prod-id').value=p.id;
  document.getElementById('prod-nom').value=p.nom;
  document.getElementById('prod-cat').value=p.cat;
  document.getElementById('prod-prix').value=p.prix;
  document.getElementById('prod-prix-old').value=p.prixOld||'';
  document.getElementById('prod-taille').value=p.taille;
  document.getElementById('prod-badge').value=p.badge||'';
  document.getElementById('prod-desc').value=p.desc||'';
  document.getElementById('prod-tags').value=p.tags.join(', ');
  const tog=document.getElementById('prod-promo-toggle');
  p.promo?tog.classList.add('on'):tog.classList.remove('on');
  document.getElementById('modalProduct').classList.add('open');
}
function saveProduct(e){
  e.preventDefault();
  const id=document.getElementById('prod-id').value;
  const isPromo=document.getElementById('prod-promo-toggle').classList.contains('on');
  const data={
    nom:document.getElementById('prod-nom').value,
    cat:document.getElementById('prod-cat').value,
    prix:parseFloat(document.getElementById('prod-prix').value),
    prixOld:document.getElementById('prod-prix-old').value?parseFloat(document.getElementById('prod-prix-old').value):null,
    taille:document.getElementById('prod-taille').value,
    badge:document.getElementById('prod-badge').value||null,
    desc:document.getElementById('prod-desc').value,
    tags:document.getElementById('prod-tags').value.split(',').map(t=>t.trim()).filter(t=>t),
    promo:isPromo
  };
  if(id){
    const idx=products.findIndex(x=>x.id===parseInt(id));
    if(idx>=0) products[idx]={...products[idx],...data};
    showToast('✅ Produit <strong>modifié</strong> avec succès.');
  } else {
    products.push({id:nextProdId++,...data});
    showToast('✅ Produit <strong>ajouté</strong> avec succès.');
  }
  closeModal('modalProduct');
  refreshAdmin();
}
function deleteProduct(id){
  if(!confirm('Supprimer ce produit ?')) return;
  products=products.filter(p=>p.id!==id);
  refreshAdmin();
  showToast('🗑 Produit supprimé.');
}
function closeModal(id){
  document.getElementById(id).classList.remove('open');
}
// ══════════════════════════════════════════════
//  TOAST
// ══════════════════════════════════════════════
function showToast(msg){
  const t=document.getElementById('toast');
  t.innerHTML=msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),3500);
}
// ══════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════
document.addEventListener('DOMContentLoaded',()=>{
  // Date min = aujourd'hui
  const dateInput=document.getElementById('rdv-date');
  if(dateInput) dateInput.min=new Date().toISOString().split('T')[0];
  renderHomePromos();
  renderCatalogue();
});
</script>
</body>
</html>
