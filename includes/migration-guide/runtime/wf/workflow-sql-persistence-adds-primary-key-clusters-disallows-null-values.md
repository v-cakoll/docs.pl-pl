---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802524"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Dodaje stanów trwałych programu SQL przepływu pracy, klucz podstawowy klastrów i nie zezwalają na wartości null w niektórych kolumn

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.7, tabele utworzone dla Store wystąpienia przepływu pracy SQL (SWIS) przy użyciu skryptu SqlWorkflowInstanceStoreSchema.sql Użyj klastra kluczy podstawowych. W związku z tym nie obsługują tożsamości <code>null</code> wartości. Działanie SWIS nie ma wpływu tej zmiany. Aktualizacje zostały wprowadzone do obsługi Replikacja transakcyjna programu SQL Server.|
|Sugestia|Plik SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql musi zostać zastosowana do istniejącej instalacji, aby to zmienić. Nowe instalacje bazy danych zostaną automatycznie zmiany.|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|

