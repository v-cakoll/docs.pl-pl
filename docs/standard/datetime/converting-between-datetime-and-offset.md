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
ms.openlocfilehash: 7607d1d9dfc4f8f286262952599f96e4872db9c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278223"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Konwertowanie pomiędzy DateTime i DateTimeOffset

Chociaż <xref:System.DateTimeOffset> Struktura zapewnia większy stopień świadomości strefy czasowej niż <xref:System.DateTime> Struktura, <xref:System.DateTime> Parametry są najczęściej używane w wywołaniach metod. Z tego powodu możliwość konwersji <xref:System.DateTimeOffset> wartości na <xref:System.DateTime> wartości i na odwrót jest szczególnie ważna. W tym temacie pokazano, jak wykonać te konwersje w taki sposób, że możliwie jak najwięcej informacji o strefie czasowej.

> [!NOTE]
> Zarówno, <xref:System.DateTime> jak i <xref:System.DateTimeOffset> typy mają pewne ograniczenia w przypadku reprezentowania czasu w strefach czasowych. Wraz z jego <xref:System.DateTime.Kind%2A> właściwością <xref:System.DateTime> może odzwierciedlać tylko uniwersalny czas koordynowany (UTC) i lokalną strefę czasową systemu. <xref:System.DateTimeOffset>odzwierciedla przesunięcie czasu od UTC, ale nie odzwierciedla rzeczywistej strefy czasowej, do której należy to przesunięcie. Aby uzyskać szczegółowe informacje o wartościach czasowych i obsłudze stref czasowych, zobacz [Wybieranie między datami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Konwersje od daty/godziny do DateTimeOffset

<xref:System.DateTimeOffset>Struktura zapewnia dwa równoważne sposoby wykonywania <xref:System.DateTime> <xref:System.DateTimeOffset> konwersji, które są odpowiednie dla większości konwersji:

- <xref:System.DateTimeOffset.%23ctor%2A>Konstruktor, który tworzy nowy <xref:System.DateTimeOffset> obiekt na podstawie <xref:System.DateTime> wartości.

- Operator niejawnej konwersji, który umożliwia przypisanie <xref:System.DateTime> wartości do <xref:System.DateTimeOffset> obiektu.

W przypadku czasu UTC i <xref:System.DateTime> wartości lokalnych <xref:System.DateTimeOffset.Offset%2A> Właściwość <xref:System.DateTimeOffset> wartości wyniki dokładnie odzwierciedla przesunięcie czasu UTC lub lokalną strefę czasową. Na przykład poniższy kod konwertuje czas UTC na jego równoważną <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

W tym przypadku przesunięcie `utcTime2` zmiennej to 00:00. Podobnie Poniższy kod konwertuje czas lokalny na jego równoważną <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Jednakże w przypadku <xref:System.DateTime> wartości <xref:System.DateTime.Kind%2A> , których właściwość jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , te dwie metody konwersji tworzą <xref:System.DateTimeOffset> wartość, której przesunięcie jest dla lokalnej strefy czasowej. Jest to pokazane w poniższym przykładzie, który jest uruchamiany w strefie czasowej w Stanach Zjednoczonych (USA).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Jeśli <xref:System.DateTime> wartość odzwierciedla datę i godzinę w innym niż lokalna strefa czasowa lub UTC, można przekonwertować ją na <xref:System.DateTimeOffset> wartość i zachować informacje o strefie czasowej, wywołując Konstruktor przeciążony <xref:System.DateTimeOffset.%23ctor%2A> . Na przykład poniższy przykład tworzy wystąpienie <xref:System.DateTimeOffset> obiektu, który odzwierciedla środkowy czas standardowy.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Drugi parametr tego przeciążenia konstruktora, <xref:System.TimeSpan> obiekt, który reprezentuje przesunięcie czasu z UTC, powinien zostać pobrany przez wywołanie <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metody odpowiedniej strefy czasowej. Pojedynczy parametr metody jest <xref:System.DateTime> wartością reprezentującą datę i godzinę do przekonwertowania. Jeśli strefa czasowa obsługuje czas letni, ten parametr umożliwia metodzie określenie odpowiedniego przesunięcia dla danego dnia i godziny.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Konwersje z DateTimeOffset na DateTime

<xref:System.DateTimeOffset.DateTime%2A>Właściwość jest najczęściej używana do <xref:System.DateTimeOffset> <xref:System.DateTime> konwersji. Jednakże zwraca <xref:System.DateTime> wartość <xref:System.DateTime.Kind%2A> , której właściwość jest <xref:System.DateTimeKind.Unspecified> , jak pokazano w poniższym przykładzie.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Oznacza to, że wszelkie informacje o <xref:System.DateTimeOffset> relacji wartości z czasem UTC są tracone przez konwersję, gdy <xref:System.DateTimeOffset.DateTime%2A> Właściwość jest używana. Ma to wpływ na <xref:System.DateTimeOffset> wartości, które odpowiadają czas UTC lub na czas lokalny systemu, ponieważ <xref:System.DateTimeOffset.DateTime%2A> Struktura odzwierciedla tylko te dwie strefy czasowe w swojej <xref:System.DateTime.Kind%2A> właściwości.

Aby zachować możliwie jak najwięcej informacji o strefie czasowej podczas konwertowania <xref:System.DateTimeOffset> do <xref:System.DateTime> wartości, można użyć <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości i.

### <a name="converting-a-utc-time"></a>Konwertowanie czasu UTC

Aby wskazać, że przekonwertowana <xref:System.DateTimeOffset.DateTime%2A> wartość jest czasem UTC, można pobrać wartość <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości. Różni się od <xref:System.DateTimeOffset.DateTime%2A> właściwości na dwa sposoby:

- Zwraca wartość, <xref:System.DateTime> której <xref:System.DateTime.Kind%2A> Właściwość jest <xref:System.DateTimeKind.Utc> .

- Jeśli <xref:System.DateTimeOffset.Offset%2A> wartość właściwości nie jest równa <xref:System.TimeSpan.Zero?displayProperty=nameWithType> , konwertuje godzinę na czas UTC.

> [!NOTE]
> Jeśli aplikacja wymaga, aby skonwertowane <xref:System.DateTime> wartości jednoznacznie identyfikować pojedynczy punkt w czasie, należy rozważyć użycie <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości do obsługi wszystkich <xref:System.DateTimeOffset> <xref:System.DateTime> konwersji.

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości do konwersji <xref:System.DateTimeOffset> wartości, której przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> <xref:System.DateTime> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości do przeprowadzenia konwersji strefy czasowej i konwersji typu na <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Konwertowanie czasu lokalnego

Aby wskazać, że <xref:System.DateTimeOffset> wartość reprezentuje czas lokalny, można przekazać <xref:System.DateTime> wartość zwracaną przez <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> Właściwość do `static` `Shared` metody (w Visual Basic) <xref:System.DateTime.SpecifyKind%2A> . Metoda zwraca datę i godzinę przekazaną do niego jako pierwszy parametr, ale ustawia <xref:System.DateTime.Kind%2A> Właściwość na wartość określoną przez jego drugi parametr. Poniższy kod używa <xref:System.DateTime.SpecifyKind%2A> metody podczas konwertowania <xref:System.DateTimeOffset> wartości, której przesunięcie odnosi się do numeru lokalnej strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Można również użyć właściwości, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Aby przekonwertować <xref:System.DateTimeOffset> wartość na <xref:System.DateTime> wartość lokalną. <xref:System.DateTime.Kind%2A>Właściwość zwracanej <xref:System.DateTime> wartości to <xref:System.DateTimeKind.Local> . Poniższy kod używa <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości podczas konwertowania <xref:System.DateTimeOffset> wartości, której przesunięcie odnosi się do numeru lokalnej strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Po pobraniu <xref:System.DateTime> wartości przy użyciu <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości `get` metoda dostępu do właściwości najpierw KONWERTUJE <xref:System.DateTimeOffset> wartość na UTC, a następnie konwertuje ją na czas lokalny, wywołując <xref:System.DateTimeOffset.ToLocalTime%2A> metodę. Oznacza to, że można pobrać wartość z właściwości, <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> Aby wykonać konwersję strefy czasowej w tym samym czasie, w którym wykonywana jest konwersja typu. Oznacza to również, że reguły dostosowania lokalnej strefy czasowej są stosowane podczas konwersji. Poniższy kod ilustruje użycie <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości do wykonania konwersji typu i strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda konwersji ogólnego przeznaczenia

W poniższym przykładzie zdefiniowano metodę o nazwie `ConvertFromDateTimeOffset` , która konwertuje <xref:System.DateTimeOffset> wartości na <xref:System.DateTime> wartości. Na podstawie jego przesunięcia decyduje o tym, czy <xref:System.DateTimeOffset> wartość jest czasem UTC, czasem lokalnym czy innym, i odpowiednio definiuje Właściwość zwracanej daty i godziny <xref:System.DateTime.Kind%2A> .

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

W poniższym przykładzie wywoływana jest `ConvertFromDateTimeOffset` Metoda konwersji <xref:System.DateTimeOffset> wartości, które reprezentują czas UTC, czas lokalny i godzinę w strefie czasowej (Europa Środkowa w warstwie Standardowa).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Należy zauważyć, że ten kod tworzy dwa założenia, które w zależności od aplikacji i źródła wartości daty i godziny mogą nie zawsze być prawidłowe:

- Przyjęto założenie, że wartość daty i godziny, której przesunięcie jest <xref:System.TimeSpan.Zero?displayProperty=nameWithType> reprezentowane przez czas UTC. W rzeczywistości czas UTC nie jest czasem w określonej strefie czasowej, ale jest to czas, w którym czasy w strefach czasowych na świecie są znormalizowane. Strefy czasowe mogą również mieć przesunięcie <xref:System.TimeSpan.Zero> .

- Przyjęto założenie, że data i godzina, o której przesunięcie jest równe, dla lokalnej strefy czasowej reprezentuje lokalną strefę czasową. Ponieważ wartości daty i godziny są odłączone od oryginalnej strefy czasowej, może to nie być przypadek; Data i godzina mogą pochodzić z innej strefy czasowej z tym samym przesunięciem.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
