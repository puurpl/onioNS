# Creating Blockchain Records for your Onion Service

Unstoppable Domains has a guide: https://docs.unstoppabledomains.com/smart-contracts/quick-start/manage-domain-records/  
Set the record as:  
  key=dweb.onion.address and value=onion-address priority  
  'dweb.onion.address' '2gzyxa5ihm7nsggfxnu52rck2vv4rvmdlkiu3zzui5du4xyclen53wid.onion 10'

Or  
  key=dweb.onion.key and value=key  

https://docs.unstoppabledomains.com/resolution/records-reference/#dweb-records Talks about the currently available record types with explanations.  

Long term it may be best to have UD add 'Tor' or 'onion' to browser.preferred_protocols (alongside 'ipfs' and 'http') and officially integrate into their DNS. This should really only be a documentation and standards change in terms of the dweb records, as the key:value pairs are freeform strings.  
