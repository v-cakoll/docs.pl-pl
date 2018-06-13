---
title: 'Porady: tworzenie stref czasowych przy użyciu reguł korygowania'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c63b93e0dc587571605edb305979b8f97bf54cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576497"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Porady: tworzenie stref czasowych przy użyciu reguł korygowania

Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:

* Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.

* Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.

* Strefa czasowa nie ma dokładnych informacji o ustawienia strefy czasowej określonym okresie historycznych.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby określić strefę czasową wymagane przez aplikację. Przeciążenie tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania. Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu albo reguł korygowania stałym lub zmiennoprzecinkową. (Definicje tych postanowień, zobacz sekcję "Terminologii strefy czasowej" w [Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Utworzone przez wywołanie niestandardowych stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie zostaną dodane do rejestru. Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.

W tym temacie przedstawiono sposób tworzenia strefy czasowej przy użyciu reguł korygowania. Aby utworzyć strefę czasową, która nie obsługuje reguł korygowania czasu letniego, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Aby utworzyć strefę czasową z zmiennoprzecinkową reguł korygowania

1. Dla każdego dostosowanie (który jest dla każdego przejścia od i z powrotem do (czas standardowy) w określonym interwale) wykonaj następujące czynności:

    1. Zdefiniuj godzinę rozpoczęcia przejścia do dostosowania strefy czasowej.

       Należy wywołać <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> — metoda i przekaż go <xref:System.DateTime> wartość, która definiuje czas przejścia, wartość całkowitą, który definiuje miesiąca przejścia, wartość całkowitą, który definiuje tygodnia, w którym następuje przejście i <xref:System.DayOfWeek> wartość, która określa dzień tygodnia, w którym następuje przejście. Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    2. Zdefiniuj godzinę zakończenia przejścia do dostosowania strefy czasowej. Wymaga to innym wywołaniu <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody. Wywołanie tej metody tworzy drugi <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    3. Wywołanie <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> — metoda i przekaż go skuteczne daty rozpoczęcia i zakończenia korekty, <xref:System.TimeSpan> obiektu, który definiuje czas przejścia i dwa <xref:System.TimeZoneInfo.TransitionTime> obiektów, które definiują podczas przejścia do i z letniego czas wystąpić. Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.AdjustmentRule> obiektu.

    4. Przypisz <xref:System.TimeZoneInfo.AdjustmentRule> obiektu do tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów.

2. Zdefiniuj nazwę wyświetlaną strefy czasowej. Dość standardowy format, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęta w nawiasy i następuje ciąg identyfikujący strefy czasowej, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada następuje nazwa wyświetlana zapisy lub regiony w strefie czasowej.

3. Zdefiniuj nazwę strefy czasowej (czas standardowy). Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.

4. Zdefiniuj nazwę strefy czasowej czasu.

5. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.

6. Utwórz wystąpienie <xref:System.TimeSpan> obiektu, który definiuje przesunięcie strefy czasowej z czasem UTC. Strefy czasowe wraz z czasem, które są później niż czas UTC mają przesunięcie dodatnią. Strefy czasowe wraz z czasem, które są starsze niż UTC mają ujemne przesunięcie.

7. Wywołanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metody można utworzyć nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano centralnej standardowa strefy czasowej dla Stanów Zjednoczonych, zawiera reguły korekty dla różnych interwałów z 1918 bieżącej.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Strefa czasowa utworzone w tym przykładzie ma wiele reguł korygowania. Należy uważać, aby upewnić się, że skuteczne daty rozpoczęcia i zakończenia reguły korekty nie pokrywają się z datami inna reguła korekty. Jeśli występuje nakładanie się <xref:System.InvalidTimeZoneException> jest generowany.

Na liczby zmiennoprzecinkowe reguł korygowania, wartość 5 jest przekazywana do `week` parametr <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, aby wskazać, że w danym miesiącu ostatniego tygodnia następuje przejście.

Podczas tworzenia tablicy <xref:System.TimeZoneInfo.AdjustmentRule> obiektów do użycia w <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> wywołanie metody kodu można zainicjować tablicy do rozmiaru wymagane przez liczby korekt ma zostać utworzony dla strefy czasowej. Zamiast tego wywołuje ten przykładowy kod <xref:System.Collections.Generic.List%601.Add%2A> metody w celu dodania poszczególnych reguł dopasowania do ogólnego <xref:System.Collections.Generic.List%601> Kolekcja <xref:System.TimeZoneInfo.AdjustmentRule> obiektów. Kod wywołuje <xref:System.Collections.Generic.List%601.CopyTo%2A> metody, aby skopiować członków tej kolekcji do tablicy.

Funkcja <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metodę, aby zdefiniować dostosowania stałych. Jest to podobne do wywoływania <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, z wyjątkiem, że wymaga tylko czas, miesiąc i dzień parametrów przejścia.

Przykład można przetestować przy użyciu kodu, takie jak następujące:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można importować:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
