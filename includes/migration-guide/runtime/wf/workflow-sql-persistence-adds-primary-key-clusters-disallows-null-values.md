---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760442"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Dodaje stanów trwałych programu SQL przepływu pracy, klucz podstawowy klastrów i nie zezwalają na wartości null w niektórych kolumn

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7, tabele utworzone dla Store wystąpienia przepływu pracy SQL (SWIS) przy użyciu skryptu SqlWorkflowInstanceStoreSchema.sql Użyj klastra kluczy podstawowych. W związku z tym nie obsługują tożsamości <code>null</code> wartości. Działanie SWIS nie ma wpływu tej zmiany. Aktualizacje zostały wprowadzone do obsługi Replikacja transakcyjna programu SQL Server.|
|Sugestia|Plik SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql musi zostać zastosowana do istniejącej instalacji, aby to zmienić. Nowe instalacje bazy danych zostaną automatycznie zmiany.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

