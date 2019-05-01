---
ms.openlocfilehash: d4f22aa41eb7aeffd655d980cb8418649462273e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757793"
---
## <a name="introduction"></a>Wprowadzenie
Przekierowanie zmiany wpływają na aplikacje, które są ponownie kompilowane pod kątem różnych .NET Framework. Obejmują one:

* Zmiany w środowisku czasu projektowania. Na przykład narzędzia do kompilacji może emitować ostrzeżenia, jeśli wcześniej nie dochodziło.

* Zmiany w środowisku uruchomieniowym. Mają one wpływu na tylko te aplikacje, które są specjalnie przeznaczone dla przebudowanymi pod inne środowisko .NET Framework. Aplikacje przeznaczone dla poprzednich wersji programu .NET Framework zachowują się tak samo, jak podczas uruchamiania w tych wersjach.

W tematach opisano zmiany przekierowanie firma Microsoft zostały sklasyfikowane poszczególne elementy według ich oczekiwanego wpływu w następujący sposób:

**Główne** to istotną zmianę, która wpływa na dużej liczby aplikacji lub wymagającym istotnych zmian w kodzie.

**Drobne** to różni się to ma wpływ na niewielką liczbę aplikacji lub wymagają drobnych modyfikacji kodu.

**Krawędzi przypadek** to zmianę, która wpływa na aplikacje w ramach bardzo konkretnych scenariuszy, które nie są wspólne.

**Przezroczysty** to zmianę, która nie ma zauważalnego wpływu na dewelopera aplikacji lub użytkownika. Aplikacja nie powinna wymagać modyfikacji ze względu na tę zmianę.
