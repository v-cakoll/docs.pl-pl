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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dc983f1f0b2405f207d69c62b800ee854fcd409
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081771"
---
# <a name="saving-and-restoring-time-zones"></a>Zapisywanie i przywracanie stref czasowych

<xref:System.TimeZoneInfo> Klasy opiera się na rejestru w celu pobrania danych wstępnie zdefiniowane strefy czasowej. Jednak rejestru jest strukturą dynamicznych. Ponadto informacje o strefie czasowej, który zawiera rejestr jest używany przez system operacyjny głównie w celu obsługi korektę czasu i konwersje w bieżącym roku. To ma dwie główne wpływ na aplikacje oparte na danych dokładne strefa czasowa:

* Strefa czasowa, która jest wymagana przez aplikację może nie być zdefiniowana w rejestrze lub mógł zostać zmieniona lub usunięta z rejestru.

* Strefa czasowa, która jest zdefiniowana w rejestrze może brakuje informacji na temat reguł określonego korygowania, które są niezbędne do konwersjami stref czasowych historycznych.

<xref:System.TimeZoneInfo> Klasy adresy te ograniczenia, za pośrednictwem Obsługa (zapisywanie) serializacji i deserializacji (Trwa przywracanie) danych w strefie czasowej.

## <a name="time-zone-serialization-and-deserialization"></a>Strefa czasowa serializacji i deserializacji

Zapisywanie i przywracanie na strefę czasową, serializacja i Deserializacja danych strefy czasowej obejmuje tylko dwie wywołania metody:

* Może wykonywać serializację <xref:System.TimeZoneInfo> obiektu przez wywołanie metody tego obiektu <xref:System.TimeZoneInfo.ToSerializedString%2A> metody. Metoda nie przyjmuje żadnych parametrów i zwraca ciąg, który zawiera informacje o strefie czasowej.

* Może wykonywać deserializację <xref:System.TimeZoneInfo> obiekt Zserializowany ciągu, przekazując ciąg do `static` (`Shared` w języku Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> metody.

## <a name="serialization-and-deserialization-scenarios"></a>Scenariusze serializacji i deserializacji

Możliwość zapisywania (lub serializować) <xref:System.TimeZoneInfo> obiekt na ciąg i przywrócić (lub deserializować) w celu późniejszego użycia zwiększa elastyczność i narzędzia <xref:System.TimeZoneInfo> klasy. W tej sekcji sprawdza, czy niektóre przypadki, w których są najbardziej przydatne serializacji i deserializacji.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializacja i Deserializacja danych strefy czasowej w aplikacji

Kiedy jest potrzebny, można przywrócić Zserializowany strefy czasowej z ciągu. Aplikacja to zrobić, jeśli strefa czasowa, pobrać z rejestru nie jest w stanie poprawnie przekonwertować daty i godziny w zakresie określonej daty. Na przykład strefa czasowa danych w rejestrze systemu Windows XP obsługuje regułę pojedynczego dopasowania, a stref czasowych zdefiniowanych w rejestrze systemu Windows Vista, zwykle zawierają informacje o dwóch reguł korygowania. Oznacza to, że konwersje historycznych czasu mogą być niedokładne. Serializacja i Deserializacja danych strefy czasowej może obsłużyć tego ograniczenia.

W poniższym przykładzie niestandardową <xref:System.TimeZoneInfo> zdefiniowano klasę, która nie zawiera żadnych reguł dopasowania do reprezentowania Stanów Zjednoczonych Wschodni czas standardowy strefy z 1883 1917 przed wprowadzeniem zmiany czasu w Stanach Zjednoczonych. Niestandardowa strefa czasowa jest serializowany w zmiennej, która ma zakres globalny. Metoda konwersji strefy czasowej, `ConvertUtcTime`, jest przekazywany czas uniwersalny czas koordynowany (UTC), aby przekonwertować. Jeśli daty i godziny występuje w 1917 lub starszym, niestandardowa Eastern Standard strefa czasowa jest przywracana z serializowanej ciągu i zastępuje strefy czasowej, pobrać z rejestru.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Obsługa wyjątków na strefę czasową

Ponieważ rejestr jest strukturą dynamiczne, jego zawartość podlegają przypadkowego lub celowego modyfikacji. Oznacza to, że strefy czasowej, która powinna być zdefiniowana w rejestrze i jest to wymagane dla aplikacji, aby pomyślnie wykonać może nie występować. Bez pomocy technicznej dla strefy czasowej serializacji i deserializacji, ma mały wyboru, aby obsłużyć wynikowy <xref:System.TimeZoneNotFoundException> przez zakończeniem aplikacji. Jednak przy użyciu strefy czasowej serializacji i deserializacji, które ułatwią Ci obsługę nieoczekiwany <xref:System.TimeZoneNotFoundException> , przywracając wymagane strefy czasowej z serializacji ciąg, a aplikacja będzie nadal działać.

Poniższy przykład tworzy i serializuje niestandardowe centralnej standardowa strefy czasowej. Próbuje pobrać centralnej standardowa strefy czasowej z rejestru. Jeśli operacja pobierania zgłasza albo <xref:System.TimeZoneNotFoundException> lub <xref:System.InvalidTimeZoneException>, obsługa wyjątków deserializuje strefy czasowej.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Przechowywanie serializacji ciągu i przywracania go w razie

Poprzednie przykłady ma przechowywane informacje o strefie czasowej do zmiennej ciągu i przywrócono ją w razie. Jednak ciąg, który zawiera Zserializowany razem, gdy informacje o strefie sam można przechowywać w niektórych nośnika magazynowania, takie jak zewnętrznego pliku, plik zasobów osadzonych w aplikacji lub w rejestrze. (Zwróć uwagę, że informacje o niestandardowych stref czasowych powinny znajdować się niezależnie od strefy czasowej systemu kluczy rejestru).

Również przechowywanie ciągu Zserializowany strefę czasową w ten sposób oddziela procedurę tworzenia strefy czasowej z samej aplikacji. Na przykład procedury tworzenia strefy czasowej można wykonać i utworzyć plik danych, który zawiera informacje o strefie czasowej historyczne, które aplikacja może użyć. Plik danych może być, a następnie można zainstalować za pomocą aplikacji, można go otworzyć i co najmniej jeden z jego stref czasowych może być zdeserializowany, gdy aplikacja wymaga ich.

Na przykład, korzystającą z zasobu osadzonego w celu przechowywania danych serializacji strefę czasową, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) i [jak: Przywracanie stref czasowych z zasobu osadzonego](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
