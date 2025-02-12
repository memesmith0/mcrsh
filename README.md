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

#new mcrsh code
#mcr() { mcrsh_macros=":$(printf "%s" "$1" | awk '{gsub(":","\\:");gsub("\n","\\\\n");print}')" ; mcrsh_c="$((mcrsh_c + 1))" ; } ;
#mcrsh_get(){ printf "%s" "$mcrsh_macros" | awk -v n="$1" '{for(i=0;i<length($0);i++){c=substr($0,i+1,1)if(c==":" && last !="\\"){g++}else if(g==n){printf "%s", c}last=c}}' ; } ;
#mcrsh(){ while read -r mcrsh_code_line; do for mcrsh_current_macro in $(seq 1 "$mcrsh_c"); do
#mcrsh_decoded_macro="$( printf "%s" "$(printf "%s" "$decoded_macro" | awk "$(mcrsh_get "$mcrsh_decoded_macro" )" )" | awk '{gsub("\\:",":");gsub("\\\\n","\n");print}' )" ;
#    done; eval "$mcrsh_code_line"; done ; } ;
#mcrsh

