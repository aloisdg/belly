#!/bin/bash

# http://unix.stackexchange.com/q/47407/150597
# http://stackoverflow.com/q/192249/1248177
# http://stackoverflow.com/q/3601515/1248177

while [[ $# -gt 1 ]]
do
key="$1"

case $key in
    -h|--head)
    HEAD="$2"
    shift
    ;;
    -t|--tail)
    TAIL="$2"
    shift
    ;;
    -n|--number)
    NUMBER=YES
    ;;
    *)
    ;;
esac
shift
done

if [ -z "${1+x}" ]; then
    echo "Error: Input file is missing."
    exit 1
fi

if [ "$HEAD" -gt "$TAIL" ]; then
    echo "Error: HEAD cant be greater than TAIL."
    exit 1
fi

if [ -z "${NUMBER+x}" ]; then
    tail -n +"$HEAD" "$1" | head -n $((TAIL-HEAD+1))
else
    tail -n +"$HEAD" "$1" | head -n $((TAIL-HEAD+1)) | cat -n
fi
