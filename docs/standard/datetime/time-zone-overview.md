---
title: Strefy czasowe — omówienie
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5fa4376cdb0496cfd25f4764257c4f3afbc7268
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697053"
---
# <a name="time-zone-overview"></a>Strefy czasowe — omówienie

<xref:System.TimeZoneInfo> Klasa upraszcza tworzenie aplikacji uwzględniających strefy czasowe. <xref:System.TimeZone> Klasy obsługuje Praca z lokalnej strefy czasowej i uniwersalny czas koordynowany (UTC). <xref:System.TimeZoneInfo> Klasa obsługuje zarówno z tych stref, jak również wszelkie strefy czasowej, o których informacje jest wstępnie zdefiniowane w rejestrze. Można również użyć <xref:System.TimeZoneInfo> do definiowania niestandardowej strefach czasowych, które system nie ma informacji o.

## <a name="time-zone-essentials"></a>Podstawowe informacje dotyczące strefy czasowej

Strefa czasowa to region geograficzny, w którym używane jest tym samym czasie. Zwykle, ale nie zawsze sąsiadujących stref czasowych są od siebie oddalone o jedną godzinę. Czas we wszystkich strefach czasowych na świecie może być wyrażona jako przesunięcie względem uniwersalnego czasu koordynowanego (UTC).

Obsługuje wiele stref czasowych na świecie czasu letniego. Czas letni próbuje zmaksymalizować godzin czasu letniego przesuwania czas do przodu o jedną godzinę w spring lub wczesnego lata, a następnie zwracanie na normalny (lub standardowa) czas w późnym lata lub spadku. Te zmiany do i z (czas standardowy) są znane jako reguł korygowania.

Przejścia do i z czasu w określonej strefie czasowej mogą być definiowane przez stałym lub zmiennoprzecinkową reguła korekty. Reguła korekty stały ustawia określonej daty, na którym każdego roku następuje przejście do lub z czasu letniego. Na przykład przejście od czasu na czas standardowy, który występuje każdego roku odbędzie się 25 października zgodna reguła korekty stały. Znacznie częściej stosowana to ruchome reguł korygowania, które określonego dnia w określonym tygodniu miesiąca określonego przejścia do lub z czasu letniego. Na przykład przejście od czasu standardowego do czasu letniego występujący w trzecim niedzielę marca następuje ruchomy reguła korekty.

Strefy czasowe, które obsługują reguł korygowania przejścia do i z czasu letniego tworzy dwa rodzaje nietypowe godziny: nieprawidłowe godziny i niejednoznacznych wartości czasu. Nieprawidłowa godzina jest moment nieistniejącej utworzone przez przejście od czasu standardowego do czasu letniego. Na przykład, jeśli występuje ten proces przejścia, w określonym dniu o 2:00 i powoduje, że czas na zmianę 3:00:00, każdego interwału czasu między 2:00:00 and 2:59:99 A.M. jest nieprawidłowy. Niejednoznaczny czas to czas, które mogą być mapowane do dwóch różnych miejsc w jednej strefie czasowej. Jest on tworzony przez przejście od czasu do czasu standardowego. Na przykład, jeśli występuje ten proces przejścia, w określonym dniu o 2:00 i powoduje, że czas na zmianę 1:00:00, każdego interwału czasu między 1:00:00 and 1:59:99 A.M. mogą być interpretowane jako (czas standardowy) lub czasu letniego.

## <a name="time-zone-terminology"></a>Terminologia strefy czasowej

W poniższej tabeli opisano terminy często używane podczas pracy ze strefami czasowymi oraz tworzenie aplikacji uwzględniających strefy czasowe.

| Termin            | Definicja |
| --------------- | ---------- |
| Reguła korekty | Reguła, która określa, kiedy następuje przejście od czasu standardowego do czasu letniego i powrót po awarii z czasu do czasu standardowego. Każda reguła korekty ma datę początkową i końcową, który definiuje, gdy reguła jest w miejscu (na przykład reguła korekty jest w miejscu od dnia 1 stycznia 1986 do 31 grudnia 2006 r.), różnicowej (ilość czasu za pomocą którego (czas standardowy) zmienia się w wyniku zastosowania th Reguła korekty e) oraz informacje o określonej daty i godziny, które przejścia są wystąpić w okresie dopasowania. Stała reguła lub zmiennoprzecinkową reguły, można wykonać przejścia. |
| Niejednoznaczny czas  | Czas, które mogą być mapowane do dwóch różnych miejsc w jednej strefie czasowej. Występuje ona, gdy czas zegara jest uwzględniany w czasie, takie jak podczas przechodzenia na strefę czasową czasu jego (czas standardowy). Na przykład, jeśli występuje ten proces przejścia, w określonym dniu o 2:00 i powoduje, że czas na zmianę 1:00:00, każdego interwału czasu między 1:00:00 and 1:59:99 A.M. mogą być interpretowane jako (czas standardowy) lub czasu letniego. |
| Stała reguła      | Reguła korekty, która ustawia określonej daty przejścia do lub z czasu letniego. Na przykład przejście od czasu na czas standardowy, który występuje każdego roku odbędzie się 25 października zgodna reguła korekty stały. |
| Przestawna reguła   | Reguła korekty, która ustawia określonego dnia w określonym tygodniu miesiąca określonego przejścia do lub z czasu letniego. Na przykład przejście od czasu standardowego do czasu letniego występujący w trzecim niedzielę marca następuje ruchomy reguła korekty. |
| Nieprawidłowa godzina    | Nieistniejącej czas, jaki jest pozostałością przejście od czasu standardowego do czasu letniego. Występuje ona, gdy czas zegara jest dostosowana do przodu w czasie, takie jak podczas przejścia od strefy czasowej (czas standardowy) do jego czasu letniego. Na przykład, jeśli występuje ten proces przejścia, w określonym dniu o 2:00 i powoduje, że czas na zmianę 3:00:00, każdego interwału czasu między 2:00:00 and 2:59:99 A.M. jest nieprawidłowy. |
| Czas przejścia | Informacje o określonej godzinie zmiany, takie jak zmiana czasu letniego (czas standardowy) lub odwrotnie, w określonej strefie czasowej. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Stref czasowych i TimezoneInfo — klasa

Na platformie .NET <xref:System.TimeZoneInfo> obiekt reprezentuje strefy czasowej. <xref:System.TimeZoneInfo> Klasa zawiera <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> metodę, która zwraca tablicę <xref:System.TimeZoneInfo.AdjustmentRule> obiektów. Każdy element tej tablicy zawiera informacje dotyczące przejścia do i z czasu w danym okresie. (Dla stref czasowych, które nie obsługują czasu letniego, metoda zwraca pustą tablicę.) Każdy <xref:System.TimeZoneInfo.AdjustmentRule> obiekt ma <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> i <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> właściwość, która definiuje określonej daty i godziny, przejścia do i z czasu letniego. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Właściwość wskazuje, czy tego przejścia jest stałe lub zmiennoprzecinkową.

.NET, zależy od informacji o strefie czasowej dostarczone przez system operacyjny Windows i przechowywane w rejestrze. Ze względu na liczbę stref czasowych na ziemi nie wszystkie istniejące stref czasowych są reprezentowane w rejestrze. Ponadto rejestr jest dynamiczne struktury, wstępnie zdefiniowane strefy czasowe może być dodane lub usunięte z niego. Na koniec rejestru nie musi zawierać dane historyczne strefy czasowej. Na przykład Windows XP rejestru zawiera dane o jeden zestaw dostosowań strefy czasowej. Windows Vista obsługuje dane dynamiczne strefy czasowej, co oznacza, że w jednej strefie czasowej mogą mieć wiele reguł dopasowania, które dotyczą określonych odstępach czasu lat. Jednak większość stref czasowych zdefiniowanych w Windows Vista rejestru i pomoc techniczna czasu ma reguł korygowania wstępnie zdefiniowany tylko jeden lub dwa.

Zależność <xref:System.TimeZoneInfo> klasy w rejestrze oznacza, że aplikacji uwzględniających strefy czasowe nie może być określone, że daną strefę czasową jest zdefiniowana w rejestrze. W rezultacie próbie utworzenia wystąpienia określonej strefy czasowej (inne niż lokalnej strefy czasowej lub strefy czasowej, który reprezentuje UTC), należy używać obsługi wyjątków. Niektóre metody polegające na umożliwieniu aplikacji, aby kontynuować, jeśli jest to wymagane powinno dodatkowo dostarczać <xref:System.TimeZoneInfo> obiektu nie można utworzyć wystąpienia z rejestru.

Do obsługi braku wymaganego strefę czasową, <xref:System.TimeZoneInfo> klasa zawiera <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody, która umożliwia tworzenie niestandardowych stref czasowych, którzy nie znajdują się w rejestrze. Aby uzyskać więcej informacji na temat tworzenia niestandardowych strefy czasowej, zobacz [jak: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [jak: Tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Ponadto można użyć <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę, aby przekonwertować nowo utworzony strefy czasowej na ciąg i zapisz go w magazynie danych (np. bazy danych, plik tekstowy, rejestr lub zasób aplikacji). Następnie można użyć <xref:System.TimeZoneInfo.FromSerializedString%2A> metodę, aby przekonwertować te parametry z powrotem do <xref:System.TimeZoneInfo> obiektu. Aby uzyskać więcej informacji, zobacz [jak: Zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [jak: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Ponieważ w każdej strefie czasowej jest określony podstawowy przesunięcie względem czasu UTC, a także przesunięcie względem czasu UTC, który odzwierciedla żadnych istniejących reguł dopasowania, czas w jednej strefie czasowej można łatwo przekształcić na czas w innej strefie czasowej. W tym celu <xref:System.TimeZoneInfo> obiektu są dostępne różne metody konwersji, w tym:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, Konwertuje czas w wyznaczonym strefie czasowej UTC.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, która konwertuje czas w wyznaczonym strefy czasowej na czas UTC.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, Konwertuje czas w jednej strefie czasowej wyznaczony czas w innej strefie czasowej wyznaczonym.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, który używa identyfikatory stref czasowych (zamiast <xref:System.TimeZoneInfo> obiektów) jako parametry, aby przekonwertować wartość czasu w jednej strefie czasowej wyznaczony czas w innej strefie czasowej wyznaczonym.

Szczegółowe informacje na temat Konwertowanie godzin między strefami czasowymi, [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
