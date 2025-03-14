# DevTinder

- Created a Vite + React application.
- Remove unnecessary code and create a hello world app.
- Install Tailwind CSS
- Install DaisyUI
- Add NavBar component to App.jsx
- Create NavBar.jsx separate component file.
- Install react router dom
- Create BrowserRouter > Routes > Route=/ Body > RouteChildren
- Create an Outlet in your Body component
- Create a footer
- Create a Login Page.
- Install axios
- CORS - Install cors in backend => add middleware to with configuration:origin and credentials:true
- Whenever you are making API call pass {withCrentials:true} to axios. (Used for getting token in browser cookie storage.)
- Go through the documentation https://redux-toolkit.js.org/tutorials/quick-start
- Install react-redux + @reduxjs/toolkit => Create a configureStore() => Provider => createSlice() => Add reducer to store
- Add Redux Dev Tools in chrome.
- Login and see if your is coming in Redux Dev Tools in state/store.
- Navbar should update as soon as user logs in.
- Refactor your code to add constants file + create a components folder.
- You should not be able to other routes without login
- If token is not present, redirect the user to login page.
- Logout
- Get the feed and the feed in the store
- build the user card on feed
- Edit profile feature is build
- show toast message on save profile
- New page to see all my connections
- New page to see all my connection requests
- Feature - Accept/Reject connection request
- Send/Ignore the user card(connection) from the feed
- Signup New User
- E2E testing

Body NavBar Route=/ => Feed Route=/login => Login Route=/connetions => Connections Router=/profile => Profile

# Deployment

- Signup on AWS
- Launch instance
- chmod 400 <secret>.pem
- ssh -i "devTinder-secret.pem" ubuntu@ec2-43-204-96-49.ap-south-1.compute.amazonaws.com
- Install Node version 16.17.0
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
  exit
  nvm install 18.18.2
  node -v

- Git clone
  git clone https://github.com/KeshavDussal/devTinder-Frontend.git
  git clone https://github.com/KeshavDussal/devTinder.git

- Frontend
  - npm install -> dependencies install
  - npm run build
  - sudo apt update
  - sudo apt install nginx
  - sudo systemctl start nginx
  - sudo systemctl enable nginx
  - Copy code from dist(build files) to /var/www/html/
  - sudo scp -r dist/\* /var/www/html/
  - Enable port :80 of your instance (by default aws blocks all port of application)
    http://13.201.78.176/ (Access with public ipaddress - note it should be http then only it will work if https remove s from it.)
- Backend

  - updated DB password (Optional)
  - npm start(prod) & npm run dev(development)
  - allowed ec2 instance public IP on mongodb server
  - npm intsall pm2 -g
  - pm2 start npm --name "devTinder-backend" -- start
  - pm2 logs
  - pm2 list, pm2 flush <name> , pm2 stop <name>, pm2 delete <name>
  - (Chatgpt search: nginx proxy pass /api to 7777 node application)
  - config nginx - /etc/nginx/sites-available/default
  - restart nginx - sudo systemctl restart nginx
  - Modify the BASEURL in frontend project to "/api"
