---
title: Konwertowanie pomiędzy DateTime i DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91ed8edd0c5cd3cb1d051157596f311718195d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107063"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Konwertowanie pomiędzy DateTime i DateTimeOffset

Chociaż struktura zapewnia większy stopień świadomości strefy czasowej <xref:System.DateTime> niż struktura, <xref:System.DateTime> parametry są najczęściej używane w wywołaniach metod. <xref:System.DateTimeOffset> Z tego powodu możliwość konwersji <xref:System.DateTimeOffset> wartości na <xref:System.DateTime> wartości i na odwrót jest szczególnie ważna. W tym temacie pokazano, jak wykonać te konwersje w taki sposób, że możliwie jak najwięcej informacji o strefie czasowej.

> [!NOTE]
> <xref:System.DateTime> Zarówno ,<xref:System.DateTimeOffset> jak i typy mają pewne ograniczenia w przypadku reprezentowania czasu w strefach czasowych. Wraz z <xref:System.DateTime.Kind%2A> jego <xref:System.DateTime> właściwością może odzwierciedlać tylko uniwersalny czas koordynowany (UTC) i lokalną strefę czasową systemu. <xref:System.DateTimeOffset>odzwierciedla przesunięcie czasu od UTC, ale nie odzwierciedla rzeczywistej strefy czasowej, do której należy to przesunięcie. Aby uzyskać szczegółowe informacje o wartościach czasowych i obsłudze stref czasowych, zobacz [Wybieranie między datami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Konwersje od daty/godziny do DateTimeOffset

Struktura zapewnia dwa równoważne sposoby <xref:System.DateTimeOffset> wykonywania <xref:System.DateTime> konwersji, które są odpowiednie dla większości konwersji: <xref:System.DateTimeOffset>

- Konstruktor, który tworzy nowy <xref:System.DateTimeOffset> obiekt na podstawie <xref:System.DateTime> wartości. <xref:System.DateTimeOffset.%23ctor%2A>

- Operator niejawnej konwersji, który umożliwia przypisanie <xref:System.DateTime> wartości <xref:System.DateTimeOffset> do obiektu.

W przypadku czasu UTC <xref:System.DateTime> i wartości <xref:System.DateTimeOffset.Offset%2A> lokalnych Właściwość wartości wyniki <xref:System.DateTimeOffset> dokładnie odzwierciedla przesunięcie czasu UTC lub lokalną strefę czasową. Na przykład poniższy kod konwertuje czas UTC na jego równoważną <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

W tym przypadku przesunięcie `utcTime2` zmiennej to 00:00. Podobnie Poniższy kod konwertuje czas lokalny na jego równoważną <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Jednakże w przypadku <xref:System.DateTime> wartości, <xref:System.DateTime.Kind%2A> których właściwość <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>jest, te dwie metody konwersji tworzą <xref:System.DateTimeOffset> wartość, której przesunięcie jest dla lokalnej strefy czasowej. Jest to pokazane w poniższym przykładzie, który jest uruchamiany w Stanach Zjednoczonych Standardowa strefa czasowa (pacyficzny).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Jeśli wartość odzwierciedla datę i godzinę w innym niż lokalna strefa czasowa lub UTC, można przekonwertować ją <xref:System.DateTimeOffset> na wartość i zachować informacje o strefie czasowej, wywołując Konstruktor przeciążony <xref:System.DateTimeOffset.%23ctor%2A>. <xref:System.DateTime> Na przykład poniższy przykład tworzy wystąpienie <xref:System.DateTimeOffset> obiektu, który odzwierciedla środkowy czas standardowy.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Drugi parametr tego przeciążenia konstruktora, <xref:System.TimeSpan> obiekt, który reprezentuje przesunięcie czasu z UTC, powinien zostać pobrany przez <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> wywołanie metody odpowiedniej strefy czasowej. Pojedynczy parametr metody jest <xref:System.DateTime> wartością reprezentującą datę i godzinę do przekonwertowania. Jeśli strefa czasowa obsługuje czas letni, ten parametr umożliwia metodzie określenie odpowiedniego przesunięcia dla danego dnia i godziny.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Konwersje z DateTimeOffset na DateTime

Właściwość jest najczęściej używana <xref:System.DateTimeOffset> do <xref:System.DateTime> konwersji. <xref:System.DateTimeOffset.DateTime%2A> Jednakże zwraca <xref:System.DateTime> wartość, której <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Unspecified>, jak pokazano w poniższym przykładzie.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Oznacza to, że wszelkie informacje o <xref:System.DateTimeOffset> relacji wartości z czasem UTC są tracone przez konwersję, <xref:System.DateTimeOffset.DateTime%2A> gdy właściwość jest używana. Ma to <xref:System.DateTimeOffset> wpływ na wartości, które odpowiadają czas UTC lub na czas lokalny systemu, <xref:System.DateTimeOffset.DateTime%2A> ponieważ struktura odzwierciedla tylko te dwie strefy czasowe <xref:System.DateTime.Kind%2A> w swojej właściwości.

Aby zachować możliwie jak najwięcej informacji o strefie czasowej podczas <xref:System.DateTimeOffset> konwertowania <xref:System.DateTime> do wartości <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> , można użyć właściwości i <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> .

### <a name="converting-a-utc-time"></a>Konwertowanie czasu UTC

Aby wskazać, że przekonwertowana <xref:System.DateTimeOffset.DateTime%2A> wartość jest czasem UTC, można pobrać wartość <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości. Różni się od <xref:System.DateTimeOffset.DateTime%2A> właściwości na dwa sposoby:

- Zwraca <xref:System.DateTime> wartość, której <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Utc>.

- Jeśli wartość <xref:System.TimeSpan.Zero?displayProperty=nameWithType>właściwości nie jest równa, konwertuje godzinę na czas UTC. <xref:System.DateTimeOffset.Offset%2A>

> [!NOTE]
> Jeśli aplikacja wymaga, aby skonwertowane <xref:System.DateTime> wartości jednoznacznie identyfikować pojedynczy punkt w czasie, należy rozważyć <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> użycie <xref:System.DateTime> właściwości do obsługi wszystkich <xref:System.DateTimeOffset> konwersji.

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości do <xref:System.DateTimeOffset> konwersji wartości, <xref:System.DateTime> której przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości do przeprowadzenia konwersji strefy czasowej i konwersji typu <xref:System.DateTimeOffset> na wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Konwertowanie czasu lokalnego

Aby wskazać, że <xref:System.DateTimeOffset> wartość reprezentuje czas lokalny, można <xref:System.DateTime> przekazać wartość zwracaną `static` przez <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> właściwość do metody (`Shared` w Visual Basic) <xref:System.DateTime.SpecifyKind%2A> . Metoda zwraca datę i godzinę przekazaną do niego jako pierwszy parametr, ale ustawia <xref:System.DateTime.Kind%2A> właściwość na wartość określoną przez jego drugi parametr. Poniższy kod używa <xref:System.DateTime.SpecifyKind%2A> metody podczas <xref:System.DateTimeOffset> konwertowania wartości, której przesunięcie odnosi się do numeru lokalnej strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Można również użyć właściwości, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> aby <xref:System.DateTimeOffset> przekonwertować wartość na wartość lokalną <xref:System.DateTime> . Właściwość zwracanej <xref:System.DateTime> wartości to <xref:System.DateTimeKind.Local>. <xref:System.DateTime.Kind%2A> Poniższy kod używa <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości podczas <xref:System.DateTimeOffset> konwertowania wartości, której przesunięcie odnosi się do numeru lokalnej strefy czasowej. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Po <xref:System.DateTime> pobraniu wartości `get` <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> przy użyciu właściwości metoda dostępu do właściwości najpierw konwertuje <xref:System.DateTimeOffset> wartość na <xref:System.DateTimeOffset.ToLocalTime%2A> UTC, a następnie konwertuje ją na czas lokalny, wywołując metodę. Oznacza to, że można pobrać wartość z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości, aby wykonać konwersję strefy czasowej w tym samym czasie, w którym wykonywana jest konwersja typu. Oznacza to również, że reguły dostosowania lokalnej strefy czasowej są stosowane podczas konwersji. Poniższy kod ilustruje użycie <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości do wykonania konwersji typu i strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda konwersji ogólnego przeznaczenia

W poniższym przykładzie zdefiniowano metodę o `ConvertFromDateTimeOffset` nazwie, <xref:System.DateTimeOffset> która konwertuje <xref:System.DateTime> wartości na wartości. Na podstawie jego przesunięcia decyduje o tym <xref:System.DateTimeOffset> , czy wartość jest czasem UTC, czasem lokalnym czy innym, i odpowiednio definiuje <xref:System.DateTime.Kind%2A> Właściwość zwracanej daty i godziny.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

W poniższym przykładzie jest wywoływana `ConvertFromDateTimeOffset` Metoda konwersji <xref:System.DateTimeOffset> wartości reprezentujących czas UTC, czas lokalny i godzinę w Stanach Zjednoczonych Centralna standardowa strefa czasowa.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Należy zauważyć, że ten kod tworzy dwa założenia, które w zależności od aplikacji i źródła wartości daty i godziny mogą nie zawsze być prawidłowe:

- Przyjęto założenie, że wartość daty i godziny, <xref:System.TimeSpan.Zero?displayProperty=nameWithType> której przesunięcie jest reprezentowane przez czas UTC. W rzeczywistości czas UTC nie jest czasem w określonej strefie czasowej, ale jest to czas, w którym czasy w strefach czasowych na świecie są znormalizowane. Strefy czasowe mogą również mieć przesunięcie <xref:System.TimeSpan.Zero>.

- Przyjęto założenie, że data i godzina, o której przesunięcie jest równe, dla lokalnej strefy czasowej reprezentuje lokalną strefę czasową. Ponieważ wartości daty i godziny są odłączone od oryginalnej strefy czasowej, może to nie być przypadek; Data i godzina mogą pochodzić z innej strefy czasowej z tym samym przesunięciem.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
