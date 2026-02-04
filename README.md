import streamlit as st
import requests
import random
from user_agent import generate_user_agent
from time import sleep

# --- إعدادات الصفحة والتصميم ---
st.set_page_config(page_title="علــش | @GX1GX1", page_icon="⚔️", layout="centered")

st.markdown("""
    <style>
    .stApp { background: #0e1117; color: white; }
    
    @keyframes pulse-gold {
        0% { transform: scale(1); box-shadow: 0 0 5px #FFD700; }
        50% { transform: scale(1.05); box-shadow: 0 0 20px #FFD700; }
        100% { transform: scale(1); box-shadow: 0 0 5px #FFD700; }
    }
    .user-avatar {
        display: block; margin: auto; border: 4px solid #FFD700;
        border-radius: 50%; animation: pulse-gold 2s infinite;
        margin-bottom: 20px;
    }

    .stButton>button {
        width: 100%; border-radius: 12px; 
        background: linear-gradient(45deg, #FFD700, #DAA520);
        color: black; font-weight: bold; border: none; height: 3.5em;
        transition: 0.3s; margin-top: 10px;
    }
    .stButton>button:hover { transform: translateY(-3px); box-shadow: 0 5px 15px rgba(255,215,0,0.4); }

    .stSelectbox div[data-baseweb="select"] { background-color: #1a1a1a; border: 1px solid #DAA520; }
    .stTextInput>div>div>input { background-color: #1a1a1a; color: #FFD700; border: 1px solid #DAA520; text-align: center; }
    
    /* تنسيقات جديدة للأقسام المضافة */
    .dev-section {
        background: linear-gradient(135deg, #1a1a1a, #2a2a2a);
        padding: 15px;
        border-radius: 10px;
        border: 2px solid #FFD700;
        margin: 10px 0;
    }
    .dev-title {
        color: #FFD700;
        text-align: center;
        font-size: 24px;
        margin-bottom: 15px;
    }
    .social-link {
        display: block;
        background: #333;
        padding: 10px;
        border-radius: 8px;
        margin: 8px 0;
        text-align: center;
        color: white;
        text-decoration: none;
        transition: 0.3s;
        border: 1px solid #555;
    }
    .social-link:hover {
        background: #444;
        border-color: #FFD700;
        transform: translateY(-2px);
    }
    </style>
    """, unsafe_allow_html=True)

# --- عرض الصورة الشخصية ---
st.markdown(f'<img src="https://i.ibb.co/cXgRkRTf/6e37bd54624a0d987f097ff5bb04a58e.jpg" class="user-avatar" width="160">', unsafe_allow_html=True)
st.markdown("<h1 style='text-align: center; color: #FFD700;'>علـــش | GX1GX1</h1>", unsafe_allow_html=True)
st.markdown("<p style='text-align: center; color: #888;'> رشق الخدمات الاجتماعية المتكاملة</p>", unsafe_allow_html=True)
st.write("---")

# --- قسم حقوق المطور ---
st.markdown("""
<div class='dev-section'>
    <div class='dev-title'>♕•المطور زيڪو الأسطورة•♕</div>
    <p style='text-align: center; color: #FFD700;'>ملك تطبيقات الرشق والتطوير</p>
</div>
""", unsafe_allow_html=True)

# --- دالة لتوليد IP عشوائي ---
def generate_random_ip():
    return ".".join(map(str, (random.randint(0, 255) for _ in range(4))))

# --- دالات الرشق الأصلية ---
def send_request(url, link, quantity=None):
    random_ip = generate_random_ip()
    headers = {
        "User-Agent": generate_user_agent(),
        "Content-Type": "application/x-www-form-urlencoded",
        "Origin": "https://leofame.com",
        "referer": url.split('?')[0],
        "cookie": "token=FAKETOKEN; cf_clearance=FAKECOOKIE",
        "X-Forwarded-For": random_ip,
        "Client-IP": random_ip
    }
    data = {
        "token": "FAKETOKEN",
        "timezone_offset": "Asia/Baghdad",
        "free_link": link
    }
    if quantity: data["quantity"] = quantity
    
    try:
        # إضافة تأخير عشوائي بين 3 إلى 7 ثوانٍ
        wait_time = random.randint(3, 7)
        st.info(f"⏳ جاري الانتظار {wait_time} ثوانٍ لتجنب الحظر...")
        sleep(wait_time)
        
        r = requests.post(url, headers=headers, data=data)
        if "Please wait" in r.text or '"error":' in r.text:
            st.error("⚠️ الموقع يطلب الانتظار. جرب لاحقاً أو غير الرابط.")
        else:
            st.success(f"✅ تم الإرسال بنجاح بـ IP وهمي: {random_ip}")
    except Exception as e:
        st.error(f"حدث خطأ في الاتصال: {e}")

# --- الأقسام الجديدة ---
st.markdown("## 📈 أقسام زيادة المتابعين والمشاهدات")

# قسم زيادة متابعين تيك توك
with st.expander("🚀 زيادة متابعين تيك توك", expanded=False):
    tiktok_followers_url = st.text_input("رابط حساب التيك توك:", placeholder="https://www.tiktok.com/@username", key="tiktok_followers")
    if st.button("بدء زيادة المتابعين", key="btn_tiktok_followers"):
        if tiktok_followers_url:
            st.info("🔗 يتم التوجيه إلى الموقع الرسمي لزيادة المتابعين...")
            st.markdown(f"[زيارة موقع زيادة المتابعين](https://leofame.com/ar/free-tiktok-followers)")
        else:
            st.warning("يرجى إدخال رابط حساب التيك توك")

# قسم زيادة متابعين انستا
with st.expander("📷 زيادة متابعين انستجرام", expanded=False):
    insta_followers_url = st.text_input("رابط حساب الانستجرام:", placeholder="https://www.instagram.com/username/", key="insta_followers")
    if st.button("بدء زيادة المتابعين", key="btn_insta_followers"):
        if insta_followers_url:
            st.info("🔗 يتم التوجيه إلى الموقع الرسمي لزيادة المتابعين...")
            st.markdown(f"[زيارة موقع زيادة المتابعين](https://leofame.com/ar/free-instagram-followers)")
        else:
            st.warning("يرجى إدخال رابط حساب الانستجرام")

# قسم زيادة لايكات انستا
with st.expander("❤️ زيادة لايكات انستجرام", expanded=False):
    insta_likes_url = st.text_input("رابط منشور الانستجرام:", placeholder="https://www.instagram.com/p/...", key="insta_likes")
    if st.button("بدء زيادة اللايكات", key="btn_insta_likes"):
        if insta_likes_url:
            st.info("🔗 يتم التوجيه إلى الموقع الرسمي لزيادة اللايكات...")
            st.markdown(f"[زيارة موقع زيادة اللايكات](https://leofame.com/ar/free-instagram-likes)")
        else:
            st.warning("يرجى إدخال رابط منشور الانستجرام")

# قسم زيادة مشاهدات انستا
with st.expander("👁️ زيادة مشاهدات انستجرام", expanded=False):
    insta_views_url = st.text_input("رابط قصة أو رييل الانستجرام:", placeholder="https://www.instagram.com/reel/...", key="insta_views")
    if st.button("بدء زيادة المشاهدات", key="btn_insta_views"):
        if insta_views_url:
            st.info("🔗 يتم التوجيه إلى الموقع الرسمي لزيادة المشاهدات...")
            st.markdown(f"[زيارة موقع زيادة المشاهدات](https://leofame.com/ar/free-instagram-views)")
        else:
            st.warning("يرجى إدخال رابط القصة أو الريل")

st.write("---")

# --- قسم معلومات المطور ---
st.markdown("## 👑 معلومات المطور والاتصال")

if st.button("📞 عرض معلومات المطور", key="btn_developer_info"):
    st.markdown("""
    <div class='dev-section'>
        <h3 style='color: #FFD700; text-align: center;'>♕ زيڪو الأسطورة ♕</h3>
        
        <h4 style='color: #DAA520;'>وسائل التواصل:</h4>
        <a href='https://wa.me/967771620853' class='social-link' target='_blank'>
            📱 واتساب المطور: 967771620853
        </a>
        
        <a href='https://t.me/W_78_22' class='social-link' target='_blank'>
            📢 قناة التليجرام الرئيسية
        </a>
        
        <a href='https://t.me/W_78_23' class='social-link' target='_blank'>
            📢 قناة التليجرام الثانوية
        </a>
        
        <a href='https://whatsapp.com/channel/0029Vb0wuwm1NCrcTkRUEP02' class='social-link' target='_blank'>
            📱 قناة الواتساب
        </a>
        
        <a href='https://tiktok.com/@zhddbv' class='social-link' target='_blank'>
            🎵 حساب التيك توك
        </a>
        
        <h4 style='color: #DAA520; margin-top: 20px;'>المواقع الرسمية:</h4>
        <a href='https://leofame.com/ar/free-tiktok-followers' class='social-link' target='_blank'>
            🌐 زيادة متابعين تيك توك
        </a>
        
        <a href='https://leofame.com/ar/free-instagram-followers' class='social-link' target='_blank'>
            🌐 زيادة متابعين انستجرام
        </a>
        
        <a href='https://leofame.com/ar/free-instagram-likes' class='social-link' target='_blank'>
            🌐 زيادة لايكات انستجرام
        </a>
        
        <a href='https://leofame.com/ar/free-instagram-views' class='social-link' target='_blank'>
            🌐 زيادة مشاهدات انستجرام
        </a>
    </div>
    """, unsafe_allow_html=True)

st.write("---")

# --- واجهة الاختيار الأصلية ---
st.markdown("## ⚔️ الخدمات الأصلية")
option = st.selectbox(
    "اختر الخدمة المطلوبة:",
    ["إعجابات يوتيوب", "إعجابات تيك توك", "حفظ منشور إنستغرام", "مشاهدات تيك توك"]
)

video_url = st.text_input("ضع الرابط هنا 👇", placeholder="https://...")

if st.button("بدأ", key="btn_main"):
    if video_url:
        with st.spinner('جاري معالجة الطلب...'):
            if option == "إعجابات يوتيوب":
                send_request("https://leofame.com/free-youtube-likes?api=1", video_url)
            elif option == "إعجابات تيك توك":
                send_request("https://leofame.com/free-tiktok-likes?api=1", video_url)
            elif option == "حفظ منشور إنستغرام":
                send_request("https://leofame.com/free-instagram-saves?api=1", video_url, "30")
            elif option == "مشاهدات تيك توك":
                send_request("https://leofame.com/ar/free-tiktok-views?api=1", video_url, "200")
    else:
        st.warning("يرجى إدخال الرابط أولاً!")

st.write("---")
st.markdown("<p style='text-align: center; font-size: 12px; color: #555;'>تم التطوير بواسطة علش @GX1GX1 | ♕ زيڪو الأسطورة ♕</p>", unsafe_allow_html=True)
