---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858598"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Wartości null coalescer nie są widoczne w debugerze, dopóki jeden krok później

|   |   |
|---|---|
|Szczegóły|Usterki w programie .NET Framework 4.5 powoduje, że wartości ustawione za pośrednictwem o wartości null operacji łączącego nie powinny być widoczne w debugerze natychmiast po zakończeniu operacji przypisania jest wykonywany podczas uruchamiania na 64-bitowej wersji Framework.|
|Sugestia|Przechodzenie krok po kroku jeden dodatkowy czas w debugerze spowoduje, że lokalne/pola. wartość do zaktualizowania poprawnie. Ponadto ten problem został rozwiązany w .NET Framework 4.6; Uaktualnianie do wersji Framework powinno rozwiązać problem.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

