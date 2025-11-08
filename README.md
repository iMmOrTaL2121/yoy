# BlockRide

A decentralized ride-sharing application built on blockchain technology, combining smart contracts, IPFS storage, and real-time WebSocket communication.

## 🚀 Features

- **Blockchain-Based Ride Sharing**: Secure and transparent ride matching using Ethereum smart contracts
- **Payment Escrow System**: Automated payment handling with escrow functionality
- **Rating System**: 1-5 star ratings for drivers and riders
- **Real-Time Communication**: WebSocket-based messaging between users
- **IPFS Integration**: Decentralized storage for user data and ride information
- **MetaMask Integration**: Web3 wallet connection for blockchain interactions
- **User Profiles**: Comprehensive user management and profile system
- **Ride Management**: Complete ride lifecycle tracking from creation to completion

## 📋 Prerequisites

- **Node.js** 16+ and npm
- **Python** 3.8+
- **MetaMask** browser extension
- **Truffle** or **Hardhat** for smart contract deployment (optional)
- **Infura** or **Alchemy** account for IPFS and blockchain access (optional)

## 🏃 Quick Start

The application works **immediately** without any configuration! It will automatically use localStorage as a fallback if IPFS credentials aren't configured.

### Step 1: Start the Backend

```bash
cd BlockRide_Backend
python manage.py runserver
```

The backend will run on `http://localhost:8000`

### Step 2: Start the Frontend

```bash
cd BlockRide_Frontend
npm install
npm start
```

The frontend will run on `http://localhost:3000`

### Step 3: Use the Application!

1. Open `http://localhost:3000` in your browser
2. Connect MetaMask (if you have it installed)
3. Sign up with your details
4. Start using the app!

## ✅ What Works Without Configuration

- ✅ User signup and login
- ✅ Ride sharing (driver offers)
- ✅ Ride receiving (rider requests)
- ✅ Real-time messaging via WebSocket
- ✅ User profiles
- ✅ All features work with localStorage fallback

## 🔧 Installation & Setup

### Backend Setup (Django)

```bash
cd BlockRide_Backend

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py makemigrations
python manage.py migrate

# Create superuser (optional)
python manage.py createsuperuser

# Run server
python manage.py runserver
```

### Frontend Setup (React)

```bash
cd BlockRide_Frontend

# Install dependencies
npm install --legacy-peer-deps

# Start development server
npm start
```

## ⚙️ Configuration

### Optional: Configure IPFS (For Better Data Persistence)

If you want to use IPFS for decentralized storage:

1. **Get Infura Credentials** (Free):
   - Go to [https://infura.io/](https://infura.io/)
   - Sign up and create an IPFS project
   - Copy your Project ID and Secret

2. **Create `.env` file** in `BlockRide_Frontend` directory:
   ```
   REACT_APP_INFURA_PROJECT_ID=your-project-id
   REACT_APP_INFURA_PROJECT_SECRET=your-project-secret
   ```

3. **Restart the React server**:
   ```bash
   npm start
   ```

**Note**: The app works perfectly fine without IPFS! It will use localStorage instead.

### Environment Variables

#### Frontend (.env)
```
REACT_APP_CONTRACT_ADDRESS=0x... (optional)
REACT_APP_INFURA_PROJECT_ID=your_project_id (optional)
REACT_APP_INFURA_PROJECT_SECRET=your_project_secret (optional)
```

#### Backend (settings.py)
```python
DEBUG = False  # Set to False in production
ALLOWED_HOSTS = ['your-domain.com']  # Update for production
SECRET_KEY = 'your-secret-key'  # Change in production
```

## 🏭 Production Deployment

### Smart Contract Deployment

#### Using Hardhat (Recommended)

```bash
# Install Hardhat
npm install --save-dev hardhat

# Initialize Hardhat project
npx hardhat init

# Deploy contract
npx hardhat run scripts/deploy.js --network <network>
```

#### Using Truffle

```bash
# Install Truffle
npm install -g truffle

# Compile contract
truffle compile

# Deploy contract
truffle migrate --network <network>
```

#### Update Contract Address

After deployment, update the contract address in:
- `BlockRide_Frontend/src/Web3 Handler/contract_production.js`
- Set environment variable: `REACT_APP_CONTRACT_ADDRESS=<deployed_address>`

### Production Build

#### Frontend

```bash
cd BlockRide_Frontend
npm run build
```

#### Backend

```bash
cd BlockRide_Backend
python manage.py collectstatic
```

## 📝 Smart Contract Features

### Production Contract Features

1. **Payment System**
   - Escrow for ride payments
   - Automatic payment release on completion
   - Refund on cancellation
   - Platform fee collection

2. **Rating System**
   - 1-5 star ratings
   - Average rating calculation
   - Rating history

3. **Ride Management**
   - Ride status tracking
   - Ride history
   - Dispute resolution

4. **Access Control**
   - User authorization
   - Owner-only functions
   - Registration control

## 🧪 Testing

### Test Smart Contract

```bash
# Run tests
npx hardhat test
# or
truffle test
```

### Test Backend

```bash
cd BlockRide_Backend
python manage.py test
```

### Test Frontend

```bash
cd BlockRide_Frontend
npm test
```

## 🚨 Troubleshooting

### Signup Page Stuck?

**Fixed!** The signup page now:
- Works even without IPFS credentials
- Works even without contract deployment
- Shows clear error messages
- Never gets stuck in loading state

### IPFS Authentication Error?

**No problem!** The app automatically:
- Detects missing/invalid credentials
- Falls back to localStorage
- Continues working normally
- Shows a warning in console (not an error)

### Contract Not Deployed?

**Works anyway!** The app:
- Detects if contract isn't deployed
- Uses localStorage for data storage
- All features work normally
- You can deploy contract later

### MetaMask Connection Issues

- Ensure MetaMask is unlocked
- Check network matches contract network
- Clear browser cache

### Network Access Issues

For network access (accessing from other devices):

**Backend:**
```bash
python manage.py runserver 0.0.0.0:8000
```

**Frontend:**
```bash
npm run start:network
# or on Unix/Mac
npm run start:network:unix
```

## 🔐 Security Considerations

1. **Smart Contract**
   - Review contract code before deployment
   - Test on testnet first
   - Set appropriate platform fees
   - Implement access controls

2. **Backend**
   - Use strong SECRET_KEY
   - Enable HTTPS
   - Configure CORS properly
   - Use environment variables for secrets

3. **Frontend**
   - Never expose private keys
   - Validate all user inputs
   - Handle errors gracefully
   - Use HTTPS in production

## 📊 Project Structure

```
Block Ride/
├── BlockRide_Backend/          # Django backend
│   ├── BlockRide_App/          # Main Django app
│   ├── BlockRide_Settings/     # Django settings
│   ├── manage.py
│   └── requirements.txt
├── BlockRide_Frontend/         # React frontend
│   ├── src/
│   │   ├── components/         # React components
│   │   ├── Pages/              # Page components
│   │   ├── Web3 Handler/       # Blockchain integration
│   │   └── config/             # Configuration files
│   └── package.json
├── contracts/                  # Smart contracts
│   ├── BlockRide.sol
│   └── BlockRide_production.sol
└── README.md
```

## 📚 Technology Stack

- **Frontend**: React 18, Web3.js, Bootstrap, React Router
- **Backend**: Django 4.2, Django Channels (WebSocket), SQLite
- **Blockchain**: Solidity, Ethereum, MetaMask
- **Storage**: IPFS (via Infura), localStorage fallback
- **Real-time**: WebSocket (Django Channels)

## 🆘 Support

For issues or questions:
1. Check the troubleshooting section above
2. Review contract and code documentation
3. Check browser console for detailed error messages
4. All errors are handled gracefully with fallbacks

## 📄 License

This project is part of the BlockRide application.

---

**Note**: Always test thoroughly on testnet before deploying to mainnet!

**You're all set! The application is ready to use right now!** 🎉

