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
ms.openlocfilehash: 6d8f4254da256bf2814f66aa62d43204fb302701
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494060"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Tworzenie wystąpień obiektów DateTimeOffset

<xref:System.DateTimeOffset> Struktury oferuje kilka sposobów, aby utworzyć nowy element <xref:System.DateTimeOffset> wartości. Wiele z nich odpowiadają bezpośrednio do metody dostępne dla nowego wystąpienia <xref:System.DateTime> wartościami ulepszeń, które pozwalają na określenie wartości daty i godziny przesunięcie względem uniwersalnego czasu koordynowanego (UTC). W szczególności, można utworzyć wystąpienie <xref:System.DateTimeOffset> wartości w następujący sposób:

* Za pomocą datę i godzinę literału.

* Przez wywołanie metody <xref:System.DateTimeOffset> konstruktora.

* Za pomocą niejawnej konwersji wartości do <xref:System.DateTimeOffset> wartości.

* Analizując ciąg reprezentujący datę i godzinę.

Ten temat zawiera większą szczegółów i przykładów kodu, które ilustrują te metody tworzenia nowego wystąpienia <xref:System.DateTimeOffset> wartości.

## <a name="date-and-time-literals"></a>Literały daty i godziny

W przypadku języków, które go obsługują, jedną z najbardziej typowych sposobów do utworzenia wystąpienia <xref:System.DateTime> wartość ma na celu dostarczenie daty i godziny jako ustaloną wartość literału. Na przykład, poniższy kod języka Visual Basic tworzy <xref:System.DateTime> obiektu, którego wartością jest 1 stycznia 2008 r. o 10:00.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset> wartości mogą również inicjowane za pomocą literałów datę i godzinę, korzystając z języków, które obsługują <xref:System.DateTime> literały. Na przykład, poniższy kod języka Visual Basic tworzy <xref:System.DateTimeOffset> obiektu.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Jak pokazano w danych wyjściowych konsoli <xref:System.DateTimeOffset> wartość utworzone w ten sposób jest przypisany przesunięcie lokalnej strefy czasowej. Oznacza to, że <xref:System.DateTimeOffset> wartości przypisane przy użyciu literału znakowego nie identyfikuje pojedynczy punkt w czasie, jeśli kod jest uruchamiany na różnych komputerach.

## <a name="datetimeoffset-constructors"></a>Konstruktory DateTimeOffset

<xref:System.DateTimeOffset> Typ definiuje sześć konstruktorów. Cztery z nich odpowiadają bezpośrednio do <xref:System.DateTime> konstruktory o dodatkowy parametr typu <xref:System.TimeSpan> definiujący daty i godziny przesunięcie względem czasu UTC. Te umożliwiają definiowanie <xref:System.DateTimeOffset> wartość na podstawie wartości jego daty i czasu składników. Na przykład w poniższym kodzie użyto tych czterech konstruktorów do tworzenia wystąpienia <xref:System.DateTimeOffset> obiektów za pomocą identycznych wartości 1/7/2008 00:05:00 +01: 00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Należy zauważyć, że gdy wartość <xref:System.DateTimeOffset> tworzone przy użyciu obiektu <xref:System.Globalization.PersianCalendar> obiektu jako jeden z argumentów dla jego konstruktora jest wyświetlana w konsoli, jest wyrażona jako data w gregoriańskim, a nie kalendarz perski. W danych wyjściowych datę przy użyciu kalendarz perski, zobacz przykład w <xref:System.Globalization.PersianCalendar> tematu.

Utwórz dwa konstruktory <xref:System.DateTimeOffset> obiektu z <xref:System.DateTime> wartości. Pierwszy z nich ma jeden parametr, <xref:System.DateTime> wartość do przekonwertowania na <xref:System.DateTimeOffset> wartość. Przesunięcie wynikowy <xref:System.DateTimeOffset> wartość zależy od <xref:System.DateTime.Kind%2A> właściwość pojedynczy parametr w konstruktorze. Jeśli wartość to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. W przeciwnym razie jego przesunięcie ustawiono równa lokalnej strefy czasowej. W poniższym przykładzie pokazano użycie tego konstruktora do utworzenia wystąpienia <xref:System.DateTimeOffset> obiektów reprezentujących UTC i lokalnej strefy czasowej:

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> Wywołanie przeciążenia <xref:System.DateTimeOffset> konstruktora, który ma jeden <xref:System.DateTime> parametr jest równoważny do wykonywania niejawnej konwersji wartości <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartość.

Drugi Konstruktor, który tworzy <xref:System.DateTimeOffset> obiektu z <xref:System.DateTime> wartość zawiera dwa parametry: <xref:System.DateTime> wartość do przekonwertowania, a <xref:System.TimeSpan> reprezentującą datę i godzinę przesunięcie względem czasu UTC. Ta wartość przesunięcia musi odpowiadać <xref:System.DateTime.Kind%2A> właściwość pierwszy parametr w konstruktorze lub <xref:System.ArgumentException> zgłaszany. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszy parametr jest <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, wartość drugiego parametru musi być <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszy parametr jest <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, wartość drugiego parametru musi być przesunięcie strefy czasowej systemu lokalnego. Jeśli <xref:System.DateTime.Kind%2A> właściwość pierwszy parametr jest <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, Przesunięcie może być dowolną prawidłową wartość. Poniższy kod ilustruje wywołania do tego konstruktora, aby przekonwertować <xref:System.DateTime> do <xref:System.DateTimeOffset> wartości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Niejawna konwersja typu

<xref:System.DateTimeOffset> Typ obsługuje jeden niejawna konwersja typu: od <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartość. (Niejawna konwersja typu jest konwersja jednego typu na inny, który nie wymaga jawnego rzutowania (w języku C#) lub konwersji (w języku Visual Basic) i nie traci informacji. To sprawia, że kod, takich jak poniższe możliwości.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Przesunięcie wynikowy <xref:System.DateTimeOffset> zależy od wartości <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> wartości właściwości. Jeśli wartość to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, przesunięcie jest równe <xref:System.TimeSpan.Zero?displayProperty=nameWithType>. Jeśli wartość <xref:System.DateTimeKind.Local?displayProperty=nameWithType> lub <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, przesunięcie ma wartość równą lokalnej strefy czasowej.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Podczas analizowania reprezentację ciągu daty i godziny

<xref:System.DateTimeOffset> Typ obsługuje cztery metody, które umożliwiają konwertowanie reprezentacją ciągu daty i godziny w <xref:System.DateTimeOffset> wartość:

* <xref:System.DateTimeOffset.Parse%2A>, który próbuje przekonwertować ciąg reprezentujący datę i godzinę <xref:System.DateTimeOffset> wartości i zgłasza wyjątek, jeśli konwersja nie powiedzie się.

* <xref:System.DateTimeOffset.TryParse%2A>, który próbuje przekonwertować ciąg reprezentujący datę i godzinę <xref:System.DateTimeOffset> wartości i zwraca `false` Jeśli konwersja nie powiedzie się.

* <xref:System.DateTimeOffset.ParseExact%2A>, który próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie do <xref:System.DateTimeOffset> wartości. Metoda zgłasza wyjątek, jeśli konwersja nie powiedzie się.

* <xref:System.DateTimeOffset.TryParseExact%2A>, który próbuje przekonwertować ciąg reprezentujący datę i godzinę w określonym formacie do <xref:System.DateTimeOffset> wartości. Metoda ta zwraca `false` Jeśli konwersja nie powiedzie się.

Poniższy przykład ilustruje sposób wywołania do każdego z tych czterech ciągów metody konwersji do utworzenia wystąpienia <xref:System.DateTimeOffset> wartość.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Zobacz także

* [Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
