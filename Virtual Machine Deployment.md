## 1. Creation Configuration

- Basic
    
    Authentication type:  Password. 
    
- Networking
    
    Public IP: None
    
    Public inbound ports: None
    
- Use Bastion to connect
    - Portal → Virtual Machine → Connect → Bastion

## 2. Install Essentials

```jsx
sudo apt install -y curl wget unzip zip vim net-tools dnsutils python3 python3-pip git
```

## 3. Azure Login

```jsx
az login --use-device-code
```

### ⚠️ Do not press Ctrl + C (shown as ^C) or the login will be interrupted.

Instead, keep the terminal open, type the link in your local browser, and manually enter the code shown in your VM terminal. (Don’t copy/paste, just type it in)

```jsx
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the
code XXXXXXXXXX to authenticate.
```

## 4. Azure Login with MFA (multi-factor authentication) Required

- MFA is required in some situation.

```jsx
az logout
az login --tenant "<TENANT ID>" --scope "https://graph.microsoft.com//.default"
```
