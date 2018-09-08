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
ms.openlocfilehash: 80a5c04f7807638a4a8b114828083835f348ac08
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191472"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Porady: tworzenie stref czasowych przy użyciu reguł korygowania

Wymagane przez aplikację informacje o strefie czasowej dokładne mogą nie występować w określonym systemie z kilku powodów:

* Strefa czasowa nigdy nie został zdefiniowany w rejestrze systemu lokalnego.

* Dane dotyczące strefy czasowej został zmodyfikowany lub usunięty z rejestru.

* Strefa czasowa nie ma dokładnych informacji na temat dostosowania strefę czasową dla określonego okresu historycznych.

W takich przypadkach można wywołać <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metodę, aby zdefiniować strefę czasową, wymagane przez aplikację. Przeciążenia tej metody można użyć do tworzenia strefy czasowej z lub bez reguł korygowania. Jeśli strefa czasowa obsługuje czasu letniego, można zdefiniować dostosowania przy użyciu obu reguł korygowania fixed lub zmiennoprzecinkową. (Dla definicji tych terminów, zobacz sekcję "Strefa czasowa terminologii" w [strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Niestandardowe stref czasowych utworzonych przez wywoływanie <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody nie są dodawane do rejestru. Zamiast tego są one dostępne tylko za pośrednictwem zwracane przez odwołanie do obiektu <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> wywołania metody.

W tym temacie przedstawiono sposób tworzenia strefy czasowej przy użyciu reguł korygowania. Aby utworzyć strefę czasową, która nie obsługuje reguł dopasowania czasu letniego, zobacz [porady: tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Aby utworzyć strefę czasową ze swobodnym reguł korygowania

1. Dla każdego dopasowania (która jest dla każdego przejścia od z powrotem do czasu standardowego w przedziałach czasu określonego) wykonaj następujące czynności:

    1. Zdefiniuj godzinę rozpoczęcia przejścia dopasowania stref czasowych.

       Należy wywołać <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody i przekazać go <xref:System.DateTime> wartość, która definiuje czas przejścia, wartość całkowitą, która definiuje miesiąca przejścia, wartość całkowitą, która definiuje tygodnia, w którym następuje przejście, i <xref:System.DayOfWeek> wartość, która określa dzień tygodnia, w którym następuje przejście. Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    2. Zdefiniuj godzinę zakończenia przejścia dopasowania stref czasowych. Wymaga to innym wywołaniu <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> metody. Drugie wystąpienie wywołanie tej metody <xref:System.TimeZoneInfo.TransitionTime> obiektu.

    3. Wywołaj <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> metody i przekazać go od daty rozpoczęcia i zakończenia korekty, <xref:System.TimeSpan> obiektu, który określa ilość czasu w przejścia i dwa <xref:System.TimeZoneInfo.TransitionTime> obiekty, które określają, kiedy przejścia do i z letniego czas wystąpienia. Tworzy wywołanie tej metody <xref:System.TimeZoneInfo.AdjustmentRule> obiektu.

    4. Przypisz <xref:System.TimeZoneInfo.AdjustmentRule> obiekt jako tablicę <xref:System.TimeZoneInfo.AdjustmentRule> obiektów.

2. Zdefiniuj nazwę wyświetlaną strefy czasowej. Nazwa wyświetlana następuje stosunkowo standardowego formatu, w którym przesunięcie strefy czasowej z uniwersalnego czasu koordynowanego (UTC) jest ujęty w nawiasy i następuje ciąg, który rozpoznaje strefę czasową, jeden lub więcej miast w strefie czasowej lub jeden lub kilka Rada zapisy lub regiony w strefie czasowej.

3. Zdefiniuj nazwę strefy czasowej (czas standardowy). Zazwyczaj ten ciąg jest również używane jako identyfikator strefy czasowej.

4. Zdefiniuj nazwę strefy czasowej (czas letni).

5. Jeśli chcesz użyć innego identyfikatora niż nazwa standardowa strefy czasowej, należy zdefiniować identyfikator strefy czasowej.

6. Utwórz wystąpienie <xref:System.TimeSpan> obiekt, który definiuje przesunięcie strefy czasowej względem czasu UTC. Strefy czasowe z czasem, które są nowsze niż UTC mają przesunięcie dodatnią. Strefy czasowe z czasem, które są starsze niż UTC mają ujemne przesunięcie.

7. Wywołaj <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> metodę, aby utworzyć wystąpienie nowej strefy czasowej.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano centralnej standardowa strefy czasowej dla Stanów Zjednoczonych, obejmującą reguł korygowania dla różnych interwałów z 1918 bieżącej.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Strefa czasowa, utworzone w tym przykładzie zawiera wiele reguł dopasowania. Należy uważać, aby upewnić się, że od daty rozpoczęcia i zakończenia dowolnej reguły dopasowania nie pokrywają się z datami inną regułę dopasowania. Jeśli występuje nakładanie się <xref:System.InvalidTimeZoneException> zgłaszany.

Dla liczb zmiennoprzecinkowych reguł korygowania, wartość 5 jest przekazywany do `week` parametru <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metodę w celu wskazania, że następuje przejście na ostatni tydzień miesiąca określonego.

Podczas tworzenia macierzy <xref:System.TimeZoneInfo.AdjustmentRule> obiekty do użycia w <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> wywołania metody, kod może zainicjować tablicy do rozmiaru wymaganego przez liczbę dostosowań ma zostać utworzony dla strefy czasowej. Zamiast tego wywołuje w tym przykładzie kodu <xref:System.Collections.Generic.List%601.Add%2A> metodę, aby dodać każdą regułę dopasowania do ogólnego <xref:System.Collections.Generic.List%601> zbiór <xref:System.TimeZoneInfo.AdjustmentRule> obiektów. Następnie wywołuje kod <xref:System.Collections.Generic.List%601.CopyTo%2A> metoda kopiowania członków tej kolekcji do tablicy.

W przykładzie użyto również <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> metodę, aby zdefiniować ustalona data korekty. Jest to podobne do wywoływania <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> metody, z wyjątkiem wymagane przez dział it tylko czasu, miesiąc i dzień parametry przejścia.

Przykład można przetestować przy użyciu kodu, takie jak następujące:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

* Odwołania do System.Core.dll dodania do projektu.

* Czy następujących przestrzeni nazw można zaimportować:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Strefy czasowe — omówienie](../../../docs/standard/datetime/time-zone-overview.md)
* [Instrukcje: Tworzenie stref czasowych bez reguł korygowania](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
