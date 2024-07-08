# Workflow 1

1- creer un repo sur GitHub <br>
2- creer un README.md ; visualiser les commits sur GitHub (red & green)  
3- cloner le repo sur la machine locale soit en utilisant <strong>https</strong> ou <strong>SSH</strong> url   

```
git clone https/ssh url 
```

effectuer des changements , naviguer au repo ,executer ensuite

```
git status
```
>git status : shows files that are created / updated/deleted but haven't been saved in a commit yet
 utiliser ensuite la commande git add file ou git add .
```
git add .
```
faire un commit => les changements sont enregistrés de manière locale
```
git commit -m "commit message" -m "description"
```
faire un push , pour faire apparaitre les changemnts sur le repo live sur GitHub

```
git push origin master 
```
pour une première fois , il faut configurer sa clé SSH en 3 étapes :
1- génerer la clé SSH
```
ssh-keygen -t ed25519 -C “user@example.com”
```
2- ajouté la clé publique au compte GitHub   
3- Specifier la clé SSH  au ssh-agent

```
eval "$(ssh-agent -s)"


```
```
ssh-add ~/.ssh/id_ed25519
```

# Workflow 2
