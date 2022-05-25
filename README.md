# kubectl-bash-auto-completion

## Introduction
The kubectl completion script for Bash can be generated with the command ```kubectl completion bash```. Sourcing the completion script in your shell enables kubectl autocompletion.

However, the completion script depends on bash-completion, which means that you have to install this software first (you can test if you have bash-completion already installed by running ```type _init_completion```).

## Install bash-completion
bash-completion is provided by many package managers. You can install it with ```apt-get install bash-completion``` or ```yum install bash-completion```, etc.

The above commands create ```/usr/share/bash-completion/bash_completion```, which is the main script of bash-completion. Depending on your package manager, you have to manually source this file in your ```~/.bashrc``` file.

To find out, reload your shell and run ```type _init_completion```. If the command succeeds, you're already set, otherwise add the following to your ```~/.bashrc``` file:

```
source /usr/share/bash-completion/bash_completion
```

Reload your shell and verify that bash-completion is correctly installed by typing ```type _init_completion```.

## Enable kubectl autocompletion
You now need to ensure that the kubectl completion script gets sourced in all your shell sessions:

```
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
```

If you have an alias for kubectl, you can extend shell completion to work with that alias:

```
echo 'alias k=kubectl' >> ~/.bashrc
echo 'complete -F __start_kubectl k' >> ~/.bashrc
```

At the end, needs to reload your shell:

```
bash -l
```
