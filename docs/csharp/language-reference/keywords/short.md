---
title: short (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0d90f31da49b94eee490e95f0cdf1d582bb0b059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184156"
---
# <a name="short-c-reference"></a>short (odwołanie w C#)

`short` Wskazuje, że typ liczby całkowitej danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.

|Typ|Zakres|Rozmiar|Typ architektury .NET|
|----------|-----------|----------|-------------------------|
|`short`|-32768 do 32767.|16-bitową liczbę całkowitą ze znakiem|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a>Literały

Można zadeklarować i zainicjować `short` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.  Jeśli literał liczby całkowitej jest poza zakresem `short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](int.md) do `short` wartości.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.

- C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
- Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a>Przeciążeń z późnym

Podczas wywoływania przeciążone metody, należy użyć rzutowania. Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `short` i [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

Za pomocą `short` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a>Konwersje

Jest wstępnie zdefiniowanych niejawna konwersja z `short` do [int](int.md), [długie](long.md), [float](float.md), [double](double.md), lub [ dziesiętna](decimal.md).

Nie można niejawnie przekonwertować nieliteralnego typy liczbowe większy rozmiar magazynu na `short` (zobacz [Tabela typów całkowitych](integral-types-table.md) dla rozmiaru magazynu typów całkowitych). Należy wziąć pod uwagę, na przykład, następujące dwa `short` zmienne `x` i `y`:

```csharp
short x = 5, y = 12;
```

Poniższa instrukcja przypisania powoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](int.md) domyślnie.

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

Aby rozwiązać ten problem, należy użyć rzutowania:

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

Istnieje również możliwość użycia poniższe instrukcje, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:

```csharp
int m = x + y;
long n = x + y;
```

Istnieje niejawna konwersja z typów zmiennoprzecinkowych `short`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).

Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Int16>
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabela typów całkowitych](integral-types-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)