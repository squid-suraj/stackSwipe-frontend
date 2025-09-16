# stackSwap

- Create a Vite + React application
- Remove unecessary code and create a Hello World app
- Install Tailwind CSS
- Install Daisy UI
- Add NavBar component to App.jsx
- Create a NavBar.jsx separate Component file
- Install react router dom
- Create BrowserRouter > Routes > Route=/ Body > RouteChildren
- Create an Outlet in your Body Component
- Create a footer
- Create a Login Page
- Install axios
- CORS - install cors in backend => add middleware to with configurations: orgin, credentials: true
- Whenever you're making API call so pass axios => { withCredentials: true }
- install react-redux + @reduxjs/toolkit - https://redux-toolkit.js.org/tutorials/quick-start
- configureStore => Provider => createSlice => add reducer to store
- Add redux devtools in chrome
- Login and see if your data is coming properly in the store
- NavBar should update as soon as user logs in
- Refactor our code to add constants file + create a components folder 
- You should not be access other routes without login
- If token is not present, redirect user to login page
- Logout Feature
- Get the feed and add the feed in th store
- build the user card on feed
- Edit Profile Feature
- Show Toast Message on save of profile
- New Page - See all my connections
- New Page - See all my Conenction REquests
- Feature - Accept/Reject connection request
- Send/Ignore the user card from the feed 
- Signup New User 
- E2E testing


Body 
    NavBar
    Route=/  => Feed
    Route=/login  => Login
    Route=/connetions => Connections
    Router=/profile => Profile



    # Deployment

    - Signup on AWS 
    - Launch instance
    - chmod 400 <secret>.pem
    - ssh -i "stackSwap-secret.pem" ubuntu@ec2-43-204-96-49.ap-south-1.compute.amazonaws.com
    - Install Node version 16.17.0
    - Git clone
    - Frontend    
        - npm install  -> dependencies install
        - npm run build
        - sudo apt update
        - sudo apt install nginx
        - sudo systemctl start nginx
        - sudo systemctl enable nginx
        - Copy code from dist(build files) to /var/www/html/
        - sudo scp -r dist/* /var/www/html/
        - Enable port :80 of your instance
    - Backend
        - updated DB password
        - allowed ec2 instance public IP on mongodb server
        - npm intsall pm2 -g
        - pm2 start npm --name "stackSwap-backend" -- start
        - pm2 logs
        - pm2 list, pm2 flush <name> , pm2 stop <name>, pm2 delete <name>
        - config nginx - /etc/nginx/sites-available/default
        - restart nginx - sudo systemctl restart nginx
        - Modify the BASEURL in frontend project to "/api"



# Ngxinx config: 

        Frontend = http://43.204.96.49/
        Backend = http://43.204.96.49:7777/
    
        Domain name = stackSwap.com => 43.204.96.49

        Frontend = stackSwap.com
        Backend = stackSwap.com:7777 => stackSwap.com/api

        nginx config : 

        server_name 43.204.96.49;

        location /api/ {
            proxy_pass http://localhost:7777/;  # Pass the request to the Node.js app
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection 'upgrade';
            proxy_set_header Host $host;
            proxy_cache_bypass $http_upgrade;
        }



# Real Time Chat using Websocket(Socket.io)
    - Build the UI for a chat window on /chat/:targetUserId
    - Setup socket.io in backend
    - npm i socket.io
    - Setup frontend socket.io-client
    - Initialise the chat
    - createSocketConnection
    - Listen to events
    - toDo:  improve the UI
    - toDo: Fix Security Bug - auth in web ockets
    - toDo: Fix bug - If I'm not fried, then I should not be able to send message
    - toDo: feat: Show Green Symbol when online???? - [last Seen 2 hours ago]
    - todo: Limit messages when fetching from DB
