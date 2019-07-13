---
ms.openlocfilehash: 130c26b7d135db232eb40a2c466aa3bdb2481ace
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858393"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Kalendarz perski korzysta z algorytmu słonecznego Hidżry

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6 <xref:System.Globalization.PersianCalendar?displayProperty=name> klasy używa algorytmu słonecznego Hidżry. Konwertowanie daty wypadające między <xref:System.Globalization.PersianCalendar?displayProperty=name> i innych kalendarzy może zwrócić wynik nieco zaczyna się od programu .NET Framework 4.6 daty wcześniejszej niż 1800 lub późniejsza niż 2023 (gregoriańskiego). Ponadto <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> jest teraz <code>March 22, 0622</code> zamiast <code>March 21, 0622</code>.|
|Sugestia|Należy pamiętać, że niektóre daty wczesne i późne mogą być nieco inne w przypadku korzystania z PersianCalendar w .NET Framework 4.6. Ponadto podczas serializowania dat między procesami, które mogą być uruchamiane w innej wersji programu .NET Framework, nie należy przechowywać je jako ciągi daty z PersianCalendar (ponieważ te wartości mogą się różnić).|
|Scope|Mały|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

