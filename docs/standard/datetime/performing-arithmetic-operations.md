---
title: Wykonywanie operacji arytmetycznych na daty i godziny
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
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: def43f84186b53f9b0d2ade0a5a92e59606ee2af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Wykonywanie operacji arytmetycznych na daty i godziny

Mimo że zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> struktury Podaj elementów członkowskich, które wykonują operacje arytmetyczne na ich wartości, wyniki operacji arytmetycznych są bardzo różnią się. W tym temacie sprawdza, czy te różnice dotyczą stopni świadomości strefę czasową w danych daty i godziny i omówiono sposób operacji pełni strefy czasowej pamiętać przy użyciu danych daty i godziny.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porównywanie i operacje arytmetyczne z wartości daty/godziny

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Właściwość umożliwia <xref:System.DateTimeKind> wartość do przypisania do daty i godziny, aby wskazać, czy reprezentuje czasu lokalnego, uniwersalny czas koordynowany (UTC) lub czas w strefie czasowej nieokreślony. Jednak te informacje ograniczonej strefy czasowej jest ignorowane w przypadku porównywania lub wykonywanie na arytmetyczne daty i czasu <xref:System.DateTimeKind> wartości. Poniższy przykład, który porównuje bieżący czas lokalny przy użyciu bieżącego czasu UTC, ilustruje to.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Metody zgłosił, że czas lokalny jest starsze niż (lub mniej niż) czasu UTC, a operacja odejmowania wskazuje, że różnica między czasem UTC i czas lokalny system w Stanach Zjednoczonych Pacyficzny standardowa strefy czasowej wynosi siedem godzin. Jednak ponieważ te dwie wartości udostępniają różne reprezentacje pojedynczy punkt w czasie, jest jasne, w tym przypadku że dany interwał czasu są całkowicie przypisane do strefy czasu lokalnego przesunięcia od czasu UTC.

Ogólnie rzecz biorąc <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwość nie ma wpływu na wyniki zwrócone przez <xref:System.DateTime.Kind> metody porównania i arytmetyczne (jak porównanie dwa identyczne punkty w czasie wskazuje), chociaż może mieć wpływ na interpretację wyników. Na przykład:

* Wynik żadnych operacji arytmetycznej wykonywane na dwóch wartości daty i godziny, którego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> równa właściwości zarówno <xref:System.DateTimeKind> odzwierciedla rzeczywistych interwał między dwiema wartościami. Podobnie porównanie dwóch takich wartości daty i godziny dokładnie odzwierciedla relacji między razy.

* Wynik operacji żadnych arytmetycznego lub porównania wykonywane na dwóch wartości daty i godziny którego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> równa właściwości zarówno <xref:System.DateTimeKind> lub dwie wartości daty i godziny z różnymi <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości właściwości odzwierciedla różnica czasu zegara między dwiema wartościami.

* Operacje arytmetyczne lub porównania na wartości lokalnej daty i godziny należy rozważyć, czy określonej wartości jest niejednoznaczny lub nieprawidłowy ani ich pod uwagę wpływ żadnych reguł korygowania, wynikające z przejścia strefy czasu lokalnego do lub z czasu letniego Oszczędzanie czasu.

* Żadnej operacji, która porównuje lub oblicza różnicę między czasem UTC i czas lokalny obejmuje przedział czasu równa przesunięcia strefy czasu lokalnego od czasu UTC w wyniku.

* Operacja porównuje lub oblicza różnicę między przez nieokreślony czas i czas UTC lub o lokalny czas odzwierciedla czasu zegara proste. Różnice dotyczące strefy czasowej nie są uznawane za i wynik nie odzwierciedla stosowania reguł korygowania strefy czasowej.

* Operacja porównuje lub oblicza różnicę między dwiema nieokreślonych razy może obejmować Nieznany interwał, które odzwierciedla różnicę czasu w dwóch różnych strefach czasowych.

Istnieje wiele scenariuszy, w której strefy czasowej różnice nie mają wpływu na obliczenia daty i godziny (omówienie niektóre z nich, zobacz [wybierania pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) lub, w którym kontekstu Data i godzina danych definiuje znaczenie operacji porównywania lub arytmetyczne.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porównywanie i operacji arytmetycznych na wartości DateTimeOffset

A <xref:System.DateTimeOffset> wartość obejmuje nie tylko daty i godziny, ale również przesunięcia, które jednoznacznie definiuje daty i godziny względem czasu UTC. Dzięki temu można zdefiniować równości nieco inaczej niż dla <xref:System.DateTimeOffset> wartości. Podczas gdy <xref:System.DateTime> wartości są równe, jeśli mają one taką samą datę i wartości typu time <xref:System.DateTimeOffset> wartości są równe, jeśli obie odwołują się do tego samego punktu w czasie. Dzięki temu <xref:System.DateTimeOffset> wartość bardziej dokładne i mniej wymaga interpretacji, gdy jest używany w porównania i w większości operacje arytmetyczne, które określają odstęp między dwoma datami i godzinami. Poniższy przykład, który jest <xref:System.DateTimeOffset> odpowiednikiem poprzedniego przykładu, która porównywana lokalnych i UTC <xref:System.DateTimeOffset> wartości, przedstawiono ten różnice w zachowaniu.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

W tym przykładzie <xref:System.DateTimeOffset.CompareTo%2A> metody oznacza, że bieżącym czasem lokalnym i bieżący czas UTC są równe i odejmowanie <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> wartości oznacza, że jest to różnica między dwa razy <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Główny ograniczenia przy użyciu <xref:System.DateTimeOffset> wartości arytmetyczne daty i czasu jest to, że chociaż <xref:System.DateTimeOffset> wartości mieć świadomość niektórych strefy czasowej, nie pełni pamiętać strefy czasowej. Mimo że <xref:System.DateTimeOffset> wartości przesunięcia odzwierciedla przesunięcie strefy czasowej z UTC podczas <xref:System.DateTimeOffset> zmiennej najpierw jest przypisywana wartość, staje się on następnie oddzielone od strefy czasowej. Ponieważ nie jest już bezpośrednio związane z czasem do zidentyfikowania, dodawania i odejmowania interwałów daty i godziny nie należy wziąć pod uwagę reguł korygowania strefę czasową.

Aby zilustrować, przejście do czasu letniego w Stanach Zjednoczonych Strefy Środkowa (czas standardowy) występuje o 2:00 9 marca 2008. Oznacza to, że dodanie interwału dwóch i pół godziny do środkowy czas stand. od 01:30:00 9 marca 2008 należy utworzyć Data i godzina 05:00. 9 marca 2008. Ponieważ jednak w poniższym przykładzie pokazano, wynik operacji dodawania jest od 4:00 9 marca 2008. Należy pamiętać, że wynik tej operacji reprezentują poprawne punktu w czasie, chociaż nie jest to czas w strefie czasowej NAS interesuje (oznacza to, że nie ma oczekiwanego strefy czasowej przesunięcie).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operacje arytmetyczne wraz z czasem w strefach czasowych

<xref:System.TimeZoneInfo> Klasa zawiera wiele metod konwersji, stosowane automatycznie dopasowania, gdy umożliwiają one Konwertowanie godzin między strefami czasowymi do innego. Należą do nich między innymi:

* <xref:System.TimeZoneInfo.ConvertTime%2A> i <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> metody, które Konwertowanie godzin między strefami czasowymi, wszelkie dwa.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> i <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody, które przekonwertować czasu, w szczególności strefie czasowej UTC lub konwersji na czas, w szczególności strefę czasową UTC.

Aby uzyskać więcej informacji, zobacz [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Klasa nie ma żadnych metod, które są automatycznie stosowane reguł korygowania podczas wykonywania arytmetyczne daty i czasu. Jednak możesz to zrobić konwertowanie czas w strefie czasowej UTC, wykonywania operacji arytmetycznej, a następnie konwertowania raz w strefie czasowej UTC. Aby uzyskać więcej informacji, zobacz [porady: użycie stref czasowych w arytmetyczne daty i czasu](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Na przykład następujący kod jest podobny do poprzedniego kodu, który dwa i pół godziny został dodany do 2:00:00 9 marca 2008. Jednak ponieważ konwertuje środkowy czas stand. do czasu UTC przed wykonuje arytmetyczne daty i czasu, a następnie konwertuje wynik do Środkowa (czas standardowy) od czasu UTC, wynikowy czas odzwierciedla przejścia letniego strefy Środkowa (czas standardowy) czas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[porady: użycie stref czasowych w arytmetyczne daty i czasu](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
