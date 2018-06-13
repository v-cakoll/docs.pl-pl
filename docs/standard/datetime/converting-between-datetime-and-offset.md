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
ms.openlocfilehash: dec0e5138ecf08783f11d21cd28d7291d27ea68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578251"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Konwertowanie pomiędzy DateTime i DateTimeOffset

Mimo że <xref:System.DateTimeOffset> struktura zapewnia wysoką świadomości strefy czasowej niż <xref:System.DateTime> struktury <xref:System.DateTime> parametry są najczęściej używane w wywołaniach metody. W związku z tym umożliwia przekonwertowanie <xref:System.DateTimeOffset> wartości do <xref:System.DateTime> wartości i na odwrót jest szczególnie ważne. W tym temacie przedstawiono sposób wykonywania tych konwersji w taki sposób, który zachowuje się jak najwięcej informacji o strefie czasowej, jak to możliwe.

> [!NOTE]
> Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> typy mają następujące ograniczenia, gdy reprezentujący razy w strefach czasowych. Z jego <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTime> jest w stanie uwzględnić tylko uniwersalny czas koordynowany (UTC) oraz system w lokalnej strefie czasowej. <xref:System.DateTimeOffset> odzwierciedla przesunięcie raz od czasu UTC, ale nie uwzględnia się, że należy rzeczywiste strefy czasowej, do którego który przesunięcie. Aby uzyskać więcej informacji o wartości czasu i pomocy technicznej dla stref czasowych, zobacz [wybór pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Konwersje z daty/godziny na DateTimeOffset

<xref:System.DateTimeOffset> Struktury udostępnia dwa sposoby równoważne przeprowadzić <xref:System.DateTime> do <xref:System.DateTimeOffset> konwersji, które są odpowiednie dla większości konwersji:

* <xref:System.DateTimeOffset.%23ctor%2A> Konstruktora, który tworzy nowy <xref:System.DateTimeOffset> na podstawie obiektu <xref:System.DateTime> wartość.

* Operator niejawnej konwersji, dzięki czemu można przypisać <xref:System.DateTime> do wartości <xref:System.DateTimeOffset> obiektu.

Dla czasu UTC i lokalnych <xref:System.DateTime> wartości, <xref:System.DateTimeOffset.Offset%2A> właściwość powstałe w ten sposób <xref:System.DateTimeOffset> wartość dokładnie odzwierciedla przesunięcia strefy UTC lub czasu lokalnego. Na przykład następujący kod konwertuje godzinę UTC na jej odpowiednik <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

W tym przypadku przesunięcie `utcTime2` zmiennej to 00:00. Podobnie poniższy kod konwertuje czasu lokalnego na jej odpowiednik <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Niemniej jednak w przypadku <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, utworzyć te metody konwersji dwóch <xref:System.DateTimeOffset> wartość, której przesunięcie jest w lokalnej strefie czasowej. Przedstawiono to w poniższym przykładzie, który jest uruchamiany w Stanach Zjednoczonych Pacyficzny standardowa strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Jeśli <xref:System.DateTime> odzwierciedla wartość daty i godziny w coś innego niż lokalnej strefie czasowej lub UTC, możesz przejść do <xref:System.DateTimeOffset> wartości i zachować informacje o strefie czasowej przez wywołanie metody przeciążonej <xref:System.DateTimeOffset.%23ctor%2A> konstruktora. Na przykład poniższy przykład tworzy <xref:System.DateTimeOffset> obiektów, które odzwierciedla Środkowa (czas standardowy).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Drugi parametr tego przeciążenia konstruktora <xref:System.TimeSpan> obiekt, który reprezentuje przesunięcie czasu UTC, powinny zostać pobrane przez wywołanie metody <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> metody odpowiedniej strefy czasowej czasu. Pojedynczy parametr metody jest <xref:System.DateTime> wartość, która reprezentuje datę i godzinę, który ma zostać przekonwertowany. Jeśli strefa czasowa obsługuje czasu letniego, ten parametr umożliwia metody przesunięcie odpowiednich dla określonej daty i godziny.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Konwersje z DateTimeOffset DateTime

<xref:System.DateTimeOffset.DateTime%2A> Jest najczęściej używana do wykonywania <xref:System.DateTimeOffset> do <xref:System.DateTime> konwersji. Jednak zwraca <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość jest <xref:System.DateTimeKind.Unspecified>, jak pokazano w poniższym przykładzie.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Oznacza to, że wszystkie informacje o <xref:System.DateTimeOffset> relacji tej wartości na czas UTC zostaną utracone w procesie konwersji po <xref:System.DateTimeOffset.DateTime%2A> właściwość jest używana. Ma to wpływ na <xref:System.DateTimeOffset> wartości, które odpowiadają czasu UTC lub czasu lokalnego systemu, ponieważ <xref:System.DateTimeOffset.DateTime%2A> struktury odzwierciedla tylko tych dwóch stref czasowych w jego <xref:System.DateTime.Kind%2A> właściwości.

Aby zachować jak najwięcej informacji o strefie czasowej, jak to możliwe, podczas konwertowania <xref:System.DateTimeOffset> do <xref:System.DateTime> wartości, można użyć <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> i <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości.

### <a name="converting-a-utc-time"></a>Konwertowanie czas UTC

Aby wskazać, że przekonwertowanego <xref:System.DateTimeOffset.DateTime%2A> wartość to godzina (UTC), można pobrać wartość <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości. Różni się od <xref:System.DateTimeOffset.DateTime%2A> właściwości na dwa sposoby:

* Zwraca <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> jest właściwość <xref:System.DateTimeKind.Utc>.

* Jeśli <xref:System.DateTimeOffset.Offset%2A> nie jest równa wartości właściwości <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, Konwertuje czas UTC.

> [!NOTE]
> Jeśli aplikacja wymaga, aby przekonwertować <xref:System.DateTime> wartości jednoznacznie zidentyfikować pojedynczy punkt w czasie, należy rozważyć użycie <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> właściwości, aby zapewnić obsługę wszystkich <xref:System.DateTimeOffset> do <xref:System.DateTime> konwersji.

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości można przekonwertować <xref:System.DateTimeOffset> wartości, których przesunięcie równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> do <xref:System.DateTime> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Poniższy kod używa <xref:System.DateTimeOffset.UtcDateTime%2A> właściwości do realizacji konwersji strefy czasowej i konwersji typu na <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Konwertowanie czasu lokalnego

Aby wskazać, że <xref:System.DateTimeOffset> wartość odpowiada czasowi lokalnemu, można przekazać <xref:System.DateTime> wartość zwrócona przez <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> właściwości `static` (`Shared` w języku Visual Basic) <xref:System.DateTime.SpecifyKind%2A> metody. Metoda zwraca wartość daty i godziny przekazywane do niego jako pierwszy parametr, ale ustawia <xref:System.DateTime.Kind%2A> właściwości na wartość określoną przez jego drugi parametr. Poniższy kod używa <xref:System.DateTime.SpecifyKind%2A> metody podczas konwertowania <xref:System.DateTimeOffset> wartość, której przesunięcie odpowiada, który w lokalnej strefie czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Można również użyć <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości można przekonwertować <xref:System.DateTimeOffset> wartości do lokalnej <xref:System.DateTime> wartość. <xref:System.DateTime.Kind%2A> Właściwości zwracana <xref:System.DateTime> wartość jest <xref:System.DateTimeKind.Local>. Poniższy kod używa <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości podczas konwertowania <xref:System.DateTimeOffset> wartość, której przesunięcie odpowiada, który w lokalnej strefie czasowej. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Po pobraniu <xref:System.DateTime> wartości przy użyciu <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości, właściwości `get` akcesor najpierw konwertuje <xref:System.DateTimeOffset> wartość na czas UTC, następnie konwertuje go na czas lokalny przez wywołanie metody <xref:System.DateTimeOffset.ToLocalTime%2A> — metoda. Oznacza to, że można pobrać wartości z <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości, aby dokonać konwersji strefy czasowej w tym samym czasie, aby dokonać konwersji typu. Oznacza to również, że strefy czasu lokalnego korekty reguły są stosowane w wykonywaniu konwersji. Poniższy kod przedstawia użycie <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> właściwości do realizacji typu i konwersji strefy czasowej.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Metoda konwersji ogólnego przeznaczenia

W poniższym przykładzie zdefiniowano metodę o nazwie `ConvertFromDateTimeOffset` konwertująca <xref:System.DateTimeOffset> wartości do <xref:System.DateTime> wartości. W oparciu o jego przesunięcie, określa czy <xref:System.DateTimeOffset> wartość czasu UTC, czas lokalny lub innym razem i definiuje zwrócona wartość daty i godziny w <xref:System.DateTime.Kind%2A> właściwości odpowiednio.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

Wykonaj przykładzie wywołuje `ConvertFromDateTimeOffset` metodę, aby przekonwertować <xref:System.DateTimeOffset> wartości, które reprezentują czas UTC, czasu lokalnego, a czas w Stanach Zjednoczonych Strefa Środkowa (czas standardowy).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Należy pamiętać, że ten kod sprawia, że dwa założenia, które w zależności od aplikacji i źródłem jego wartości daty i godziny nie zawsze jest nieprawidłowy:

* Przyjęto założenie, że data i godzina wartość, której przesunięcie <xref:System.TimeSpan.Zero?displayProperty=nameWithType> reprezentuje czas UTC. W rzeczywistości UTC nie jest czas, w szczególności strefę czasową, ale czas, w odniesieniu do której są standaryzowane razy w strefach czasowych na świecie. Strefy czasowe można również mają przesunięcie równe <xref:System.TimeSpan.Zero>.

* Przyjęto założenie, że data i czas, w których przesunięcie equals, który w lokalnej strefie czasowej reprezentuje w lokalnej strefie czasowej. Ponieważ wartości daty i godziny są oddzielone od oryginalnej strefy czasowej, nie może to być sprawa; Data i godzina można muszą pochodzić z innej strefy czasowej z tym samym przesunięcie.

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
