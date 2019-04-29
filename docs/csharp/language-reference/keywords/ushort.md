---
title: ushort — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660401"
---
# <a name="ushort-c-reference"></a>ushort (odwołanie w C#)

`ushort` — Słowo kluczowe wskazuje typ liczby całkowitej danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.

|Typ|Zakres|Rozmiar|Typ architektury .NET|
|----------|-----------|----------|-------------------------|
|`ushort`|0 do 65 535.|Liczba całkowita bez znaku 16-bitowych|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Można zadeklarować i zainicjować `ushort` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne. Jeśli literał liczby całkowitej jest poza zakresem `ushort` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 65,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](int.md) do `ushort` wartości.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:

- C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
- Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a>Przeciążeń z późnym

Należy użyć rzutowania, po wywołaniu metody przeciążone. Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `ushort` i [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

Za pomocą `ushort` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a>Konwersje

Jest wstępnie zdefiniowanych niejawna konwersja z `ushort` do [int](int.md), [uint](uint.md), [długie](long.md), [ulong](ulong.md), [float ](float.md), [double](double.md), lub [dziesiętna](decimal.md).

Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md) lub [char](char.md) do `ushort`. W przeciwnym razie rzutowania może służyć do wykonania jawnej konwersji. Należy wziąć pod uwagę, na przykład, następujące dwa `ushort` zmienne `x` i `y`:

```csharp
ushort x = 5, y = 12;
```

Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

Aby rozwiązać ten problem, należy użyć rzutowania:

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

Możliwe jest jednak należy zastosować następujące polecenia, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:

```csharp
int m = x + y;
long n = x + y;
```

Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `ushort`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).

Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.UInt16>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów całkowitych](integral-types-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
