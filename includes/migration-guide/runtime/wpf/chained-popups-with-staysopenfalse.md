---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621253"
---
### <a name="chained-popups-with-staysopenfalse"></a>Połączone okienka podręczne z StaysOpen = false

#### <a name="details"></a>Szczegóły

Okno podręczne z StaysOpen = false ma być zamknięte po kliknięciu poza oknem podręcznym. Gdy dwa lub więcej takich okien podręcznych jest łańcucha (tj. jeden zawiera inny), wystąpił wiele problemów, w tym:<ul><li>Otwórz dwa poziomy, kliknij poza P2, ale wewnątrz P1.  Nic się nie dzieje.</li><li>Otwórz dwa poziomy, kliknij poza P1.  Zamknij oba okna podręczne.</li><li>Otwórz i Zamknij dwa poziomy.  Następnie spróbuj ponownie otworzyć P2.  Nic się nie dzieje.</li><li>Spróbuj otworzyć trzy poziomy.  Nie możesz.  (Nic się nie dzieje lub pierwsze dwa poziomy są zamykane, w zależności od tego, gdzie klikniesz). Te przypadki (i inne warianty) działają teraz zgodnie z oczekiwaniami.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
