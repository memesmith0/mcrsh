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
#mcrsh_c=0
#mcr_macros=""

#mcr() { mcr_macros=":$(printf "%s" "$1" | awk '{gsub(":","\\\\:");gsub("\n","\\\\n");print}')" ; mcrsh_c="$((mcrsh_c + 1))" ; } ;
#
#mcrsh() {
#  while read -r mcrsh_code_line; do
#    for mcrsh_current_macro in $(seq 1 "$mcrsh_c"); do
#      mcrsh_encoded_macro=$(printf "%s" "$mcr_macros" | awk '{gsub("\\\\:",":"); print}' | awk -v g="$mcrsh_current_macro" '{if(NR==g){print $0;exit}}')
#      if [ -n "$mcrsh_encoded_macro" ]; then
#        decoded_macro=$(printf "%s" "$mcrsh_encoded_macro" | awk '{gsub("\\\\:",":");gsub("\\\\n","\n");print}')
#        mcrsh_code_line=$(echo "$mcrsh_code_line" | sed "s/\$${mcrsh_current_macro}/$decoded_macro/g")
#      fi
#    done
#    eval "$mcrsh_code_line"
#  done
#}

#mcrsh
#mcrsh_c=0
