#!/bin/bash

# Copyright (C) 2022 WhiteBlackGoose
# 
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; If not, see <http://www.gnu.org/licenses/>.

cd ~/.password-store

PROBLEMS=0
for i in `find . -name "*.gpg" -type f`; do
    gpg --pinentry-mode cancel --list-packets $i 2> /tmp/pass-check-health-error > /dev/null
    if [[ -f /tmp/pass-check-health-error ]]; then
        o=$(cat /tmp/pass-check-health-error)
        if [[ $o == *"gpg: decryption failed: No secret key"* ]]; then
        if [[ $o != *"gpg: public key decryption failed: Operation cancelled"* ]]; then
            printf "No key for $i:\n"
            PROBLEMS=$(( $PROBLEMS + 1 ))
        fi
        fi
    fi
    rm /tmp/pass-check-health-error
done

printf "Found problems: $PROBLEMS\n"
