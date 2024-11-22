root@bcfbf592000e:/passoire# ls
config  crypto-helper  init.sh  logs  my_own_cryptographic_algorithm  web
root@bcfbf592000e:/passoire# cd crypto-helper
root@bcfbf592000e:/passoire/crypto-helper# ls
crypto-helper.sh  flag_9  node_modules  package-lock.json  package.json  server.js
root@bcfbf592000e:/passoire/crypto-helper# cd crypto-helper.sh
bash: cd: crypto-helper.sh: Not a directory
root@bcfbf592000e:/passoire/crypto-helper# cat crypto-helper.sh 
#!/bin/bash

# Define the path to the Node.js server file
NODE_SERVER_FILE="/passoire/crypto-helper/server.js"
LOG_FILE="/passoire/logs/crypto-helper.log"

# Define a file to store the PID of the Node.js server
PID_FILE="/passoire/logs/crypto-helper.pid"


# Check the first parameter
if [ "$1" == "start" ]; then
  if [ -f "$PID_FILE" ]; then
    echo "Server is already running. Use 'stop' first if you want to restart it."
  else
    echo "Starting the Node.js server..."
    # Start the server in the background using nohup and save its PID
    nohup node $NODE_SERVER_FILE > $LOG_FILE 2>&1 &
    echo $! > "$PID_FILE"
    echo "Server started with PID $(cat $PID_FILE)."
  fi

elif [ "$1" == "stop" ]; then
  if [ -f "$PID_FILE" ]; then
    PID=$(cat "$PID_FILE")
    echo "Stopping the Node.js server with PID $PID..."
    # Kill the server process
    kill "$PID"
    rm -f "$PID_FILE"
    echo "Server stopped."
  else
    echo "No server is running."
  fi

else
  echo "Usage: $0 {start|stop}"
fi

root@bcfbf592000e:/passoire/crypto-helper#