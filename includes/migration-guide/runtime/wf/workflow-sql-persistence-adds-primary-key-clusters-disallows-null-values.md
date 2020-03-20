---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802524"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trwałość SQL przepływu pracy dodaje klastry kluczy podstawowych i nie zezwala na wartości null w niektórych kolumnach

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7, tabele utworzone dla magazynu wystąpień przepływu pracy SQL (SWIS) przez skrypt SqlWorkflowInstanceStoreSchema.sql używają klastrowanych kluczy podstawowych. Z tego powodu tożsamości nie <code>null</code> obsługują wartości. Zmiana ta nie ma wpływu na działanie SWIS. Aktualizacje zostały wprowadzone do obsługi replikacji transakcyjnej programu SQL Server.|
|Sugestia|Plik SQLWorkflowInstanceStoreSchemaUpgrade.sql musi być stosowany do istniejących instalacji, aby doświadczyć tej zmiany. Nowe instalacje bazy danych automatycznie zostaną zmienione.|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
