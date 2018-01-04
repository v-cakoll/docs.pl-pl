---
title: "Przegląd stref czasowych"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e93eee00983bc2ff1c466b1240629f1193358e96
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="time-zone-overview"></a>Przegląd stref czasowych

<xref:System.TimeZoneInfo> Klasy ułatwia tworzenie aplikacji obsługujących strefę czasową. <xref:System.TimeZone> Klasy obsługuje Praca z lokalną strefą czasową i uniwersalny czas koordynowany (UTC). <xref:System.TimeZoneInfo> Klasa obsługuje zarówno z tych stref oraz wszelkie strefy czasowej, o których informacje jest wstępnie zdefiniowane w rejestrze. Można również użyć <xref:System.TimeZoneInfo> do definiowania niestandardowych stref czasowych, które system nie ma informacji o.

## <a name="time-zone-essentials"></a>Podstawowe informacje dotyczące strefy czasowej

Strefę czasową to region geograficzny, w którym jest używane jednocześnie. Zwykle, ale nie zawsze sąsiadujących stref czasowych są od siebie. Czas w tych strefach czasowych na świecie może być wyrażona jako przesunięcia z uniwersalnego czasu koordynowanego (UTC).

Obsługuje wiele stref czasowych na świecie czasu letniego. Czas letni próbuje zmaksymalizować godzin czasu letniego przesuwania czas do przodu o jedną godzinę spring lub wczesnego lata, a następnie powrót do normalnej (lub standard) czas w późne lato lub spadek. Te zmiany do i z (czas standardowy) są nazywane reguł korygowania.

Można zdefiniować przejścia do i z czasu w strefie czasowej określonej przez ustalony lub przestawne reguła korekty. Reguła korekty stałym ustawia określonego dnia, w którym następuje przejście do lub z czasu letniego każdego roku. Na przykład przejście od czasu na czas standardowy, który występuje w każdym roku 25 października następuje reguły korekty stałym. Znacznie więcej typowe są zmiennoprzecinkową reguł korygowania, które określonego dnia w określonym tygodniu określonego miesiąca przejścia do lub z czasu letniego. Na przykład przejście ze wsch. czas letni występujący w niedzielę trzeci marca następuje przestawne reguła korekty.

Dla stref czasowych, które obsługują reguł korygowania przejścia do i z czasu letniego tworzy dwa rodzaje nietypowe godziny: nieprawidłowy czas i niejednoznacznych wartości czasu. Nieprawidłowa godzina jest czasem nieistniejącą utworzone przez przejście ze wsch. czas letni. Na przykład, jeśli występuje ten proces przejścia w określonym dniu o 2:00 i powoduje, że czas, aby zmiana godzinach 3:00, każdego interwału czasu między 2:00:00 i 2:59:99 o jest nieprawidłowy. Niejednoznaczny czas to czas, które mogą być mapowane do dwóch różnych miejsc, w jednej strefie czasowej. Jest on tworzony przez przejścia od czasu do czasu standardowego. Na przykład, jeśli występuje ten proces przejścia w określonym dniu o 2:00 i powoduje, że czas na zmianę godziny 1:00, każdego interwału czasu od godziny 1:00 i 1:59:99 o mogą być interpretowane jako czas standardowy lub czas letni.

## <a name="time-zone-terminology"></a>Terminologia strefy czasowej

W poniższej tabeli opisano terminy najczęściej używanych podczas pracy ze stref czasowych i tworzenie aplikacji obsługujących strefę czasową.

| Termin            | Definicja |
| --------------- | ---------- |
| Reguła korekty | Zasada, która określa, kiedy następuje przejście od czasu standardowego do czasu letniego i od czasu do czasu standardowego. Każda reguła korekty ma datę rozpoczęcia i zakończenia, który definiuje, gdy reguła jest w miejscu (na przykład reguła korekty znajduje się w miejscu z 1 stycznia 1986 r. do 31 grudnia 2006), różnicowa (ilość czasu, o którą czas standardowy zostanie zmieniona wyniku stosowania th Reguła korekty e) oraz informacje o określoną datę i godzinę, które mają wystąpić w okresie korekty przejścia. Stała reguła lub regułę przestawne, można wykonać przejścia. |
| Niejednoznaczny czas  | Czas, które mogą być mapowane do dwóch różnych miejsc, w jednej strefie czasowej. Nastąpi to po czas zegara jest uwzględniany w czasie, takie jak podczas przejścia z czasu letniego strefę czasową na jego czas standardowy. Na przykład, jeśli występuje ten proces przejścia w określonym dniu o 2:00 i powoduje, że czas na zmianę godziny 1:00, każdego interwału czasu od godziny 1:00 i 1:59:99 o mogą być interpretowane jako czas standardowy lub czas letni. |
| Stała reguła      | Reguła korekty, która ustawia określonej daty przejścia do lub z czasu letniego. Na przykład przejście od czasu na czas standardowy, który występuje w każdym roku 25 października następuje reguły korekty stałym. |
| Przestawna reguła   | Reguła korekty, która ustawia określony dzień określonym tygodniu miesiąca określonego przejścia do lub z czasu letniego. Na przykład przejście ze wsch. czas letni występujący w niedzielę trzeci marca następuje przestawne reguła korekty. |
| Nieprawidłowa godzina    | Czas nieistniejącą jest artefaktu przejście ze wsch. czas letni. Nastąpi to po czasu zegar zostanie przesunięty do przodu w czasie, takie jak podczas przejścia od czasu standardowego strefę czasową jego czas letni. Na przykład, jeśli występuje ten proces przejścia w określonym dniu o 2:00 i powoduje, że czas, aby zmiana godzinach 3:00, każdego interwału czasu między 2:00:00 i 2:59:99 o jest nieprawidłowy. |
| Czas przejścia | Informacje o określonym czasie zmienić, takie jak zmiana czasu na czas standardowy lub odwrotnie, w szczególności strefy czasowej. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Strefy czasowe i TimeZoneInfo — klasa

W środowisku .NET <xref:System.TimeZoneInfo> obiekt reprezentuje strefę czasową. <xref:System.TimeZoneInfo> Klasa zawiera <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> metodę, która zwraca tablicę <xref:System.TimeZoneInfo.AdjustmentRule> obiektów. Każdy element tej tablicy zawiera informacje dotyczące przejścia do i z czasu letniego dla danego okresu. (Dla stref czasowych, które nie obsługują czasu letniego, metoda zwraca pustą tablicę). Każdy <xref:System.TimeZoneInfo.AdjustmentRule> obiekt ma <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> i <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> właściwość, która definiuje określonej daty i godziny przejścia do i z czasu letniego. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Właściwość wskazuje, czy tego przejścia jest stały lub zmiennoprzecinkową.

.NET zależy od informacji o strefie czasowej dostarczane przez system operacyjny i przechowywane w rejestrze. Ze względu na liczbę stref czasowych ziemi nie wszystkie istniejące stref czasowych są reprezentowane w rejestrze. Ponadto ponieważ rejestru jest strukturą dynamicznych, wstępnie zdefiniowane strefy czasowe można dodać do lub z niej usuwać. Na koniec rejestru nie musi zawierać dane historyczne strefy czasowej. Na przykład w systemie Windows XP rejestru zawiera dane dotyczące tylko jednego zestawu ustawienia strefy czasowej. Windows Vista obsługuje dane dynamiczne strefy czasowej, co oznacza, że jednej strefie czasowej może mieć wiele reguł korygowania mające zastosowanie do określonych odstępach czasu lat. Większość stref czasowych zdefiniowanych w Windows Vista rejestru i pomocy technicznej czasu letniego jednak tylko jedna lub dwie reguły korekty wstępnie zdefiniowane.

Zależność <xref:System.TimeZoneInfo> klasy do rejestru oznacza, że aplikacji obsługujących strefę czasową nie może być określone w rejestrze, którym jest zdefiniowany daną strefę czasową. W związku z tym próba utworzenia wystąpienia określonej strefy czasowej (inne niż w lokalnej strefie czasowej lub strefy czasowej, który reprezentuje czas UTC) należy używać obsługi wyjątków. Powinien on również zawierał niektóre metody aplikacji, aby kontynuować, jeśli jest to wymagane przez <xref:System.TimeZoneInfo> z rejestru nie można utworzyć wystąpienia obiektu.

Do obsługi braku strefę czasową wymagane <xref:System.TimeZoneInfo> klasa zawiera <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, która umożliwia tworzenie niestandardowych stref czasowych, które nie znajdują się w rejestrze. Aby uzyskać więcej informacji na temat tworzenia niestandardowych strefy czasowej, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) i [porady: tworzenie stref czasowych przy użyciu reguł korygowania](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Ponadto można użyć <xref:System.TimeZoneInfo.ToSerializedString%2A> metodę, aby nowo utworzony strefy czasowej są skonwertowane do ciągu i zapisz go w magazynie danych (np. bazy danych pliku tekstowego, rejestru lub zasobów aplikacji). Następnie można użyć <xref:System.TimeZoneInfo.FromSerializedString%2A> metodę, aby przekonwertować te parametry z powrotem do <xref:System.TimeZoneInfo> obiektu. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Ponieważ każdej strefy czasowej jest określony podstawowy przesunięcie od czasu UTC, a także przesunięcie od czasu UTC, które odzwierciedla żadnych istniejących reguł korygowania, czas w strefie czasowej co mogą łatwo konwertowane na czas w innej strefie czasowej. W tym celu <xref:System.TimeZoneInfo> obiektu zawiera kilka metod konwersji, w tym:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, który konwertuje na czas w wyznaczonym strefę czasową UTC.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, który konwertuje czasu w wyznaczonym strefie czasowej UTC.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, który konwertuje czasu w jednej strefie czasowej wyznaczonych w innej strefie czasowej wyznaczony czas.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, który używa identyfikatory stref czasowych (zamiast <xref:System.TimeZoneInfo> obiektów) jako parametry, aby przekonwertować czasu w jednej strefie czasowej wyznaczony na czas w innej strefie czasowej wyznaczonych.

Aby uzyskać szczegółowe informacje na Konwertowanie godzin między strefami czasowymi, zobacz [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
