---
title: Zapisywanie i przywracanie stref czasowych
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4e04de61ed5636d0102af694220dce06c256751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-restoring-time-zones"></a>Zapisywanie i przywracanie stref czasowych

<xref:System.TimeZoneInfo> Klasa korzysta z rejestru w celu pobrania danych wstępnie zdefiniowane strefy czasowej. Jednak rejestru jest strukturą dynamicznych. Ponadto rejestru zawierającego informacje o strefie czasowej jest używany przez system operacyjny głównie w celu obsługi konwersje i dopasowania czasu w bieżącym roku. To ma dwa główne wpływ na aplikacje korzystające z danych dokładne strefa czasowa:

* Strefę czasową, który jest wymagany przez aplikację może nie być zdefiniowana w rejestrze lub mógł zostać zmienione lub usunięte z rejestru.

* Strefy czasowej, która jest zdefiniowana w rejestrze może brakuje informacji o regułach szczególne dostosowanie, które są wymagane podczas konwersji strefy czasowej historycznych.

<xref:System.TimeZoneInfo> Klasy adresy te ograniczenia za pośrednictwem jego obsługę (zapisywanie) serializacji i deserializacji (przywracanie), strefa czasowa danych.

## <a name="time-zone-serialization-and-deserialization"></a>Strefa czasowa serializacja i deserializacja

Zapisywanie i przywracanie strefy czasowej przez serializację i deserializację strefa czasowa danych obejmuje tylko dwie wywołania metody:

* Może wykonywać serializację <xref:System.TimeZoneInfo> obiektu przez wywołanie obiektu <xref:System.TimeZoneInfo.ToSerializedString%2A> metody. Metoda nie przyjmuje żadnych parametrów i zwraca wartość typu ciąg, który zawiera informacje o strefie czasowej.

* Może wykonywać deserializację <xref:System.TimeZoneInfo> obiekt z ciągu serializacji, przekazując tego ciągu do `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> metody.

## <a name="serialization-and-deserialization-scenarios"></a>Serializacja i deserializacja scenariuszy

Możliwość zapisania (lub serializować) <xref:System.TimeZoneInfo> obiektu na ciąg i do przywrócenia (lub deserializacji) go do późniejszego użytku zwiększa zarówno narzędzie i elastyczności <xref:System.TimeZoneInfo> klasy. W tej sekcji sprawdza, czy niektóre sytuacje, w których są najbardziej przydatne serializacji i deserializacji.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializacja i Deserializacja danych strefy czasowej w aplikacji

Gdy wymagany jest można przywrócić serializacji strefy czasowej z ciągu. Aplikacja to zrobić, jeśli strefa czasowa pobrać z rejestru nie można poprawnie przekonwertować daty i godziny w zakresie określonej daty. Na przykład strefa czasowa danych w rejestrze systemu Windows XP obsługuje reguły korekty pojedynczego, a stref czasowych zdefiniowanych w rejestrze systemu Windows Vista zwykle zawierają informacje o dwóch reguł korygowania. Oznacza to, że konwersje historycznych czasu mogą być niedokładne. Serializacja i Deserializacja danych strefy czasowej może obsłużyć tego ograniczenia.

W poniższym przykładzie niestandardowego <xref:System.TimeZoneInfo> zdefiniowano klasę, która nie ma dopasowania reguł do reprezentowania USA Wschodni czas standardowy strefy z 1883 1917 przed wprowadzeniem czasu letniego w Stanach Zjednoczonych. Niestandardowa strefa czasowa jest serializowany w zmiennej, która ma zakres globalny. Metoda konwersji strefy czasowej, `ConvertUtcTime`, jest przekazywany czas uniwersalny czas koordynowany (UTC) do konwersji. Jeśli daty i godziny występuje w 1917 lub starszym, niestandardowe Eastern Standard strefy czasowej został przywrócony z serializacji ciągu i zastępuje strefy czasowej pobrać z rejestru.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Obsługa wyjątków strefy czasowej

Rejestr jest strukturą dynamicznych, jego zawartość podlegają przypadkowego lub umyślnego modyfikacji. Oznacza to, że strefy czasowej, który powinien być zdefiniowany w rejestrze i który jest wymagany dla aplikacji, aby pomyślnie wykonać mogą być nieobecne. Bez obsługi strefy czasowej serializacji i deserializacji, masz mało wyboru, aby obsłużyć powstałe w ten sposób <xref:System.TimeZoneNotFoundException> poprzez zakończenie aplikacji. Jednak przy użyciu strefy czasowej serializacji i deserializacji, można obsługiwać nieoczekiwany <xref:System.TimeZoneNotFoundException> przez przywrócenie wymagane strefy czasowej z serializacji ciągu, a aplikacja będzie nadal działać.

Poniższy przykład tworzy i serializuje niestandardowych centralnej standardowa strefy czasowej. Próbuje pobrać centralnej standardowa strefy czasowej z rejestru. Jeśli operacja pobierania zgłasza albo <xref:System.TimeZoneNotFoundException> lub <xref:System.InvalidTimeZoneException>, obsługa wyjątków deserializuje strefę czasową.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Przechowywanie serializacji ciągu i przywracania go w razie potrzeby

Poprzednich przykładach ma przechowywane informacje o strefie czasowej zmiennej ciągu, a następnie przywróci je w razie potrzeby. Jednak ciąg, który zawiera seryjnych razem, gdy informacje o strefie może się znajdować się w niektórych nośniku, takich jak zewnętrznego pliku, plik zasobów osadzonych w aplikacji lub w rejestrze. (Należy pamiętać, że oprócz strefy czasowej systemu kluczy rejestru powinny być przechowywane informacje o niestandardowych stref czasowych).

Również przechowywanie ciąg serializacji strefę czasową w ten sposób oddziela procedury tworzenia strefy czasowej z samej aplikacji. Na przykład procedury tworzenia strefy czasowej można wykonać i utworzyć plik danych zawierający informacje historyczne strefy czasowej, używaną przez aplikację. Plik danych może być następnie można zainstalować za pomocą aplikacji, można go otworzyć i co najmniej jednego z jego stref czasowych może być zdeserializowany, gdy aplikacja wymaga ich.

Na przykład, używaną do przechowywania danych serializacji strefy czasowej osadzonego zasobu, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [porady: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
