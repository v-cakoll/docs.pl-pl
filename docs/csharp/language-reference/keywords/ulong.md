---
title: ulong — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 97db22612e900658746f40cd117ff941135027a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660427"
---
# <a name="ulong-c-reference"></a>ulong (odwołanie w C#)

`ulong` — Słowo kluczowe oznacza integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.

|Typ|Zakres|Rozmiar|Typ architektury .NET|
|----------|-----------|----------|-------------------------|
|`ulong`|0 — 18,446,744,073,709,551,615|Liczba całkowita bez znaku 64-bitowych|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Można zadeklarować i zainicjować `ulong` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.  Jeśli literał liczby całkowitej jest poza zakresem `ulong` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt64.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 7,934,076,125, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `ulong` wartości.

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:

- C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
- Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

Literały całkowite mogą również zawierać sufiks, który oznacza typ. Sufiks `UL` lub `ul` jednoznacznie identyfikuje literał liczbowy jako `ulong` wartość. `L` Oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.Int64.MaxValue?displayProperty=nameWithType>. I `U` lub `u` oznacza sufiks `ulong` jeśli przekracza wartość literału <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. W poniższym przykładzie użyto `ul` sufiks do oznaczania długich liczb całkowitych:

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:

1. [int](int.md)
2. [uint](uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Przeciążeń z późnym

Typowym zastosowaniem sufiks jest wywołanie metody przeciążone. Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `ulong` i [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

Przy użyciu sufiksu z `ulong` parametru gwarantuje, że poprawnego typu ma nazwę, na przykład:

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a>Konwersje

Jest wstępnie zdefiniowanych niejawna konwersja z `ulong` do [float](float.md), [double](double.md), lub [dziesiętna](decimal.md).

Istnieje niejawna konwersja z `ulong` do dowolnego typu całkowitoliczbowego. Na przykład następująca instrukcja generuje błąd kompilacji bez jawnego rzutowania:

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md), [ushort](ushort.md), [uint](uint.md), lub [char](char.md) do `ulong`.

Ponadto istnieje niejawna konwersja z typów zmiennoprzecinkowych `ulong`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).

Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.UInt64>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów całkowitych](integral-types-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
