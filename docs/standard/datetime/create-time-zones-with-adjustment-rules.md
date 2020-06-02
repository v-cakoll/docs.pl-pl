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
ms.openlocfilehash: b7e938581dfde3f1566aa2506302292686c2fc5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278171"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Instrukcje: Tworzenie stref czasowych przy użyciu reguł korygowania

Precyzyjne informacje o strefie czasowej, które są wymagane przez aplikację, mogą nie być obecne w określonym systemie z kilku powodów:

- Strefa czasowa nigdy nie została zdefiniowana w rejestrze systemu lokalnego.

- Dane dotyczące strefy czasowej zostały zmodyfikowane lub usunięte z rejestru.

- Strefa czasowa nie ma dokładnych informacji na temat korekt stref czasowych w danym okresie historycznym.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę w celu zdefiniowania strefy czasowej wymaganej przez aplikację. Można użyć przeciążenia tej metody, aby utworzyć strefę czasową z lub bez reguł korekty. Jeśli strefa czasowa obsługuje czas letni, można zdefiniować korekty przy użyciu stałych lub przestawnych reguł korekty. (W przypadku definicji tych warunków Zobacz sekcję "terminologia strefy czasowej" w temacie [Omówienie strefy czasowej](time-zone-overview.md)).

> [!IMPORTANT]
> Niestandardowe strefy czasowe utworzone przez wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są dodawane do rejestru. Zamiast tego można uzyskać do nich dostęp tylko za pomocą odwołania do obiektu zwróconego przez <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołanie metody.

W tym temacie pokazano, jak utworzyć strefę czasową z regułami korekty. Aby utworzyć strefę czasową, która nie obsługuje zasad korekty czasu letniego, zobacz [How to: Create czas Zones bez reguł korekty](create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Aby utworzyć strefę czasową przy użyciu zmiennoprzecinkowych reguł dopasowania

1. Dla każdej korekty (czyli dla każdego przejścia z powrotem do czasu standardowego w określonym przedziale czasu) wykonaj następujące czynności:

    1. Zdefiniuj początkowy czas przejścia dla korekty strefy czasowej.

       Należy wywołać <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metodę i przekazać ją do <xref:System.DateTime> wartości definiującej czas przejścia, wartość całkowitą, która definiuje miesiąc przejścia, wartość całkowitą, która definiuje tydzień, w którym następuje przejście, oraz <xref:System.DayOfWeek> wartość określającą dzień tygodnia, w którym następuje przejście. To wywołanie metody tworzy wystąpienie <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    2. Zdefiniuj końcowy czas przejścia dla korekty strefy czasowej. Wymaga to innego wywołania <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody. To wywołanie metody tworzy wystąpienie drugiego <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    3. Wywołaj <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metodę i przekaż ją do obowiązujących dat rozpoczęcia i zakończenia korekty, <xref:System.TimeSpan> obiektu, który definiuje czas w przejściu, i dwa <xref:System.TimeZoneInfo.TransitionTime> obiekty, które definiują, kiedy nastąpi przejście do i od czasu letniego. To wywołanie metody tworzy wystąpienie <xref:System.TimeZoneInfo.AdjustmentRule> obiektu.

    4. Przypisz <xref:System.TimeZoneInfo.AdjustmentRule> obiekt do tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów.

2. Zdefiniuj nazwę wyświetlaną strefy czasowej. Nazwa wyświetlana jest zgodna z formatem standardowym, w którym przesunięcie strefy czasowej od skoordynowanego czasu uniwersalnego (UTC) jest ujęte w nawiasy i następuje przez ciąg identyfikujący strefę czasową, co najmniej jeden z miast w strefie czasowej lub jeden lub więcej krajów lub regionów w strefie czasowej.

3. Zdefiniuj nazwę czasu standardowego strefy czasowej. Zazwyczaj ten ciąg jest również używany jako identyfikator strefy czasowej.

4. Zdefiniuj nazwę czasu letniego strefy czasowej.

5. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, zdefiniuj identyfikator strefy czasowej.

6. Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasu UTC. Strefy czasowe, które są późniejsze niż UTC, są przesunięte pozytywnie. Strefy czasowe o porach wcześniejszym niż UTC mają ujemne przesunięcie.

7. Wywołaj <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano centralną strefę czasową dla Stany Zjednoczone, która zawiera reguły dostosowawcze dla różnych przedziałów czasu od 1918 do obecne.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Strefa czasowa utworzona w tym przykładzie ma wiele reguł korekty. Należy zwrócić uwagę, aby upewnić się, że obowiązujące daty rozpoczęcia i zakończenia dowolnych reguł korekty nie nakładają się na daty innej reguły korekty. Jeśli występuje nakładanie się, <xref:System.InvalidTimeZoneException> jest zgłaszany.

W przypadku liczbowych reguł dopasowania wartość 5 jest przenoszona do `week` parametru metody, <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> Aby wskazać, że przejście następuje w ostatnim tygodniu danego miesiąca.

W przypadku tworzenia tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów do użycia w <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> wywołaniu metody kod może inicjować tablicę do rozmiaru wymaganego przez liczbę korekt do utworzenia dla strefy czasowej. Zamiast tego, ten kod wywołuje <xref:System.Collections.Generic.List%601.Add%2A> metodę w celu dodania każdej reguły korekty do ogólnej <xref:System.Collections.Generic.List%601> kolekcji <xref:System.TimeZoneInfo.AdjustmentRule> obiektów. Następnie kod wywołuje <xref:System.Collections.Generic.List%601.CopyTo%2A> metodę w celu skopiowania elementów członkowskich tej kolekcji do tablicy.

W przykładzie używa się również <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metody do definiowania korekt dat stałych. Jest to podobne do wywoływania <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, z tą różnicą, że wymaga tylko czasu, miesiąca i dnia parametrów przejścia.

Przykład może być testowany przy użyciu kodu, takiego jak:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Że importowane są następujące przestrzenie nazw:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
- [Strefy czasowe — omówienie](time-zone-overview.md)
- [Instrukcje: Tworzenie stref czasowych bez reguł korygowania](create-time-zones-without-adjustment-rules.md)
