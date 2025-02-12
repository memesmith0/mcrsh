#!/usr/bin/sh
#Copyright (C) 2025 by john morris beck <john.morris.beck@hotmail.com>
#
#Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is#hereby granted.
#
#THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL
#
#IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER
#
#RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF
#
#THIS SOFTWARE.
#old mcrsh
mcr(){ while read -r i; do eval "$( printf "%s" "$i" | awk "$1" ; )" ; done ; } &&
mcrsh(){ while read -r i; do eval "$i"; done ; } &&
mcrsh ; 

#new mcrsh
#mcrsh_c=0
#mcr() { mcrsh_m="$mcrsh_m:$(printf "%s" "$1" | awk '{gsub(":","\\:");gsub("\n","\\\\n");print}')" ; mcrsh_c="$((mcrsh_c + 1))" ; } ;
#mcrsh(){ while read -r mcrsh_l; do mcrsh_e="$mcrsh_l"; if [ "$mcrsh_c" -gt "0" ] ; then mcrsh_i=1; while [ "$mcrsh_i" -le "$mcrsh_c" ]; do 
#								      mcrsh_e="$(printf "%s" "$mcrsh_e" | awk "$(printf "%s" "$mcrsh_m" | awk -v n="$mcrsh_i" '{for(;i<length($0);i++){c=substr($0,i+1,1);if(c==":"&&l !="\\"){g++}else if(g==n){printf "%s",c}l=c}}' | awk '{gsub("\\:",":");gsub("\\\\n","\n");print}')" )" ; mcrsh_i="$((mcrsh_i + 1))" ; 
#done; fi; eval "$mcrsh_e"; done ; } ;
#mcrsh
