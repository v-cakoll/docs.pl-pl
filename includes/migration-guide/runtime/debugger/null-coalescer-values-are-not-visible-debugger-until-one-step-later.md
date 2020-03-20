---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858598"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Null coalescer wartości nie są widoczne w debugerze, aż jeden krok później

|   |   |
|---|---|
|Szczegóły|Błąd w programie .NET Framework 4.5 powoduje, że wartości ustawione za pomocą operacji scalania null nie są widoczne w debugerze natychmiast po wykonaniu operacji przypisania podczas uruchamiania w 64-bitowej wersji frameworka.|
|Sugestia|Krok po jednym dodatkowym czasie w debugerze spowoduje, że wartość lokalnego/pola zostanie poprawnie zaktualizowana. Ponadto ten problem został rozwiązany w .NET Framework 4.6; aktualizacji do tej wersji ram, należy rozwiązać ten problem.|
|Zakres|Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
