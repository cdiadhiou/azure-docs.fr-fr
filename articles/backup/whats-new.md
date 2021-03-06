---
title: Nouveautés de Sauvegarde Azure
description: En savoir plus sur les nouvelles fonctionnalités de Sauvegarde Azure.
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: 62a6146990863c339917777b2624fee76ebe60d8
ms.sourcegitcommit: 9d9221ba4bfdf8d8294cf56e12344ed05be82843
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98569417"
---
# <a name="whats-new-in-azure-backup"></a>Nouveautés de Sauvegarde Azure

Sauvegarde Azure s’améliore constamment et publie de nouvelles fonctionnalités qui améliorent la protection de vos données dans Azure. Ces nouvelles fonctionnalités étendent la protection de vos données aux nouveaux types de charges de travail, améliorent la sécurité et améliorent la disponibilité de vos données de sauvegarde. Elles ajoutent également de nouvelles fonctionnalités de gestion, de surveillance et d’automatisation.

Pour en savoir plus sur les nouvelles versions, vous pouvez créer un signet sur cette page ou [vous abonner aux mises à jour ici](https://azure.microsoft.com/updates/?query=backup).

## <a name="updates-summary"></a>Résumé des mises à jour

- Janvier 2021
  - [Sauvegarde de disque Azure (en préversion)](disk-backup-overview.md)
  - [Chiffrement au repos à l’aide de clés gérées par le client désormais généralement disponible](encryption-at-rest-with-cmk.md)
- Novembre 2020
  - [Modèle Azure Resource Manager pour une sauvegarde de partage de fichiers Azure (AFS)](#azure-resource-manager-template-for-afs-backup)
  - [Sauvegardes incrémentielles pour les bases de données SAP HANA sur des machines virtuelles Azure](#incremental-backups-for-sap-hana-databases)
- Septembre 2020
  - [Centre de sauvegarde](#backup-center)
  - [Sauvegarder Azure Database pour PostgreSQL](#backup-azure-database-for-postgresql)
  - [Sauvegarde et restauration sélectives sur disque](#selective-disk-backup-and-restore)
  - [Restauration inter-région pour les bases de données SQL Server et SAP HANA sur des machines virtuelles Azure](#cross-region-restore-for-sql-server-and-sap-hana)
  - [Prise en charge de la sauvegarde de machines virtuelles avec un maximum de 32 disques](#support-for-backup-of-vms-with-up-to-32-disks)
  - [Expérience de configuration de la sauvegarde simplifiée pour SQL dans les machines virtuelles Azure](#simpler-backup-configuration-for-sql-in-azure-vms)
  - [Sauvegarde SAP HANA dans des machines virtuelles RHEL Azure](#backup-sap-hana-in-rhel-azure-virtual-machines)
  - [Stockage redondant interzone (ZRS) pour les données de sauvegarde](#zone-redundant-storage-zrs-for-backup-data)
  - [Suppression réversible pour les charges de travail SQL Server et SAP HANA dans les machines virtuelles Azure](#soft-delete-for-sql-server-and-sap-hana-workloads)

## <a name="azure-disk-backup-in-preview"></a>Sauvegarde de disque Azure (en préversion)

La sauvegarde de disques Azure offre une solution clé en main qui fournit une gestion du cycle de vie des instantanés pour les [disques managés Azure](https://docs.microsoft.com/azure/virtual-machines/managed-disks-overview) en automatisant la création périodique d’instantanés et en les conservant pour une durée configurée à l’aide d’une stratégie de sauvegarde. Vous pouvez gérer les instantanés des disques sans aucun coût d’infrastructure et sans avoir recours à aucun script personnalisé ni aucune surcharge de gestion. Il s’agit d’une solution de sauvegarde avec cohérence en cas d’incident qui effectue une sauvegarde ponctuelle d’un disque managé au moyen d’[instantanés incrémentiels](https://docs.microsoft.com/azure/virtual-machines/windows/disks-incremental-snapshots) avec une prise en charge de plusieurs sauvegardes par jour. Il s’agit également d’une solution sans agent qui n’a pas d’impact sur les performances des applications de production. Elle prend en charge la sauvegarde et la restauration des disques du système d’exploitation et des données (y compris des disques partagés), qu’ils soient ou non actuellement attachés à une machine virtuelle Azure en cours d’exécution.

Pour plus d’informations, consultez [Sauvegarde de disque Azure (en préversion)](disk-backup-overview.md).

## <a name="encryption-at-rest-using-customer-managed-keys"></a>Chiffrement au repos à l’aide de clés gérées par le client

La prise en charge du chiffrement au repos à l’aide de clés gérées par le client est désormais généralement disponible. Vous avez ainsi la possibilité de chiffrer les données de sauvegarde dans vos coffres Recovery Services à l’aide de vos propres clés stockées dans des coffres de clés Azure. La clé de chiffrement utilisée pour le chiffrement des sauvegardes dans le coffre Recovery Services peut être différente de celle utilisée pour le chiffrement de la source. Les données sont protégées à l’aide d’une clé de chiffrement des données basée sur l’algorithme AES 256, qui est à son tour protégée à l’aide de vos clés stockées dans le Key Vault. Par rapport au chiffrement à l’aide de clés gérées par la plateforme (qui est disponible par défaut), cela vous offre davantage de contrôle sur vos clés et peut vous aider à mieux répondre à vos besoins en matière de conformité.

Pour plus d’informations, consultez [Chiffrement des données de sauvegarde à l’aide de clés gérées par le client](encryption-at-rest-with-cmk.md).

## <a name="azure-resource-manager-template-for-afs-backup"></a>Modèle Azure Resource Manager pour une sauvegarde AFS

Sauvegarde Azure prend désormais en charge la configuration de la sauvegarde pour les partages de fichiers Azure existants à l’aide d’un modèle Azure Resource Manager (ARM). Le modèle configure la protection d’un partage de fichiers Azure existant en spécifiant les détails appropriés pour le coffre et la stratégie de sauvegarde Recovery Services. Il crée éventuellement un coffre et une stratégie de sauvegarde Recovery Services, puis enregistre le compte de stockage contenant le partage de fichiers dans le coffre Recovery Services.

Pour plus d’informations, consultez [Modèles Azure Resource Manager pour la Sauvegarde Azure](backup-rm-template-samples.md).

## <a name="incremental-backups-for-sap-hana-databases"></a>Sauvegardes incrémentielles pour les bases de données SAP HANA

Sauvegarde Azure prend maintenant en charge les sauvegardes incrémentielles pour les bases de données SAP HANA hébergées sur des machines virtuelles Azure. Cela permet d’obtenir des sauvegardes plus rapides et plus rentables de vos données SAP HANA.

Pour plus d’informations, consultez [diverses options disponibles lors de la création d’une stratégie de sauvegarde](sap-hana-faq-backup-azure-vm.md#policy) et la procédure de [création d’une stratégie de sauvegarde pour les bases de données SAP HANA](tutorial-backup-sap-hana-db.md#creating-a-backup-policy).

## <a name="backup-center"></a>Centre de sauvegarde

Sauvegarde Azure a activé une nouvelle fonctionnalité de gestion native pour gérer l’ensemble de votre espace de sauvegarde à partir d’une console centrale. Le centre de sauvegarde vous offre la possibilité de surveiller, d’utiliser, de gérer et d’optimiser la protection des données à grande échelle de façon cohérente et unifiée avec les expériences de gestion natives d’Azure.

Avec le centre de sauvegarde, vous bénéficiez d’une vue agrégée de votre inventaire sur les abonnements, les emplacements, les groupes de ressources, les coffres et même les locataires à l’aide d’Azure Lighthouse. Le centre de sauvegarde est également un centre d’action dans lequel vous pouvez déclencher vos activités de sauvegarde, telles que la configuration de la sauvegarde, la restauration, la création de stratégies ou de coffres, le tout à partir d’un seul emplacement. En outre, grâce à une intégration transparente à Azure Policy, vous pouvez désormais gérer votre environnement et suivre la conformité du point de vue de la sauvegarde. Les stratégies Azure intégrées spécifiques à Sauvegarde Azure vous permettent également de configurer des sauvegardes à grande échelle.

Pour plus d’informations, consultez [Vue d’ensemble du centre de sauvegarde](backup-center-overview.md).

## <a name="backup-azure-database-for-postgresql"></a>Sauvegarder Azure Database pour PostgreSQL

Sauvegarde Azure et les services de base de données Azure constituent ensemble une solution de sauvegarde d’entreprise pour Azure PostgreSQL (maintenant en préversion). Vous pouvez désormais répondre à vos besoins de conformité et de protection des données avec une stratégie de sauvegarde contrôlée par le client qui permet la rétention des sauvegardes pendant maximum 10 ans. Vous disposez ainsi d’un contrôle granulaire pour gérer les opérations de sauvegarde et de restauration au niveau de la base de données individuelle. De même, vous pouvez effectuer des restaurations dans les versions PostgreSQL ou dans le stockage d’objets Blob en toute simplicité.

Pour plus d’informations, consultez [Sauvegarde Azure Database pour PostgreSQL](backup-azure-database-postgresql.md).

## <a name="selective-disk-backup-and-restore"></a>Sauvegarde et restauration sélectives sur disque

Sauvegarde Azure prend en charge la sauvegarde de tous les disques (système d’exploitation et données) d’une machine virtuelle à travers la solution de sauvegarde de machine virtuelle. Désormais, en utilisant la fonctionnalité de sauvegarde et restauration sélectives de disques, vous pouvez sauvegarder un sous-ensemble de disques de données d’une machine virtuelle. Cela offre une solution efficace et économique pour vos besoins en sauvegarde et restauration. Chaque point de récupération contient uniquement les disques inclus dans l’opération de sauvegarde.

Pour plus d’informations, consultez [Sauvegarde et restauration sélectives sur disque pour les machines virtuelles Azure](selective-disk-backup-restore.md).

## <a name="cross-region-restore-for-sql-server-and-sap-hana"></a>Restauration inter-région pour SQL Server et SAP HANA

Grâce à l’introduction de la restauration inter-région, vous pouvez maintenant initier des restaurations dans une région secondaire à votre gré pour réduire les réels problèmes de temps d’arrêt dans une région principale pour votre environnement. Ainsi, la région secondaire effectue la restauration sous le contrôle total du client. Sauvegarde Azure utilise les données sauvegardées répliquées dans la région secondaire pour de telles restaurations.

Désormais, en plus de la prise en charge de la restauration inter-région pour les machines virtuelles Azure, la fonctionnalité a été étendue à la restauration des bases de données SQL et SAP HANA dans les machines virtuelles Azure également.

Pour plus d’informations, consultez [Restauration inter-région pour les bases de données SQL](restore-sql-database-azure-vm.md#cross-region-restore) et [Restauration inter-région pour les bases de données SAP HANA](sap-hana-db-restore.md#cross-region-restore).

## <a name="support-for-backup-of-vms-with-up-to-32-disks"></a>Prise en charge de la sauvegarde de machines virtuelles avec un maximum de 32 disques

Jusqu’à présent, Sauvegarde Azure prenait en charge 16 disques managés par machine virtuelle. Désormais, Sauvegarde Azure prend en charge la sauvegarde d’un maximum de 32 disques managés par machine virtuelle.

Pour plus d’informations, consultez [Matrice de prise en charge de stockage de machine virtuelle](backup-support-matrix-iaas.md#vm-storage-support).

## <a name="simpler-backup-configuration-for-sql-in-azure-vms"></a>Configuration de sauvegarde plus simple pour SQL dans les machines virtuelles Azure

La configuration de sauvegardes pour votre SQL Server dans les machines virtuelles Azure est désormais encore plus facile avec la configuration de sauvegarde en ligne intégrée au volet des machines virtuelles du portail Azure. En quelques étapes, vous pouvez activer la sauvegarde de vos SQL Server pour protéger toutes les bases de données existantes, ainsi que celles qui sont ajoutées ultérieurement.

Pour plus d’informations, consultez [Sauvegarder un SQL Server à partir du volet de la machine virtuelle](backup-sql-server-vm-from-vm-pane.md).

## <a name="backup-sap-hana-in-rhel-azure-virtual-machines"></a>Sauvegarde SAP HANA sur des machines virtuelles RHEL Azure

Sauvegarde Azure est la solution de sauvegarde native pour Azure et est certifiée BackInt par SAP. Sauvegarde Azure a maintenant ajouté la prise en charge de Red Hat Enterprise Linux (RHEL), l’un des systèmes d’exploitation Linux les plus courants exécutant SAP HANA.

Pour plus d’informations, consultez [Matrice de prise en charge du scénario de sauvegarde de base de données SAP HANA](sap-hana-backup-support-matrix.md#scenario-support).

## <a name="zone-redundant-storage-zrs-for-backup-data"></a>Stockage redondant interzone (ZRS) pour les données de sauvegarde

Stockage Azure offre un bon compromis entre hautes performances, haute disponibilité et haute résilience des données grâce à ses diverses options de redondance. Sauvegarde Azure vous permet d’étendre ces avantages aux données de sauvegarde, avec des options pour stocker vos sauvegardes dans un stockage localement redondant (LRS) et un stockage géoredondant (GRS). Maintenant, il existe des options de durabilité supplémentaires avec la prise en charge supplémentaire du stockage redondant interzone (ZRS).

Pour plus d’informations, consultez [Définir la redondance du stockage pour le coffre Recovery Services](backup-create-rs-vault.md#set-storage-redundancy).

## <a name="soft-delete-for-sql-server-and-sap-hana-workloads"></a>Suppression réversible pour les charges de travail SQL Server et SAP HANA

Les préoccupations en matière de risques de sécurité, comme les logiciels malveillants, le ransomware et les intrusions, sont de plus en plus nombreuses. Ces problèmes de sécurité peuvent coûter cher, à la fois en termes d’argent et de données. Pour vous protéger contre ces attaques, Sauvegarde Azure fournit des fonctionnalités de sécurité visant à protéger les données de sauvegarde après la suppression.

Une fonctionnalité de ce type est la suppression réversible. Avec la suppression réversible, même si un intervenant malveillant supprime une sauvegarde (ou même si les données de sauvegarde sont accidentellement supprimées), les données de sauvegarde sont conservées pendant 14 jours supplémentaires, ce qui permet la récupération de cet élément de sauvegarde sans perte de données. La conservation des données de sauvegarde pendant 14 jours supplémentaires à l’état « suppression réversible » n’engendre aucun frais pour vous.

Actuellement, en plus de la prise en charge de la suppression réversible pour les machines virtuelles Azure, les charges de travail SQL Server et SAP HANA dans les machines virtuelles Azure sont également protégées avec la suppression réversible.

Pour plus d’informations, consultez [Suppression réversible pour les charges de travail SQL Server sur une machine virtuelle Azure et SAP HANA sur une machine virtuelle Azure](soft-delete-sql-saphana-in-azure-vm.md).

## <a name="next-steps"></a>Étapes suivantes

- [Aide et bonnes pratiques de Sauvegarde Azure](guidance-best-practices.md)
