# Flask-2
from flask import Flask, url_for

app = Flask(__name__)


@app.route('/')
def home():
    user_url = url_for('user_profile', name='Sunnat')
    contact_url = url_for('contact')

    return f'''
        <h1>Bosh sahifaga xush kelibsiz!</h1>
        <p>Quyidagi sahifalarga o'tishingiz mumkin:</p>
        <ul>
            <li><a href="{user_url}">Sunnatning profili </a></li>
            <li><a href="{contact_url}">Aloqa sahifasi</a></li>
        </ul>
    '''


@app.route('/user/<name>')
def user_profile(name):
    home_url = url_for('home')
    return f'''
        <h1>Foydalanuvchi sahifasi</h1>
        <p>Salom, <strong>{name}</strong>! Profilingizga xush kelibsiz.</p>
        <hr>
        <a href="{home_url}">Bosh sahifaga qaytish</a>
    '''


@app.route('/contact')
def contact():
    home_url = url_for('home')
    return f'''
        <h1>Aloqa sahifasi</h1>
        <p>Biz bilan bog'lanish uchun: +998 50 005 26 36</p>
        <hr>
        <a href="{home_url}">Bosh sahifaga qaytish</a>
    '''


if __name__ == '__main__':
    app.run(debug=True)
