<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SmartVoice ATM | Fully Functional Voice Banking</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-blue: #2563eb;
            --blue-dark: #1e40af;
            --blue-light: #3b82f6;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --dark-bg: #0f172a;
            --darker-bg: #0a0f1e;
            --card-bg: #1e293b;
            --text-light: #f1f5f9;
            --text-muted: #94a3b8;
            --glass-bg: rgba(255, 255, 255, 0.05);
            --glass-border: rgba(255, 255, 255, 0.1);
            --shadow-lg: 0 20px 40px rgba(0, 0, 0, 0.3);
            --shadow-md: 0 10px 20px rgba(0, 0, 0, 0.2);
            --radius-lg: 24px;
            --radius-md: 16px;
            --radius-sm: 12px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--darker-bg) 0%, var(--dark-bg) 100%);
            color: var(--text-light);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        /* Background Animation */
        .gradient-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: 
                radial-gradient(circle at 20% 80%, rgba(37, 99, 235, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(16, 185, 129, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(245, 158, 11, 0.05) 0%, transparent 50%);
        }

        .noise-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 400 400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.02'/%3E%3C/svg%3E");
            z-index: -1;
            opacity: 0.3;
        }

        /* Main Container */
        .container {
            width: 100%;
            max-width: 1400px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 30px;
        }

        /* Header */
        .header {
            text-align: center;
            padding: 30px;
            width: 100%;
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: var(--radius-lg);
            box-shadow: var(--shadow-lg);
        }

        .header h1 {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--primary-blue), var(--success));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 10px;
        }

        .subtitle {
            font-size: 1.2rem;
            color: var(--text-muted);
            max-width: 800px;
            margin: 0 auto;
        }

        /* Status Indicator */
        .status-indicator {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 12px 24px;
            background: rgba(16, 185, 129, 0.2);
            border-radius: 50px;
            margin-top: 20px;
            border: 2px solid rgba(16, 185, 129, 0.3);
        }

        .status-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--success);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        /* Main ATM Interface */
        .atm-interface {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            width: 100%;
        }

        @media (max-width: 1024px) {
            .atm-interface {
                grid-template-columns: 1fr;
                max-width: 800px;
            }
        }

        /* ATM Screen Panel */
        .atm-panel {
            background: var(--card-bg);
            border-radius: var(--radius-lg);
            padding: 40px;
            box-shadow: var(--shadow-lg);
            display: flex;
            flex-direction: column;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .screen-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.05);
        }

        .bank-logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .bank-logo i {
            font-size: 2.5rem;
            color: var(--primary-blue);
        }

        .bank-logo h2 {
            font-size: 2rem;
            font-weight: 700;
        }

        .balance-display {
            text-align: right;
        }

        .balance-label {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 5px;
        }

        .balance-amount {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--success);
        }

        /* Main Display */
        .main-display {
            flex: 1;
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--radius-md);
            padding: 30px;
            margin-bottom: 30px;
            border: 2px solid rgba(255, 255, 255, 0.05);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            min-height: 300px;
        }

        .welcome-screen {
            animation: fadeIn 0.5s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .welcome-icon {
            font-size: 4rem;
            margin-bottom: 25px;
            color: var(--primary-blue);
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        .screen-title {
            font-size: 2.2rem;
            font-weight: 700;
            margin-bottom: 15px;
            background: linear-gradient(135deg, var(--text-light), var(--primary-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .screen-message {
            font-size: 1.2rem;
            color: var(--text-muted);
            line-height: 1.6;
            max-width: 500px;
            margin: 0 auto;
        }

        .voice-prompt {
            background: rgba(37, 99, 235, 0.1);
            border-radius: var(--radius-md);
            padding: 20px;
            margin-top: 30px;
            border-left: 4px solid var(--primary-blue);
            animation: glow 2s infinite alternate;
        }

        @keyframes glow {
            from { box-shadow: 0 0 10px rgba(37, 99, 235, 0.2); }
            to { box-shadow: 0 0 20px rgba(37, 99, 235, 0.4); }
        }

        .prompt-text {
            font-size: 1.4rem;
            font-weight: 600;
            color: var(--primary-blue);
            margin-bottom: 10px;
        }

        .prompt-hint {
            font-size: 1rem;
            color: var(--text-muted);
        }

        /* Amount Input Display */
        .amount-display {
            display: none;
            width: 100%;
            text-align: center;
        }

        .amount-input {
            font-size: 4rem;
            font-weight: 800;
            margin: 30px 0;
            color: var(--text-light);
            min-height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }

        .amount-input .digit {
            background: rgba(255, 255, 255, 0.05);
            padding: 10px 20px;
            border-radius: var(--radius-md);
            min-width: 80px;
            text-align: center;
            border: 2px solid rgba(255, 255, 255, 0.1);
        }

        .amount-input .currency {
            font-size: 2rem;
            color: var(--text-muted);
        }

        .amount-instruction {
            font-size: 1.2rem;
            color: var(--text-muted);
            margin-bottom: 30px;
        }

        /* Transaction Screen */
        .transaction-screen {
            display: none;
            width: 100%;
            text-align: center;
        }

        .transaction-icon {
            font-size: 4rem;
            margin-bottom: 25px;
            color: var(--success);
        }

        .transaction-amount {
            font-size: 5rem;
            font-weight: 800;
            margin: 30px 0;
            color: var(--success);
        }

        .transaction-message {
            font-size: 1.3rem;
            color: var(--text-light);
            line-height: 1.6;
        }

        /* Control Panel */
        .control-panel {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-top: 30px;
        }

        .control-button {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--radius-md);
            padding: 25px 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            color: var(--text-light);
            font-weight: 600;
            font-size: 1.1rem;
        }

        .control-button:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-5px);
            border-color: var(--primary-blue);
            box-shadow: var(--shadow-md);
        }

        .control-button i {
            font-size: 2.5rem;
            color: var(--primary-blue);
        }

        .control-button.withdraw i { color: var(--danger); }
        .control-button.deposit i { color: var(--success); }
        .control-button.balance i { color: var(--warning); }

        /* Keypad Panel */
        .keypad-panel {
            background: var(--card-bg);
            border-radius: var(--radius-lg);
            padding: 40px;
            box-shadow: var(--shadow-lg);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .keypad-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 30px;
        }

        .keypad-header i {
            font-size: 2.5rem;
            color: var(--primary-blue);
        }

        .keypad-header h2 {
            font-size: 1.8rem;
            font-weight: 700;
        }

        /* Functional Keypad */
        .keypad {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-bottom: 30px;
        }

        .key {
            aspect-ratio: 1;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--radius-md);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s ease;
            color: var(--text-light);
            user-select: none;
        }

        .key:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-3px);
            border-color: var(--primary-blue);
        }

        .key:active {
            transform: translateY(1px);
            background: rgba(255, 255, 255, 0.15);
        }

        .key.clear {
            grid-column: span 2;
            aspect-ratio: auto;
            background: rgba(239, 68, 68, 0.1);
            border-color: rgba(239, 68, 68, 0.3);
        }

        .key.clear:hover {
            background: rgba(239, 68, 68, 0.2);
            border-color: var(--danger);
        }

        .key.enter {
            background: rgba(16, 185, 129, 0.1);
            border-color: rgba(16, 185, 129, 0.3);
        }

        .key.enter:hover {
            background: rgba(16, 185, 129, 0.2);
            border-color: var(--success);
        }

        /* Function Buttons */
        .function-buttons {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
        }

        .function-button {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--radius-md);
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            color: var(--text-light);
            font-weight: 600;
            font-size: 1.2rem;
        }

        .function-button:hover {
            background: rgba(255, 255, 255, 0.1);
            transform: translateY(-5px);
            box-shadow: var(--shadow-md);
        }

        .function-button i {
            font-size: 1.8rem;
        }

        .function-button.withdraw {
            background: rgba(239, 68, 68, 0.1);
            border-color: rgba(239, 68, 68, 0.3);
        }

        .function-button.withdraw:hover {
            background: rgba(239, 68, 68, 0.2);
            border-color: var(--danger);
        }

        .function-button.deposit {
            background: rgba(16, 185, 129, 0.1);
            border-color: rgba(16, 185, 129, 0.3);
        }

        .function-button.deposit:hover {
            background: rgba(16, 185, 129, 0.2);
            border-color: var(--success);
        }

        /* Voice Control Panel */
        .voice-panel {
            background: var(--card-bg);
            border-radius: var(--radius-lg);
            padding: 40px;
            box-shadow: var(--shadow-lg);
            border: 1px solid rgba(255, 255, 255, 0.05);
            margin-top: 30px;
            width: 100%;
        }

        .voice-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 25px;
        }

        .voice-header i {
            font-size: 2.5rem;
            color: var(--primary-blue);
        }

        .voice-header h2 {
            font-size: 1.8rem;
            font-weight: 700;
        }

        /* Voice Activity */
        .voice-activity {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 30px;
        }

        .voice-indicator {
            flex: 1;
            height: 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .voice-level {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--danger), var(--warning), var(--success));
            border-radius: 10px;
            transition: width 0.1s ease;
        }

        .voice-status {
            padding: 12px 24px;
            background: rgba(16, 185, 129, 0.1);
            border-radius: 50px;
            font-weight: 600;
            color: var(--success);
            border: 2px solid rgba(16, 185, 129, 0.3);
            min-width: 160px;
            text-align: center;
        }

        .voice-status.listening {
            background: rgba(37, 99, 235, 0.1);
            color: var(--primary-blue);
            border-color: rgba(37, 99, 235, 0.3);
            animation: pulse 1.5s infinite;
        }

        /* Voice Conversation */
        .voice-conversation {
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--radius-md);
            padding: 25px;
            max-height: 300px;
            overflow-y: auto;
            border: 2px solid rgba(255, 255, 255, 0.05);
        }

        .conversation-item {
            margin-bottom: 20px;
            padding-bottom: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }

        .conversation-item:last-child {
            margin-bottom: 0;
            padding-bottom: 0;
            border-bottom: none;
        }

        .speaker {
            font-weight: 700;
            margin-bottom: 8px;
        }

        .speaker.user {
            color: var(--primary-blue);
        }

        .speaker.atm {
            color: var(--success);
        }

        .message {
            color: var(--text-light);
            line-height: 1.5;
        }

        /* Microphone Permission Modal */
        .permission-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(15, 23, 42, 0.95);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            backdrop-filter: blur(10px);
        }

        .modal-content {
            background: var(--card-bg);
            border-radius: var(--radius-lg);
            padding: 50px;
            max-width: 600px;
            text-align: center;
            border: 1px solid var(--glass-border);
            box-shadow: var(--shadow-lg);
            animation: modalAppear 0.3s ease-out;
        }

        @keyframes modalAppear {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        .modal-icon {
            font-size: 5rem;
            color: var(--primary-blue);
            margin-bottom: 30px;
            animation: bounce 2s infinite;
        }

        .modal-content h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            font-weight: 700;
        }

        .modal-content p {
            font-size: 1.2rem;
            color: var(--text-muted);
            line-height: 1.6;
            margin-bottom: 30px;
        }

        .permission-button {
            background: linear-gradient(135deg, var(--primary-blue), var(--blue-dark));
            border: none;
            border-radius: var(--radius-md);
            color: white;
            font-weight: 600;
            font-size: 1.2rem;
            padding: 18px 40px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin: 30px auto 0;
        }

        .permission-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(37, 99, 235, 0.3);
        }

        /* Quick Amount Buttons */
        .quick-amounts {
            display: flex;
            gap: 15px;
            margin: 30px 0;
            justify-content: center;
            flex-wrap: wrap;
        }

        .quick-amount {
            padding: 12px 25px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: var(--radius-md);
            cursor: pointer;
            transition: all 0.2s ease;
            font-weight: 600;
            color: var(--text-light);
        }

        .quick-amount:hover {
            background: rgba(37, 99, 235, 0.1);
            border-color: var(--primary-blue);
        }

        /* Transaction History */
        .transaction-history {
            background: rgba(0, 0, 0, 0.2);
            border-radius: var(--radius-md);
            padding: 25px;
            margin-top: 30px;
        }

        .history-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .history-list {
            max-height: 200px;
            overflow-y: auto;
        }

        .history-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: var(--radius-sm);
            margin-bottom: 10px;
            border-left: 4px solid;
        }

        .history-item.withdrawal {
            border-left-color: var(--danger);
        }

        .history-item.deposit {
            border-left-color: var(--success);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .atm-interface {
                gap: 20px;
            }
            
            .header h1 {
                font-size: 2.2rem;
            }
            
            .screen-title {
                font-size: 1.8rem;
            }
            
            .amount-input {
                font-size: 3rem;
            }
            
            .transaction-amount {
                font-size: 3.5rem;
            }
            
            .control-panel {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="gradient-bg"></div>
    <div class="noise-overlay"></div>

    <!-- Microphone Permission Modal -->
    <div class="permission-modal" id="permissionModal">
        <div class="modal-content">
            <div class="modal-icon">
                <i class="fas fa-microphone-alt"></i>
            </div>
            <h2>Enable Voice Control</h2>
            <p>This ATM uses automatic voice recognition for hands-free operation. Please allow microphone access to begin.</p>
            
            <div style="text-align: left; margin: 30px 0; padding: 25px; background: rgba(0,0,0,0.2); border-radius: var(--radius-md);">
                <p style="margin-bottom: 15px; font-weight: 600; color: var(--primary-blue);">What happens when you allow:</p>
                <ul style="list-style: none; padding-left: 0;">
                    <li style="margin-bottom: 12px; display: flex; align-items: center; gap: 12px;">
                        <i class="fas fa-check-circle" style="color: var(--success);"></i>
                        <span>Voice system starts automatically</span>
                    </li>
                    <li style="margin-bottom: 12px; display: flex; align-items: center; gap: 12px;">
                        <i class="fas fa-check-circle" style="color: var(--success);"></i>
                        <span>Speak commands like "withdraw $200" or "check balance"</span>
                    </li>
                    <li style="margin-bottom: 12px; display: flex; align-items: center; gap: 12px;">
                        <i class="fas fa-check-circle" style="color: var(--success);"></i>
                        <span>All buttons also work for manual control</span>
                    </li>
                </ul>
            </div>
            
            <button class="permission-button" id="enableMicrophone">
                <i class="fas fa-microphone"></i>
                ENABLE MICROPHONE
            </button>
            
            <p style="margin-top: 25px; font-size: 0.9rem; color: var(--text-muted);">
                If no prompt appears, check browser settings or refresh the page
            </p>
        </div>
    </div>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1><i class="fas fa-universal-access"></i> SmartVoice ATM</h1>
            <p class="subtitle">Fully functional banking with automatic voice control and manual keypad. Speak commands or use buttons.</p>
            <div class="status-indicator" id="statusIndicator">
                <div class="status-dot"></div>
                <span id="statusText">Voice System Initializing...</span>
            </div>
        </div>

        <!-- Main ATM Interface -->
        <div class="atm-interface">
            <!-- ATM Screen Panel -->
            <div class="atm-panel">
                <div class="screen-header">
                    <div class="bank-logo">
                        <i class="fas fa-universal-access"></i>
                        <h2>SmartVoice Bank</h2>
                    </div>
                    <div class="balance-display">
                        <div class="balance-label">Available Balance</div>
                        <div class="balance-amount" id="currentBalance">$2,500.00</div>
                    </div>
                </div>

                <!-- Main Display -->
                <div class="main-display">
                    <!-- Welcome Screen -->
                    <div class="welcome-screen" id="welcomeScreen">
                        <div class="welcome-icon">
                            <i class="fas fa-microphone-alt"></i>
                        </div>
                        <div class="screen-title">Welcome to SmartVoice ATM</div>
                        <div class="screen-message">
                            Use voice commands or manual controls to perform transactions.
                            <br>Speak naturally or use the keypad below.
                        </div>
                        
                        <div class="voice-prompt">
                            <div class="prompt-text">Try saying: "Withdraw $200" or "Check my balance"</div>
                            <div class="prompt-hint">Speak clearly into your microphone</div>
                        </div>
                    </div>

                    <!-- Amount Input Screen -->
                    <div class="amount-display" id="amountScreen">
                        <div class="screen-title" id="amountTitle">Enter Amount</div>
                        <div class="amount-input" id="amountInput">
                            <span class="currency">$</span>
                            <span class="digit" id="amountValue">0</span>
                        </div>
                        <div class="amount-instruction" id="amountInstruction">
                            Enter amount using keypad or voice, then press ENTER
                        </div>
                        
                        <!-- Quick Amount Buttons -->
                        <div class="quick-amounts" id="quickAmounts">
                            <!-- Will be populated by JavaScript -->
                        </div>
                    </div>

                    <!-- Transaction Screen -->
                    <div class="transaction-screen" id="transactionScreen">
                        <div class="transaction-icon" id="transactionIcon">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <div class="screen-title" id="transactionTitle">Transaction Complete</div>
                        <div class="transaction-amount" id="transactionAmount">$0.00</div>
                        <div class="transaction-message" id="transactionMessage"></div>
                    </div>
                </div>

                <!-- Control Panel -->
                <div class="control-panel">
                    <div class="control-button withdraw" onclick="startWithdrawal()">
                        <i class="fas fa-money-bill-wave"></i>
                        <span>Withdraw</span>
                    </div>
                    <div class="control-button deposit" onclick="startDeposit()">
                        <i class="fas fa-coins"></i>
                        <span>Deposit</span>
                    </div>
                    <div class="control-button balance" onclick="checkBalance()">
                        <i class="fas fa-balance-scale"></i>
                        <span>Balance</span>
                    </div>
                    <div class="control-button" onclick="setPin()">
                        <i class="fas fa-key"></i>
                        <span>Set PIN</span>
                    </div>
                    <div class="control-button" onclick="showHistory()">
                        <i class="fas fa-history"></i>
                        <span>History</span>
                    </div>
                    <div class="control-button" onclick="showHelp()">
                        <i class="fas fa-question-circle"></i>
                        <span>Help</span>
                    </div>
                </div>

                <!-- Transaction History -->
                <div class="transaction-history" id="historyPanel" style="display: none;">
                    <div class="history-header">
                        <h3>Recent Transactions</h3>
                        <button onclick="hideHistory()" style="background: none; border: none; color: var(--text-muted); cursor: pointer;">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    <div class="history-list" id="historyList">
                        <!-- History will be populated by JavaScript -->
                    </div>
                </div>
            </div>

            <!-- Keypad Panel -->
            <div class="keypad-panel">
                <div class="keypad-header">
                    <i class="fas fa-keyboard"></i>
                    <h2>Transaction Keypad</h2>
                </div>

                <!-- Functional Keypad -->
                <div class="keypad">
                    <div class="key" onclick="addDigit('1')">1</div>
                    <div class="key" onclick="addDigit('2')">2</div>
                    <div class="key" onclick="addDigit('3')">3</div>
                    <div class="key" onclick="addDigit('4')">4</div>
                    <div class="key" onclick="addDigit('5')">5</div>
                    <div class="key" onclick="addDigit('6')">6</div>
                    <div class="key" onclick="addDigit('7')">7</div>
                    <div class="key" onclick="addDigit('8')">8</div>
                    <div class="key" onclick="addDigit('9')">9</div>
                    <div class="key clear" onclick="clearAmount()">CLEAR</div>
                    <div class="key" onclick="addDigit('0')">0</div>
                    <div class="key enter" onclick="submitAmount()">ENTER</div>
                </div>

                <!-- Function Buttons -->
                <div class="function-buttons">
                    <div class="function-button withdraw" onclick="startWithdrawal()">
                        <i class="fas fa-money-bill-wave"></i>
                        <span>WITHDRAW CASH</span>
                    </div>
                    <div class="function-button deposit" onclick="startDeposit()">
                        <i class="fas fa-coins"></i>
                        <span>DEPOSIT FUNDS</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Voice Control Panel -->
        <div class="voice-panel">
            <div class="voice-header">
                <i class="fas fa-robot"></i>
                <h2>Voice Control System</h2>
            </div>
            
            <div class="voice-activity">
                <div class="voice-indicator">
                    <div class="voice-level" id="voiceLevel"></div>
                </div>
                <div class="voice-status" id="voiceStatus">
                    INITIALIZING...
                </div>
            </div>
            
            <div class="voice-conversation" id="voiceConversation">
                <div class="conversation-item">
                    <div class="speaker atm">ATM:</div>
                    <div class="message">Voice system loading. Please wait...</div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ATM State
        const atmState = {
            balance: 2500.00,
            isListening: false,
            speechRecognizer: null,
            currentMode: 'welcome', // welcome, withdrawal, deposit, balance, pin
            currentAmount: '',
            voiceEnabled: true,
            transactions: [
                { type: 'withdrawal', amount: 100, date: 'Today', time: '10:30 AM', description: 'Cash withdrawal' },
                { type: 'deposit', amount: 500, date: 'Yesterday', time: '2:15 PM', description: 'Check deposit' },
                { type: 'withdrawal', amount: 50, date: 'Oct 3', time: '4:45 PM', description: 'Store purchase' }
            ]
        };

        // DOM Elements
        const permissionModal = document.getElementById('permissionModal');
        const enableMicrophoneBtn = document.getElementById('enableMicrophone');
        const statusIndicator = document.getElementById('statusIndicator');
        const statusText = document.getElementById('statusText');
        const currentBalance = document.getElementById('currentBalance');
        const welcomeScreen = document.getElementById('welcomeScreen');
        const amountScreen = document.getElementById('amountScreen');
        const amountValue = document.getElementById('amountValue');
        const amountTitle = document.getElementById('amountTitle');
        const amountInstruction = document.getElementById('amountInstruction');
        const quickAmounts = document.getElementById('quickAmounts');
        const transactionScreen = document.getElementById('transactionScreen');
        const transactionTitle = document.getElementById('transactionTitle');
        const transactionAmount = document.getElementById('transactionAmount');
        const transactionMessage = document.getElementById('transactionMessage');
        const transactionIcon = document.getElementById('transactionIcon');
        const voiceLevel = document.getElementById('voiceLevel');
        const voiceStatus = document.getElementById('voiceStatus');
        const voiceConversation = document.getElementById('voiceConversation');
        const historyPanel = document.getElementById('historyPanel');
        const historyList = document.getElementById('historyList');

        // Quick amounts for withdrawals/deposits
        const quickAmountOptions = [20, 50, 100, 200, 500];

        // Initialize ATM
        document.addEventListener('DOMContentLoaded', () => {
            // Setup microphone permission button
            enableMicrophoneBtn.addEventListener('click', initializeVoiceSystem);
            
            // Load transaction history
            renderTransactionHistory();
            
            // Try to auto-initialize voice system after a short delay
            setTimeout(() => {
                if (!atmState.speechRecognizer) {
                    initializeVoiceSystem();
                }
            }, 1000);
        });

        // Initialize Voice System
        function initializeVoiceSystem() {
            const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
            
            if (!SpeechRecognition) {
                showMessage("Voice recognition is not supported in your browser. Please use Chrome or Edge for best experience.");
                statusText.textContent = "Voice Not Supported";
                statusIndicator.style.background = "rgba(239, 68, 68, 0.2)";
                statusIndicator.style.borderColor = "rgba(239, 68, 68, 0.3)";
                return;
            }
            
            // Hide permission modal
            permissionModal.style.opacity = '0';
            setTimeout(() => {
                permissionModal.style.display = 'none';
            }, 300);
            
            // Create speech recognizer
            atmState.speechRecognizer = new SpeechRecognition();
            atmState.speechRecognizer.continuous = true;
            atmState.speechRecognizer.interimResults = false;
            atmState.speechRecognizer.lang = 'en-US';
            atmState.speechRecognizer.maxAlternatives = 3;
            
            // Event handlers
            atmState.speechRecognizer.onstart = () => {
                updateVoiceStatus(true);
                atmState.isListening = true;
                addConversation("ATM", "Voice system activated. I'm listening. You can speak commands now.");
                speakMessage("Voice system activated. I'm listening. You can speak commands now.");
            };
            
            atmState.speechRecognizer.onresult = (event) => {
                const transcript = event.results[event.results.length - 1][0].transcript.trim();
                console.log('Voice command:', transcript);
                processVoiceCommand(transcript);
            };
            
            atmState.speechRecognizer.onerror = (event) => {
                console.error('Speech recognition error:', event.error);
                
                if (event.error === 'not-allowed' || event.error === 'permission-denied') {
                    // Show permission modal again
                    permissionModal.style.display = 'flex';
                    setTimeout(() => {
                        permissionModal.style.opacity = '1';
                    }, 10);
                    
                    showMessage("Microphone access was denied. Please allow microphone access to use voice commands.");
                    statusText.textContent = "Microphone Access Denied";
                    statusIndicator.style.background = "rgba(239, 68, 68, 0.2)";
                    statusIndicator.style.borderColor = "rgba(239, 68, 68, 0.3)";
                } else if (event.error === 'no-speech') {
                    // No speech detected, restart quietly
                    restartRecognition();
                } else {
                    setTimeout(restartRecognition, 1000);
                }
            };
            
            atmState.speechRecognizer.onend = () => {
                updateVoiceStatus(false);
                if (atmState.isListening) {
                    // Auto-restart if we're still listening
                    setTimeout(restartRecognition, 100);
                }
            };
            
            // Start listening
            startListening();
            
            // Start voice level animation
            startVoiceLevelAnimation();
            
            // Initial greeting
            setTimeout(() => {
                speakMessage("Welcome to SmartVoice ATM. You can speak commands like 'withdraw money', 'deposit funds', or 'check balance'. You can also use the keypad and buttons.");
            }, 1500);
        }

        // Start listening
        function startListening() {
            if (atmState.speechRecognizer && !atmState.isListening) {
                try {
                    atmState.speechRecognizer.start();
                    atmState.isListening = true;
                } catch (error) {
                    console.error('Error starting recognition:', error);
                    setTimeout(startListening, 1000);
                }
            }
        }

        // Restart recognition
        function restartRecognition() {
            if (atmState.speechRecognizer && atmState.isListening) {
                try {
                    atmState.speechRecognizer.stop();
                    setTimeout(() => {
                        atmState.speechRecognizer.start();
                    }, 100);
                } catch (error) {
                    console.error('Error restarting recognition:', error);
                }
            }
        }

        // Update voice status
        function updateVoiceStatus(listening) {
            if (listening) {
                voiceStatus.textContent = "LISTENING...";
                voiceStatus.classList.add('listening');
                statusText.textContent = "Voice System Active";
                statusIndicator.style.background = "rgba(37, 99, 235, 0.2)";
                statusIndicator.style.borderColor = "rgba(37, 99, 235, 0.3)";
            } else {
                voiceStatus.textContent = "READY";
                voiceStatus.classList.remove('listening');
                statusText.textContent = "Voice System Ready";
                statusIndicator.style.background = "rgba(16, 185, 129, 0.2)";
                statusIndicator.style.borderColor = "rgba(16, 185, 129, 0.3)";
            }
        }

        // Voice level animation
        function startVoiceLevelAnimation() {
            let level = 0;
            let direction = 1;
            
            function animate() {
                if (!atmState.isListening) return;
                
                // Simulate voice level changes
                level += direction * (5 + Math.random() * 15);
                if (level > 100) {
                    level = 100;
                    direction = -1;
                } else if (level < 0) {
                    level = 0;
                    direction = 1;
                }
                
                voiceLevel.style.width = level + '%';
                
                setTimeout(animate, 100);
            }
            
            animate();
        }

        // Process voice commands
        function processVoiceCommand(command) {
            const lowerCommand = command.toLowerCase();
            
            // Add to conversation
            addConversation("You", command);
            
            // Greeting
            if (lowerCommand.includes('hello') || lowerCommand.includes('hi') || lowerCommand.includes('hey')) {
                const response = "Hello! Welcome to SmartVoice ATM. What can I help you with today?";
                speakMessage(response);
                addConversation("ATM", response);
                return;
            }
            
            // Withdrawal
            if (lowerCommand.includes('withdraw') || lowerCommand.includes('take out') || lowerCommand.includes('get cash')) {
                const amount = extractAmount(lowerCommand);
                if (amount > 0) {
                    processWithdrawal(amount);
                } else {
                    startWithdrawal();
                    const response = "How much would you like to withdraw? Please enter the amount using the keypad or say the amount.";
                    speakMessage(response);
                    addConversation("ATM", response);
                }
                return;
            }
            
            // Deposit
            if (lowerCommand.includes('deposit') || lowerCommand.includes('add money') || lowerCommand.includes('put in')) {
                const amount = extractAmount(lowerCommand);
                if (amount > 0) {
                    processDeposit(amount);
                } else {
                    startDeposit();
                    const response = "How much would you like to deposit? Please enter the amount using the keypad or say the amount.";
                    speakMessage(response);
                    addConversation("ATM", response);
                }
                return;
            }
            
            // Balance check
            if (lowerCommand.includes('balance') || lowerCommand.includes('how much') || lowerCommand.includes('check balance')) {
                checkBalance();
                return;
            }
            
            // Help
            if (lowerCommand.includes('help') || lowerCommand.includes('what can') || lowerCommand.includes('options')) {
                showHelp();
                return;
            }
            
            // Process amounts
            const amount = extractAmount(lowerCommand);
            if (amount > 0) {
                if (atmState.currentMode === 'withdrawal') {
                    processWithdrawal(amount);
                } else if (atmState.currentMode === 'deposit') {
                    processDeposit(amount);
                } else {
                    setAmount(amount);
                }
                return;
            }
            
            // Default response
            const response = "I didn't understand that. You can say 'withdraw', 'deposit', 'check balance', or use the buttons and keypad.";
            speakMessage(response);
            addConversation("ATM", response);
        }

        // Extract amount from speech
        function extractAmount(command) {
            const numberWords = {
                'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5,
                'six': 6, 'seven': 7, 'eight': 8, 'nine': 9, 'ten': 10,
                'eleven': 11, 'twelve': 12, 'thirteen': 13, 'fourteen': 14,
                'fifteen': 15, 'sixteen': 16, 'seventeen': 17, 'eighteen': 18,
                'nineteen': 19, 'twenty': 20, 'thirty': 30, 'forty': 40,
                'fifty': 50, 'sixty': 60, 'seventy': 70, 'eighty': 80,
                'ninety': 90, 'hundred': 100, 'thousand': 1000
            };
            
            let amount = 0;
            const words = command.toLowerCase().split(/\s+/);
            let tempAmount = 0;
            
            for (let i = 0; i < words.length; i++) {
                const word = words[i].replace(/[^a-z]/g, '');
                if (numberWords[word] !== undefined) {
                    if (word === 'hundred') {
                        tempAmount = tempAmount === 0 ? 100 : tempAmount * 100;
                    } else if (word === 'thousand') {
                        tempAmount = tempAmount === 0 ? 1000 : tempAmount * 1000;
                    } else {
                        tempAmount += numberWords[word];
                    }
                } else if (word === 'dollars' || word === 'dollar' || word === 'bucks') {
                    amount = tempAmount > 0 ? tempAmount : amount;
                    tempAmount = 0;
                }
            }
            
            if (tempAmount > 0) {
                amount = tempAmount;
            }
            
            if (amount === 0) {
                const numericMatch = command.match(/\$?(\d+[,.]?\d*)/);
                if (numericMatch) {
                    amount = parseFloat(numericMatch[1].replace(',', ''));
                }
            }
            
            return amount;
        }

        // Start withdrawal process
        function startWithdrawal() {
            atmState.currentMode = 'withdrawal';
            atmState.currentAmount = '';
            
            welcomeScreen.style.display = 'none';
            transactionScreen.style.display = 'none';
            amountScreen.style.display = 'block';
            
            amountTitle.textContent = "Withdraw Amount";
            amountInstruction.textContent = "Enter amount to withdraw, then press ENTER";
            amountValue.textContent = '0';
            
            // Show quick amounts
            renderQuickAmounts();
            
            // Speak instruction
            speakMessage("Please enter the amount you want to withdraw using the keypad or say the amount.");
        }

        // Start deposit process
        function startDeposit() {
            atmState.currentMode = 'deposit';
            atmState.currentAmount = '';
            
            welcomeScreen.style.display = 'none';
            transactionScreen.style.display = 'none';
            amountScreen.style.display = 'block';
            
            amountTitle.textContent = "Deposit Amount";
            amountInstruction.textContent = "Enter amount to deposit, then press ENTER";
            amountValue.textContent = '0';
            
            // Show quick amounts
            renderQuickAmounts();
            
            // Speak instruction
            speakMessage("Please enter the amount you want to deposit using the keypad or say the amount.");
        }

        // Render quick amounts
        function renderQuickAmounts() {
            quickAmounts.innerHTML = '';
            
            quickAmountOptions.forEach(amount => {
                const button = document.createElement('div');
                button.className = 'quick-amount';
                button.textContent = `$${amount}`;
                button.onclick = () => setAmount(amount);
                quickAmounts.appendChild(button);
            });
        }

        // Set amount
        function setAmount(amount) {
            atmState.currentAmount = amount.toString();
            amountValue.textContent = formatAmount(amount);
        }

        // Add digit to current amount
        function addDigit(digit) {
            if (atmState.currentAmount.length >= 6) return; // Limit to 6 digits
            
            if (atmState.currentAmount === '0') {
                atmState.currentAmount = digit;
            } else {
                atmState.currentAmount += digit;
            }
            
            amountValue.textContent = formatAmount(parseFloat(atmState.currentAmount));
        }

        // Clear amount
        function clearAmount() {
            atmState.currentAmount = '';
            amountValue.textContent = '0';
        }

        // Format amount with commas
        function formatAmount(amount) {
            return amount.toLocaleString('en-US', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            });
        }

        // Submit amount
        function submitAmount() {
            const amount = parseFloat(atmState.currentAmount) || 0;
            
            if (amount <= 0) {
                showMessage("Please enter a valid amount greater than zero.");
                return;
            }
            
            if (atmState.currentMode === 'withdrawal') {
                processWithdrawal(amount);
            } else if (atmState.currentMode === 'deposit') {
                processDeposit(amount);
            }
        }

        // Process withdrawal
        function processWithdrawal(amount) {
            if (amount <= 0) {
                showMessage("Please enter a valid amount to withdraw.");
                return;
            }
            
            if (amount > atmState.balance) {
                showMessage(`Insufficient funds. Your balance is $${formatAmount(atmState.balance)}. Please try a smaller amount.`);
                speakMessage(`Insufficient funds. Your balance is $${formatAmount(atmState.balance)}. Please try a smaller amount.`);
                return;
            }
            
            // Process withdrawal
            atmState.balance -= amount;
            atmState.transactions.unshift({
                type: 'withdrawal',
                amount: amount,
                date: 'Today',
                time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}),
                description: 'Cash withdrawal'
            });
            
            // Update display
            updateBalance();
            renderTransactionHistory();
            
            // Show transaction screen
            showTransaction('withdrawal', amount, `Withdrawal successful. $${formatAmount(amount)} dispensed.`);
            
            // Speak confirmation
            speakMessage(`Withdrawal successful. $${formatAmount(amount)} has been dispensed. Your new balance is $${formatAmount(atmState.balance)}.`);
        }

        // Process deposit
        function processDeposit(amount) {
            if (amount <= 0) {
                showMessage("Please enter a valid amount to deposit.");
                return;
            }
            
            // Process deposit
            atmState.balance += amount;
            atmState.transactions.unshift({
                type: 'deposit',
                amount: amount,
                date: 'Today',
                time: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}),
                description: 'Cash deposit'
            });
            
            // Update display
            updateBalance();
            renderTransactionHistory();
            
            // Show transaction screen
            showTransaction('deposit', amount, `Deposit successful. $${formatAmount(amount)} added to account.`);
            
            // Speak confirmation
            speakMessage(`Deposit successful. $${formatAmount(amount)} has been added to your account. Your new balance is $${formatAmount(atmState.balance)}.`);
        }

        // Check balance
        function checkBalance() {
            showTransaction('balance', atmState.balance, `Current available balance`);
            speakMessage(`Your current balance is $${formatAmount(atmState.balance)}.`);
        }

        // Show transaction
        function showTransaction(type, amount, message) {
            welcomeScreen.style.display = 'none';
            amountScreen.style.display = 'none';
            transactionScreen.style.display = 'block';
            
            if (type === 'withdrawal') {
                transactionIcon.innerHTML = '<i class="fas fa-money-bill-wave"></i>';
                transactionIcon.style.color = 'var(--danger)';
                transactionTitle.textContent = 'Withdrawal Complete';
                transactionAmount.textContent = `-$${formatAmount(amount)}`;
                transactionAmount.style.color = 'var(--danger)';
            } else if (type === 'deposit') {
                transactionIcon.innerHTML = '<i class="fas fa-coins"></i>';
                transactionIcon.style.color = 'var(--success)';
                transactionTitle.textContent = 'Deposit Complete';
                transactionAmount.textContent = `+$${formatAmount(amount)}`;
                transactionAmount.style.color = 'var(--success)';
            } else {
                transactionIcon.innerHTML = '<i class="fas fa-balance-scale"></i>';
                transactionIcon.style.color = 'var(--warning)';
                transactionTitle.textContent = 'Account Balance';
                transactionAmount.textContent = `$${formatAmount(amount)}`;
                transactionAmount.style.color = 'var(--warning)';
            }
            
            transactionMessage.textContent = message;
            
            // Return to welcome screen after 5 seconds
            setTimeout(() => {
                transactionScreen.style.display = 'none';
                welcomeScreen.style.display = 'block';
                atmState.currentMode = 'welcome';
            }, 5000);
        }

        // Update balance
        function updateBalance() {
            currentBalance.textContent = `$${formatAmount(atmState.balance)}`;
        }

        // Set PIN
        function setPin() {
            showMessage("PIN setup feature will be available in the full version.");
            speakMessage("PIN setup feature will be available in the full version.");
        }

        // Show history
        function showHistory() {
            historyPanel.style.display = 'block';
        }

        // Hide history
        function hideHistory() {
            historyPanel.style.display = 'none';
        }

        // Render transaction history
        function renderTransactionHistory() {
            historyList.innerHTML = '';
            
            atmState.transactions.slice(0, 5).forEach(trans => {
                const item = document.createElement('div');
                item.className = `history-item ${trans.type}`;
                
                const icon = trans.type === 'withdrawal' ? 'fa-arrow-up' : 'fa-arrow-down';
                const color = trans.type === 'withdrawal' ? 'var(--danger)' : 'var(--success)';
                const sign = trans.type === 'withdrawal' ? '-' : '+';
                
                item.innerHTML = `
                    <div style="display: flex; align-items: center; gap: 15px;">
                        <div style="width: 40px; height: 40px; border-radius: var(--radius-sm); background: rgba(255,255,255,0.05); display: flex; align-items: center; justify-content: center;">
                            <i class="fas ${icon}" style="color: ${color};"></i>
                        </div>
                        <div>
                            <div style="font-weight: 600;">${trans.description}</div>
                            <div style="font-size: 0.9rem; color: var(--text-muted);">${trans.date} • ${trans.time}</div>
                        </div>
                    </div>
                    <div style="font-size: 1.3rem; font-weight: 700; color: ${color}">
                        ${sign}$${formatAmount(trans.amount)}
                    </div>
                `;
                
                historyList.appendChild(item);
            });
        }

        // Show help
        function showHelp() {
            const helpMessage = "You can use voice commands: 'Withdraw [amount]', 'Deposit [amount]', 'Check balance'. Or use the buttons and keypad for manual control. Quick amounts are available for common transactions.";
            
            showTransaction('help', 0, "Voice commands and manual controls available");
            speakMessage(helpMessage);
            addConversation("ATM", helpMessage);
        }

        // Add conversation
        function addConversation(speaker, message) {
            const item = document.createElement('div');
            item.className = 'conversation-item';
            
            item.innerHTML = `
                <div class="speaker ${speaker.toLowerCase()}">${speaker}:</div>
                <div class="message">${message}</div>
            `;
            
            voiceConversation.appendChild(item);
            voiceConversation.scrollTop = voiceConversation.scrollHeight;
            
            // Limit to 10 messages
            const messages = voiceConversation.querySelectorAll('.conversation-item');
            if (messages.length > 10) {
                messages[0].remove();
            }
        }

        // Speak message
        function speakMessage(text) {
            if (!atmState.voiceEnabled) return;
            
            const SpeechSynthesis = window.speechSynthesis;
            SpeechSynthesis.cancel();
            
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.rate = 0.9;
            utterance.pitch = 1;
            utterance.volume = 1;
            
            // Select a voice
            const voices = SpeechSynthesis.getVoices();
            if (voices.length > 0) {
                const preferredVoice = voices.find(v => 
                    v.name.includes('Google') || 
                    v.name.includes('Microsoft') ||
                    v.name.includes('Samantha')
                ) || voices[0];
                utterance.voice = preferredVoice;
            }
            
            SpeechSynthesis.speak(utterance);
        }

        // Show message
        function showMessage(text) {
            addConversation("System", text);
        }

        // Auto-detect speech synthesis voices
        if (speechSynthesis.onvoiceschanged !== undefined) {
            speechSynthesis.onvoiceschanged = () => {
                console.log('Voices loaded:', speechSynthesis.getVoices().length);
            };
        }

        // Keyboard shortcuts
        document.addEventListener('keydown', (event) => {
            // Number keys
            if (event.key >= '0' && event.key <= '9') {
                addDigit(event.key);
            }
            
            // Enter key
            if (event.key === 'Enter') {
                submitAmount();
            }
            
            // Escape key
            if (event.key === 'Escape') {
                clearAmount();
                welcomeScreen.style.display = 'block';
                amountScreen.style.display = 'none';
                transactionScreen.style.display = 'none';
                historyPanel.style.display = 'none';
            }
            
            // Space to simulate voice
            if (event.key === ' ' && !event.target.matches('button, .key, .control-button, .function-button')) {
                event.preventDefault();
                const commands = ["withdraw 200", "deposit 500", "check balance"];
                const randomCommand = commands[Math.floor(Math.random() * commands.length)];
                processVoiceCommand(randomCommand);
            }
        });
    </script>
</body>
</html>
