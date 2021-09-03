# mini site de recherche de fichier 
## Auteur du projet
Ce projet à était créée par moi (tristan carnesciali)

## pour ce site vous aurez besoin de :
- wampserveur (pour le tester en local)
- visual studio code (pour le code) 

## voici le code de recherhce de fichier 

```php
 function rechercherficiheripp($ipp){
    $dossier = 'C:Users/tcarnesciali/Desktop/RM_RECUP_TOTALE/extract';
    $ouverture = opendir($dossier);

    // Stockage des variables
    $annees = array();
    while ($fichierannee = readdir($ouverture)) {
        if ($fichierannee != "." && $fichierannee != "..") {//ne prend pas en compte ses fichier invisible
            $annees[] = $fichierannee;
        }
    }
    closedir($ouverture);

    foreach ($annees as $annee) {
        $dossier = 'C:Users/tcarnesciali/Desktop/RM_RECUP_TOTALE/extract/'.$annee.'';//cherche les fichier corespondent dans dossier (avec le foreach)
        $ouverture = opendir($dossier);
        $contenu = array();
        while ($fichieripp = readdir($ouverture)) {
            if ($fichieripp != "." && $fichieripp != "..") { //ne prend pas en compte ses fichier invisible
                $contenu[] = $fichieripp;
            }
        }
        closedir($ouverture);

        foreach ($contenu as $liste_fichier_ipp) {
            if (substr($liste_fichier_ipp,-3) != "xml"){ //permet de ne pas prendre en compte les fichier xml
                if (substr($liste_fichier_ipp,0,12) == $ipp) { //permet de verifier si il y a un numéro du fichier qui correspond avec qu'on a rentrée à la page d'avant
                    if (filesize($dossier.'/'.$liste_fichier_ipp)>3200) //ne prend pas en compte les fichier qui moins de 3200 octet
                        echo "$liste_fichier_ipp\n " ; //affiche les fichier trouvés
                }
            }
        }
    }
}
```

## Resultat de la racherche

![recherche](https://www.zupimages.net/up/21/35/bzqn.png)



