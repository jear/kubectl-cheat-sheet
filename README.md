    # kubectl-cheat-sheet
    https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-output-verbosity-and-debugging 

    # install kubectl
    curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
    chmod +x kubectl 
    sudo mv kubectl /usr/local/bin

        
    # k9s https://k9scli.io/ 
    wget https://github.com/derailed/k9s/releases/download/v0.24.2/k9s_Linux_x86_64.tar.gz

    # DNS
    kubectl run netutils --image=gcr.io/run-ai-lab/netutils --restart=Never -- sleep infinity
