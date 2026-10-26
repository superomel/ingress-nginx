cd images/nginx/rootfs
docker build --network=host -t 614895517292.dkr.ecr.us-east-2.amazonaws.com/patch/ingress-nginx:1.30.6-patch-rootfs -f Dockerfile .

cd ../../

REGISTRY="614895517292.dkr.ecr.us-east-2.amazonaws.com/patch/ingress-nginx"
 \
                                    TAG="1.30.6-patched" \
                                    ARCH="amd64" \
                                    BASE_IMAGE="614895517292.dkr.ecr.us-east-2.amazonaws.com/patch/ingress-nginx:1.30.6-patch-rootfs" \
                                    make clean-image build image

docker tag 614895517292.dkr.ecr.us-east-2.amazonaws.com/patch/ingress-nginx/controller:1.30.6-patched 614895517292.dkr.ecr.us-east-2.amazonaws.com/patch/ingress-nginx:1.30.6-patched
