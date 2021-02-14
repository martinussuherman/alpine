#!/bin/sh

if [ ! -z "$ECHOWNDIRS" ]; then
   if [ ! -d "$ECHOWNDIRS" ]; then
      mkdir -p $ECHOWNDIRS
   fi

   chown $EUSER:$EGROUP $ECHOWNDIRS
fi

if [ ! -z "$ECHOWNFILES" ]; then
   if [ ! -f "$ECHOWNFILES" ]; then
      touch $ECHOWNFILES
   fi

   chown $EUSER:$EGROUP $ECHOWNFILES
fi
