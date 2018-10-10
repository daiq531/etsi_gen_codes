# etsi_gen_codes
store the ETSI NFV SOL generated codes client part python egg package 

Steps
1. view online SOL interface yaml defination:
LCM link: https://forge.etsi.org/swagger/editor/?url=https://forge.etsi.org/jenkins/job/NFV%20-%20Network%20Functions%20Virtualisation/job/sol002-sol003-master/lastSuccessfulBuild/artifact/build/SOL003-VNFLifecycleManagement-API.yaml/*view*/
PKGM link: https://forge.etsi.org/swagger/editor/?url=https://forge.etsi.org/jenkins/job/NFV%20-%20Network%20Functions%20Virtualisation/job/sol002-sol003-master/lastSuccessfulBuild/artifact/build/SOL003-VNFPackageManagement-API.yaml/*view*/

2. download SOL spec yaml file
wget https://forge.etsi.org/jenkins/job/NFV%20-%20Network%20Functions%20Virtualisation/job/sol002-sol003-master/lastSuccessfulBuild/artifact/build/SOL003-VNFLifecycleManagement-API.yaml
wget https://forge.etsi.org/jenkins/job/NFV%20-%20Network%20Functions%20Virtualisation/job/sol002-sol003-master/lastSuccessfulBuild/artifact/build/SOL003-VNFPackageManagement-API.yaml

3. get swagger-codegen
wget http://central.maven.org/maven2/io/swagger/swagger-codegen-cli/2.2.3/swagger-codegen-cli-2.2.3.jar -O swagger-codegen-cli.jar

4. generate client code
java -jar swagger-codegen-cli.jar generate -i SOL003-VNFPackageManagement-API.yaml -l python -o out/sol003_pkgm_client/ -D supportPython2=true -D packageName=sol003_pkgm_client
java -jar swagger-codegen-cli.jar generate -i SOL003-VNFLifecycleManagement-API.yaml -l python -o out/sol003_lcm_client/ -D supportPython2=true -D packageName=sol003_lcm_client

5. generate python egg package
python setup.py bdist_egg

Note:
1. The newest swagger-codegen version can not work correctlly.
2. store the original interface yaml file in case the online file on forge change frequentlly.
