---
title: 'Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: 4ef3d93746c5688dc15fc7e45d9be054dcfba4c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132552"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania

Precyzyjne informacje o strefie czasowej, które są wymagane przez aplikację, mogą nie być obecne w określonym systemie z kilku powodów:

- Strefa czasowa nigdy nie została zdefiniowana w rejestrze systemu lokalnego.

- Dane dotyczące strefy czasowej zostały zmodyfikowane lub usunięte z rejestru.

- Strefa czasowa nie ma dokładnych informacji na temat korekt stref czasowych w danym okresie historycznym.

W takich przypadkach można wywołać metodę <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>, aby zdefiniować strefę czasową wymaganą przez aplikację. Można użyć przeciążenia tej metody, aby utworzyć strefę czasową z lub bez reguł korekty. Jeśli strefa czasowa obsługuje czas letni, można zdefiniować korekty przy użyciu stałych lub przestawnych reguł korekty. (W przypadku definicji tych warunków Zobacz sekcję "terminologia strefy czasowej" w temacie [Omówienie strefy czasowej](../../../docs/standard/datetime/time-zone-overview.md)).

> [!IMPORTANT]
> Niestandardowe strefy czasowe utworzone przez wywołanie metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> nie są dodawane do rejestru. Zamiast tego można uzyskać do nich dostęp tylko za pomocą odwołania do obiektu zwróconego przez wywołanie metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.

W tym temacie pokazano, jak utworzyć strefę czasową z regułami korekty. Aby utworzyć strefę czasową, która nie obsługuje zasad korekty czasu letniego, zobacz [How to: Create czas Zones bez reguł korekty](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Aby utworzyć strefę czasową przy użyciu zmiennoprzecinkowych reguł dopasowania

1. Dla każdej korekty (czyli dla każdego przejścia z powrotem do czasu standardowego w określonym przedziale czasu) wykonaj następujące czynności:

    1. Zdefiniuj początkowy czas przejścia dla korekty strefy czasowej.

       Należy wywołać metodę <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> i przekazać ją do <xref:System.DateTime> wartości, która definiuje czas przejścia, wartość całkowitą, która definiuje miesiąc przejścia, wartość całkowitą, która definiuje tydzień, w którym następuje przejście, oraz wartość <xref:System.DayOfWeek>, która definiuje dzień tygodnia, w którym następuje przejście. To wywołanie metody tworzy wystąpienie obiektu <xref:System.TimeZoneInfo.TransitionTime>.

    2. Zdefiniuj końcowy czas przejścia dla korekty strefy czasowej. Wymaga to innego wywołania metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>. To wywołanie metody tworzy wystąpienie drugiego <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    3. Wywołaj metodę <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> i przekaż jej datę początkową i końcową korekty, obiekt <xref:System.TimeSpan>, który definiuje czas w przejściu i dwa <xref:System.TimeZoneInfo.TransitionTime> obiekty, które definiują, kiedy wystąpią przejścia do i z czasu letniego. To wywołanie metody tworzy wystąpienie obiektu <xref:System.TimeZoneInfo.AdjustmentRule>.

    4. Przypisz obiekt <xref:System.TimeZoneInfo.AdjustmentRule> do tablicy obiektów <xref:System.TimeZoneInfo.AdjustmentRule>.

2. Zdefiniuj nazwę wyświetlaną strefy czasowej. Nazwa wyświetlana jest zgodna z formatem standardowym, w którym przesunięcie strefy czasowej od skoordynowanego czasu uniwersalnego (UTC) jest ujęte w nawiasy i następuje przez ciąg identyfikujący strefę czasową, co najmniej jeden z miast w strefie czasowej lub jeden lub więcej Cou ntries lub regiony w strefie czasowej.

3. Zdefiniuj nazwę czasu standardowego strefy czasowej. Zazwyczaj ten ciąg jest również używany jako identyfikator strefy czasowej.

4. Zdefiniuj nazwę czasu letniego strefy czasowej.

5. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, zdefiniuj identyfikator strefy czasowej.

6. Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasu UTC. Strefy czasowe, które są późniejsze niż UTC, są przesunięte pozytywnie. Strefy czasowe o porach wcześniejszym niż UTC mają ujemne przesunięcie.

7. Wywołaj metodę <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>, aby utworzyć wystąpienie nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano centralną strefę czasową dla Stany Zjednoczone, która zawiera reguły dostosowawcze dla różnych przedziałów czasu od 1918 do obecne.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Strefa czasowa utworzona w tym przykładzie ma wiele reguł korekty. Należy zwrócić uwagę, aby upewnić się, że obowiązujące daty rozpoczęcia i zakończenia dowolnych reguł korekty nie nakładają się na daty innej reguły korekty. Jeśli wystąpi nakładanie się, zostanie zgłoszony <xref:System.InvalidTimeZoneException>.

W przypadku reguł dopasowań zmiennoprzecinkowych wartość 5 jest przesyłana do `week` parametru metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, aby wskazać, że przejście następuje w ostatnim tygodniu danego miesiąca.

W przypadku tworzenia tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów do użycia w wywołaniu metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> kod może inicjować tablicę do rozmiaru wymaganego przez liczbę korekt do utworzenia dla strefy czasowej. Zamiast tego, ten kod wywołuje metodę <xref:System.Collections.Generic.List%601.Add%2A>, aby dodać każdą regułę korekty do ogólnej <xref:System.Collections.Generic.List%601> kolekcji obiektów <xref:System.TimeZoneInfo.AdjustmentRule>. Następnie kod wywołuje metodę <xref:System.Collections.Generic.List%601.CopyTo%2A>, aby skopiować elementy członkowskie tej kolekcji do tablicy.

W przykładzie zastosowano również metodę <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>, aby zdefiniować stałe korekty daty. Jest to podobne do wywołania metody <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, z tą różnicą, że wymaga tylko czasu, miesiąca i dnia parametrów przejścia.

Przykład może być testowany przy użyciu kodu, takiego jak:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md)
- [Instrukcje: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
