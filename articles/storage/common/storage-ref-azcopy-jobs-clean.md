---
title: azcopy jobs clean | Microsoft Docs
description: Cet article fournit des informations de référence sur la commande azcopy clean.
author: normesta
ms.service: storage
ms.topic: reference
ms.date: 07/24/2020
ms.author: normesta
ms.subservice: common
ms.reviewer: zezha-msft
ms.openlocfilehash: 4a2c717601747e15556608559450b35bb934410b
ms.sourcegitcommit: aaa65bd769eb2e234e42cfb07d7d459a2cc273ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98879103"
---
# <a name="azcopy-jobs-clean"></a>azcopy jobs clean

Supprimer tous les fichiers journaux et fichiers de plan pour tous les travaux

```
azcopy jobs clean [flags]
```

## <a name="related-conceptual-articles"></a>Articles conceptuels associés

- [Bien démarrer avec AzCopy](storage-use-azcopy-v10.md)
- [Transférer des données avec AzCopy et le Stockage Blob](./storage-use-azcopy-v10.md#transfer-data)
- [Transférer des données avec AzCopy et le stockage de fichiers](storage-use-azcopy-files.md)
- [Configurer, optimiser et dépanner AzCopy](storage-use-azcopy-configure.md)

## <a name="examples"></a>Exemples

```
  azcopy jobs clean --with-status=completed
```

## <a name="options"></a>Options

**--help**                Aide pour le nettoyage.

**--with-status** string   Supprime uniquement les travaux avec cet état, valeurs disponibles : `Canceled`, `Completed`, `Failed`, `InProgress`, `All` (par défaut `All`)

## <a name="options-inherited-from-parent-commands"></a>Options héritées des commandes parentes

**--cap-mbps float**      Limite la vitesse de transfert, en mégabits par seconde. Par moment, le débit peut dépasser légèrement cette limite. Si cette option est définie sur zéro ou si elle est omise, le débit n’est pas limité.

**--output-type** string   Met en forme la sortie de la commande. Les formats possibles sont « text » et « JSON ». La valeur par défaut est « text ». (par défaut : « text »).

La chaîne **--trusted-microsoft-suffixes** spécifie des suffixes de domaine supplémentaires où des jetons de connexion Azure Active Directory peuvent être envoyés.  La valeur par défaut est «  *.core.windows.net;* .core.chinacloudapi.cn; *.core.cloudapi.de;* .core.usgovcloudapi.net ». Tous les éléments répertoriés ici sont ajoutés à la valeur par défaut. Pour la sécurité, vous devez placer uniquement des domaines Microsoft Azure ici. Séparez plusieurs entrées par des points-virgules.

## <a name="see-also"></a>Voir aussi

- [azcopy jobs](storage-ref-azcopy-jobs.md)
