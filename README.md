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

1- je commence par créer mon repo sur ma machine locale  
2- executer la commande ls-la ; qu'est ce qu'on remarque  
3-ce n'est pas un git repo  
```
git init
```
4- qd on execute 
```
git status
```
on remarque que les fichiers sont untracked , il faut les stager donc on execute
```
git add .
```

5-faire commit  
6- si on essaie push ça marche pas , car git ne sait où il doit faire le push    
Donc il faut revenir créer un remote repo dans gitHub et le connecter au repo local sur ma machine
7-puis Faire le push en spécifiant cette fois la référence càd le ssh url de notre remote repo  
```
git remote add origin ssh url
```
8- pour voir les repo remote connectés à celui local :  
```
git remote -v
```
9-finalement faire le push  

```
git push --set-upstream origin master
```
 # Branching
 Default Branch == Master/Main/Dev    
 On peut éventuellemnt créer d'autre branches avant de merger == feature branch 

 
 1- pour faire apparaitre les branches de mon repo  
 
```
git branch
```

2-Pour créer une nouvelle branche  

```
git checkout -n branch-name
```
3- Pour switch entre les branches  

```
git checkout target-branch
```
 4-par exemple je vais créer une branche qui va contenir des modifications sur mon README.md  
 
```
git branch -b feature-readme-instructions
```

 5-maintenant j'effectue des changements sur ma feature branch , je fais add puis commit puis   
 
```
git push --set-upstream feature-readme-instructions
```

6-On regarde sur gitHub == LA Branche est bien rajoutée  

## pull request 

> it's a request to have your code pulled to another branch
Par exemple ici on va puller de feature au master branch


<br>
Géneralement lorqu'on fait un pull request c'est pour que le code soit révisé et confirmé   
Une fois le code est mergé au mastee , il faut nettoyé cette feature branch càd la suprimmer  

```
git branch -d name
```

On remarque que c'est changement n'apparaissent que sur GitHub et non sur l'editeur   , faire alors un pull
```
git pull origin master
```

## Merging Conflicts 

C'est qd deux personnes par exemple modifient les memes parties du code sur deux branches différentes et procédent pour merger dans la branche master == overwritten files
