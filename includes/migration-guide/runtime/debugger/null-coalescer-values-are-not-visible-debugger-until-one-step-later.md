---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620297"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Wartości parametrów łączenia wartości null nie są widoczne w debugerze, dopóki nie zostanie później jeden krok

#### <a name="details"></a>Szczegóły

Usterka w .NET Framework 4,5 powoduje, że wartości ustawione za pośrednictwem operacji łączenia zerowego nie będą widoczne w debugerze natychmiast po wykonaniu operacji przypisania w przypadku uruchamiania w wersji 64-bitowej struktury.

#### <a name="suggestion"></a>Sugestia

Przechodzenie po jednym dodatkowym czasie w debugerze spowoduje, że wartość lokalna/pole zostanie prawidłowo zaktualizowane. Ten problem został również rozwiązany w .NET Framework 4,6; uaktualnienie do tej wersji środowiska powinno rozwiązać problem.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
