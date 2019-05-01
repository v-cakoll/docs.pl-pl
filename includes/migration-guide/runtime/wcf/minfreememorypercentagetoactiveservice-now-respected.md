---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61842029"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService teraz jest zachowana.

|   |   |
|---|---|
|Szczegóły|To ustawienie określa minimalną ilość pamięci, która musi być dostępny na serwerze, zanim można aktywować usługę WCF. Zaprojektowano w celu zapobieżenia <xref:System.OutOfMemoryException?displayProperty=name> wyjątków. W .NET Framework 4.5 ustawienie to nie miało wpływu. W programie .NET Framework 4.5.1 ustawienie zostanie wykryty.|
|Sugestia|Wystąpi wyjątek, jeśli pamięci na serwerze sieci web jest mniejsza niż wartość procentowa zdefiniowane przez ustawienie konfiguracji. Niektórych usług WCF, które pomyślnie uruchomiona i został uruchomiony w środowisku ograniczone pamięci może teraz zakończyć się niepowodzeniem.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
