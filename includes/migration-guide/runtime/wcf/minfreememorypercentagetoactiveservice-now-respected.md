---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620367"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService jest teraz przestrzegane

#### <a name="details"></a>Szczegóły

To ustawienie określa minimalną ilość pamięci, która musi być dostępna na serwerze, zanim będzie można aktywować usługę WCF. Jest ona przeznaczona do zapobiegania <xref:System.OutOfMemoryException?displayProperty=fullName> wyjątkom. W .NET Framework 4,5 to ustawienie nie ma żadnego wpływu. W .NET Framework 4.5.1 zostanie zaobserwowane ustawienie.

#### <a name="suggestion"></a>Sugestia

Wyjątek występuje, jeśli wolna ilość dostępnej pamięci na serwerze sieci Web jest mniejsza niż wartość procentowa zdefiniowana przez ustawienie konfiguracji. Niektóre usługi WCF, które zostały pomyślnie uruchomione i działały w ograniczonym środowisku pamięci, mogą teraz kończyć się niepowodzeniem.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
