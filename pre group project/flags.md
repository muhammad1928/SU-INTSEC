# root@bcfbf592000e:/passoire/config# cat passoire.sql
# flag 3
crypto.php     docker-compose.yml  flag_3           index.php  logout.php  my_files.php       settings.php  
# flag 5
(3, 'flag_5', 'see-password-hash@that-is-the-fl.ag', 'dc55c5867507fbafc3a2284dcd80028cdb948412'),

# root@bcfbf592000e:/passoire/crypto-helper#

# root@bcfbf592000e:/passoire/crypto-helper# cat crypto-helper.sh 
## flag 9
crypto-helper.sh  flag_9  node_modules  package-lock.json  package.json  server.js
flag_9 is 564ffa189a52c873f94be7bcab00ef6a259435b8.

This flag is readable by an attacker if something is insecure in the crypto-helper api. But that shouldn't be the case, right?

trying to find more
and more