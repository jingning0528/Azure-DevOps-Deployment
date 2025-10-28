## 1. Creation Configuration

- Basic
    
    Authentication type:  Password. (Don’t use SSH public key, which will be banned by the privacy restriction.)
    
- Networking
    
    Public IP: None
    
    Public inbound ports: None
    

## 2. Install Essentials

```jsx
sudo apt install -y curl wget unzip zip vim net-tools dnsutils python3 python3-pip git
```

## 3. Azure Login

```jsx
az login --use-device-code
```

### ⚠️Warning: Don’t cope link or code ‘XXXXXXXXX’ into browser.

Just remember the code and type into browser, since the ^C is the interrupt shortcut which will end the login process.

```jsx
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the
code XXXXXXXXXX to authenticate.
```

## 4. Azure Login with MFA (multi-factor authentication) Required

```jsx
az logout
az login --tenant "<TENANT ID>" --scope "https://graph.microsoft.com//.default"
```
