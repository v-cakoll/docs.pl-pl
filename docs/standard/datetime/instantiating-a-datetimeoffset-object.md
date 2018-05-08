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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48ea87bb5eb1e302ae6a1169c22ea30bd4bc7ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="instantiating-a-datetimeoffset-object"></a>Tworzenie wystąpień obiektów DateTimeOffset

<xref:System.DateTimeOffset> Struktury oferuje wiele sposobów, aby utworzyć nowy <xref:System.DateTimeOffset> wartości. Wiele z nich odpowiada bezpośrednio do metody dostępne dla nowego wystąpienia <xref:System.DateTime> wartości ulepszeń, dzięki którym można określić wartość daty i godziny przesunięcie z uniwersalnego czasu koordynowanego (UTC). W szczególności, można utworzyć wystąpienia <xref:System.DateTimeOffset> wartość w następujący sposób:

* Za pomocą datę i godzinę literału.

* Wywołując <xref:System.DateTimeOffset> konstruktora.

* Przez niejawnie konwertowania wartości na <xref:System.DateTimeOffset> wartość.

* Analizując reprezentację ciągu daty i godziny.

Ten temat zawiera większy szczegółów i kod przykłady ilustrujące te metody tworzenia nowego wystąpienia <xref:System.DateTimeOffset> wartości.

## <a name="date-and-time-literals"></a>Literały daty i godziny

Dla języków, które obsługują, jednym z najbardziej typowych sposobów wystąpienia <xref:System.DateTime> wartość ma na celu dostarczenie datę i godzinę jako ustalony wartość literału. Na przykład następujący kod Visual Basic tworzy <xref:System.DateTime> obiektu, którego wartość wynosi 1 stycznia 2008 o 10:00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> wartości można również zainicjować przy użyciu literały daty i godziny, korzystając z języków, które obsługują <xref:System.DateTime> literały. Na przykład następujący kod Visual Basic tworzy <xref:System.DateTimeOffset> obiektu.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak pokazano na dane wyjściowe konsoli, <xref:System.DateTimeOffset> wartość utworzone w ten sposób jest przypisywana przesunięcie w lokalnej strefie czasowej. Oznacza to, że <xref:System.DateTimeOffset> wartość przypisane przy użyciu literał znakowy nie identyfikuje pojedynczy punkt czasu, jeśli kod jest uruchamiany na różnych komputerach.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset> Typ definiuje sześciu konstruktorów. Cztery z nich odpowiada bezpośrednio do <xref:System.DateTime> konstruktorów z dodatkowy parametr typu <xref:System.TimeSpan> definiuje daty i czasu przesunięcie od czasu UTC. Te umożliwiają definiowanie <xref:System.DateTimeOffset> wartość na podstawie wartości daty i czasu składników. Na przykład w poniższym kodzie użyto do utworzenia wystąpienia te cztery konstruktorów <xref:System.DateTimeOffset> obiektów z identycznymi wartościami 2008-7-1 00:05:00 +01: 00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Należy zauważyć, że gdy wartość <xref:System.DateTimeOffset> wdrożyć przy użyciu obiektu <xref:System.Globalization.PersianCalendar> obiekt jako jeden z argumentów dla jego konstruktora jest wyświetlany w konsoli, jest wyrażona jako data gregoriańska zamiast perska kalendarza. Do wyjściowego datę przy użyciu perska kalendarza, zapoznaj się z przykładem w <xref:System.Globalization.PersianCalendar> tematu.

Utwórz dwa konstruktory <xref:System.DateTimeOffset> obiekt z <xref:System.DateTime> wartości. Pierwszy z nich ma jeden parametr <xref:System.DateTime> wartość do przekonwertowania na <xref:System.DateTimeOffset> wartość. Przesunięcie powstałe w ten sposób <xref:System.DateTimeOffset> wartość zależy od <xref:System.DateTime.Kind%2A> właściwości konstruktora jeden parametr. Jeśli jego wartość wynosi <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. W przeciwnym razie jego przesunięcie ma wartość równą w lokalnej strefie czasowej. Poniższy przykład przedstawia użycie tego konstruktora do utworzenia wystąpienia <xref:System.DateTimeOffset> obiekty reprezentujące UTC i w lokalnej strefie czasowej:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Wywoływanie przeciążenia <xref:System.DateTimeOffset> konstruktora, który ma jeden <xref:System.DateTime> parametru jest odpowiednikiem wykonywania niejawnej konwersji wartości <xref:System.DateTime> do wartości <xref:System.DateTimeOffset> wartość.

Drugi Konstruktor, który tworzy <xref:System.DateTimeOffset> obiekt z <xref:System.DateTime> wartość ma dwa parametry: <xref:System.DateTime> wartości do konwersji, a <xref:System.TimeSpan> przesunięcie wartości reprezentujący datę i godzinę w formacie UTC. Ta wartość przesunięcia musi odpowiadać <xref:System.DateTime.Kind%2A> właściwości pierwszy parametr konstruktora lub <xref:System.ArgumentException> jest generowany. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszym parametrem jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, wartość drugiego parametru musi być <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszym parametrem jest <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, wartość drugiego parametru musi być przesunięcie strefy czasowej systemu lokalnego. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszym parametrem jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, Przesunięcie może mieć dowolną prawidłową wartość. Poniższy kod ilustruje wywołania do tego konstruktora do przekonwertowania <xref:System.DateTime> do <xref:System.DateTimeOffset> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Niejawna konwersja typu

<xref:System.DateTimeOffset> Typu obsługuje jeden niejawna konwersja typu: z <xref:System.DateTime> do wartości <xref:System.DateTimeOffset> wartość. (Niejawna konwersja typu jest konwersji z jednego typu do innego, która nie wymaga jawnego rzutowania (w języku C#) lub konwersji (w języku Visual Basic), a nie traci informacji. Powoduje to dodanie kodu, takie jak następujące możliwości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Przesunięcie powstałe w ten sposób <xref:System.DateTimeOffset> zależy od wartości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości właściwości. Jeśli jego wartość wynosi <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli wartość <xref:System.DateTimeKind.Local?displayProperty=nameWithType> lub <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, przesunięcie ma wartość równą w lokalnej strefie czasowej.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Podczas analizowania reprezentację ciągu daty i godziny

<xref:System.DateTimeOffset> Typu obsługuje cztery metody, dzięki którym można przekonwertować z reprezentacji ciągu daty i godziny w <xref:System.DateTimeOffset> wartość:

* <xref:System.DateTimeOffset.Parse%2A>, które próbuje przekonwertować z reprezentacji ciągu daty i godziny do <xref:System.DateTimeOffset> wartości i zgłasza wyjątek, jeśli konwersja nie powiedzie się.

* <xref:System.DateTimeOffset.TryParse%2A>, które próbuje przekonwertować z reprezentacji ciągu daty i godziny do <xref:System.DateTimeOffset> wartości i zwraca `false` Jeśli konwersji nie powiedzie się.

* <xref:System.DateTimeOffset.ParseExact%2A>, które podejmuje próbę przekonwertowania reprezentację ciągu daty i godziny w określonym formacie do <xref:System.DateTimeOffset> wartości. Metoda zgłasza wyjątek, jeśli konwersja nie powiedzie się.

* <xref:System.DateTimeOffset.TryParseExact%2A>, które podejmuje próbę przekonwertowania reprezentację ciągu daty i godziny w określonym formacie do <xref:System.DateTimeOffset> wartości. Metoda zwraca `false` Jeśli konwersji nie powiedzie się.

Poniższy przykład przedstawia wywołania do każdej z tych metod konwersji ciągu czterech wystąpienia <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Zobacz także

[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
