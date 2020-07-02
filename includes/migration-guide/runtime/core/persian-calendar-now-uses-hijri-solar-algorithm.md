---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621286"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>W kalendarzu Perski jest teraz używany algorytm słoneczny Hijri

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> Klasa używa algorytmu słonecznego kalendarza Hidżry. Konwertowanie dat między <xref:System.Globalization.PersianCalendar?displayProperty=fullName> i innymi kalendarzami może spowodować nieco inne wyniki zaczynające się od .NET Framework 4,6 dla dat wcześniejszych niż 1800 lub późniejsze niż 2023 (gregoriański). Ponadto <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest teraz <code>March 22, 0622</code> zamiast <code>March 21, 0622</code> .

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że niektóre wczesne lub późne daty mogą być nieco inne podczas korzystania z PersianCalendar w .NET Framework 4,6. Ponadto podczas serializowania dat między procesami, które mogą być uruchamiane w różnych wersjach .NET Framework, nie należy przechowywać ich jako ciągów dat PersianCalendar (ponieważ te wartości mogą być różne).

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
