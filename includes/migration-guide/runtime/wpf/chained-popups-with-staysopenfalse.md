---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857199"
---
### <a name="chained-popups-with-staysopenfalse"></a>Wyskakujące okienka łańcuchowe z StaysOpen=False

|   |   |
|---|---|
|Szczegóły|Popup z StaysOpen=False ma zostać zamknięty po kliknięciu poza wyskakującym okienkiem. Gdy dwa lub więcej takich pop-pów jest przykutych do łańcucha (tj. jeden zawiera inny), było wiele problemów, w tym:<ul><li>Otwórz dwa poziomy, kliknij poza P2, ale wewnątrz P1.  Nic się nie dzieje.</li><li>Otwórz dwa poziomy, kliknij poza P1.  Oba wyskakujące okienka zamykają się.</li><li>Otwórz i zamknij dwa poziomy.  Następnie spróbuj ponownie otworzyć P2.  Nic się nie dzieje.</li><li>Spróbuj otworzyć trzy poziomy.  Nie można.  (Albo nic się nie dzieje, albo pierwsze dwa poziomy zamykają się, w zależności od tego, gdzie klikniesz). Te przypadki (i inne warianty) działają teraz zgodnie z oczekiwaniami.</li></ul>|
|Zakres|Brzeg|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
