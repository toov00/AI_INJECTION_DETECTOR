# AI Prompt Injection Detector

> Security analysis tool for detecting prompt injection vulnerabilities in smart contracts with AI oracle integrations

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://reactjs.org/)
[![Solidity](https://img.shields.io/badge/Solidity-0.8+-363636?logo=solidity)](https://soliditylang.org/)

---

## Overview

As blockchain protocols increasingly integrate AI/LLM capabilities through oracles, a new critical attack surface emerges: **prompt injection vulnerabilities**. This tool helps security auditors and developers identify and understand these vulnerabilities before deployment.

## Features

### **Contract Analysis Engine**
- Automatically detects AI oracle integrations in Solidity code
- Identifies missing security controls (input validation, response verification, rate limiting)
- Calculates risk scores based on vulnerability severity
- Provides actionable remediation recommendations

### **Attack Vector Library**
- Comprehensive reference of 5 major injection techniques
- Real-world attack payloads with explanations
- Severity classifications (Critical/High)
- Mitigation strategies for each attack type

### **Visual Security Dashboard**
- Risk scoring (0-100 scale)
- Vulnerability categorization by severity
- Security checklist validation
- Clean, intuitive interface

## Quick Start

### **Option 1: Open Directly**
1. Download `index.html`
2. Open in any modern browser
3. Start analyzing contracts immediately

No build tools, dependencies, or setup required!

### **Option 2: Local Server**
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Visit http://localhost:8000
```

### **Option 3: Deploy to GitHub Pages**
```bash
git clone https://github.com/yourusername/ai-prompt-injection-detector.git
cd ai-prompt-injection-detector

# Push to GitHub and enable Pages in Settings
```

## Usage

### **Analyzing a Contract**

1. **Navigate to Contract Analyzer tab**
2. **Paste your Solidity code** or click "Load Example Contract"
3. **Click "Analyze Contract"**
4. **Review results:**
   - Risk score
   - Detected AI oracle integrations
   - Specific vulnerabilities
   - Security checklist

### **Exploring Attack Vectors**

1. **Switch to Attack Library tab**
2. **Browse attack techniques** organized by severity
3. **Review each attack:**
   - Attack payload
   - How it works
   - Potential impact
   - Mitigation strategy

## Attack Vectors Covered

### **Critical Severity**
- **Ignore Previous Instructions**: Complete system prompt override
- **JSON Structure Manipulation**: Malicious response format injection

### **High Severity**
- **Role Switching**: AI permission/authority manipulation
- **Delimiter Escape**: Input boundary breakout
- **Context Poisoning**: False context injection for decision manipulation

## How It Works

### **Static Analysis**
The tool scans Solidity code using regex pattern matching to detect:
- AI oracle function calls (`aiOracle.query()`, `llm.generate()`, etc.)
- User input in prompts
- Response parsing patterns
- Security control implementations

### **Vulnerability Detection**
For each detected AI oracle integration, it checks for:

```javascript
Input Validation    : require(validate(userInput))
Response Verification : verifyResponse(aiResponse)  
Rate Limiting       : rateLimit modifier
Trusted Oracle      : whitelist verification
```

Missing controls are flagged as vulnerabilities with severity ratings.

### **Risk Scoring**
```
Risk Score = Σ(vulnerability severity × weight)
- Critical: 40 points
- High: 25 points
```

## Example Vulnerable Contract

```solidity
// VULNERABLE: Multiple security issues
contract VulnerableAITrader {
    IAIOracle public aiOracle;
    
    // No input validation
    // No response verification
    function executeTradeIntent(string memory userIntent) public {
        // Directly concatenates user input
        string memory prompt = "Execute: " + userIntent;
        
        // Calls AI oracle without protection
        string memory response = aiOracle.query(prompt);
        
        // Executes based on unverified response
        _executeTrade(response);
    }
}
```

**Detected Issues:**
- Missing Input Validation (Critical)
- No Response Verification (High)

**Risk Score: 65/100**

## Educational Value

This tool serves as a:
- **Learning resource** for understanding AI security in Web3
- **Reference implementation** for security analysis tools
- **Portfolio demonstration** of AI + blockchain expertise
- **Research platform** for emerging attack vectors

## Technical Architecture

**Tech Stack:**
- React 18 (via CDN)
- Tailwind CSS
- Pure JavaScript (no build process)
- Single-file deployment

## Why This Matters for Web3 Security

### **Emerging Threat Landscape**
As protocols like:
- **Morpheus** (decentralized AI)
- **Fetch.ai** (autonomous agents)
- **Chainlink Functions** (off-chain compute)

...integrate AI capabilities, prompt injection becomes a critical attack vector that traditional auditors aren't equipped to detect.

### **Real-World Impact**
- Fund transfers based on manipulated AI decisions
- Access control bypass through role manipulation
- Validation bypass via context poisoning
- Smart contract logic subversion

## Use Cases

### **For Security Auditors**
1. Add to security review workflow
2. Identify AI-specific vulnerabilities
3. Generate finding reports
4. Educate clients on AI risks

### **For Developers**
1. Test contracts during development
2. Learn secure AI oracle patterns
3. Implement recommended protections
4. Validate security measures

### **For Researchers**
1. Study attack vector effectiveness
2. Develop new detection methods
3. Benchmark security across protocols
4. Contribute to Web3 AI safety

## Future Enhancements

- [ ] Support for multiple AI models (GPT, Claude, Llama)
- [ ] Custom attack vector creation
- [ ] PDF report generation
- [ ] CI/CD integration
- [ ] Multi-chain support (Solana, Cosmos)
- [ ] Historical vulnerability database
- [ ] Automated fix suggestions

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License, see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by the intersection of blockchain security and AI safety research
- Thanks to the Web3 security community for insights on emerging threats

---

Built with love for Web3 Security × AI Safety
