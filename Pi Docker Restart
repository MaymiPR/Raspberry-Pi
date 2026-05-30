#!/bin/bash

echo "============================="
echo "     PI DOCKER RESTART       "
echo "============================="
echo ""

if ! command -v docker &>/dev/null; then
    echo "Docker is not installed."
    exit 1
fi

echo "Available containers:"
echo ""
docker ps -a --format "{{.Names}}\t{{.Status}}" | nl -w2 -s") "

echo ""
read -p "Enter container name to restart: " container < /dev/tty

if [ -z "$container" ]; then
    echo "No container entered, exiting."
    exit 1
fi

if docker ps -a --format "{{.Names}}" | grep -q "^${container}$"; then
    echo ""
    echo "Restarting $container..."
    docker restart "$container"
    echo "Done!"
else
    echo "Container '$container' not found."
fi

echo ""
echo "============================="
