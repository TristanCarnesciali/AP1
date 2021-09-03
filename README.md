# le temps des tempêtes
## Auteur du projet
Ce projet à était créée par moi (tristan carnesciali)</br>
voici une photo de moi</br>
![gigachad](https://i.kym-cdn.com/photos/images/newsfeed/002/143/785/bca.jpg)

## voici un peux de code

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
test [site](https://pointerpointer.com/)



