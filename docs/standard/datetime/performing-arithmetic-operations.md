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
ms.openlocfilehash: 0db0331620da8337930bfacf5d1bbd9913647afa
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344159"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Wykonywanie operacji arytmetycznych na wartościach dat i godzin

Chociaż zarówno <xref:System.DateTime> struktury, jak i <xref:System.DateTimeOffset> struktury zapewniają elementy członkowskie, które wykonują operacje arytmetyczne na ich wartościach, wyniki operacji arytmetycznych są bardzo różne. W tym temacie analizuje te różnice, odnosi się do stopni świadomości strefy czasowej w danych daty i godziny i omówiono sposób wykonywania operacji w pełni strefę czasową za pomocą danych daty i godziny.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Porównania i operacje arytmetyczne z wartościami DateTime

Właściwość <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> umożliwia <xref:System.DateTimeKind> wartość, która ma być przypisana do daty i godziny, aby wskazać, czy reprezentuje czas lokalny, skoordynowany czas uniwersalny (UTC) lub czas w nieokreślonej strefie czasowej. Jednak ta ograniczona strefa czasowa jest ignorowana podczas porównywania lub <xref:System.DateTimeKind> wykonywania arytmetyki daty i godziny wartości. Poniższy przykład, który porównuje bieżący czas lokalny z bieżącym czasem UTC, ilustruje to.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

Metoda <xref:System.DateTime.CompareTo%28System.DateTime%29> raportuje, że czas lokalny jest wcześniejszy (lub mniejszy) czas UTC, a operacja odejmowania wskazuje, że różnica między czasem UTC a czasem lokalnym dla systemu w standardowej strefie czasowej usa pacific wynosi siedem godzin. Ale ponieważ te dwie wartości zapewniają różne reprezentacje pojedynczego punktu w czasie, jest jasne, w tym przypadku, że przedział czasu jest całkowicie przypisać do przesunięcia lokalnej strefy czasowej z UTC.

Bardziej ogólnie rzecz <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> biorąc, właściwość nie <xref:System.DateTime.Kind> wpływa na wyniki zwracane przez porównanie i metody arytmetyczne (jak wskazuje porównanie dwóch identycznych punktów w czasie), chociaż może mieć wpływ na interpretację tych wyników. Przykład:

- Wynik każdej operacji arytmetycznej wykonywanej na dwie <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości daty i godziny, których właściwości są równe, <xref:System.DateTimeKind> odzwierciedla rzeczywisty przedział czasu między dwiema wartościami. Podobnie porównanie dwóch takich wartości daty i godziny dokładnie odzwierciedla relację między czasami.

- Wynik każdej operacji arytmetycznej lub porównania wykonywanej na <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> dwie wartości <xref:System.DateTimeKind> daty i godziny, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> których właściwości są równe lub na dwie wartości daty i godziny z różnymi wartościami właściwości odzwierciedla różnicę w czasie zegara między dwiema wartościami.

- Operacje arytmetyczne lub porównawcze w lokalnych wartościach daty i godziny nie biorą pod uwagę, czy określona wartość jest niejednoznaczna czy nieprawidłowa, ani nie uwzględniają wpływu jakichkolwiek reguł korekty, które wynikają z przejścia lokalnej strefy czasowej do lub z światła dziennego oszczędność czasu.

- Każda operacja, która porównuje lub oblicza różnicę między czasem UTC a czasem lokalnym, zawiera przedział czasu równy odsuniętemu od czasu UTC w wyniku lokalnej strefy czasowej.

- Każda operacja, która porównuje lub oblicza różnicę między nieokreślonym czasem a czasem UTC lub czasem lokalnym, odzwierciedla prosty czas zegara. Różnice w strefie czasowej nie są brane pod uwagę, a wynik nie odzwierciedla stosowania reguł korekty strefy czasowej.

- Każda operacja, która porównuje lub oblicza różnicę między dwoma nieokreślonymi czasami może zawierać nieznany interwał, który odzwierciedla różnicę między czasem w dwóch różnych strefach czasowych.

Istnieje wiele scenariuszy, w których różnice stref czasowych nie wpływają na obliczenia daty i godziny (w celu omówienia niektórych z nich, zobacz [Wybór między DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) lub w którym kontekst danych daty i godziny definiuje znaczenie operacji porównawczych lub arytmetycznych.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Porównania i operacje arytmetyczne z wartościami DateTimeOffset

Wartość <xref:System.DateTimeOffset> zawiera nie tylko datę i godzinę, ale także przesunięcie, które jednoznacznie definiuje tę datę i godzinę względem czasu UTC. Dzięki temu można zdefiniować równość <xref:System.DateTimeOffset> nieco inaczej niż w przypadku wartości. Podczas <xref:System.DateTime> gdy wartości są równe, jeśli mają <xref:System.DateTimeOffset> tę samą wartość daty i godziny, wartości są równe, jeśli oba odnoszą się do tego samego punktu w czasie. To sprawia, <xref:System.DateTimeOffset> że wartość bardziej dokładne i mniej potrzeby interpretacji, gdy jest używany w porównaniach i w większości operacji arytmetycznych, które określają interwał między dwiema datami i godzinami. Poniższy przykład, który <xref:System.DateTimeOffset> jest odpowiednikiem poprzedniego przykładu, <xref:System.DateTimeOffset> który porównał wartości lokalne i UTC, ilustruje tę różnicę w zachowaniu.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

W tym przykładzie <xref:System.DateTimeOffset.CompareTo%2A> metoda wskazuje, że bieżący czas lokalny i bieżący czas <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> UTC są równe, a <xref:System.TimeSpan.Zero?displayProperty=nameWithType>odejmowanie wartości wskazuje, że różnica między dwoma razy jest .

Głównym ograniczeniem <xref:System.DateTimeOffset> używania wartości w arytmetyce <xref:System.DateTimeOffset> daty i godziny jest to, że chociaż wartości mają pewną świadomość strefy czasowej, nie są w pełni świadome strefy czasowej. Mimo <xref:System.DateTimeOffset> że przesunięcie wartości odzwierciedla przesunięcie strefy czasowej z <xref:System.DateTimeOffset> czasu UTC, gdy zmienna jest najpierw przypisana wartość, staje się odłączony od strefy czasowej później. Ponieważ nie jest już bezpośrednio skojarzony z identyfikowalnym czasem, dodawanie i odejmowanie dat i interwałów czasu nie uwzględnia reguł dopasowania strefy czasowej.

Aby zilustrować, przejście na czas letni w centralnej strefie czasowej stanów USA odbywa się o godzinie 2:00. w dniu 9 marca 2008 r. Oznacza to, że dodanie dwu-i półgodzinnego interwału do centralnego czasu standardowego o godzinie 1:30 czasu środkowego. w dniu 9 marca 2008 r., powinien przedstawić datę i godzinę 5:00 Rano. w dniu 9 marca 2008 r. Jednak, jak pokazano w poniższym przykładzie, wynik dodania wynosi 4:00 Rano. w dniu 9 marca 2008 r. Należy zauważyć, że wynik tej operacji reprezentuje poprawny punkt w czasie, chociaż nie jest to czas w strefie czasowej, w której jesteśmy zainteresowani (oznacza to, że nie ma oczekiwanego przesunięcia strefy czasowej).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operacje arytmetyczne z czasem w strefach czasowych

Klasa <xref:System.TimeZoneInfo> zawiera szereg metod konwersji, które automatycznie stosują korekty podczas konwertowania czasów z jednej strefy czasowej na inną. Należą do nich między innymi:

- I <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> metody, które konwertuje razy między dowolnymi dwiema strefami czasowymi.

- Metody <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> i metody, które konwertuje czas w określonej strefie czasowej do CZASU UTC lub konwertować UTC do czasu w określonej strefie czasowej.

Aby uzyskać szczegółowe informacje, zobacz [Konwertowanie czasów między strefami czasowymi](../../../docs/standard/datetime/converting-between-time-zones.md).

Klasa <xref:System.TimeZoneInfo> nie zawiera żadnych metod, które automatycznie stosują reguły dopasowania podczas wykonywania arytmetyki daty i godziny. Można to jednak zrobić, konwertując czas w strefie czasowej na utc, wykonując operację arytmetyczną, a następnie konwertując z czasu UTC z powrotem na czas w strefie czasowej. Aby uzyskać szczegółowe informacje, zobacz [Jak: Używanie stref czasowych w arytmetyce daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Na przykład poniższy kod jest podobny do poprzedniego kodu, który dodał dwie i pół godziny do 2:00 rano. w dniu 9 marca 2008 r. Ponieważ jednak czas standardowy jest konwertowany na czas STANDARDOWY centralny na czas UTC przed wykonaniem arytmetyki daty i godziny, a następnie konwertuje wynik z czasu UTC z powrotem na centralny czas standardowy, wynikowy czas odzwierciedla przejście centralnej standardowej strefy czasowej na czas letni Czas.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Zobacz też

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
- [Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
