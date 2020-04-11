---
title: Wbudowane konwersje numeryczne — odwołanie do języka C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: b7d53e508e4d585c746a3cc61824cdace7707deb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121453"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Wbudowane konwersje numeryczne (odwołanie do języka C#)

C# zawiera zestaw typów liczbowych [całekowych](integral-numeric-types.md) i [zmiennoprzecinkowych.](floating-point-numeric-types.md) Istnieje konwersja między dowolnymi dwoma typami liczbowymi, niejawnymi lub jawnymi. Do wykonania jawnej konwersji należy użyć [wyrażenia rzutowego.](../operators/type-testing-and-cast.md#cast-expression)

## <a name="implicit-numeric-conversions"></a>Niejawne konwersje liczbowe

W poniższej tabeli przedstawiono wstępnie zdefiniowane niejawne konwersje między wbudowanymi typami liczbowymi:

|Z|Do|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`short`, `int` `long`, `float` `double`, , , lub`decimal`|
|[Bajtów](integral-numeric-types.md)|`short`, `ushort` `int`, `uint` `long`, `ulong` `float`, `double`, , , , lub`decimal`|
|[short](integral-numeric-types.md)|`int`, `long` `float`, `double`, , lub`decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint` `long`, `ulong` `float`, `double`, , , lub`decimal`|
|[int](integral-numeric-types.md)|`long`, `float` `double`, , lub`decimal`|
|[Uint](integral-numeric-types.md)|`long`, `ulong` `float`, `double`, , lub`decimal`|
|[long](integral-numeric-types.md)|`float`, `double`, lub`decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`, lub`decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Niejawne konwersje `int`z `ulong` , `float` `uint` `long`, `ulong` , `double` lub do i z `long` lub do może spowodować utratę precyzji, ale nigdy nie utraty rzędu wielkości. Inne niejawne konwersje liczbowe nigdy nie tracą żadnych informacji.

Należy również pamiętać, że

- Każdy [integralny typ numeryczny](integral-numeric-types.md) jest niejawnie konwertowany na dowolny [zmiennoprzecinnikowy typ liczbowy.](floating-point-numeric-types.md)

- Nie ma żadnych niejawnych konwersji do `byte` i `sbyte` typów. Nie ma żadnych konwersji `double` `decimal` niejawnych z i typów.

- Nie ma żadnych konwersji `decimal` niejawnych `float` `double` między typem a typami lub.

- Wartość wyrażenia stałego typu `int` (na przykład wartość reprezentowana przez literał całkowity) może być `sbyte`niejawnie konwertowana na `byte`, , `short`, `ushort` `uint`, , lub `ulong`, jeśli mieści się w zakresie typu docelowego:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Jak pokazano w poprzednim przykładzie, jeśli stała wartość nie mieści się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)

## <a name="explicit-numeric-conversions"></a>Jawne konwersje numeryczne

W poniższej tabeli przedstawiono wstępnie zdefiniowane jawne konwersje między wbudowanymi typami liczbowymi, dla których nie ma [konwersji niejawnej:](#implicit-numeric-conversions)

|Z|Do|
|----------|--------|
|[Sbyte](integral-numeric-types.md)|`byte`, `ushort` `uint`, , lub`ulong`|
|[Bajtów](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte` `ushort`, `uint`, , lub`ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`, lub`short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `uint`, , , lub`ulong`|
|[Uint](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort`, , lub`int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , , lub`ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint`, , , lub`long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong`, , , , lub`decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , , , lub`decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , , , lub`double`|

> [!NOTE]
> Jawna konwersja liczbowa może spowodować utratę danych <xref:System.OverflowException>lub zgłosić wyjątek, zazwyczaj .

Należy również pamiętać, że

- Podczas konwertowania wartości typu integralnego na inny typ integralny wynik zależy od [kontekstu sprawdzania przepełnienia](../keywords/checked-and-unchecked.md). W sprawdzonym kontekście konwersja powiedzie się, jeśli wartość źródłowa mieści się w zakresie typu docelowego. W przeciwnym <xref:System.OverflowException> razie jest wyrzucany. W niezaznaczone kontekście konwersja zawsze powiedzie się i przebiega w następujący sposób:

  - Jeśli typ źródła jest większy niż typ docelowy, wartość źródłowa jest obcinana przez odrzucenie jego "dodatkowych" najbardziej znaczących bitów. Wynik jest następnie traktowany jako wartość typu docelowego.

  - Jeśli typ źródła jest mniejszy niż typ docelowy, wartość źródłowsza jest rozszerzona lub rozszerzona zerem, tak aby była tego samego rozmiaru co typ docelowy. Rozszerzenie znaku jest używany, jeśli typ źródła jest podpisany; rozszerzenie zero jest używane, jeśli typ źródła jest niepodpisany. Wynik jest następnie traktowany jako wartość typu docelowego.

  - Jeśli typ źródła ma ten sam rozmiar co typ docelowy, wartość źródłowsza jest traktowana jako wartość typu docelowego.

- Podczas konwertowania wartości na `decimal` typ całkowity wartość jest zaokrąglana w kierunku zera do najbliższej wartości integralnej. Jeśli wynikowa wartość całkowita znajduje się poza zakresem typu docelowego, <xref:System.OverflowException> jest rzutowy.

- Podczas konwertowania `double` lub `float` wartości na typ całkowity, ta wartość jest zaokrąglana w kierunku zera do najbliższej wartości integralnej. Jeśli wynikowa wartość całkowita znajduje się poza zakresem typu docelowego, wynik zależy od [kontekstu sprawdzania przepełnienia](../keywords/checked-and-unchecked.md). W kontekście zaznaczone <xref:System.OverflowException> jest wyrzucane, podczas gdy w kontekście niezaznaczone wynik jest nieokreśloną wartością typu docelowego.

- Podczas `double` konwersji `float`na `double` wartość jest zaokrąglana do najbliższej `float` wartości. Jeśli `double` wartość jest zbyt mała lub zbyt `float` duża, aby zmieścić się w typie, wynik wynosi zero lub nieskończoność.

- `float` Podczas konwertowania `double` lub do `decimal`, `decimal` wartość źródłowa jest konwertowana na reprezentację i zaokrąglana do najbliższej liczby po 28 miejscu po przecinku, jeśli jest to wymagane. W zależności od wartości wartości źródłowej może wystąpić jeden z następujących wyników:

  - Jeśli wartość źródło jest zbyt mała, `decimal`aby być reprezentowana jako , wynik staje się zero.

  - Jeśli wartość źródłowa jest NaN (nie liczba), nieskończoność lub `decimal`zbyt <xref:System.OverflowException> duży, aby być reprezentowane jako , jest generowany.

- `decimal` Podczas konwersji `float` `double`do lub , wartość źródło `float` jest `double` zaokrąglana do najbliższej lub wartości, odpowiednio.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Niejawne konwersje liczbowe](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Jawne konwersje numeryczne](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Odlewanie i konwersje typu](../../programming-guide/types/casting-and-type-conversions.md)
