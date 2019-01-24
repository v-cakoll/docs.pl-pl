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
ms.openlocfilehash: d4bce84d26e8f498f065c887b583e18d8ea7c786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651204"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Konwertowanie pomiędzy DateTime i DateTimeOffset

Mimo że <xref:System.DateTimeOffset> struktura zapewnia wysoką świadomości strefy czasowej niż <xref:System.DateTime> struktury <xref:System.DateTime> parametry są najczęściej używane w wywołaniach metod. W związku z tym umożliwia przekonwertowanie <xref:System.DateTimeOffset> wartości <xref:System.DateTime> wartości i odwrotnie jest szczególnie ważne. W tym temacie przedstawiono sposób wykonywania tych konwersji w sposób, który zachowuje się jak najwięcej informacji o strefie czasowej, jak to możliwe.

> [!NOTE]
> Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> typy mają pewne ograniczenia, gdy reprezentujący razy w strefach czasowych. Za pomocą jego <xref:System.DateTime.Kind%2A> właściwości <xref:System.DateTime> jest w stanie w celu uwzględnienia tylko uniwersalnego czasu koordynowanego (UTC) i systemu w lokalnej strefie czasowej. <xref:System.DateTimeOffset> odzwierciedla czas przesunięcie względem czasu UTC, ale go nie odzwierciedlać rzeczywiste strefy czasowej, do którego, przesunięcie należy. Aby uzyskać szczegółowe informacje o wartości czasu i pomoc techniczna dla stref czasowych, zobacz [Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Konwersje z typu DateTime do klasy DateTimeOffset

<xref:System.DateTimeOffset> Struktura zapewnia dwa sposoby równoważne do wykonania <xref:System.DateTime> do <xref:System.DateTimeOffset> konwersji, które są odpowiednie dla większości konwersje:

* <xref:System.DateTimeOffset.%23ctor%2A> Konstruktora, który tworzy nową <xref:System.DateTimeOffset> na podstawie obiektu <xref:System.DateTime> wartość.

* Operator niejawnej konwersji, która umożliwia przypisywanie <xref:System.DateTime> wartość <xref:System.DateTimeOffset> obiektu.

Dla czasu UTC i lokalnych <xref:System.DateTime> wartości <xref:System.DateTimeOffset.Offset%2A> właściwość wynikowy <xref:System.DateTimeOffset> wartość dokładnie odzwierciedla przesunięcie strefy czasu UTC, czy czas lokalny. Na przykład, poniższy kod Konwertuje czas UTC na odpowiadającą jej <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

W tym przypadku przesunięcie `utcTime2` zmiennej to 00:00. Podobnie, następującego kodu Konwertuje czas lokalny na odpowiadającą jej <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Jednak w przypadku <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, utworzyć te metody konwersji dwóch <xref:System.DateTimeOffset> wartość, której przesunięcie jest lokalnej strefy czasowej. Jest to pokazane w poniższym przykładzie, który jest uruchamiany w Stanach Zjednoczonych Pacyficznego standardowa strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Jeśli <xref:System.DateTime> wartość odzwierciedla datę i godzinę w innych jednostkach niż lokalnej strefy czasowej lub czasu UTC, możesz przekonwertować go na <xref:System.DateTimeOffset> wartości i zachowanie informacji o strefie czasowej przez wywołanie metody przeciążonej <xref:System.DateTimeOffset.%23ctor%2A> konstruktora. Na przykład, poniższy przykład tworzy wystąpienie <xref:System.DateTimeOffset> obiekt, który odzwierciedla Środkowa (czas standardowy).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Drugi parametr tego przeciążenia konstruktora <xref:System.TimeSpan> obiekt, który reprezentuje przesunięcie czasu względem czasu UTC, powinien być pobierany przez wywołanie <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metody odpowiedniej strefy czasowej czasu. Pojedynczy parametr metody jest <xref:System.DateTime> wartość, która reprezentuje datę i godzinę, które ma zostać przekonwertowany. Jeśli strefa czasowa obsługuje czasu letniego, ten parametr umożliwia metody określić przesunięcie odpowiednie dla tej określonej daty i godziny.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Konwersje z DateTimeOffset do daty/godziny

<xref:System.DateTimeOffset.DateTime%2A> Jest najczęściej używana do wykonywania <xref:System.DateTimeOffset> do <xref:System.DateTime> konwersji. Zwraca jednak <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Unspecified>, tak jak pokazano w poniższym przykładzie.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Oznacza to, że wszystkie informacje o <xref:System.DateTimeOffset> relacji tej wartości na czas UTC jest utracone podczas konwersji po <xref:System.DateTimeOffset.DateTime%2A> właściwość jest używana. Ma to wpływ na <xref:System.DateTimeOffset> wartości, które odpowiadają czasu UTC lub czasu lokalnego systemu, ponieważ <xref:System.DateTimeOffset.DateTime%2A> struktury odzwierciedla tylko tych dwóch stref czasowych w jego <xref:System.DateTime.Kind%2A> właściwości.

Aby zachować jak najwięcej informacji o strefie czasowej, jak to możliwe, podczas konwertowania <xref:System.DateTimeOffset> do <xref:System.DateTime> wartości, można użyć <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości.

### <a name="converting-a-utc-time"></a>Konwertowanie na czas UTC

Aby wskazać, że przekonwertowanego <xref:System.DateTimeOffset.DateTime%2A> wartość czasu UTC, możesz pobrać wartość <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości. Różni się od <xref:System.DateTimeOffset.DateTime%2A> właściwości na dwa sposoby:

* Zwraca <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Utc>.

* Jeśli <xref:System.DateTimeOffset.Offset%2A> nie jest równa wartości właściwości <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, Konwertuje czas UTC.

> [!NOTE]
> Jeśli aplikacja wymaga, aby przekonwertować <xref:System.DateTime> jednoznacznie identyfikuje pojedynczy punkt w czasie, należy rozważyć użycie <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości, aby zapewnić obsługę wszystkich <xref:System.DateTimeOffset> do <xref:System.DateTime> konwersji.

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości, aby przekonwertować <xref:System.DateTimeOffset> wartość jest równa którego przesunięcie <xref:System.TimeSpan.Zero?displayProperty=nameWithType> do <xref:System.DateTime> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwość do przeprowadzania konwersji strefy czasowej i konwersji typów <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Konwertowanie na czas lokalny

Aby wskazać, że <xref:System.DateTimeOffset> wartość odpowiada czasowi lokalnemu, możesz przekazywać <xref:System.DateTime> wartość zwrócona przez obiekt <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> właściwości `static` (`Shared` w języku Visual Basic) <xref:System.DateTime.SpecifyKind%2A> metody. Metoda zwraca datę i godzinę, o których przekazanego do niej jako pierwszego parametru, ale ustawia <xref:System.DateTime.Kind%2A> właściwości na wartość określoną przez jej drugi parametr. Poniższy kod używa <xref:System.DateTime.SpecifyKind%2A> metody podczas konwertowania <xref:System.DateTimeOffset> wartość, której przesunięcie odnosi się do tego dla lokalnej strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Można również użyć <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości, aby przekonwertować <xref:System.DateTimeOffset> wartości do lokalnego <xref:System.DateTime> wartość. <xref:System.DateTime.Kind%2A> Właściwości zwracanego <xref:System.DateTime> wartość <xref:System.DateTimeKind.Local>. Poniższy kod używa <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości podczas konwertowania <xref:System.DateTimeOffset> wartość, której przesunięcie odnosi się do tego dla lokalnej strefy czasowej. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Po pobraniu <xref:System.DateTime> wartość przy użyciu <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwość, właściwości `get` najpierw konwertuje metody dostępu <xref:System.DateTimeOffset> wartość względem czasu UTC, następnie konwertuje ją na czas lokalny, wywołując <xref:System.DateTimeOffset.ToLocalTime%2A> metody. Oznacza to, że można pobrać wartość z zakresu od <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości w celu wykonania konwersji strefy czasowej, w tym samym czasie, aby przeprowadzić konwersję typu. Oznacza to również, że reguły korekty strefy czasu lokalnego są stosowane w konwersji. Poniższy kod ilustruje sposób korzystania z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości typu i konwersji strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda konwersji ogólnego przeznaczenia

W poniższym przykładzie zdefiniowano metodę o nazwie `ConvertFromDateTimeOffset` konwertująca <xref:System.DateTimeOffset> wartości <xref:System.DateTime> wartości. Oparte na przesunięcie, określa, czy <xref:System.DateTimeOffset> wartość czasu UTC, czasem lokalnym lub innym razem i definiuje zwrócona wartość daty i godziny w <xref:System.DateTime.Kind%2A> właściwość odpowiednio.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Postępuj zgodnie z przykład wywołuje `ConvertFromDateTimeOffset` metodę, aby przekonwertować <xref:System.DateTimeOffset> wartości, które reprezentują czas UTC, czas lokalny i czas, w Stanach Zjednoczonych Strefa Środkowa (czas standardowy).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Należy zwrócić uwagę na to, że ten kod sprawia, że dwa założenia, które w zależności od aplikacji i źródłem jego wartości daty i godziny zawsze jest nieprawidłowy:

* Przyjęto założenie, że data i godzina wartość, której przesunięcie <xref:System.TimeSpan.Zero?displayProperty=nameWithType> reprezentuje UTC. W rzeczywistości UTC jest czas w określonej strefie czasowej, ale czas, w odniesieniu do której są standaryzowane razy w strefach czasowych na świecie. Strefy czasowe mogą też istnieć przesunięcie <xref:System.TimeSpan.Zero>.

* Przyjęto założenie, że data i godzina, którego przesunięcie equals w przypadku lokalnej strefy czasowej reprezentuje lokalnej strefy czasowej. Ponieważ wartości daty i godziny są oddzielone od oryginalnej strefy czasowej, to może nie być wielkości liter; daty i godziny mogą pochodzić w innej strefie czasowej z tego samego przesunięcie.

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
