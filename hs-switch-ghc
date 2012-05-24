#!/bin/bash
#
# Switch GHC's version (recreate symbolic links).
#

path="/usr/local/bin"

version=${1}

if [ "${version}" == "" ] ; then
    echo "usage: ./ghc_switch.sh <version>"
    exit 0
fi

ghc_target=$(ls ${path} | grep "^ghc-${version}")
ghci_target=$(ls ${path} | grep "^ghci-${version}")
ghc_pkg_target=$(ls ${path} | grep "^ghc-pkg-${version}")
haddock_target=$(ls ${path} | grep "^haddock-ghc-${version}")

i=0
for x in ${ghc_target} ; do
    i=$((i+1))
done

if [ ${i} -eq 0 ] ; then
    echo "no such version"
    exit 0
elif [ $i -ne 1 ] ; then
    echo "too generic version, match with:"
    echo "${ghc_target}"
    exit 0
fi

echo "ghc -> ${ghc_target}"
ln -sf "${path}/${ghc_target}" "${path}/ghc"

echo "ghci -> ${ghci_target}"
ln -sf "${path}/${ghci_target}" "${path}/ghci"

echo "ghc-pkg -> ${ghc_pkg_target}"
ln -sf "${path}/${ghc_pkg_target}" "${path}/ghc-pkg"

echo "haddock -> ${haddock_target}"
ln -sf "${path}/${haddock_target}" "${path}/haddock"
