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
ms.openlocfilehash: 428553f75db2cca6705ac72873e86e120e94d134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132592"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Konwertowanie pomiędzy DateTime i DateTimeOffset

Chociaż struktura <xref:System.DateTimeOffset> zapewnia większą stopień świadomości strefy czasowej niż struktura <xref:System.DateTime>, parametry <xref:System.DateTime> są najczęściej używane w wywołaniach metod. Z tego powodu możliwość konwersji wartości <xref:System.DateTimeOffset> na wartości <xref:System.DateTime> i na odwrót jest szczególnie ważna. W tym temacie pokazano, jak wykonać te konwersje w taki sposób, że możliwie jak najwięcej informacji o strefie czasowej.

> [!NOTE]
> Zarówno <xref:System.DateTime>, jak i typy <xref:System.DateTimeOffset> mają pewne ograniczenia w przypadku reprezentowania czasu w strefach czasowych. Mając Właściwość <xref:System.DateTime.Kind%2A>, <xref:System.DateTime> może odzwierciedlać tylko uniwersalny czas koordynowany (UTC) i lokalną strefę czasową systemu. <xref:System.DateTimeOffset> odzwierciedla przesunięcie czasu z UTC, ale nie odzwierciedla rzeczywistej strefy czasowej, do której należy to przesunięcie. Aby uzyskać szczegółowe informacje o wartościach czasowych i obsłudze stref czasowych, zobacz [Wybieranie między datami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Konwersje od daty/godziny do DateTimeOffset

Struktura <xref:System.DateTimeOffset> zapewnia dwa równoważne sposoby wykonywania <xref:System.DateTime> <xref:System.DateTimeOffset> konwersji, które są odpowiednie dla większości konwersji:

- Konstruktor <xref:System.DateTimeOffset.%23ctor%2A>, który tworzy nowy obiekt <xref:System.DateTimeOffset> na podstawie wartości <xref:System.DateTime>.

- Operator niejawnej konwersji, który umożliwia przypisanie wartości <xref:System.DateTime> do obiektu <xref:System.DateTimeOffset>.

W przypadku wartości czasu UTC i lokalnego <xref:System.DateTime> wartość właściwości <xref:System.DateTimeOffset.Offset%2A> wyników <xref:System.DateTimeOffset> dokładnie odzwierciedla przesunięcia czasu UTC lub lokalnej strefy czasowej. Na przykład poniższy kod konwertuje czas UTC na jego równoważną wartość <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

W tym przypadku przesunięcie zmiennej `utcTime2` to 00:00. Podobnie Poniższy kod konwertuje czas lokalny na jego równoważną wartość <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Jednak w przypadku wartości <xref:System.DateTime>, których właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, te dwie metody konwersji generują <xref:System.DateTimeOffset> wartość, której przesunięcie jest stosowane przez lokalną strefę czasową. Jest to pokazane w poniższym przykładzie, który jest uruchamiany w strefie czasowej w Stanach Zjednoczonych (USA).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Jeśli <xref:System.DateTime> wartość odzwierciedla datę i godzinę w innym niż lokalna strefa czasowa lub UTC, można przekonwertować ją na wartość <xref:System.DateTimeOffset> i zachować informacje o strefie czasowej, wywołując przeciążony Konstruktor <xref:System.DateTimeOffset.%23ctor%2A>. Na przykład poniższy przykład tworzy wystąpienie obiektu <xref:System.DateTimeOffset>, który odzwierciedla środkowy czas standardowy.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Drugi parametr tego przeciążenia konstruktora, obiekt <xref:System.TimeSpan>, który reprezentuje przesunięcie czasu od czasu UTC, należy pobrać, wywołując metodę <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> odpowiedniej strefy czasowej. Pojedynczy parametr metody jest wartością <xref:System.DateTime>, która reprezentuje datę i godzinę do przekonwertowania. Jeśli strefa czasowa obsługuje czas letni, ten parametr umożliwia metodzie określenie odpowiedniego przesunięcia dla danego dnia i godziny.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Konwersje z DateTimeOffset na DateTime

Właściwość <xref:System.DateTimeOffset.DateTime%2A> jest najczęściej używana do przeprowadzenia <xref:System.DateTimeOffset> do konwersji <xref:System.DateTime>. Zwraca jednak wartość <xref:System.DateTime>, której Właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Unspecified>, jak pokazano w poniższym przykładzie.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Oznacza to, że wszelkie informacje o relacji <xref:System.DateTimeOffset> wartości z czasem UTC zostaną utracone przez konwersję, gdy zostanie użyta Właściwość <xref:System.DateTimeOffset.DateTime%2A>. Ma to wpływ na <xref:System.DateTimeOffset> wartości, które odnoszą się do czasu UTC lub czasu lokalnego systemu, ponieważ struktura <xref:System.DateTimeOffset.DateTime%2A> odzwierciedla tylko te dwie strefy czasowe w <xref:System.DateTime.Kind%2A> właściwości.

Aby zachować możliwie jak najwięcej informacji o strefie czasowej podczas konwertowania <xref:System.DateTimeOffset> na wartość <xref:System.DateTime>, można użyć właściwości <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>.

### <a name="converting-a-utc-time"></a>Konwertowanie czasu UTC

Aby wskazać, że przekonwertowaną wartość <xref:System.DateTimeOffset.DateTime%2A> jest czas UTC, można pobrać wartość właściwości <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>. Różni się od właściwości <xref:System.DateTimeOffset.DateTime%2A> na dwa sposoby:

- Zwraca <xref:System.DateTime> wartość, której Właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Utc>.

- Jeśli wartość właściwości <xref:System.DateTimeOffset.Offset%2A> nie jest równa <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, konwertuje godzinę na czas UTC.

> [!NOTE]
> Jeśli aplikacja wymaga, aby przekonwertowane wartości <xref:System.DateTime> jednoznacznie identyfikować pojedynczy punkt w czasie, należy rozważyć użycie właściwości <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> do obsługi wszystkich <xref:System.DateTimeOffset> konwersji <xref:System.DateTime>.

Poniższy kod używa właściwości <xref:System.DateTimeOffset.UtcDateTime%2A> do konwersji wartości <xref:System.DateTimeOffset>, której przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> do wartości <xref:System.DateTime>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Poniższy kod używa właściwości <xref:System.DateTimeOffset.UtcDateTime%2A> do przeprowadzenia konwersji strefy czasowej i konwersji typu na wartość <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Konwertowanie czasu lokalnego

Aby wskazać, że wartość <xref:System.DateTimeOffset> reprezentuje czas lokalny, można przekazać <xref:System.DateTime> wartość zwróconą przez właściwość <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> do `static` (`Shared` w Visual Basic) metody <xref:System.DateTime.SpecifyKind%2A>. Metoda zwraca datę i godzinę przekazaną do niego jako pierwszy parametr, ale ustawia właściwość <xref:System.DateTime.Kind%2A> na wartość określoną przez drugi parametr. Poniższy kod używa metody <xref:System.DateTime.SpecifyKind%2A> podczas konwertowania wartości <xref:System.DateTimeOffset>, której przesunięcie odnosi się do numeru lokalnej strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Można również użyć właściwości <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> do przekonwertowania wartości <xref:System.DateTimeOffset> na wartość lokalną <xref:System.DateTime>. Właściwość <xref:System.DateTime.Kind%2A> zwracanej wartości <xref:System.DateTime> jest <xref:System.DateTimeKind.Local>. Poniższy kod używa właściwości <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> podczas konwertowania wartości <xref:System.DateTimeOffset>, której przesunięcie odnosi się do numeru lokalnej strefy czasowej. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Po pobraniu wartości <xref:System.DateTime> przy użyciu właściwości <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>, metoda dostępu `get` do właściwości najpierw konwertuje wartość <xref:System.DateTimeOffset> na UTC, a następnie konwertuje ją na czas lokalny, wywołując metodę <xref:System.DateTimeOffset.ToLocalTime%2A>. Oznacza to, że można pobrać wartość z właściwości <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>, aby wykonać konwersję strefy czasowej w tym samym czasie, w którym wykonywana jest konwersja typu. Oznacza to również, że reguły dostosowania lokalnej strefy czasowej są stosowane podczas konwersji. Poniższy kod ilustruje użycie właściwości <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> do wykonania konwersji typu i strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda konwersji ogólnego przeznaczenia

W poniższym przykładzie zdefiniowano metodę o nazwie `ConvertFromDateTimeOffset`, która konwertuje wartości <xref:System.DateTimeOffset> na wartości <xref:System.DateTime>. Na podstawie jego przesunięcia decyduje o tym, czy <xref:System.DateTimeOffset> wartość jest czasem UTC, czasem lokalnym, czy innym, i definiuje odpowiednio Właściwość <xref:System.DateTime.Kind%2A> wartości daty i godziny.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

W poniższym przykładzie jest wywoływana metoda `ConvertFromDateTimeOffset`, która umożliwia konwertowanie wartości <xref:System.DateTimeOffset>, które reprezentują czas UTC, czas lokalny i godzinę w standardowej strefie czasowej (USA).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Należy zauważyć, że ten kod tworzy dwa założenia, które w zależności od aplikacji i źródła wartości daty i godziny mogą nie zawsze być prawidłowe:

- Przyjęto założenie, że wartość daty i godziny, której przesunięcie jest <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, reprezentuje czas UTC. W rzeczywistości czas UTC nie jest czasem w określonej strefie czasowej, ale jest to czas, w którym czasy w strefach czasowych na świecie są znormalizowane. Strefy czasowe mogą również mieć przesunięcie <xref:System.TimeSpan.Zero>.

- Przyjęto założenie, że data i godzina, o której przesunięcie jest równe, dla lokalnej strefy czasowej reprezentuje lokalną strefę czasową. Ponieważ wartości daty i godziny są odłączone od oryginalnej strefy czasowej, może to nie być przypadek; Data i godzina mogą pochodzić z innej strefy czasowej z tym samym przesunięciem.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
