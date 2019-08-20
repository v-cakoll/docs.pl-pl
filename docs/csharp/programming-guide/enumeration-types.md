---
title: Typy wyliczeniowe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: fea12a32d39f98ddc575e2d538e7501d2ff49768
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590547"
---
# <a name="enumeration-types-c-programming-guide"></a>Typy wyliczeniowe (C# Przewodnik programowania)

Typ wyliczenia (nazywany również wyliczeniem lub wyliczeniem) zapewnia wydajny sposób definiowania zestawu nazwanych stałych, które mogą być przypisane do zmiennej. Załóżmy na przykład, że musisz zdefiniować zmienną, której wartość będzie zawierać dzień tygodnia. Istnieje tylko siedem wartości, które będą kiedykolwiek przechowywane w tej zmiennej. Aby zdefiniować te wartości, można użyć typu wyliczenia, który jest zadeklarowany za pomocą słowa kluczowego [enum](../language-reference/keywords/enum.md) .

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Domyślnie typem podstawowym każdego elementu w wyliczeniu jest [int](../language-reference/builtin-types/integral-numeric-types.md). Możesz określić inny typ liczbowy całkowity przy użyciu dwukropka, jak pokazano w poprzednim przykładzie. Aby uzyskać pełną listę możliwych typów, zobacz [Wyliczenie (C# odwołanie)](../language-reference/keywords/enum.md).

Można sprawdzić bazowe wartości liczbowe przez rzutowanie na typ podstawowy, jak pokazano w poniższym przykładzie.

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

Poniżej przedstawiono zalety użycia wyliczenia zamiast typu liczbowego:

- Jasno określono kod klienta, który wartości są prawidłowe dla zmiennej.

- W programie Visual Studio funkcja IntelliSense wyświetla zdefiniowane wartości.

Jeśli nie określisz wartości dla elementów na liście moduł wyliczający, wartości są automatycznie zwiększane o 1. W poprzednim przykładzie `Day.Sunday` ma wartość `Day.Monday` 0, ma wartość 1 i tak dalej. Podczas tworzenia nowego `Day` obiektu będzie on miał `Day.Sunday` wartość domyślną (0), jeśli nie zostanie jawnie przypisana wartość. Podczas tworzenia wyliczenia wybierz najbardziej logiczną wartość domyślną i nadaj jej wartość zero. Spowoduje to, że wszystkie wyliczenia mają tę wartość domyślną, jeśli nie będą jawnie przypisywać wartości podczas tworzenia.

Jeśli zmienna `meetingDay` jest typu `Day`, a następnie (bez jawnego rzutowania) można przypisać tylko jedną z wartości zdefiniowanych przez `Day`. W przypadku zmiany dnia spotkania można przypisać nową wartość z `Day` do: `meetingDay`

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> Można przypisać dowolną dowolną liczbę całkowitą do `meetingDay`. Na przykład ten wiersz kodu nie powoduje błędu: `meetingDay = (Day) 42`. Jednak nie należy tego robić, ponieważ niejawne oczekiwanie jest fakt, że zmienna enum będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie. Aby przypisać arbitralną wartość do zmiennej typu wyliczenia, należy wprowadzić wysokie ryzyko dla błędów.

Można przypisać dowolne wartości do elementów na liście modułów wyliczających typu wyliczenia i można również użyć wartości obliczanych:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Typy wyliczeniowe jako flagi bitowe

Możesz użyć typu wyliczenia, aby zdefiniować flagi bitowe, które umożliwiają wystąpienie typu wyliczenia do przechowywania dowolnej kombinacji wartości, które są zdefiniowane na liście modułów wyliczających. (Oczywiście Niektóre kombinacje mogą nie być znaczące ani niedozwolone w kodzie programu).

<xref:System.FlagsAttribute?displayProperty=nameWithType> `OR` Abyutworzyć`NOT` Wyliczenie flag bitowych ,`XOR`należy zastosować atrybut i odpowiednio zdefiniować wartości, aby można było wykonywać na nich operacje bitowe. `AND` W wyliczeniu flag bitowych należy uwzględnić nazwaną stałą o wartości zero, co oznacza, że flagi nie są ustawione. Nie należy dawać flagi wartością zero, jeśli nie ma znaczenia "nie ustawiono flag".

W poniższym przykładzie jest definiowana inna wersja `Day` wyliczenia o nazwie. `Days` `Days``Flags` ma atrybut, a każda wartość jest przypisana kolejną większą potęgą 2. Dzięki temu można utworzyć zmienną, `Days` której wartość to. `Days.Tuesday | Days.Thursday`

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Aby ustawić flagę w wyliczeniu, użyj operatora `OR` bitowego, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Aby określić, czy określona flaga jest ustawiona, użyj operacji bitowej `AND` , jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

Aby uzyskać więcej informacji o tym <xref:System.FlagsAttribute?displayProperty=nameWithType> , co należy wziąć pod uwagę podczas definiowania typów wyliczeniowych przy użyciu atrybutu, zobacz. <xref:System.Enum?displayProperty=nameWithType>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Używanie metod system. Enum do odnajdywania i manipulowania wartościami wyliczanymi

Wszystkie wyliczenia są wystąpieniami <xref:System.Enum?displayProperty=nameWithType> typu. Nie można utworzyć nowych klas z <xref:System.Enum?displayProperty=nameWithType>, ale można użyć jej metod w celu odnalezienia informacji o wartościach i manipulowania nimi w wystąpieniu wyliczenia.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.

Możesz również utworzyć nową metodę dla wyliczenia przy użyciu metody rozszerzenia. Aby uzyskać więcej informacji, zobacz [jak: Utwórz nową metodę dla wyliczenia](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Enum?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](./index.md)
- [enum](../language-reference/keywords/enum.md)
