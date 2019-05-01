---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664931"
---
### <a name="chained-popups-with-staysopenfalse"></a>Tworzenie łańcucha okna podręczne z StaysOpen = False

|   |   |
|---|---|
|Szczegóły|Okno podręczne z StaysOpen = False powinien można zamknąć, gdy klikniesz poza menu podręcznego. Gdy dwa lub więcej takich okien podręcznych łańcuch jest tworzony przez (czyli jeden zawiera inny), było wiele problemów, w tym:<ul><li>Otwarte dwa poziomy, kliknij poza P2, ale wewnątrz P1.  Nic się nie dzieje.</li><li>Otwarte dwa poziomy, kliknij poza P1.  Zamknij oba okna podręczne.</li><li>Otwierających i zamykających dwa poziomy.  Następnie spróbuj ponownie otworzyć P2.  Nic się nie dzieje.</li><li>Spróbuj otworzyć trzy poziomy.  To nie jest możliwe.  (Nic się nie dzieje lub zamknąć pierwsze dwa poziomy, w zależności od tego, gdzie należy kliknąć.) Te przypadki (i inne odmiany) teraz działać zgodnie z oczekiwaniami.</li></ul>|
|Zakres|Krawędź|
|Wersja|4.7.1|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
