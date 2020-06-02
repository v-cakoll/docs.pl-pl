---
title: Zapisywanie i przywracanie stref czasowych
ms.date: 04/10/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 8da26988d2e141ac704f0d3756cd8a50602cb3fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281053"
---
# <a name="saving-and-restoring-time-zones"></a>Zapisywanie i przywracanie stref czasowych

<xref:System.TimeZoneInfo>Klasa opiera się na rejestrze, aby pobrać wstępnie zdefiniowane dane strefy czasowej. Rejestr jest jednak strukturą dynamiczną. Ponadto informacje o strefie czasowej, które zawiera rejestr, są używane przez system operacyjny głównie do obsługi korekt czasowych i konwersji w bieżącym roku. Ma to dwie główne konsekwencje dla aplikacji, które opierają się na dokładnych danych strefy czasowej:

- Strefa czasowa wymagana przez aplikację może nie być zdefiniowana w rejestrze lub zmieniono nazwę lub usunięto ją z rejestru.

- Strefa czasowa zdefiniowana w rejestrze może nie mieć informacji o konkretnych regułach korekty, które są niezbędne do historycznych konwersji stref czasowych.

<xref:System.TimeZoneInfo>Klasa eliminuje te ograniczenia w ramach obsługi serializacji (zapisywania) i deserializacji (Przywracanie) danych strefy czasowej.

## <a name="time-zone-serialization-and-deserialization"></a>Serializacja i deserializacja strefy czasowej

Zapisywanie i przywracanie strefy czasowej przez Serializowanie i deserializacja danych strefy czasowej obejmuje tylko dwa wywołania metody:

- Obiekt można serializować, <xref:System.TimeZoneInfo> wywołując metodę tego obiektu <xref:System.TimeZoneInfo.ToSerializedString%2A> . Metoda nie przyjmuje parametrów i zwraca ciąg, który zawiera informacje o strefie czasowej.

- Można zdeserializować <xref:System.TimeZoneInfo> obiekt z ciągu serializowanego, przekazując ten ciąg do `static` `Shared` metody (w Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> .

## <a name="serialization-and-deserialization-scenarios"></a>Scenariusze serializacji i deserializacji

Możliwość zapisywania (lub serializacji) <xref:System.TimeZoneInfo> obiektu w ciągu i przywracania (lub deserializacji) do późniejszego użycia zwiększa zarówno narzędzie, jak i elastyczność <xref:System.TimeZoneInfo> klasy. Ta sekcja analizuje niektóre sytuacje, w których Serializacja i deserializacja są najbardziej przydatne.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializowanie i deserializacja danych strefy czasowej w aplikacji

Serializowana strefa czasowa może zostać przywrócona z ciągu, gdy jest to konieczne. Aplikacja może to zrobić, jeśli strefa czasowa pobierana z rejestru nie może prawidłowo przekonwertować daty i godziny w określonym zakresie dat. Na przykład dane strefy czasowej w rejestrze systemu Windows XP obsługują jedną regułę korygowania, podczas gdy strefy czasowe zdefiniowane w rejestrze systemu Windows Vista zwykle zawierają informacje o dwóch regułach korekty. Oznacza to, że konwersje czasu historycznego mogą być niedokładne. Serializacja i deserializacja danych strefy czasowej może obsłużyć to ograniczenie.

W poniższym przykładzie Klasa niestandardowa, <xref:System.TimeZoneInfo> która nie ma reguł dostosowawczych, jest definiowana w taki sposób, aby reprezentować strefę czasową w Stanach Zjednoczonych od 1883 do 1917 przed wprowadzeniem czasu letniego w Stany Zjednoczone. Niestandardowa strefa czasowa jest serializowana w zmiennej z zakresem globalnym. Metoda konwersji strefy czasowej, `ConvertUtcTime` ,,, jest przenoszona do konwersji na czasy uniwersalnego czasu koordynowanego (UTC). Jeśli data i godzina występuje w 1917 lub wcześniejszych, niestandardowa Wschodnia strefa czasowa jest przywracana z serializowanego ciągu i zastępuje strefę czasową pobieraną z rejestru.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Obsługa wyjątków strefy czasowej

Ponieważ rejestr jest strukturą dynamiczną, jej zawartość podlega przypadkowej lub celowej modyfikacji. Oznacza to, że może brakować strefy czasowej, która powinna być zdefiniowana w rejestrze i która jest wymagana do pomyślnego wykonania aplikacji. Bez obsługi serializacji i deserializacji strefy czasowej masz niewielki wybór, ale aby obsługiwać wyniki, <xref:System.TimeZoneNotFoundException> kończąc aplikację. Jednak przy użyciu serializacji i deserializacji strefy czasowej można obsłużyć nieoczekiwane, <xref:System.TimeZoneNotFoundException> przywracając wymaganą strefę czasową z serializowanego ciągu, a aplikacja będzie nadal działać.

Poniższy przykład tworzy i deserializacji niestandardowej centralnej strefy czasowej. Następnie próbuje pobrać centralną standardową strefę czasową z rejestru. Jeśli operacja pobierania zgłasza albo <xref:System.TimeZoneNotFoundException> lub <xref:System.InvalidTimeZoneException> , program obsługi wyjątków deserializacji strefę czasową.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Przechowywanie serializowanego ciągu i przywracanie go w razie konieczności

Poprzednie przykłady zawierają informacje o strefie czasowej w zmiennej ciągu i przywrócone w razie potrzeby. Jednak ciąg, który zawiera serializowane informacje o strefie czasowej, może być przechowywany w pewnym nośniku magazynującym, takim jak plik zewnętrzny, plik zasobów osadzony w aplikacji lub w rejestrze. (Należy pamiętać, że informacje o niestandardowych strefach czasowych powinny być przechowywane niezależnie od kluczy strefy czasowej systemu w rejestrze).

Przechowywanie serializowanego ciągu strefy czasowej również oddziela procedurę tworzenia strefy czasowej od samej aplikacji. Na przykład można wykonać procedurę tworzenia strefy czasowej i utworzyć plik danych zawierający historyczne informacje o strefie czasowej, które mogą być używane przez aplikację. Plik danych może być następnie instalowany z aplikacją i może być otwarty, a co najmniej jedna strefa czasowa może zostać odszeregowana, gdy aplikacja tego wymaga.

Aby zapoznać się z przykładem korzystającym z zasobu osadzonego do przechowywania danych strefy czasowej, zobacz [How to: Save Time](save-time-zones-to-an-embedded-resource.md) Zones to a Embedded Resource (informacje o tym, [jak przywrócić strefy czasowe z zasobu osadzonego](restore-time-zones-from-an-embedded-resource.md)).

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
