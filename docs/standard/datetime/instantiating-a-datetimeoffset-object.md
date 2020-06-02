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
ms.openlocfilehash: c290af0c9cef619000a6620ba35209489856c5b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281599"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Tworzenie wystąpień obiektów DateTimeOffset

<xref:System.DateTimeOffset>Struktura oferuje wiele metod tworzenia nowych <xref:System.DateTimeOffset> wartości. Wiele z nich odnosi się bezpośrednio do metod dostępnych do tworzenia wystąpień nowych <xref:System.DateTime> wartości, z rozszerzeniami, które umożliwiają określenie wartości daty i godziny przesunięcia od skoordynowanego czasu uniwersalnego (UTC). W szczególności można utworzyć wystąpienie <xref:System.DateTimeOffset> wartości w następujący sposób:

- Przy użyciu literału daty i godziny.

- Wywołując <xref:System.DateTimeOffset> Konstruktor.

- Przez niejawne przekonwertowanie wartości na <xref:System.DateTimeOffset> wartość.

- Przez analizowanie ciągu reprezentującego datę i godzinę.

Ten temat zawiera bardziej szczegółowe informacje i przykłady kodu, które ilustrują te metody tworzenia wystąpienia nowych <xref:System.DateTimeOffset> wartości.

## <a name="date-and-time-literals"></a>Literały daty i godziny

W przypadku języków, które go obsługują, jednym z najczęstszych metod tworzenia wystąpienia <xref:System.DateTime> wartości jest podanie daty i godziny jako zakodowanej wartości literału. Na przykład poniższy kod Visual Basic tworzy <xref:System.DateTime> obiekt, którego wartość to 1 stycznia 2008, o 10:00 am.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>wartości można także inicjować przy użyciu literałów daty i godziny w przypadku używania języków, które obsługują <xref:System.DateTime> literały. Na przykład poniższy kod Visual Basic tworzy <xref:System.DateTimeOffset> obiekt.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak pokazuje dane wyjściowe konsoli, <xref:System.DateTimeOffset> wartość utworzona w ten sposób przypisuje przesunięcie lokalnej strefy czasowej. Oznacza to, że <xref:System.DateTimeOffset> wartość przypisana przy użyciu literału znakowego nie identyfikuje pojedynczego punktu czasu, jeśli kod jest uruchamiany na różnych komputerach.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset>Typ definiuje sześć konstruktorów. Cztery z nich odpowiadają bezpośrednio <xref:System.DateTime> konstruktorom, z dodatkowym parametrem typu <xref:System.TimeSpan> , który definiuje datę i godzinę przesunięcia od czasu UTC. Umożliwiają one Definiowanie <xref:System.DateTimeOffset> wartości na podstawie wartości poszczególnych składników daty i godziny. Na przykład poniższy kod używa tych czterech konstruktorów do tworzenia wystąpień <xref:System.DateTimeOffset> obiektów z identycznymi wartościami 7/1/2008 12:05 am + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Należy zauważyć, że gdy wartość <xref:System.DateTimeOffset> obiektu skonkretyzowanygo przy użyciu <xref:System.Globalization.PersianCalendar> obiektu, jako jeden z argumentów konstruktora, zostanie wyświetlona w konsoli, jest wyrażona jako data w kalendarzu gregoriańskim, a nie w przypadku kalendarza perski. Aby wyprowadzić datę przy użyciu kalendarza perski, zapoznaj się z przykładem w <xref:System.Globalization.PersianCalendar> temacie.

Pozostałe dwa konstruktory tworzą <xref:System.DateTimeOffset> obiekt z <xref:System.DateTime> wartości. Pierwszy z nich ma jeden parametr, <xref:System.DateTime> wartość do przekonwertowania na <xref:System.DateTimeOffset> wartość. Przesunięcie wartości otrzymanej <xref:System.DateTimeOffset> zależy od <xref:System.DateTime.Kind%2A> właściwości pojedynczego parametru konstruktora. Jeśli wartość jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . W przeciwnym razie jego przesunięcie jest równe wartości dla lokalnej strefy czasowej. Poniższy przykład ilustruje użycie tego konstruktora do tworzenia wystąpienia <xref:System.DateTimeOffset> obiektów reprezentujących czas UTC i lokalną strefę czasową:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Wywołanie przeciążenia <xref:System.DateTimeOffset> konstruktora, który ma jeden <xref:System.DateTime> parametr, jest równoznaczne z przeprowadzeniem niejawnej konwersji <xref:System.DateTime> wartości na <xref:System.DateTimeOffset> wartość.

Drugi Konstruktor, który tworzy <xref:System.DateTimeOffset> obiekt z wartości, <xref:System.DateTime> ma dwa parametry: <xref:System.DateTime> wartość do przekonwertowania i <xref:System.TimeSpan> wartość reprezentującą przesunięcie daty i godziny od czasu UTC. Ta wartość przesunięcia musi odpowiadać <xref:System.DateTime.Kind%2A> Właściwości pierwszego parametru konstruktora lub <xref:System.ArgumentException> jest generowany. Jeśli <xref:System.DateTime.Kind%2A> Właściwość pierwszego parametru jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , wartość drugiego parametru musi być <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Jeśli <xref:System.DateTime.Kind%2A> Właściwość pierwszego parametru to <xref:System.DateTimeKind.Local?displayProperty=nameWithType> , wartość drugiego parametru musi być przesunięciem strefy czasowej systemu lokalnego. Jeśli <xref:System.DateTime.Kind%2A> Właściwość pierwszego parametru jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , przesunięcie może być dowolną prawidłową wartością. Poniższy kod ilustruje wywołania tego konstruktora do konwersji <xref:System.DateTime> na <xref:System.DateTimeOffset> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Niejawna konwersja typu

<xref:System.DateTimeOffset>Typ obsługuje jedną niejawną konwersję typu: od <xref:System.DateTime> wartości do <xref:System.DateTimeOffset> wartości. (Niejawna konwersja typu jest konwersją z jednego typu na inny, który nie wymaga jawnego rzutowania (w języku C#) ani konwersji (w Visual Basic) i nie utraci informacji. Sprawia, że kod może być podobny do poniższego.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Przesunięcie wartości otrzymanej <xref:System.DateTimeOffset> zależy od <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości właściwości. Jeśli wartość jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Jeśli wartość jest albo <xref:System.DateTimeKind.Local?displayProperty=nameWithType> lub <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , przesunięcie jest ustawione jako równe wartości dla lokalnej strefy czasowej.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analizowanie ciągu reprezentującego datę i godzinę

<xref:System.DateTimeOffset>Typ obsługuje cztery metody, które umożliwiają konwersję ciągu reprezentującego datę i godzinę do <xref:System.DateTimeOffset> wartości:

- <xref:System.DateTimeOffset.Parse%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę na <xref:System.DateTimeOffset> wartość i zgłasza wyjątek, jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.TryParse%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę na <xref:System.DateTimeOffset> wartość i zwraca, `false` Jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.ParseExact%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie na <xref:System.DateTimeOffset> wartość. Metoda zgłasza wyjątek, jeśli konwersja nie powiedzie się.

- <xref:System.DateTimeOffset.TryParseExact%2A>, która próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie na <xref:System.DateTimeOffset> wartość. Metoda zwraca `false` , jeśli konwersja nie powiedzie się.

Poniższy przykład ilustruje wywołania każdej z tych czterech metod konwersji ciągów w celu utworzenia wystąpienia <xref:System.DateTimeOffset> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Zobacz także

- [Daty, godziny i strefy czasowe](index.md)
