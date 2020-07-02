---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621250"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Trwałość SQL przepływu pracy dodaje klastry kluczy podstawowych i nie zezwala na wartości null w niektórych kolumnach

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,7, tabele utworzone dla magazynu wystąpienia przepływu pracy SQL (SWIS) przez skrypt SqlWorkflowInstanceStoreSchema. SQL używają klastrowanych kluczy podstawowych. Z tego powodu tożsamości nie obsługują <code>null</code> wartości. Ta zmiana nie ma wpływu na operację SWIS. Wprowadzono aktualizacje obsługujące SQL Server replikację transakcyjną.

#### <a name="suggestion"></a>Sugestia

Aby można było obsłużyć tę zmianę, należy zastosować plik SQL SqlWorkflowInstanceStoreSchemaUpgrade. SQL do istniejących instalacji. Nowe instalacje baz danych zostaną automatycznie zmienione.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4,7|
|Typ|Środowisko uruchomieniowe|
