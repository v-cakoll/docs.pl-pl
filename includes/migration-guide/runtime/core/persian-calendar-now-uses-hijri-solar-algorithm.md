---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858393"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Perski kalendarz wykorzystuje teraz algorytm słoneczny Hidżry

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6, <xref:System.Globalization.PersianCalendar?displayProperty=name> klasa używa algorytmu słonecznego Hidżry. Konwertowanie <xref:System.Globalization.PersianCalendar?displayProperty=name> dat między i innych kalendarzy może spowodować nieco inny wynik, począwszy od .NET Framework 4.6 dla dat wcześniejszych niż 1800 lub później niż 2023 (gregoriański). Ponadto, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest <code>March 22, 0622</code> teraz <code>March 21, 0622</code>zamiast .|
|Sugestia|Należy pamiętać, że niektóre wczesne lub późne daty mogą być nieco inne podczas korzystania z PersianCalendar w .NET Framework 4.6. Ponadto podczas serializacji dat między procesami, które mogą działać w różnych wersjach programu .NET Framework, nie przechowuj je jako persianCalendar ciągów daty (ponieważ te wartości mogą być różne).|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
