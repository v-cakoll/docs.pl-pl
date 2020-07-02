---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615684"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>Tworzenie pliku edmx Entity Framework w programie Visual Studio 2013 może zakończyć się niepowodzeniem z powodu błędu MSB4062 w przypadku korzystania z zadań EntityDeploySplit lub EntityClean

#### <a name="details"></a>Szczegóły

W narzędziach MSBuild 12.0 (dołączonych do programu Visual Studio 2013) zostały zmienione lokalizacje plików programu MSBuild, co powoduje, że starsze pliki obiektów docelowych programu Entity Framework są nieprawidłowe. W wyniku tego zadania `EntityDeploySplit` i `EntityClean` kończą się niepowodzeniem, ponieważ nie można odnaleźć biblioteki `Microsoft.Data.Entity.Build.Tasks.dll`. Należy pamiętać, że ten problem wynika ze zmiany dotyczącej zestawu narzędzi (MSBuild/VS), a nie ze zmiany w programie .NET Framework. Wystąpi on tylko w przypadku uaktualniania narzędzi dla deweloperów, a nie w przypadku uaktualniania samego programu .NET Framework.

#### <a name="suggestion"></a>Sugestia

Pliki obiektów docelowych Entity Framework są naprawione do pracy z nowym układem MSBuild począwszy od wersji .NET Framework 4.6. Uaktualnienie do tej wersji platformy Framework rozwiąże ten problem. Można również użyć [tego obejścia](https://stackoverflow.com/a/24249247/131944) , aby bezpośrednio poprawić pliki docelowe.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4.5.1       |
| Typ    | Przekierowanie |
