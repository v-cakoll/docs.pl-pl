---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235412"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Wartości null coalescer nie są widoczne w debugerze, dopóki jeden krok później

|   |   |
|---|---|
|Szczegóły|Usterki w programie .NET Framework 4.5 powoduje, że wartości ustawione za pośrednictwem o wartości null operacji łączącego nie powinny być widoczne w debugerze natychmiast po zakończeniu operacji przypisania jest wykonywany podczas uruchamiania na 64-bitowej wersji Framework.|
|Sugestia|Przechodzenie krok po kroku jeden dodatkowy czas w debugerze spowoduje, że lokalne/pola. wartość do zaktualizowania poprawnie. Ponadto ten problem został rozwiązany w .NET Framework 4.6; Uaktualnianie do wersji Framework powinno rozwiązać problem.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
