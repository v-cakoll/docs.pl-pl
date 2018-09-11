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
ms.openlocfilehash: c2a50823b812541786cf1bebfd6b1262ce2e9314
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271997"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Wykonywanie operacji arytmetycznych na wartościach dat i godzin

Mimo że zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> struktury zapewniają elementów członkowskich, które wykonują operacje arytmetyczne na wartości, wyniki operacji arytmetycznych różnią się bardzo. W tym temacie sprawdza, czy te różnice dotyczą stopni świadomości strefy czasowej w danych daty i godziny i w tym artykule omówiono sposób wykonywania pełni strefy czasowej operacji pamiętać przy użyciu danych daty i godziny.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porównywanie i operacje arytmetyczne wartościami daty/godziny

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Właściwość umożliwia <xref:System.DateTimeKind> wartość do przypisania do daty i godziny, aby wskazać, czy reprezentuje czas lokalny, uniwersalny czas koordynowany (UTC) lub czas w nieokreślonej strefy czasowej. Jednak te informacje ograniczoną strefę czasową jest ignorowane w przypadku porównywania lub wykonywanie arytmetyka na daty i godziny <xref:System.DateTimeKind> wartości. Ilustruje to poniższy przykład porównuje bieżący czas lokalny przy użyciu bieżącego czasu UTC.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Metoda zgłasza, że czasu lokalnego jest wcześniejsza niż (lub mniej niż) czasu UTC, a operacja odejmowania wskazuje, że różnica między czasem UTC i czasem lokalnym systemem w Stanach Zjednoczonych Standardowe i Pacyfik, część strefa czasowa jest siedem godzin. Ale ponieważ te dwie wartości zapewniają różne reprezentacje pojedynczy punkt w czasie, usuń zaznaczenie w tym przypadku czy dany interwał czasu są całkowicie przypisane do przesunięcie strefy czasu lokalnego względem czasu UTC.

Ogólnie rzecz biorąc <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> właściwość nie ma wpływu na wyniki zwrócone przez <xref:System.DateTime.Kind> metody porównania i operacje arytmetyczne (co wskazuje na to funkcja porównania dwa identyczne punkty w czasie), chociaż może mieć wpływ na interpretację wyników. Na przykład:

* Wynik każdej operacji arytmetycznych wykonywane na dwie wartości daty i godziny, którego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> równa obie właściwości <xref:System.DateTimeKind> odzwierciedla przedział czasu rzeczywistego, między dwiema wartościami. Podobnie porównanie dwóch takich wartości daty i godziny dokładnie odzwierciedla relacji między wartościami godziny.

* Wynik każdej operacji arytmetycznych lub porównaniach wykonywane na dwie wartości daty i godziny, którego <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> równa obie właściwości <xref:System.DateTimeKind> lub dwie wartości daty i godziny, z różnymi <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości właściwości odzwierciedla różnica czasu zegara między dwiema wartościami.

* Operacji arytmetycznych lub porównaniach na wartości lokalne daty i godziny należy rozważyć, czy określonej wartości lub jest ona niejednoznaczna nieprawidłowa ani nie są pod uwagę wpływ żadnych reguł dopasowania, wynikających z przejścia strefy czasu lokalnego do lub z czasu letniego co umożliwia zaoszczędzenie czasu.

* Każdej operacji, która porównuje lub oblicza różnicę między czasem UTC i czasem lokalnym obejmuje przedział czasu równy przesunięcie strefy czasu lokalnego względem czasu UTC, w wyniku.

* Każdej operacji, która porównuje lub oblicza różnicę między przez nieokreślony czas i czasem UTC lub czasu lokalnego odzwierciedla czas zegara proste. Nie są uwzględniane różnice stref czasowych, a wynik nie będzie odzwierciedlał stosowania reguł dopasowania stref czasowych.

* Każdej operacji, która porównuje lub oblicza różnicę między dwoma nieokreślony czas może obejmować nieznany interwału, który zawiera różnicę między czasem w dwóch różnych strefach czasowych.

Istnieje wiele scenariuszy, w której strefie czasowej różnice nie wpływają na obliczenia daty i godziny (omówienie niektórych z nich można znaleźć [Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) lub, w którym kontekście Data i godzina danych definiuje znaczenie operacji porównywania lub operacje arytmetyczne.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porównywanie i operacji arytmetycznych na wartościach wartości DateTimeOffset

A <xref:System.DateTimeOffset> wartość obejmuje nie tylko daty i czasu, ale także przesunięcie, która jednoznacznie określa, że data i godzina względem czasu UTC. Dzięki temu można zdefiniować równość trochę inaczej niż <xref:System.DateTimeOffset> wartości. Natomiast <xref:System.DateTime> wartości są równe, jeśli mają one tę samą datę i godzinę, <xref:System.DateTimeOffset> wartości są równe, jeśli oba odnoszą się do tego samego punktu w czasie. To sprawia, że <xref:System.DateTimeOffset> wartości bardziej dokładne i mniej wymagające interpretacji, gdy jest używana w porównaniach i w większości operacje arytmetyczne, które określają interwał między dwiema datami i godzinami. Poniższy przykład, który jest <xref:System.DateTimeOffset> odpowiednikiem poprzedniego przykładu, która w porównaniu z lokalnym i czasem UTC <xref:System.DateTimeOffset> wartości, pokazano różnicę w działaniu.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

W tym przykładzie <xref:System.DateTimeOffset.CompareTo%2A> metody oznacza, że bieżącym czasem lokalnym i bieżący czas UTC są równe i odejmowania <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> wartości oznacza, że różnica między dwiema wartościami godziny jest <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Dyrektor ograniczenie użycia <xref:System.DateTimeOffset> wartości arytmetyka daty i godziny jest to, że chociaż <xref:System.DateTimeOffset> wartości mają pewne świadomości strefy czasowej, nie są w pełni pamiętać strefy czasowej. Mimo że <xref:System.DateTimeOffset> przesunięcie wartości odzwierciedla przesunięcie strefy czasowej względem czasu UTC podczas <xref:System.DateTimeOffset> zmiennej najpierw jest przypisywana wartość, staje się on następnie oddzielone od strefy czasowej. Dlatego nie jest już bezpośrednio związane z czasem do zidentyfikowania, dodawania i odejmowania, Data i godzina interwałów, które nie należy traktować reguł korygowania strefę czasową.

Aby zilustrować, przejście do czasu letniego w Stanach Zjednoczonych Środkowy czas standardowy strefy odbywa się o 2:00 9 marca 2008. Oznacza to, że dodanie interwału dwóch i pół godziny do środkowy czas standardowy o godzinie 1:30:00 9 marca 2008 powinno to dawać daty i godziny 5:00:00 9 marca 2008. Jednakże jak pokazano na poniższym przykładzie, wynik dodawania jest 4:00:00 9 marca 2008. Należy pamiętać, że ten wynik tej operacji reprezentują prawidłowy punkt w czasie, chociaż nie jest to czas w strefie czasowej, w którym jesteśmy zainteresowani (oznacza to, że nie ma oczekiwanego strefy czasowej przesunięcie).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operacje arytmetyczne z czasem w strefach czasowych

<xref:System.TimeZoneInfo> Klasy zawiera szereg metod konwersji, które automatyczne stosowanie dostosowań, podczas ich Konwertowanie godzin między strefami czasowymi do innego. Należą do nich między innymi:

* <xref:System.TimeZoneInfo.ConvertTime%2A> i <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> metody, które Konwertowanie godzin między strefami czasowymi, wszelkie dwie.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> i <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody, które przekonwertować wartość czasu w określonej strefie czasowej UTC lub konwersji czasu UTC na czas w określonej strefy czasowej.

Aby uzyskać więcej informacji, zobacz [Konwertowanie godzin między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Klasa nie zapewnia żadnych metod, które automatyczne stosowanie reguł korygowania, gdy wykonujesz arytmetyka daty i godziny. Jednakże można to zrobić przez konwertowanie czas w strefie czasowej UTC, wykonywanie operacji arytmetycznych i następnie konwertując względem czasu UTC do czasu w strefie czasowej. Aby uzyskać więcej informacji, zobacz [porady: użycie stref czasowych w arytmetyka daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Na przykład poniższy kod jest podobny do poprzedniego kodu, który dodaje dwa i pół godziny do 2:00:00 9 marca 2008. Jednak ponieważ środkowy czas standardowy go konwertuje na czas UTC, zanim wykonuje arytmetyczne daty i czasu, a następnie konwertuje wynik względem czasu UTC do Środkowa (czas standardowy), czasu wynikowy odzwierciedla przejście letniego strefy Środkowa (czas standardowy) czas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
* [Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
