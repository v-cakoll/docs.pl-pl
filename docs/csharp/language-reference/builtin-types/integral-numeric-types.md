---
title: Typy liczbowe integralne — odwołanie do języka C#
description: Poznaj zakres, rozmiar magazynu i zastosowania dla każdego z typów liczbowych.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093204"
---
# <a name="integral-numeric-types--c-reference"></a>Typy liczbowe integralne (odwołanie do języka C#)

Typy *liczbowe integralne* reprezentują liczby całkowite. Wszystkie typy liczbowe integralne są [typami wartości.](value-types.md) Są one również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literału](#integer-literals). Wszystkie typy liczbowe integralne obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [logiczne bitowe,](../operators/bitwise-and-shift-operators.md) [porównywanie](../operators/comparison-operators.md)i [równość.](../operators/equality-operators.md)

## <a name="characteristics-of-the-integral-types"></a>Charakterystyka typów integralnych

C# obsługuje następujące wstępnie zdefiniowane typy całki:

|Typ/słowo kluczowe języka C#|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------|
|`sbyte`|od -128 do 127|Podpisana 8-bitowa liczba całkowita|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|Od 0 do 255|Niepodpisana 8-bitowa liczba całkowita|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|od -32 768 do 32 767|Podpisana 16-bitowa liczba całkowita|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|od 0 do 65 535|Niepodpisana 16-bitowa liczba całkowita|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 do 2 147 483 647|Podpisana 32-bitowa liczba całkowita|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 do 4.294.967.295|Niepodpisana 32-bitowa liczba całkowita|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9 223 372 036.854.775.808 do 9.223.372.036.854.775.807|Podpisana 64-bitowa liczba całkowita|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 do 18 446 744 773 709 551 615|Niepodpisana 64-bitowa liczba całkowita|<xref:System.UInt64?displayProperty=nameWithType>|

W powyższej tabeli każde słowo kluczowe typu C# z kolumny po lewej stronie jest aliasem dla odpowiedniego typu .NET. Są wymienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Domyślną wartością każdego typu `0`integralnego jest zero, . Każdy z typów całki ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura służy do reprezentowania podpisanej liczby całkowitej bez górnych lub dolnych granic.

## <a name="integer-literals"></a>Literały całkowite

Literały całkowite mogą być

- *dziesiętne:* bez prefiksu
- *szesnastkowy:* `0x` z `0X` prefiksem lub prefiksem
- *binarny:* `0b` `0B` z prefiksem lub prefiksem (dostępny w języku C# 7.0 i nowszych)

Poniższy kod przedstawia przykład każdego z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

W poprzednim przykładzie pokazano `_` również użycie jako *separatora cyfr*, który jest obsługiwany począwszy od Języka C# 7.0. Separatora cyfr można używać ze wszystkimi rodzajami literałów liczbowych.

Typ literału całkowitego jest określany przez jego sufiks w następujący sposób:

- Jeśli literał nie ma sufiksu, jego typ jest pierwszym z następujących `int` `uint`typów, w których można reprezentować jego wartość: , , `long`, `ulong`.
- Jeśli literał `U` jest sufiksprzez lub `u`, jego typ jest pierwszym z następujących `uint` `ulong`typów, w których jego wartość może być reprezentowana: , .
- Jeśli literał `L` jest sufiksprzez lub `l`, jego typ jest pierwszym z następujących `long` `ulong`typów, w których jego wartość może być reprezentowana: , .

  > [!NOTE]
  > Małej litery `l` można użyć jako sufiksu. Jednak generuje to ostrzeżenie kompilatora, ponieważ litera `l` może być mylona z cyfrą `1`. Użyj `L` dla jasności.

- Jeśli literał jest sufiksowany `LU` `Lu`przez `lU` `UL`, `Ul` `uL`, `ul`, `ulong`, lub `lu`jego typ jest .

Jeśli wartość reprezentowana przez literał całkowity <xref:System.UInt64.MaxValue?displayProperty=nameWithType>przekracza, występuje błąd kompilatora [CS1021.](../../misc/cs1021.md)

Jeżeli określony typ literału `int` całkowitego jest i wartość reprezentowana przez literał jest w zakresie typu docelowego, `sbyte` `byte`wartość `short` `ushort`może `uint`być `ulong`niejawnie konwertowane na , , , , , , lub:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie znajduje się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)

Można również użyć rzutowania do konwersji wartości reprezentowanej przez literał całkowity na typ inny niż określony typ literału:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Konwersje

Można przekonwertować dowolny typ liczbowy na dowolny inny integralny typ numeryczny. Jeśli typ docelowy może przechowywać wszystkie wartości typu źródłowego, konwersja jest niejawna. W przeciwnym razie należy użyć [ `()` operatora rzutowania](../operators/type-testing-and-cast.md#cast-operator-) do wywołania jawnej konwersji. Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje liczbowe](numeric-conversions.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Typy całonowe](~/_csharplang/spec/types.md#integral-types)
- [Literały całkowite](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Typy zmiennoprzecinkowe](floating-point-numeric-types.md)
- [Standardowe ciągi formatu numerycznego](../../../standard/base-types/standard-numeric-format-strings.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
