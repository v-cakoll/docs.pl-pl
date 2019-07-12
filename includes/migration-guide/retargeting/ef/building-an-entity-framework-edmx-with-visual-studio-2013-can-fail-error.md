---
ms.openlocfilehash: 25060a42b4ff66b1e25881b8c704ae0958e5f245
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804570"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Tworzenie pliku edmx Entity Framework w programie Visual Studio 2013 może zakończyć się niepowodzeniem z powodu błędu MSB4062 w przypadku korzystania z zadań EntityDeploySplit lub EntityClean

|   |   |
|---|---|
|Szczegóły|W narzędziach MSBuild 12.0 (dołączonych do programu Visual Studio 2013) zostały zmienione lokalizacje plików programu MSBuild, co powoduje, że starsze pliki obiektów docelowych programu Entity Framework są nieprawidłowe. W wyniku tego zadania <code>EntityDeploySplit</code> i <code>EntityClean</code> kończą się niepowodzeniem, ponieważ nie można odnaleźć biblioteki <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Należy pamiętać, że ten problem wynika ze zmiany dotyczącej zestawu narzędzi (MSBuild/VS), a nie ze zmiany w programie .NET Framework. Wystąpi on tylko w przypadku uaktualniania narzędzi dla deweloperów, a nie w przypadku uaktualniania samego programu .NET Framework.|
|Sugestia|Pliki obiektów docelowych Entity Framework są naprawione do pracy z nowym układem MSBuild począwszy od wersji .NET Framework 4.6. Uaktualnienie do tej wersji platformy Framework rozwiąże ten problem. Alternatywnie [to obejście](https://stackoverflow.com/a/24249247/131944) może służyć do poprawiania bezpośrednio pliki obiektów docelowych.|
|Scope|Duży|
|Wersja|4.5.1|
|Typ|Przekierowanie|

