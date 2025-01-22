# onioNS (finally?)
A privacy-respecting, cryptographically secure, and fully decentralized name service for authenticated, human-readable onion addresses.

This README provides an outline of the project. For detailed information on specific components, please see the respective **README** files in each directory.

---

## Table of Contents
- [Web Lookup](#web-lookup)
- [Overview](#overview)
- [How It Works](#how-it-works)
- [Usage](#usage)
- [Planned Features](#planned-features)
- [Considerations](#considerations)
- [Contributing](#contributing)
- [License](#license)

---

## Web Lookup 
- **ClearNet:** https://alltheonions.pw/  
- **Tor:** http://fvf3zavvvw373w6bbxo6nwjdhwel3x5wc2v4iosnmtm5t54guv5mnuid.onion/ - Sorry it's only available sporadically. I am finding new hosting.  
- **BlockChain** alltheonions.unstoppable  
This page currently allows visitors to resolve Unstoppable Domains. At the moment it works with a variety of records, not just onion records.  
In the background it uses a connection to Infura API (free level): https://www.infura.io/  
It is incredibly basic (inefficient) and just a proof of concept, please don't abuse it and bear in mind it really cannot handle many requests at the moment (API rate limit).  

---

## Overview
**onioNS** aims to improve how users discover and verify Tor onion services by providing a **human-readable naming system**. Using a combination of **Unstoppable Domains (UD)** and Tor’s existing architecture, onioNS lets you map memorable addresses—e.g., `something.crypto`—to actual onion addresses. This process includes:

- **Privacy Respect** – Minimal personal data collection and optional anonymity in domain registration.  
- **Cryptographic Security** – Blockchain-backed name records and cryptographic keys for verification.  
- **Full Decentralization** – Records are stored and retrieved through decentralized infrastructure, reducing single points of failure.  
- **Fundraising Opportunity** – May be possible to raise money for the Tor project and other privacy initiatives by teaming up with UD in the sale of .tor or .onion domains.  

---

## How It Works and Integration

1. **Leveraging Unstoppable Domains**  
   - We store records on the UD name service, which operates on various TLDs (e.g. `.crypto`, `.blockchain`, `.x`, etc.).  
   - For an up-to-date list of UD’s TLDs, see their repo:  (there is one somewhere on their GH - update this with exact link)  
     [Unstoppable Domains Supported TLDs](https://github.com/unstoppabledomains)  
   - Each UD name can contain references (via DNS-like records) to:
     - **Onion addresses** (i.e., the Tor `.onion` domains)  
     - **Signing keys** (for verifying the authenticity of the onion service)
     Both of those records will need to be stored in TXT records as key:value pairs  

2. **Resolution on Exit Nodes**  
   - Tor exit nodes can run an extra program or module to resolve UD domains to onion addresses, or could run modified hybrid resolvers. Until integration with the Tor browser the records should be returned as CNAME records.  
   - This preserves the same security and decentralization Tor already offers for regular DNS. That relies on the exit nodes.  
   - Multiple retrieval methods from multiple sources (including a local node) provide redundancy and trust minimization, either for individual nodes or across the network as is currently the case.

3. **Client-Side Resolution**  
   - A Tor-enabled browser (or other privacy-centric browser) can resolve these UD-based addresses with **DNS over HTTPS (DoH)** or **DoH-over-Tor**, if such community run services were to exist.  
   - Users can also rely on **RPC** calls via a provider or their own local node.  
   - This setup gives users control over DNS resolution while maintaining security and privacy.
   - We will also host a simple web interface that lets visitors resolve UDs for onion addresses.  

4. **Verification of Services**  
   - Tor service owners can store their **onion address** (or more than one, with priorities) and **signing key** in the UD records.  
   - Visitors could verify authenticity using cryptographic keys provided in these records.  

5. **Domain/Subdomain Registration**  
   - Operators can obtain a UD domain or subdomain.  
   - We plan to allow **free subdomains** under our main UD domain, with optional donations. This will still require gas to be paid and even being donation run this will require some sort of anti abuse mechanism to be determined.  
   - An easy web interface (accessible via clearnet and Tor) will let owners set records, all while respecting privacy.  

---

## Usage

1. **Obtain or Mint a Domain**  
   - Purchase a domain from Unstoppable Domains (or another integrated provider).  
   - Or request a subdomain (e.g., `yoursubdomain.alltheonions.crypto`) via our interface (coming soon).  

2. **Set Your Onion Records**  
   - Use our web interface (or direct blockchain interaction - web interface coming soon) to add records pointing to your onion address.  
   - Optionally include a signing key record so visitors can verify the authenticity of your service.
  
---

- **Configure Your Client**  
   - In your Tor browser or similar setup, enable the resolution mechanism (DoH, DoH-over-Tor, or RPC to a local node).  
   - Typing in your `.crypto`, `.blockchain`, or `.x` domain should now direct you to the mapped onion address.  

---

## Planned Features

- **Integration Plugins**  
  - Browser add-ons or Node modules for streamlined resolution. RPC (local or remote), API or DOH (https or Tor)    

---

## Considerations

The best idea seems to be to add records following the existing standard set by UD: dweb.onion.address for example. There is an issue with resolving onion addresses - it seems best for exit nodes to resolve onion records to CNAME records with onion addresses. This allows the most freedom for future adoption with the fewest issues, it seems. So exit nodes can resolve onion records as CNAME records, immediately and without effort on the client attaining functionality. The client modifications to Tor browser (either official or not) are easier managed by the client and could include functionality to deal with onion and ipfs records for example - but that is controllable by the client and therefore not as much of a concern - at that point it seems better to already be following UD standards and be able to return a browser.preferred record which could allow clients to choose their own behavior (Tor browser will likely still want to always prioritize onion records).  


---

## Contributing

We welcome community contributions. Please get in touch. Or just go ahead and fork the repo to get started.  
Get in touch: [Email](mailto:puurpl.x@ud.me)  

---

## License  



---
