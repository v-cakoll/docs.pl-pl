---
title: Wykonywanie operacji arytmetycznych na wartościach dat i godzin
ms.date: 04/10/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01314c160fc531f5c97a1369c8444dce7f590d53
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106612"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Wykonywanie operacji arytmetycznych na wartościach dat i godzin

<xref:System.DateTime> Chociaż struktury<xref:System.DateTimeOffset> i zapewniają składowe, które wykonują operacje arytmetyczne na ich wartości, wyniki operacji arytmetycznych są bardzo różne. Ten temat zawiera informacje o różnicach, odniesieniu ich do stopni rozpoznawania strefy czasowej w danych daty i godziny. omówiono w nim wykonywanie operacji w pełni opartej na strefie czasowej przy użyciu danych daty i godziny.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porównania i operacje arytmetyczne z wartościami DateTime

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Właściwość umożliwiaprzypisaniewartościdodatyigodzinywceluwskazania,czyreprezentujeonaczaslokalny,uniwersalnyczaskoordynowany(UTC),czyczaswnieokreślonej<xref:System.DateTimeKind> strefie czasowej. Jednak te ograniczone informacje o strefie czasowej są ignorowane podczas porównywania lub wykonywania operacji arytmetycznych <xref:System.DateTimeKind> na wartościach daty i godziny. Poniższy przykład, który porównuje bieżący czas lokalny z bieżącym czasem UTC, ilustruje to.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Metoda zgłasza, że czas lokalny jest wcześniejszy niż czas UTC, a operacja odejmowania wskazuje, że różnica między czasem UTC a czasem lokalnym dla systemu w Stanach Zjednoczonych Standardowa strefa czasowa pacyficznego to siedem godzin. Jednak ponieważ te dwie wartości zapewniają różne reprezentacje pojedynczego punktu w czasie, w tym przypadku jest jasne, że ten przedział czasu jest całkowicie przypisany do przesunięcia lokalnej strefy czasowej z czasu UTC.

Bardziej ogólnie <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> rzecz biorąc, właściwość nie wpływa na wyniki zwracane przez <xref:System.DateTime.Kind> metody porównania i arytmetyczne (w miarę jak porównanie dwóch identycznych punktów w czasie wskazuje), chociaż może to wpływać na interpretację tych wyników. Na przykład:

- Wynik operacji arytmetycznych na dwóch wartościach daty i godziny, których <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwości są równe <xref:System.DateTimeKind> , odzwierciedla rzeczywiste przedział czasu między tymi dwiema wartościami. Podobnie porównanie dwóch takich wartości daty i godziny dokładnie odzwierciedla relacje między nimi.

- Wynik operacji arytmetycznych lub porównania wykonanych na dwóch wartościach daty i godziny, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> których właściwości są <xref:System.DateTimeKind> równe lub dwie wartości daty i godziny o różnych <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartościach właściwości odzwierciedlają różnicę w czasie zegara między tymi dwiema wartościami.

- Operacje arytmetyczne lub porównania na lokalnych wartościach daty i godziny nie są brane pod uwagę, czy konkretna wartość jest niejednoznaczna, czy nieprawidłowa, ani nie podejmuje wpływu na skutki wszelkich reguł korekty wynikających ze przejścia lokalnej strefy czasowej do lub z czasu letniego. Oszczędność czasu.

- Każda operacja, która porównuje lub oblicza różnicę między czasem UTC a czasem lokalnym, obejmuje przedział czasu równy przesunięciu strefy czasowej z UTC w wyniku.

- Każda operacja, która porównuje lub oblicza różnicę między nieokreślonym czasem a czasem UTC lub czasem lokalnym odzwierciedla prosty czas zegara. Różnice między strefami czasowymi nie są brane pod uwagę, a wynik nie odzwierciedla zastosowania reguł dostosowania strefy czasowej.

- Każda operacja, która porównuje lub oblicza różnicę między dwoma nieokreślonymi czasami może obejmować nieznany interwał, który odzwierciedla różnicę między czasem w dwóch różnych strefach czasowych.

Istnieje wiele scenariuszy, w których różnice między strefami czasowymi nie wpływają na obliczenia daty i godziny (w przypadku omówienia niektórych z nich, zobacz [Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) lub w których kontekście danych daty i godziny definiuje znaczenie operacji porównania lub arytmetycznych.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porównania i operacje arytmetyczne z wartościami DateTimeOffset

<xref:System.DateTimeOffset> Wartość zawiera nie tylko datę i godzinę, ale również przesunięcie, które jednoznacznie definiuje datę i godzinę względem czasu UTC. Dzięki temu można zdefiniować równość nieco inaczej niż w przypadku <xref:System.DateTimeOffset> wartości. Wartości są równe, jeśli mają taką samą wartość daty i godziny, wartości <xref:System.DateTimeOffset> są równe, jeśli oba odwołują się do tego samego punktu w czasie. <xref:System.DateTime> Pozwala to na <xref:System.DateTimeOffset> dokładniejsze i mniejsze wykorzystanie interpretacji w przypadku porównywania i w większości operacji arytmetycznych, które określają interwał między dwiema datami i godzinami. Poniższy przykład, który jest <xref:System.DateTimeOffset> odpowiednikiem poprzedniego przykładu w porównaniu wartości lokalnych i UTC <xref:System.DateTimeOffset> , ilustruje tę różnicę w zachowaniu.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

W tym przykładzie <xref:System.DateTimeOffset.CompareTo%2A> Metoda wskazuje, że bieżący czas lokalny i bieżący czas UTC są równe, a odejmowanie <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> wartości wskazuje, że różnica między nimi wynosi <xref:System.TimeSpan.Zero?displayProperty=nameWithType>dwa razy.

Głównym ograniczeniem używania <xref:System.DateTimeOffset> wartości w czasie arytmetycznym jest to, że chociaż <xref:System.DateTimeOffset> wartości mają pewną świadomość strefy czasowej, nie są w pełni świadome strefy czasowej. Chociaż przesunięcie <xref:System.DateTimeOffset> wartości odzwierciedla przesunięcie strefy czasowej z UTC, gdy zmienna jest przypisana po raz pierwszy, staje się nieskojarzona z strefą czasową. <xref:System.DateTimeOffset> Ponieważ nie jest już bezpośrednio skojarzony z możliwym do zidentyfikowania czasem, Dodawanie i odejmowanie interwałów daty i czasu nie uwzględnia reguł korekty strefy czasowej.

Aby zilustrować, przechodzenie do czasu letniego w Stanach Zjednoczonych Centralna standardowa strefa czasowa występuje o godz. 2:00 9 marca 2008. Oznacza to, że dodanie interwału dwóch i pół godziny do środkowego czasu standardowego o 1:30 rano 9 marca 2008 powinien utworzyć datę i godzinę 5:00 rano 9 marca 2008. Jednak, jak pokazano na poniższym przykładzie, wynikiem dodania jest 4:00 rano 9 marca 2008. Należy zauważyć, że ten wynik operacji reprezentuje właściwy punkt w czasie, chociaż nie jest to godzina w strefie czasowej, w której jesteśmy zainteresowani (czyli nie ma oczekiwanego przesunięcia strefy czasowej).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operacje arytmetyczne z czasami w strefach czasowych

<xref:System.TimeZoneInfo> Klasa zawiera szereg metod konwersji, które automatycznie stosują korekty podczas konwertowania czasu z jednej strefy czasowej na inną. Należą do nich między innymi:

- Metody <xref:System.TimeZoneInfo.ConvertTime%2A> i<xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> , które konwertują czasy między dowolnymi dwiema strefami czasowymi.

- Metody <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> i<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> , które konwertują czas w określonej strefie czasowej na czas UTC lub konwertują czasu UTC na czas w określonej strefie czasowej.

Aby uzyskać szczegółowe informacje, zobacz [konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Klasa nie udostępnia żadnych metod, które automatycznie stosują reguły korekty podczas wykonywania operacji arytmetycznych daty i czasu. Można to zrobić przez przekonwertowanie czasu w strefie czasowej na UTC, wykonanie operacji arytmetycznej, a następnie konwersję z powrotem na godzinę w strefie czasowej. Aby uzyskać szczegółowe informacje [, zobacz How to: Używaj stref czasowych w czasie operacji arytmetycznych](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Na przykład poniższy kod jest podobny do poprzedniego kodu, który dodał dwie i pół godziny do 2:00 rano 9 marca 2008. Jednak ze względu na to, że konwertuje środkowy czas standardowy na UTC przed wykonaniem operacji arytmetycznych daty i godziny, a następnie konwertuje wynik z z powrotem do centralnego czasu standardowego, a wynikowy czas odzwierciedla centralne przejście standardowej strefy czasowej do czasu letniego. pierwszym.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Używanie stref czasowych w czasie operacji arytmetycznych](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
