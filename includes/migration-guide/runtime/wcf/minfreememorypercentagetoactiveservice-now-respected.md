---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235638"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService teraz jest zachowana.

|   |   |
|---|---|
|Szczegóły|To ustawienie określa minimalną ilość pamięci, która musi być dostępny na serwerze, zanim można aktywować usługę WCF. Zaprojektowano w celu zapobieżenia <xref:System.OutOfMemoryException?displayProperty=name> wyjątków. W .NET Framework 4.5 ustawienie to nie miało wpływu. W programie .NET Framework 4.5.1 ustawienie zostanie wykryty.|
|Sugestia|Wystąpi wyjątek, jeśli pamięci na serwerze sieci web jest mniejsza niż wartość procentowa zdefiniowane przez ustawienie konfiguracji. Niektórych usług WCF, które pomyślnie uruchomiona i został uruchomiony w środowisku ograniczone pamięci może teraz zakończyć się niepowodzeniem.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
