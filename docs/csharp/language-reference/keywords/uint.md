---
title: uint — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 9a60460f67f9b6cf0b57d40ebf2789536e870d75
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633146"
---
# <a name="uint-c-reference"></a>uint (odwołanie w C#)

`uint` — Słowo kluczowe oznacza integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.

|Typ|Zakres|Rozmiar|Typ architektury .NET|
|----------|-----------|----------|-------------------------|
|`uint`|4 294 967 0 Aby 295|Liczba całkowita bez znaku 32-bitowy|<xref:System.UInt32?displayProperty=nameWithType>|

**Uwaga** `uint` typ nie jest zgodny ze specyfikacją CLS. Użyj `int` zawsze, gdy jest to możliwe.

## <a name="literals"></a>Literały

Można zadeklarować i zainicjować `uint` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne. Jeśli literał liczby całkowitej jest poza zakresem `uint` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `uint` wartości.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Począwszy od C# 7.0, kilka funkcje zostały dodane do zwiększenia czytelności:

- C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
- Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

Literały całkowite mogą również zawierać sufiks, który oznacza typ. Sufiks `U` lub "u" oznacza albo `uint` lub `ulong`, w zależności od wartości liczbowej literału. W poniższym przykładzie użyto `u` sufiks, aby wskazać liczbą całkowitą bez znaku obu typów. Należy zauważyć, że pierwszym literał `uint` ponieważ jej wartość jest mniejsza niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a drugą jest wartość `ulong` ponieważ jej wartość jest większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:

1. [int](int.md)
2. `uint`
3. [long](long.md)
4. [ulong](ulong.md)

## <a name="conversions"></a>Konwersje

Jest wstępnie zdefiniowanych niejawna konwersja z `uint` do [długie](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), lub [ dziesiętna](decimal.md). Na przykład:

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

Brak wstępnie zdefiniowanych niejawna konwersja z [bajtów](byte.md), [ushort](ushort.md), lub [char](char.md) do `uint`. W przeciwnym razie należy użyć rzutowania. Na przykład poniższa instrukcja przypisania spowoduje błąd kompilacji bez rzutowania:

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `uint`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).

Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.UInt32>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów całkowitych](integral-types-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
