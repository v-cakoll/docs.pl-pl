---
title: Tworzenie wystąpień obiektów DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
ms.openlocfilehash: 1b1178623258393eab28a7087eb04c47b55a9176
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122310"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Tworzenie wystąpień obiektów DateTimeOffset

Struktura <xref:System.DateTimeOffset> oferuje kilka sposobów tworzenia nowych wartości <xref:System.DateTimeOffset>. Wiele z nich odnosi się bezpośrednio do metod dostępnych dla tworzenia wystąpienia nowych wartości <xref:System.DateTime>, z rozszerzeniami, które umożliwiają określenie wartości daty i godziny przesunięcia od skoordynowanego czasu uniwersalnego (UTC). W szczególności można utworzyć wystąpienie <xref:System.DateTimeOffset> wartości w następujący sposób:

- Przy użyciu literału daty i godziny.

- Wywołując Konstruktor <xref:System.DateTimeOffset>.

- Przez niejawne przekonwertowanie wartości na wartość <xref:System.DateTimeOffset>.

- Przez analizowanie ciągu reprezentującego datę i godzinę.

Ten temat zawiera bardziej szczegółowe informacje i przykłady kodu, które ilustrują te metody tworzenia wystąpienia nowych wartości <xref:System.DateTimeOffset>.

## <a name="date-and-time-literals"></a>Literały daty i godziny

W przypadku języków, które go obsługują, jednym z najczęstszych metod tworzenia wystąpienia <xref:System.DateTime> jest podanie daty i godziny jako wartości literału, który jest zakodowany. Na przykład poniższy kod Visual Basic tworzy obiekt <xref:System.DateTime>, którego wartość to 1 stycznia 2008, o 10:00 AM.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

wartości <xref:System.DateTimeOffset> można również inicjować przy użyciu literałów daty i godziny w przypadku używania języków, które obsługują <xref:System.DateTime> literały. Na przykład poniższy kod Visual Basic tworzy obiekt <xref:System.DateTimeOffset>.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak pokazuje dane wyjściowe konsoli, wartość <xref:System.DateTimeOffset> utworzona w ten sposób przypisuje przesunięcie lokalnej strefy czasowej. Oznacza to, że wartość <xref:System.DateTimeOffset> przypisywana przy użyciu literału znakowego nie identyfikuje pojedynczego punktu czasu, jeśli kod jest uruchamiany na różnych komputerach.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

Typ <xref:System.DateTimeOffset> definiuje sześć konstruktorów. Cztery z nich odnoszą się bezpośrednio do konstruktorów <xref:System.DateTime>, z dodatkowym parametrem typu <xref:System.TimeSpan>, który definiuje przesunięcie daty i godziny od czasu UTC. Umożliwiają one zdefiniowanie wartości <xref:System.DateTimeOffset> na podstawie wartości poszczególnych składników daty i godziny. Na przykład poniższy kod używa tych czterech konstruktorów do tworzenia wystąpień <xref:System.DateTimeOffset> obiektów z identycznymi wartościami 7/1/2008 12:05 AM + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Należy zauważyć, że gdy wartość <xref:System.DateTimeOffset> obiektu utworzonego przy użyciu obiektu <xref:System.Globalization.PersianCalendar> jako jeden z argumentów konstruktora jest wyświetlany w konsoli, zostanie ona wyrażona jako data w kalendarzu gregoriańskim, a nie w obszarze kalendarza perski. Aby wyprowadzić datę przy użyciu kalendarza perski, zapoznaj się z przykładem w temacie <xref:System.Globalization.PersianCalendar>.

Pozostałe dwa konstruktory tworzą obiekt <xref:System.DateTimeOffset> z wartości <xref:System.DateTime>. Pierwszy z nich ma jeden parametr, <xref:System.DateTime> wartość do przekonwertowania na wartość <xref:System.DateTimeOffset>. Przesunięcie obliczonej wartości <xref:System.DateTimeOffset> zależy od właściwości <xref:System.DateTime.Kind%2A> jednego parametru konstruktora. Jeśli wartość jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. W przeciwnym razie jego przesunięcie jest równe wartości dla lokalnej strefy czasowej. Poniższy przykład ilustruje użycie tego konstruktora do tworzenia wystąpień <xref:System.DateTimeOffset> obiektów reprezentujących czas UTC i lokalną strefę czasową:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Wywołanie przeciążenia konstruktora <xref:System.DateTimeOffset>, który ma jeden parametr <xref:System.DateTime> jest równoznaczne z przeprowadzeniem niejawnej konwersji wartości <xref:System.DateTime> do wartości <xref:System.DateTimeOffset>.

Drugi Konstruktor, który tworzy obiekt <xref:System.DateTimeOffset> z wartości <xref:System.DateTime> ma dwa parametry: wartość <xref:System.DateTime> do przekonwertowania i wartość <xref:System.TimeSpan> reprezentującą przesunięcie daty i godziny z czasu UTC. Ta wartość przesunięcia musi odpowiadać właściwości <xref:System.DateTime.Kind%2A> pierwszego parametru konstruktora lub zostanie wygenerowany <xref:System.ArgumentException>. Jeśli właściwość <xref:System.DateTime.Kind%2A> pierwszego parametru jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, wartość drugiego parametru musi być <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli właściwość <xref:System.DateTime.Kind%2A> pierwszego parametru jest <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, wartość drugiego parametru musi być przesunięciem strefy czasowej systemu lokalnego. Jeśli właściwość <xref:System.DateTime.Kind%2A> pierwszego parametru jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, przesunięcie może być dowolną prawidłową wartością. Poniższy kod ilustruje wywołania tego konstruktora w celu przekonwertowania <xref:System.DateTime> na wartości <xref:System.DateTimeOffset>.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Niejawna konwersja typu

Typ <xref:System.DateTimeOffset> obsługuje jedną niejawną konwersję typu: od wartości <xref:System.DateTime> do wartości <xref:System.DateTimeOffset>. (Niejawna konwersja typu jest konwersją z jednego typu na inny, który nie wymaga jawnego rzutowania C#(in) ani konwersji (w Visual Basic) i nie utraci informacji. Sprawia, że kod może być podobny do poniższego.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Przesunięcie obliczonej wartości <xref:System.DateTimeOffset> zależy od wartości właściwości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType>. Jeśli wartość jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli wartość jest równa <xref:System.DateTimeKind.Local?displayProperty=nameWithType> lub <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, przesunięcie jest ustawione tak samo, jak w przypadku lokalnej strefy czasowej.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analizowanie ciągu reprezentującego datę i godzinę

Typ <xref:System.DateTimeOffset> obsługuje cztery metody, które umożliwiają konwersję ciągu reprezentującego datę i godzinę do wartości <xref:System.DateTimeOffset>:

- <xref:System.DateTimeOffset.Parse%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę na wartość <xref:System.DateTimeOffset> i zgłasza wyjątek, jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.TryParse%2A>, która próbuje skonwertować ciąg reprezentujący datę i godzinę do wartości <xref:System.DateTimeOffset> i zwraca `false`, jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.ParseExact%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie na wartość <xref:System.DateTimeOffset>. Metoda zgłasza wyjątek, jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.TryParseExact%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie na wartość <xref:System.DateTimeOffset>. Metoda zwraca `false`, jeśli konwersja nie powiedzie się.

Poniższy przykład ilustruje wywołania każdej z tych czterech metod konwersji ciągów, aby utworzyć wystąpienie <xref:System.DateTimeOffset> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
