<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Le Fromager du CAVA - Commandes & Plats du jour</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800&family=Playfair+Display:wght@400;700;900&display=swap" rel="stylesheet">
    <!-- Font Awesome 6 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: #fefaf2;
            color: #2c2b28;
            scroll-behavior: smooth;
        }

        :root {
            --ivoire-orange: #f77f00;
            --ivoire-orange-fonce: #e06e00;
            --ivoire-vert: #009245;
            --ivoire-vert-fonce: #007a3a;
            --ivoire-blanc: #ffffff;
            --gris-doux: #4a4a48;
        }

        .flag-strip {
            height: 6px;
            background: linear-gradient(90deg, #f77f00 0%, #f77f00 33%, #ffffff 33%, #ffffff 66%, #009245 66%, #009245 100%);
            width: 100%;
        }

        .navbar {
            background: white;
            box-shadow: 0 5px 20px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .logo h1 {
            font-family: 'Playfair Display', serif;
            font-weight: 800;
            font-size: 1.7rem;
            background: linear-gradient(135deg, var(--ivoire-orange), var(--ivoire-vert));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .logo p {
            font-size: 0.75rem;
            color: var(--gris-doux);
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
            flex-wrap: wrap;
        }

        .nav-links a {
            text-decoration: none;
            font-weight: 600;
            color: #333;
        }

        .nav-links a:hover {
            color: var(--ivoire-orange);
        }

        .btn-admin {
            background: #2c3e50;
            color: white !important;
            padding: 0.5rem 1rem;
            border-radius: 40px;
            font-size: 0.9rem;
        }

        .btn-location {
            background: var(--ivoire-vert);
            color: white !important;
            padding: 0.6rem 1.2rem;
            border-radius: 40px;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: 0.2s;
            border: none;
            cursor: pointer;
        }
        
        .cart-icon-header {
            position: relative;
            cursor: pointer;
            font-size: 28px;
            transition: transform 0.3s;
            color: var(--ivoire-vert);
            background: #f0f7ec;
            width: 48px;
            height: 48px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
        }
        .cart-icon-header:hover {
            transform: scale(1.05);
            background: #e2f0db;
        }
        .cart-count-badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background-color: var(--ivoire-orange);
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 12px;
            font-weight: bold;
            min-width: 20px;
            text-align: center;
        }

        .hero {
            background: linear-gradient(120deg, #fff7ed, #fff2e4);
            text-align: center;
            padding: 3rem 2rem;
        }

        .hero h2 {
            font-size: 2.5rem;
            font-family: 'Playfair Display', serif;
            color: var(--ivoire-vert);
        }

        .section-title {
            text-align: center;
            font-size: 2rem;
            font-weight: 800;
            margin: 3rem 0 1rem;
            background: linear-gradient(135deg, var(--ivoire-orange), var(--ivoire-vert));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: inline-block;
            width: 100%;
        }

        .category-sub {
            text-align: center;
            font-size: 1.2rem;
            color: #5a5a55;
            margin-bottom: 2rem;
        }

        .menu-grid, .week-grid {
            max-width: 1400px;
            margin: 2rem auto;
            padding: 0 2rem;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 2rem;
        }

        .food-card {
            background: white;
            border-radius: 32px;
            overflow: hidden;
            box-shadow: 0 15px 30px -12px rgba(0,0,0,0.1);
            transition: 0.25s ease;
            border: 1px solid rgba(247,127,0,0.2);
        }

        .food-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 30px -10px rgba(0,146,69,0.15);
        }

        .card-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            background: #f3e9dc;
        }

        .card-content {
            padding: 1.2rem 1.2rem 1.5rem;
        }

        .card-title {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            flex-wrap: wrap;
            margin-bottom: 10px;
        }

        .card-title h3 {
            font-size: 1.3rem;
        }

        .price {
            font-weight: 800;
            font-size: 1.3rem;
            color: var(--ivoire-vert);
            background: #eef6ea;
            padding: 0.2rem 0.8rem;
            border-radius: 40px;
        }

        .desc {
            color: #5c5a55;
            margin: 10px 0;
            font-size: 0.85rem;
        }

        .badge {
            background: #fff0e0;
            padding: 0.25rem 0.7rem;
            border-radius: 30px;
            font-size: 0.7rem;
            font-weight: 600;
            color: var(--ivoire-orange-fonce);
            display: inline-block;
        }

        .btn-add {
            background: var(--ivoire-orange);
            border: none;
            color: white;
            padding: 10px 0;
            width: 100%;
            border-radius: 40px;
            font-weight: bold;
            margin-top: 12px;
            cursor: pointer;
            transition: 0.2s;
            font-size: 0.9rem;
        }

        .btn-add:hover {
            background: var(--ivoire-vert);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.6);
            z-index: 2000;
            animation: fadeIn 0.3s;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .modal-content {
            background: linear-gradient(135deg, #ffffff 0%, #fef7ef 100%);
            margin: 50px auto;
            padding: 25px;
            width: 90%;
            max-width: 650px;
            border-radius: 32px;
            max-height: 85%;
            overflow-y: auto;
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            animation: slideUp 0.3s;
            position: relative;
        }
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        @media (max-width: 768px) {
            .modal-content {
                margin: 20px auto;
                padding: 18px;
                width: 95%;
            }
        }
        .close-modal {
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
            color: #999;
        }
        .close-modal:hover {
            color: var(--ivoire-orange);
        }
        .cart-item-modal {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 12px;
            border-bottom: 1px solid #ffe0b5;
            background: white;
            margin-bottom: 10px;
            border-radius: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .cart-total {
            font-size: 20px;
            font-weight: bold;
            margin: 20px 0;
            text-align: right;
            color: var(--ivoire-vert);
            padding-top: 15px;
            border-top: 2px solid var(--ivoire-orange);
        }
        .delivery-form-modal {
            margin: 20px 0;
            padding: 15px;
            background: white;
            border-radius: 24px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        .delivery-form-modal h3 {
            color: var(--ivoire-vert);
            margin-bottom: 15px;
            font-size: 1.2rem;
        }
        .form-group {
            margin-bottom: 12px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #555;
            font-weight: bold;
            font-size: 14px;
        }
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 30px;
            font-size: 14px;
            transition: border-color 0.3s;
            font-family: inherit;
        }
        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--ivoire-orange);
        }
        .confirm-btn {
            background: linear-gradient(135deg, var(--ivoire-vert) 0%, var(--ivoire-vert-fonce) 100%);
            color: white;
            border: none;
            padding: 14px;
            width: 100%;
            border-radius: 40px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
            margin-top: 10px;
        }
        .confirm-btn:hover {
            transform: scale(1.02);
        }
        .notification {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(135deg, var(--ivoire-vert) 0%, #00632e 100%);
            color: white;
            padding: 12px 24px;
            border-radius: 50px;
            display: none;
            z-index: 2100;
            animation: slideIn 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-weight: 500;
        }
        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        .btn-quantity {
            background: var(--ivoire-orange);
            border: none;
            padding: 5px 12px;
            border-radius: 30px;
            cursor: pointer;
            font-weight: bold;
            color: white;
            margin: 0 3px;
        }
        .btn-remove {
            background: #dc3545;
            border: none;
            padding: 5px 10px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            margin-left: 8px;
        }
        .location-section {
            background: linear-gradient(145deg, #f5efe5, #fffaf2);
            margin: 2rem;
            border-radius: 48px;
            padding: 2rem;
        }
        footer {
            background: #1e2a1b;
            color: #efebdd;
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
        }
        @media (max-width: 800px) {
            .menu-grid, .week-grid {
                grid-template-columns: 1fr;
            }
            .nav-container {
                flex-direction: row;
                gap: 10px;
            }
        }
        .today-badge {
            background: var(--ivoire-vert);
            color: white;
            border-radius: 40px;
            padding: 8px 18px;
            display: inline-block;
            font-size: 0.9rem;
            margin-bottom: 20px;
        }

        /* Style pour l'upload d'images en mode admin */
        .image-upload-area {
            margin: 10px 0;
            padding: 10px;
            background: #f9f9f9;
            border-radius: 12px;
            text-align: center;
            cursor: pointer;
            transition: 0.2s;
            border: 2px dashed #ccc;
        }
        .image-upload-area:hover {
            border-color: var(--ivoire-orange);
            background: #fff5ec;
        }
        .upload-icon {
            font-size: 1.2rem;
            color: var(--ivoire-vert);
            margin-right: 5px;
        }
        .admin-controls {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 1000;
            background: white;
            padding: 10px 20px;
            border-radius: 40px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            display: none;
        }
        .admin-controls.show {
            display: block;
        }
        .toggle-admin-btn {
            background: var(--ivoire-orange);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 40px;
            cursor: pointer;
            font-weight: bold;
        }
    </style>
</head>
<body>
<div class="flag-strip"></div>
<nav class="navbar">
    <div class="nav-container">
        <div class="logo">
            <h1>🍽️ Restaurant Le Fromager <span style="color:#f77f00;">du CAVA</span></h1>
            <p>Commandez • Paiement à la livraison ou par wave</p>
        </div>
        <div class="nav-links">
            <a href="#menu">Menu</a>
            <a href="#" id="dailySpecialsNavBtn">Plats du jour</a>
            <button id="navLocBtn" class="btn-location"><i class="fas fa-map-marker-alt"></i> CAVA</button>
            <div class="cart-icon-header" id="cartIconBtn">
                🛒
                <span class="cart-count-badge" id="cartCountBadge">0</span>
            </div>
        </div>
    </div>
</nav>

<header class="hero">
    <h2>🔥 Commandez vos plats préférés. Livraison rapide à Abidjan. 🔥</h2>
</header>

<main>
    <!-- SECTION PLATS DU JOUR DYNAMIQUE AVEC VRAIES IMAGES -->
    <div id="dynamicDailySpecials">
        <div class="section-title">📅 Plats du jour</div>
        <div class="category-sub" id="dayInfoMessage">Chargement du menu du jour...</div>
        <div class="week-grid" id="dailySpecialsGrid"></div>
    </div>

    <!-- SECTION MENU COMPLET -->
    <div id="menu">
        <div class="section-title">🍗 📸 Toute notre carte</div>
        <div class="menu-grid" id="fullMenuGrid"></div>
    </div>

    <div id="localisation" class="location-section">
        <div style="max-width: 1000px; margin:auto; text-align:center;">
            <h3><i class="fas fa-map-marked-alt"></i> Centre Artisanal d'Abidjan (CAVA)</h3>
            <p>Restaurant Le Fromager du CAVA - Boulevard de Marseille, Treichville/Plateau situé au milieu du centre Artisanal</p>
            <button id="openMapBtn" class="btn-location" style="background:#f77f00;"><i class="fab fa-google"></i> Ouvrir dans Google Maps</button>
        </div>
    </div>
</main>
<footer>
    <p>© 2025 Le Fromager du CAVA - Paiement à la livraison • Centre Artisanal d'Abidjan 🇨🇮</p>
</footer>

<!-- MODALE PANIER -->
<div id="cartModal" class="modal">
    <div class="modal-content">
        <span class="close-modal" id="closeModalBtn">&times;</span>
        <h2 style="color: var(--ivoire-vert);"><i class="fas fa-shopping-cart"></i> Votre panier</h2>
        <div id="cartItemsModalList"></div>
        <div class="cart-total" id="cartTotalModal">Total: 0 FCFA</div>
        <div class="delivery-form-modal">
            <h3><i class="fas fa-truck"></i> Livraison & paiement à la livraison</h3>
            <div class="form-group">
                <label>Nom complet *</label>
                <input type="text" id="modalClientName" placeholder="Votre nom">
            </div>
            <div class="form-group">
                <label>Téléphone *</label>
                <input type="tel" id="modalClientPhone" placeholder="Numéro de téléphone">
            </div>
            <div class="form-group">
                <label>Adresse de livraison *</label>
                <textarea id="modalClientAddress" rows="2" placeholder="Adresse complète, quartier, point de repère"></textarea>
            </div>
            <div class="form-group">
                <label>Instructions (optionnel)</label>
                <textarea id="modalClientNote" rows="2" placeholder="Porte, code, etc."></textarea>
            </div>
        </div>
        <button class="confirm-btn" id="confirmOrderModalBtn">✅ Valider la commande - Paiement à la livraison</button>
        <p style="font-size: 0.75rem; margin-top: 12px; text-align:center;">* Paiement en espèces à la réception ou via l'application Wave.ci</p>
    </div>
</div>

<!-- Bouton admin flottant -->
<div class="admin-controls" id="adminControls">
    <button class="toggle-admin-btn" id="toggleAdminBtn">Mode Admin: OFF</button>
</div>

<div id="notification" class="notification"></div>

<script>
    // ========== STOCKAGE LOCAL DES IMAGES DES PLATS DU JOUR ==========
    let dailyPlatImages = JSON.parse(localStorage.getItem("dailyPlatImages") || "{}");
    
    function saveDailyImages() {
        localStorage.setItem("dailyPlatImages", JSON.stringify(dailyPlatImages));
    }
    
    function getDailyPlatKey(dayNum, platName) {
        return `day_${dayNum}_${platName.replace(/\s/g, '_')}`;
    }
    
    // BANQUE D'IMAGES RÉELLES POUR LES PLATS DU JOUR (LIENS VERS DE VRAIES PHOTOS CULINAIRES)
    // Chaque plat se voit attribuer une image réaliste et appétissante
    const realFoodImages = {
        // Lundi
        "Gombo grillé poisson": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Gombo grillé poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce légumes poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce légumes poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Couscous poisson": "https://images.pexels.com/photos/958545/pexels-photo-958545.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Couscous poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Attiéké poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Attiéké poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Tchèp poisson": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Tchèp poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Frite poisson": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Frite poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Cabato": "https://images.pexels.com/photos/372851/pexels-photo-372851.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Placali": "https://images.pexels.com/photos/958545/pexels-photo-958545.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce côpè": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        // Mardi
        "Soupe de carpe": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Soupe de poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce Feuille poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce Feuille poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Alloc ko poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Alloc ko poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Poisson braisé": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        // Mercredi
        "Foutou sauce graine pattes de boeuf": "https://images.pexels.com/photos/958545/pexels-photo-958545.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Tchèp au soumara poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Tchèp au soumara poisson": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Soupe de carpe riz": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Soupe de carpe attiéké": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        // Jeudi
        "Riz sauce graine poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Riz sauce graine poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Alloco Poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Riz sauce feuille Poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Riz sauce feuille poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "placali sauce côpè": "https://images.pexels.com/photos/958545/pexels-photo-958545.jpeg?auto=compress&cs=tinysrgb&w=600",
        // Vendredi
        "Riz sauce arachide poulet": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Riz sauce arachide poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Kedjenou poulet": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Kedjenou poisson": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Sauce claire poisson": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Banane plantain grillée": "https://images.pexels.com/photos/372851/pexels-photo-372851.jpeg?auto=compress&cs=tinysrgb&w=600",
        // Samedi
        "Braised fish special": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Grilled chicken yassa": "https://images.pexels.com/photos/616363/pexels-photo-616363.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Riz gras (poulet/poisson)": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Attiéké red oil": "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Mafé Tiga": "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600",
        "Soupe kandia": "https://images.pexels.com/photos/2338407/pexels-photo-2338407.jpeg?auto=compress&cs=tinysrgb&w=600"
    };
    
    function getRealImageForPlat(platName) {
        if (realFoodImages[platName]) {
            return realFoodImages[platName];
        }
        // Image générique par défaut pour les plats non listés
        return "https://images.pexels.com/photos/70497/pexels-photo-70497.jpeg?auto=compress&cs=tinysrgb&w=600";
    }
    
    // Fonction pour uploader une image personnalisée (mode admin)
    function uploadImageForPlat(dayNum, platName, element) {
        const input = document.createElement('input');
        input.type = 'file';
        input.accept = 'image/*';
        input.onchange = (e) => {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (event) => {
                    const imageData = event.target.result;
                    const key = getDailyPlatKey(dayNum, platName);
                    dailyPlatImages[key] = imageData;
                    saveDailyImages();
                    const imgElement = element.querySelector('.card-img');
                    if (imgElement) imgElement.src = imageData;
                    showNotification(`Image personnalisée ajoutée pour ${platName}`);
                };
                reader.readAsDataURL(file);
            }
        };
        input.click();
    }
    
    // ========== MENU COMPLET ==========
    const menuData = [
        { id: 1, name: "Tchèp Poisson", price: 2000, desc: "Poisson braisé épicé, alloco/pain", badge: "⭐ Spécialité", image: "https://i.pinimg.com/736x/2e/3c/c2/2e3cc2588f4a38b8f9265876005c91c6.jpg" },
        { id: 2, name: "Tchèp Poulet", price: 1500, desc: "Poulet tendre grillé, frites/alloco", badge: "🔥 Saveur fumée", image: "https://i.ytimg.com/vi/JD9h7ijXWwc/maxresdefault.jpg" },
        { id: 3, name: "Riz sauce Feuille + Poisson", price: 2000, desc: "Riz blanc, sauce feuilles fraîches, poisson fumé", badge: "Traditionnel", image: "https://i.ytimg.com/vi/CoEk8NGyvps/maxresdefault.jpg" },
        { id: 4, name: "Riz sauce Feuille + Poulet", price: 1500, desc: "Poulet mijoté, sauce onctueuse", badge: "Plat du jour", image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSETPtfKgkl7FzdlnL0eEvPUfhRVhAiYxrSsw&st" },
        { id: 5, name: "Riz sauce Arachide + Poisson", price: 2000, desc: "Sauce arachide crémeuse, poisson frais", badge: "Onctueux", image: "https://images.pexels.com/photos/1279330/pexels-photo-1279330.jpeg?auto=compress&cs=tinysrgb&w=600" },
        { id: 6, name: "Riz sauce Arachide + Poulet", price: 1500, desc: "Sauce arachide, poulet fermier", badge: "Palmier", image: "https://images.pexels.com/photos/699953/pexels-photo-699953.jpeg?auto=compress&cs=tinysrgb&w=600" },
        { id: 7, name: "Riz sauce Légume + Viande", price: 2000, desc: "Légumes frais, bœuf tendre", badge: "Équilibre", image: "data:image/jpeg;base64,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" },
        { id: 8, name: "Riz sauce Légume + poisson", price: 2000, desc: "Légumes frais, bœuf tendre", badge: "Équilibre", image: "data:image/jpeg;base64,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" },
        { id: 9, name: "Riz sauce Légume + poulet", price: 2000, desc: "Légumes frais, bœuf tendre", badge: "Équilibre", image: ""},
        { id : 11,name: "Riz sauce gombo grillé + poulet", price: 2000, desc: "gombo mijotés, poisson braisé", badge: "Riche en fer", image: "https://cdn.thefork.com/tf-lab/image/upload/restaurant/41e96b6a-e014-4103-89c7-152c2a4cc576/d61e52e4-c19d-484c-a1fa-bf82c9f2d087.jpg" },
        { id: 12, name: "Attiéké Poisson", price: 2000, desc: "Attiéké fin, poisson grillé", badge: "Spécialité ivoirienne", image: "https://i.ytimg.com/vi/uAsMFZGECdM/maxresdefault.jpg" },
        { id: 13, name: "Attiéké Poulet", price: 1800, desc: "Semoule de manioc, poulet braisé", badge: "Rapide", image: "https://www.cuisinedecheznous.net/_next/image/?url=https%3A%2F%2Fwww.cuisinedecheznous.net%2Fwp-content%2Fuploads%2Fsites%2F7%2F2026%2F02%2F1771238369865-recipe-57294-hd.jpg&w=1920&q=75" }
    ];

    // ========== GESTION DES JOURS ==========
    function getCurrentDayInAbidjan() {
        const now = new Date();
        const abidjanDate = new Date(now.toLocaleString("en-US", { timeZone: "Africa/Abidjan" }));
        let dayIndex = abidjanDate.getDay();
        if(dayIndex === 0) return 7;
        return dayIndex;
    }

    const dailyMenus = {
        1: { dayName: "Lundi", plats: ["Gombo grillé poisson", "Gombo grillé poulet", "Sauce légumes poisson", "Sauce légumes poulet", "Couscous poisson", "Couscous poulet", "Attiéké poisson", "Attiéké poulet", "Tchèp poisson", "Tchèp poulet", "Frite poisson", "Frite poulet", "Cabato", "Placali", "Sauce côpè"], defaultPrice: 2000, customPrices: { "Cabato": 2000, "Placali": 2000, "Tchèp poulet": 1500 } },
        2: { dayName: "Mardi", plats: ["Soupe de carpe", "Soupe de poulet", "Sauce Feuille poisson", "Sauce Feuille poulet", "Couscous poisson", "Couscous poulet", "Attiéké poisson", "Attiéké poulet", "Sauce légumes poisson", "Sauce légumes poulet", "Tchèp poisson", "Tchèp poulet", "Alloc ko poulet", "Alloc ko poisson", "Frite poisson", "Frite poulet", "Poisson braisé"], defaultPrice: 2000, customPrices: {} },
        3: { dayName: "Mercredi", plats: ["Foutou sauce graine pattes de boeuf", "Tchèp au soumara poulet", "Tchèp au soumara poisson", "Tchèp au soumara viande", "Frite poulet", "Frite poisson", "Alloko poulet", "Alloko poisson", "Sauce graine", "Sauce gombo grillé", "Sauce légumes", "Soupe de carpe riz", "Soupe de carpe attiéké", "Attiéké poisson", "Attiéké poulet", "Couscous poisson", "Couscous poulet"], defaultPrice: 2000, customPrices: { "Sauce graine": 1500, "Sauce gombo grillé": 1500, "Sauce légumes": 1500 } },
        4: { dayName: "Jeudi", plats: ["Riz sauce graine poisson", "Riz sauce graine poulet", "Attiéké poulet", "Attiéké Poisson", "Alloco Poisson", "Riz sauce feuille Poisson", "Riz sauce feuille poulet", "placali sauce côpè", "Riz sauce légume Poisson", "Tchèp Poisson", "Tchèp poulet"], defaultPrice: 2000, customPrices: {} },
        5: { dayName: "Vendredi", plats: ["Riz sauce arachide poulet", "Riz sauce arachide poisson", "Kedjenou poulet", "Kedjenou poisson", "Sauce claire poisson", "Sauce légume poulet", "Banane plantain grillée", "Sauce légume poisson"], defaultPrice: 2000, customPrices: { "Banane plantain grillée": 1000 } },
        6: { dayName: "Samedi", plats: ["Braised fish special", "Grilled chicken yassa", "Riz gras (poulet/poisson)", "Attiéké red oil", "Mafé Tiga", "Soupe kandia"], defaultPrice: 2000, customPrices: {} },
        7: { dayName: "Dimanche", plats: ["Repos - Commande uniquement via Menu principal", "Plat surprise sur demande"], defaultPrice: 0, customPrices: {} }
    };

    function getPriceForPlat(platName, dayObj) {
        if(dayObj.customPrices && dayObj.customPrices[platName]) return dayObj.customPrices[platName];
        return dayObj.defaultPrice;
    }

    function generateDailyPlatsFromDate() {
        const dayNum = getCurrentDayInAbidjan();
        const dayData = dailyMenus[dayNum];
        if(!dayData) return [];
        const results = [];
        for(let platRaw of dayData.plats) {
            let name = platRaw;
            let price = getPriceForPlat(name, dayData);
            let desc = `Plat du ${dayData.dayName} - Spécialité maison`;
            let badge = `📆 ${dayData.dayName}`;
            const key = getDailyPlatKey(dayNum, name);
            let image = dailyPlatImages[key];
            if (!image) image = getRealImageForPlat(name);
            results.push({ id: `daily_${dayNum}_${name.replace(/\s/g, '_')}`, name, price, desc, badge, image, dayNum });
        }
        return results;
    }

    let isAdminMode = false;

    function renderDynamicDailySpecials() {
        const container = document.getElementById("dailySpecialsGrid");
        const dayNum = getCurrentDayInAbidjan();
        const dayData = dailyMenus[dayNum];
        const dayName = dayData ? dayData.dayName : "Aujourd'hui";
        const infoDiv = document.getElementById("dayInfoMessage");
        if(dayNum === 7) infoDiv.innerHTML = `📌 ${dayName} : Menu varié disponible dans la carte complète ci-dessous. Repos plats du jour.`;
        else infoDiv.innerHTML = `🔥 ${dayName} ${new Date().toLocaleDateString('fr-FR', { timeZone: 'Africa/Abidjan' })} - Découvrez nos suggestions spéciales 🔥`;
        const platsList = generateDailyPlatsFromDate();
        if(!platsList.length) { container.innerHTML = `<div style="text-align:center; padding:40px;">Aucun plat du jour programmé.</div>`; return; }
        let html = "";
        platsList.forEach(plat => {
            html += `<div class="food-card" data-plat-name="${plat.name}" data-day-num="${plat.dayNum}">
                        <img class="card-img" src="${plat.image}" alt="${plat.name}" onerror="this.src='https://images.pexels.com/photos/70497/pexels-photo-70497.jpeg?auto=compress&cs=tinysrgb&w=600'">
                        <div class="card-content">
                            <div class="card-title"><h3>${plat.name}</h3><span class="price">${plat.price} FCFA</span></div>
                            <div class="desc">${plat.desc}</div>
                            <span class="badge">${plat.badge}</span>`;
            if (isAdminMode && dayNum !== 7 && plat.price > 0) {
                html += `<div class="image-upload-area" data-plat-name="${plat.name}" data-day-num="${plat.dayNum}"><i class="fas fa-upload upload-icon"></i> Changer l'image (réelle)</div>`;
            }
            if (plat.price > 0) html += `<button class="btn-add-daily" data-name="${plat.name.replace(/"/g, '&quot;')}" data-price="${plat.price}" data-id="${plat.id}">Ajouter au panier</button>`;
            else html += `<button class="btn-add-daily" disabled style="background:#ccc;">Indisponible aujourd'hui</button>`;
            html += `</div></div>`;
        });
        container.innerHTML = html;
        document.querySelectorAll('.btn-add-daily:not([disabled])').forEach(btn => {
            btn.addEventListener('click', () => {
                addToCart(btn.getAttribute('data-id'), btn.getAttribute('data-name'), parseInt(btn.getAttribute('data-price')));
            });
        });
        if (isAdminMode) {
            document.querySelectorAll('.image-upload-area').forEach(area => {
                area.onclick = (e) => {
                    e.stopPropagation();
                    const platName = area.getAttribute('data-plat-name');
                    const dayNum = parseInt(area.getAttribute('data-day-num'));
                    const cardElement = area.closest('.food-card');
                    uploadImageForPlat(dayNum, platName, cardElement);
                };
            });
        }
    }

    // ========== PANIER ==========
    let cart = [];
    function saveCart() { localStorage.setItem("cava_cart", JSON.stringify(cart)); updateCartUI(); }
    function loadCart() { const saved = localStorage.getItem("cava_cart"); if(saved) { try { cart = JSON.parse(saved); updateCartUI(); } catch(e) {} } }
    function updateCartUI() { const count = cart.reduce((sum, item) => sum + item.quantity, 0); document.getElementById("cartCountBadge").innerText = count; if(document.getElementById("cartModal").style.display === "block") renderCartModal(); }
    function addToCart(id, name, price) { const existing = cart.find(item => item.id === id); if(existing) existing.quantity++; else cart.push({ id, name, price, quantity: 1 }); saveCart(); showNotification(`${name} ajouté au panier !`); }
    function updateQuantity(id, delta) { const idx = cart.findIndex(item => item.id == id); if(idx !== -1) { const newQty = cart[idx].quantity + delta; if(newQty <= 0) cart.splice(idx,1); else cart[idx].quantity = newQty; saveCart(); renderCartModal(); } }
    function removeItem(id) { cart = cart.filter(item => item.id != id); saveCart(); renderCartModal(); }
    function renderCartModal() {
        const container = document.getElementById("cartItemsModalList");
        if(cart.length === 0) { container.innerHTML = '<p style="text-align:center; padding:30px;">🛒 Votre panier est vide</p>'; document.getElementById("cartTotalModal").innerHTML = "Total: 0 FCFA"; return; }
        let subtotal = 0, html = "";
        cart.forEach(item => { subtotal += item.price * item.quantity; html += `<div class="cart-item-modal"><div><strong>${item.name}</strong><br>${item.price} FCFA x ${item.quantity}</div><div><button class="btn-quantity" data-id="${item.id}" data-delta="-1">-</button><span style="margin:0 8px;">${item.quantity}</span><button class="btn-quantity" data-id="${item.id}" data-delta="1">+</button><button class="btn-remove" data-id="${item.id}">🗑️ Suppr.</button></div></div>`; });
        container.innerHTML = html;
        document.getElementById("cartTotalModal").innerHTML = `<strong>Sous-total: ${subtotal.toLocaleString()} FCFA</strong><br>Livraison incluse (offerte)<br><span style="font-size:1.3rem;">Total: ${subtotal.toLocaleString()} FCFA</span>`;
        document.querySelectorAll(".btn-quantity").forEach(btn => btn.onclick = () => updateQuantity(btn.getAttribute("data-id"), parseInt(btn.getAttribute("data-delta"))));
        document.querySelectorAll(".btn-remove").forEach(btn => btn.onclick = () => removeItem(btn.getAttribute("data-id")));
    }
    function showNotification(msg) { const notif = document.getElementById("notification"); notif.textContent = msg; notif.style.display = "block"; setTimeout(() => notif.style.display = "none", 3000); }
    function openCartModal() { renderCartModal(); document.getElementById("cartModal").style.display = "block"; }
    function closeCartModal() { document.getElementById("cartModal").style.display = "none"; }
    function confirmOrderFromModal() {
        const name = document.getElementById("modalClientName").value.trim();
        const phone = document.getElementById("modalClientPhone").value.trim();
        const address = document.getElementById("modalClientAddress").value.trim();
        if (!name || !phone || !address) { showNotification("Veuillez remplir nom, téléphone et adresse."); return; }
        if (cart.length === 0) { showNotification("Panier vide."); return; }
        const total = cart.reduce((sum, i) => sum + (i.price * i.quantity), 0);
        const order = { id: Date.now(), date: new Date().toLocaleString("fr-FR", { timeZone: "Africa/Abidjan" }), client: { name, phone, address, note: document.getElementById("modalClientNote").value }, items: cart.map(i => ({ name: i.name, price: i.price, quantity: i.quantity })), total, status: "En attente", payment: "Paiement à la livraison" };
        let orders = JSON.parse(localStorage.getItem("resto_orders") || "[]");
        orders.push(order); localStorage.setItem("resto_orders", JSON.stringify(orders));
        showNotification(`Commande enregistrée ! Total: ${total} FCFA à payer à la livraison.`);
        cart = []; saveCart(); closeCartModal();
        document.getElementById("modalClientName").value = ""; document.getElementById("modalClientPhone").value = ""; document.getElementById("modalClientAddress").value = ""; document.getElementById("modalClientNote").value = "";
    }

    function generateFullMenu() {
        const container = document.getElementById("fullMenuGrid");
        let html = "";
        menuData.forEach(plat => { html += `<div class="food-card"><img class="card-img" src="${plat.image}" alt="${plat.name}" onerror="this.src='https://images.pexels.com/photos/70497/pexels-photo-70497.jpeg?auto=compress&cs=tinysrgb&w=600'"><div class="card-content"><div class="card-title"><h3>${plat.name}</h3><span class="price">${plat.price} FCFA</span></div><div class="desc">${plat.desc}</div><span class="badge">${plat.badge}</span><button class="btn-add-full" data-id="${plat.id}" data-name="${plat.name}" data-price="${plat.price}">Ajouter au panier</button></div></div>`; });
        container.innerHTML = html;
        document.querySelectorAll('.btn-add-full').forEach(btn => btn.addEventListener('click', () => addToCart(btn.getAttribute('data-id'), btn.getAttribute('data-name'), parseInt(btn.getAttribute('data-price')))));
    }

    function toggleAdminMode() { isAdminMode = !isAdminMode; const btn = document.getElementById("toggleAdminBtn"); btn.textContent = `Mode Admin: ${isAdminMode ? 'ON' : 'OFF'}`; btn.style.background = isAdminMode ? '#009245' : '#f77f00'; renderDynamicDailySpecials(); showNotification(isAdminMode ? "Mode admin activé - Cliquez pour changer les images" : "Mode admin désactivé"); }

    document.addEventListener("DOMContentLoaded", () => {
        renderDynamicDailySpecials(); generateFullMenu(); loadCart();
        document.getElementById("cartIconBtn").addEventListener("click", openCartModal);
        document.getElementById("closeModalBtn").addEventListener("click", closeCartModal);
        document.getElementById("confirmOrderModalBtn").addEventListener("click", confirmOrderFromModal);
        document.getElementById("navLocBtn").addEventListener("click", () => window.open("https://www.google.com/maps/search/?api=1&query=CAVA+Centre+artisanal+d'Abidjan", '_blank'));
        document.getElementById("openMapBtn").addEventListener("click", () => window.open("https://www.google.com/maps/search/?api=1&query=CAVA+Centre+artisanal+d'Abidjan", '_blank'));
        document.getElementById("dailySpecialsNavBtn").addEventListener("click", (e) => { e.preventDefault(); document.getElementById("dynamicDailySpecials").scrollIntoView({ behavior: 'smooth' }); renderDynamicDailySpecials(); });
        document.getElementById("toggleAdminBtn").addEventListener("click", toggleAdminMode);
        let clickCount = 0; document.querySelector(".hero").addEventListener("dblclick", () => toggleAdminMode());
        window.onclick = (event) => { if (event.target === document.getElementById("cartModal")) closeCartModal(); };
    });
</script>
</body>
</html>
