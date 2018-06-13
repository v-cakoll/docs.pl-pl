---
title: Typy wyliczeniowe (C# przewodnik programowania w języku)
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: a97c3569899e7cf99dd522024de8373c60076571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339056"
---
# <a name="enumeration-types-c-programming-guide"></a>Typy wyliczeniowe (C# przewodnik programowania w języku)

Typ wyliczenia (nazywana również wyliczenie lub wyliczenia) umożliwia wydajne do zdefiniowania zestawu o nazwie stałe całkowite, przypisane do zmiennej. Na przykład załóżmy, że trzeba zdefiniować zmienną, której wartość reprezentuje dzień tygodnia. Istnieje tylko siedem istotnych wartości, które kiedykolwiek zapisze tej zmiennej. Aby zdefiniować te wartości, można użyć typem wyliczenia, który został zadeklarowany za pomocą [wyliczenia](../../csharp/language-reference/keywords/enum.md) — słowo kluczowe.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Domyślnie jest typu bazowego dla każdego elementu w elemencie enum [int](../../csharp/language-reference/keywords/int.md). Można określić inny typ liczbowy integralną przy użyciu dwukropek, jak pokazano w poprzednim przykładzie. Aby uzyskać pełną listę możliwych typów, zobacz [enum (odwołanie w C#)](../../csharp/language-reference/keywords/enum.md).

Możesz sprawdzić podstawowej wartości liczbowych przez rzutowanie na typ podstawowy, jak przedstawiono na poniższym przykładzie.

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

Zalety korzystania z wyliczeniem zamiast typu liczbowego są następujące:

- Wyraźnie określ wartości, które są prawidłowe dla zmiennej kodu klienta.

- W programie Visual Studio IntelliSense wyświetla zdefiniowanymi wartościami.

Jeśli nie określisz wartości elementów na liście modułu wyliczającego, wartości są automatycznie zwiększana o 1. W poprzednim przykładzie `Day.Sunday` ma wartość 0, `Day.Monday` ma wartość 1 i tak dalej. Podczas tworzenia nowego `Day` obiektu, będzie mieć wartość domyślną równą `Day.Sunday` (0), jeśli nie zostanie jawnie przypisany jej wartość. Podczas tworzenia wyliczenia wybierz najbardziej logicznym wartość domyślną i nadaj mu wartość zero. Który spowoduje, że wszystkie typy wyliczeniowe za tę wartość domyślną, jeśli nie są one jawnie przypisywane wartość po ich utworzeniu.

Jeśli zmienna `meetingDay` jest typu `Day`, a następnie (bez jawnego rzutowania) można przypisać tylko ona jedną z wartości zdefiniowanych przez `Day`. I zmiana dzień spotkania można przypisać nowe wartości z `Day` do `meetingDay`:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Można przypisać dowolną wartość całkowitą dowolnego do `meetingDay`. Na przykład ten wiersz kodu nie generuje błąd: `meetingDay = (Day) 42`. Jednak użytkownik nie należy tego robić ponieważ niejawne oczekuje się, że zmiennej wyliczenia będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie. Aby przypisać dowolną wartość do zmiennej typu wyliczenia jest wprowadzenie duże ryzyko błędów.

Można przypisać wartości do elementów na liście modułu wyliczającego dla typu wyliczeniowego, a także można użyć obliczanej wartości:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczeniowe jako flagi bitów

Typem wyliczenia można użyć do definiowania flagi bitów, co włącza wystąpienie typu wyliczenia w celu przechowywania dowolnej kombinacji wartości, które są zdefiniowane na liście modułu wyliczającego. (Oczywiście niektórych kombinacji nie może być przydatne lub dozwolonych w kodzie programu.)

Utwórz nieco wyliczenia flag, stosując <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybut i odpowiednio definiowanie wartości, aby `AND`, `OR`, `NOT` i `XOR` Operacje bitowe mogą być wykonywane na nich. W nieco wyliczenia flag obejmują nazwanej stałej o wartości zero oznacza "nie flagi są ustawione." Nie ma flagi wartość równą zero, jeśli nie oznacza to "nie flagi są ustawiane".

W poniższym przykładzie inna wersja `Day` wyliczenia, które nosi nazwę `Days`, jest zdefiniowany. `Days` ma `Flags` atrybutów i wartości jest przypisany następny większy potęgą liczby 2. Dzięki temu można utworzyć `Days` zmiennej, którego wartość jest `Days.Tuesday | Days.Thursday`.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Aby ustawić flagę w wyliczeniu, użyj operatora testu koniunkcji `OR` operatora, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Aby określić, czy ustawiono flagę określonych, użyj bitowej `AND` operacji, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Aby uzyskać więcej informacji o tym, co należy wziąć pod uwagę podczas definiowania Typy wyliczeniowe z <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutów, zobacz <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Przy użyciu metod element System.Enum do odnajdywania i manipulowania wartości wyliczenia

Wszystkie typy wyliczeniowe są wystąpieniami klasy <xref:System.Enum?displayProperty=nameWithType> typu. Nie może wyprowadzać nowe klasy z <xref:System.Enum?displayProperty=nameWithType>, ale jego metody umożliwia odnajdywanie informacji o i manipulowania wartości w określonym wystąpieniu wyliczenia.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.

Można również utworzenie nowej metody dla wyliczenia za pomocą metody rozszerzenia. Aby uzyskać więcej informacji, zobacz [porady: utworzenie nowej metody wyliczania](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Zobacz także
 <xref:System.Enum?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)  
 [enum](../../csharp/language-reference/keywords/enum.md)
