    # kubectl-cheat-sheet
    https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-output-verbosity-and-debugging 
    
    https://unofficial-kubernetes.readthedocs.io/en/latest/user-guide/kubectl-cheatsheet/

    # install kubectl
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x kubectl 
    sudo mv kubectl /usr/local/bin
    
    # Auto completion for alias
    cat <<EOF >> $HOME/.bashrc
    alias k=kubectl
    complete -F __start_kubectl k
    source <(kubectl completion bash)
    EOF
 
    . $HOME/.bashrc


    # Install helm
    HELM_RELEASE=3.17.3
    wget https://get.helm.sh/helm-v$HELM_RELEASE-linux-amd64.tar.gz
    tar zxvf helm-v$HELM_RELEASE-linux-amd64.tar.gz 
    sudo cp linux-amd64/helm /usr/local/bin
    rm -fr linux-amd64/
        
    # k9s https://k9scli.io/ 
    K9S_RELEASE=0.50.6
    wget https://github.com/derailed/k9s/releases/download/v$K9S_RELEASE/k9s_Linux_amd64.tar.gz
    gunzip k9s_Linux_amd64.tar.gz && tar xf k9s_Linux_amd64.tar && rm k9s_Linux_amd64.tar
    chmod +x k9s
    sudo mv k9s /usr/local/bin/


    # kubectx + kubens: Power tools for kubectl
    # https://github.com/ahmetb/kubectx#installation
    sudo git clone https://github.com/ahmetb/kubectx /opt/kubectx
    sudo ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx
    sudo ln -s /opt/kubectx/kubens /usr/local/bin/kubens



    # DNS
    # kubectl run netutils --image=gcr.io/run-ai-lab/netutils --restart=Never -- sleep infinity
    k apply -f dnsutils.yml 
    
    k get svc 
    k exec -n default dnsutils -- nslookup 10.111.49.242
    242.49.111.10.in-addr.arpa	name = spark-master.hpe-ai-coe.svc.cluster.local.
