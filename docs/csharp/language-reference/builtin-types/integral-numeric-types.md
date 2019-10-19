---
title: Całkowite typy liczbowe — C# odwołanie
description: Poznaj zakres, rozmiar magazynu i użycie dla każdego z typów całkowitych.
ms.date: 10/18/2019
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
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579195"
---
# <a name="integral-numeric-types--c-reference"></a>Całkowite typy liczbowe (C# odwołanie)

**Całkowite typy liczbowe** są podzbiorem **typów prostych** i mogą być inicjowane za pomocą [*literałów*](#integer-literals). Wszystkie typy całkowite są również typami wartości. Wszystkie typy liczbowe całkowite obsługują operatory [arytmetyczne](../operators/arithmetic-operators.md), [bitowe logiczne](../operators/bitwise-and-shift-operators.md), [porównania](../operators/comparison-operators.md)i [równości](../operators/equality-operators.md) .

## <a name="characteristics-of-the-integral-types"></a>Cechy typów całkowitych

C#obsługuje następujące wstępnie zdefiniowane typy całkowite:

|C#Type/słowo kluczowe|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 do 127|8-bitowa liczba całkowita ze znakiem|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|od 0 do 255|8-bitowa liczba całkowita bez znaku|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32 768 do 32 767|16-bitowa liczba całkowita ze znakiem|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|od 0 do 65 535|16-bitowa liczba całkowita bez znaku|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2 147 483 648 do 2 147 483 647|32-bitowa liczba całkowita|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|od 0 do 4 294 967 295|Niepodpisany 32-bitowa liczba całkowita|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-zakresu od do 9 223 372 036 854 775 807|64-bitowa liczba całkowita|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|od 0 do 18446744073709551615 są|Niepodpisany 64-bitowa liczba całkowita|<xref:System.UInt64?displayProperty=nameWithType>|

W powyższej tabeli każde C# słowo kluczowe type z lewej kolumny jest aliasem odpowiadającego typu .NET. Są one zamienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Wartością domyślną każdego typu całkowitego jest zero, `0`. Każdy z typów całkowitych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.

Użyj struktury <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, aby reprezentować liczbę całkowitą ze znakiem bez górnych lub dolnych granic.

## <a name="integer-literals"></a>Literały całkowite

Literały całkowite mogą być

- *Decimal*: bez żadnego prefiksu
- *szesnastkowe*: z prefiksem `0x` lub `0X`
- *plik binarny*: z prefiksem `0b` lub `0B` ( C# dostępnym w 7,0 i nowszych)

Poniższy kod ilustruje przykład każdego z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

W powyższym przykładzie przedstawiono również użycie `_` jako *separatora cyfr*, który jest obsługiwany od C# 7,0. Można użyć separatora cyfr z wszystkimi rodzajami literałów liczbowych.

Typ literału liczby całkowitej jest określany na podstawie jego sufiksu w następujący sposób:

- Jeśli literał nie ma sufiksu, jego typ to pierwszy z następujących typów, w którym można przedstawić jego wartość: `int`, `uint`, `long` `ulong`.
- Jeśli literał jest sufiksem `U` lub `u`, jego typ jest pierwszym z następujących typów, w których można reprezentować wartość: `uint` `ulong`.
- Jeśli literał jest sufiksem `L` lub `l`, jego typ jest pierwszym z następujących typów, w których można reprezentować wartość: `long` `ulong`.

  > [!NOTE]
  > Jako sufiksu można użyć małych liter `l`. Jednak spowoduje to wygenerowanie ostrzeżenia kompilatora, ponieważ `l` można mylić z cyfrą `1`. Użyj `L` do przejrzystości.

- Jeśli literał jest sufiksem `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` lub `lu`, jego typ to `ulong`.

Jeśli wartość reprezentowana przez literał liczby całkowitej przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, wystąpi błąd kompilatora [CS1021](../../misc/cs1021.md) .

Wartość reprezentowana przez literał liczby całkowitej może być niejawnie konwertowana na typ z mniejszym zakresem niż określony typ literału. Jest to możliwe, gdy wartość znajduje się w zakresie typu docelowego:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie należy do zakresu typu docelowego, wystąpi błąd kompilatora [CS0031](../../misc/cs0031.md) .

Można również użyć rzutowania, aby przekonwertować wartość reprezentowaną przez literał liczby całkowitej na typ inny niż określony typ literału:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Konwersje

Istnieje niejawna konwersja (nazywana *konwersją rozszerzającą*) między dwoma typami całkowitymi, w których typ docelowy może przechowywać wszystkie wartości typu źródłowego. Na przykład istnieje niejawna konwersja z `int` do `long`, ponieważ zakres `int` wartości jest prawidłowym podzbiorem `long`. Istnieją niejawne konwersje z mniejszego niepodpisanego typu całkowitego na większy typ całkowity ze znakiem. Istnieje również niejawna konwersja z dowolnego typu całkowitego na dowolny typ zmiennoprzecinkowy.  Nie istnieje niejawna konwersja z dowolnego podpisanego typu całkowitego do dowolnego niepodpisanego typu całkowitego.

Należy użyć jawnego rzutowania do przekonwertowania jednego typu całkowitego na inny typ całkowity, gdy niejawna konwersja nie jest zdefiniowana z typu źródłowego na typ docelowy. Jest to tzw. *Konwersja na wąskie*. Jawny przypadek jest wymagany, ponieważ konwersja może spowodować utratę danych.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Typy całkowite](~/_csharplang/spec/types.md#integral-types)
- [Literały całkowite](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Typy zmiennoprzecinkowe](floating-point-numeric-types.md)
- [Tabela wartości domyślnych](../keywords/default-values-table.md)
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Tabela typów wbudowanych](../keywords/built-in-types-table.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
