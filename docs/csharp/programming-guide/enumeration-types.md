---
title: Typy wyliczeniowe - C# Programming Guide
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 7c40e16e9c495c5e69dcdd74c3698d51b0d49785
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240063"
---
# <a name="enumeration-types-c-programming-guide"></a>Typy wyliczeniowe (C# Programming Guide)

Typ wyliczenia (zwaną również wyliczenia lub typu wyliczeniowego) udostępnia efektywny sposób, aby zdefiniować zestaw nazwanych stałych liczbach całkowitych, które można przypisać do zmiennej. Na przykład załóżmy, że trzeba zdefiniować zmienną, w której wartość będzie reprezentować dnia tygodnia. Istnieją tylko siedem istotne wartości, które nigdy nie będą przechowywane w tej zmiennej. Aby zdefiniować te wartości, można użyć typem wyliczenia, która jest zadeklarowana za pomocą [wyliczenia](../../csharp/language-reference/keywords/enum.md) — słowo kluczowe.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Domyślnie jest podstawowym typem każdy element w typie wyliczeniowym [int](../../csharp/language-reference/keywords/int.md). Za pomocą dwukropka, można określić inny typ liczbowy całkowity, jak pokazano w poprzednim przykładzie. Aby uzyskać pełną listę możliwych typów, zobacz [enum (odwołanie w C#)](../../csharp/language-reference/keywords/enum.md).

Podstawowej wartości liczbowe można sprawdzić przez rzutowanie typu podstawowego, co ilustruje poniższy przykład.

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

Korzyści wynikające z używania wyliczenia zamiast typu numerycznego są następujące:

- Jednoznacznie określić kod klienta, które wartości są prawidłowe dla zmiennej.

- W programie Visual Studio funkcja IntelliSense wyświetla zdefiniowanymi wartościami.

Jeśli nie określisz wartości elementów na liście modułu wyliczającego, wartości są automatycznie zwiększany o 1. W poprzednim przykładzie `Day.Sunday` ma wartość 0, `Day.Monday` ma wartość 1 i tak dalej. Podczas tworzenia nowego `Day` obiektu ma wartość domyślną `Day.Sunday` (0), jeśli nie jawnie przypisać jej wartości. Podczas tworzenia wyliczenia wybrać najbardziej logicznym wartość domyślną, a następnie nadaj mu wartość zero. Który spowoduje, że wszystkie typy wyliczeniowe za tę wartość domyślną, jeśli ich nie są jawnie przypisane wartości podczas ich tworzenia.

Jeśli zmienna `meetingDay` typu `Day`, a następnie (bez jawnego rzutowania) można przypisać tylko ona jedną z wartości zdefiniowanych przez `Day`. Jeśli zmieni się w dniu spotkania, może przypisać nowej wartości z `Day` do `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Można przypisać dowolną wartość dowolnego liczby całkowitej do `meetingDay`. Na przykład ten wiersz kodu nie generuje błąd: `meetingDay = (Day) 42`. Jednak możesz nie należy tego robić, ponieważ niejawna oczekuje się, że zmienna enum będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie. Aby przypisać dowolną wartość do zmiennej typu wyliczeniowego jest wprowadzenie wysokie ryzyko błędów.

Wszelkie wartości można przypisać do elementów na liście moduł wyliczający typu wyliczeniowego, a można również użyć obliczonych wartości:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczeniowe jako znaczniki bitowe

Typ wyliczenia można użyć do zdefiniowania flag bitowych, co umożliwia wystąpienie typu wyliczenia do przechowywania dowolną kombinację wartości, które zostały zdefiniowane na liście modułu wyliczającego. (Oczywiście niektóre kombinacje mogą nie być znaczenia lub dozwolonych w kodzie programu.)

Utwórz trochę wyliczenia flag, stosując <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybut i odpowiednio definiowanie wartości tak, aby `AND`, `OR`, `NOT` i `XOR` Operacje bitowe mogą być wykonywane na nich. W trochę wyliczenia flag obejmują nazwanej stałej o wartości zero, co oznacza "nie flagi są ustawione." Nie ma flagi wartość zero, jeśli nie oznacza "nie flagi są ustawione".

W poniższym przykładzie inną wersję `Day` wyliczenia, które nosi nazwę `Days`, jest zdefiniowana. `Days` ma `Flags` atrybutu, a każda wartość jest przypisany następną większa potęgą liczby 2. Dzięki temu można utworzyć `Days` zmienna, której wartość jest `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Aby ustawić flagę w wyliczeniu, użyj operatora testu koniunkcji `OR` operatora, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Aby określić, czy ustawiono flagę określonego, użyj bitowej `AND` operacji, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Aby uzyskać więcej informacji o tym, co należy wziąć pod uwagę podczas definiowania typów wyliczeń za pomocą <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutów, zobacz <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Korzystając z metody System.Enum odnajdywać i manipulować wartościami typu enum

Wszystkie typy wyliczeniowe są wystąpieniami <xref:System.Enum?displayProperty=nameWithType> typu. Nie możesz wywodzić nowe klasy z <xref:System.Enum?displayProperty=nameWithType>, ale jego metody umożliwia odnajdywanie informacji o i manipulować wartościami w wystąpieniu typu wyliczeniowego.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.

Można również utworzyć nowej metody dla wyliczenia przy użyciu metody rozszerzenia. Aby uzyskać więcej informacji, zobacz [jak: Utworzenie nowej metody wyliczania](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Enum?displayProperty=nameWithType>  
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)  
- [enum](../../csharp/language-reference/keywords/enum.md)
