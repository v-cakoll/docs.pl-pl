---
title: Integralne typy liczbowe — odwołanie do języka C#
description: Poznaj zakres, rozmiar magazynu i zastosowania dla każdego z całkowitych typów liczbowych.
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
ms.openlocfilehash: 51ea64065ea8422e5885022105545780bc916f06
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739006"
---
# <a name="integral-numeric-types--c-reference"></a>Integralne typy liczbowe (odwołanie do języka C#)

*Integralne typy liczbowe* reprezentują liczby całkowite. Wszystkie integralne typy liczbowe są [typami wartości](value-types.md). Są to również [proste typy](value-types.md#built-in-value-types) i mogą być inicjowane za pomocą [literałów](#integer-literals). Wszystkie integralne typy liczbowe obsługują [operatory arytmetyczne,](../operators/arithmetic-operators.md) [logiczne bitowe,](../operators/bitwise-and-shift-operators.md) [porównanie](../operators/comparison-operators.md)i [równości.](../operators/equality-operators.md)

## <a name="characteristics-of-the-integral-types"></a>Charakterystyka typów całkowitych

C# obsługuje następujące wstępnie zdefiniowane typy całek:

|Typ/słowo kluczowe C#|Zakres|Rozmiar|Typ .NET|
|----------|-----------|----------|-------------|
|`sbyte`|od -128 do 127|Podpisana 8-bitowa 8-bitowa czkawce|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|od 0 do 255|Niepodpisana 8-bitowa 8-bitowa czkawce|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|od -32 768 do 32 767|Podpisana 16-bitowa 10-bitowa 100 000 całkowita|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|od 0 do 65 535|Niepodpisana 16-bitowa 10-bitowa 100 000 całkowita|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648 do 2.147.483.647|Podpisana 32-bitowa całkowita 20da|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|od 0 do 4 294 967 295|Niepodpisana 32-bitowa 32-bitowa gnilizna|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9.223.372.036.854.775.808 do 9.223.372.036.854.775.807|Podpisana 64-bitowa całkowita rzeszj|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|od 0 do 18.446.744.073.709.551.615|Niepodpisana 64-bitowa 60-bitowa ćwięk|<xref:System.UInt64?displayProperty=nameWithType>|

W poprzedniej tabeli każde słowo kluczowe typu C# z lewej kolumny jest aliasem dla odpowiedniego typu .NET. Są wymienne. Na przykład następujące deklaracje deklarują zmienne tego samego typu:

```csharp
int a = 123;
System.Int32 b = 123;
```

Domyślną wartością każdego typu `0`całkowitego jest zero, . Każdy z typów całkowitych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.

Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania podpisanej liczby całkowitej bez górnej lub dolnej granicy.

## <a name="integer-literals"></a>Literały liczby całkowitej

Literały całkowite można

- *dziesiętne:* bez prefiksu
- *szesnastkowe:* `0X` z prefiksem lub prefiksem `0x`
- *binary*: `0b` z `0B` prefiksem lub (dostępnym w języku C# 7.0 i nowszym)

Poniższy kod pokazuje przykład każdego z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

W poprzednim przykładzie pokazano `_` również użycie jako *separator cyfry*, który jest obsługiwany począwszy od C# 7.0. Separatora cyfr można używać z wszelkiego rodzaju literałami liczbowymi.

Typ literału liczby całkowitej jest określany przez jego sufiks w następujący sposób:

- Jeśli literał nie ma sufiksu, jego typ jest pierwszym z następujących `int`typów, w których jego wartość może być reprezentowana: , `uint`, `long`, `ulong`.
- `U` Jeśli literał jest sufiksem przez lub `u`, jego typ jest pierwszym z następujących `uint` `ulong`typów, w których jego wartość może być reprezentowana: , .
- `L` Jeśli literał jest sufiksem przez lub `l`, jego typ jest pierwszym z następujących `long` `ulong`typów, w których jego wartość może być reprezentowana: , .

  > [!NOTE]
  > Można użyć litery małych `l` jako sufiksu. Jednak to generuje ostrzeżenie kompilatora, ponieważ `l` literę `1`można pomylić z cyfrą . Użyj `L` dla jasności.

- Jeśli literał jest sufiksem `uL` `ul`przez `LU` `UL` `Ul`, `lU`, `lu`, , `ulong` `Lu`, , lub , jego typ jest .

Jeśli wartość reprezentowana przez litera liczba <xref:System.UInt64.MaxValue?displayProperty=nameWithType>całkowita przekracza , występuje błąd kompilatora [CS1021.](../../misc/cs1021.md)

Jeśli określony typ literału całkowitej `int` jest i wartość reprezentowana przez literał znajduje się w zakresie typu docelowego, wartość może być niejawnie konwertowane na `sbyte`, `byte` `short`, , `ushort`, `uint`, lub `ulong`:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Jak pokazano w poprzednim przykładzie, jeśli wartość literału nie mieści się w zakresie typu docelowego, występuje błąd kompilatora [CS0031.](../../misc/cs0031.md)

Można również użyć rzutowania do konwersji wartości reprezentowanej przez literał liczby całkowitej na typ inny niż określony typ literału:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Konwersje

Można przekonwertować dowolny całkowity typ liczbowy na dowolny inny integralny typ liczbowy. Jeśli typ docelowy może przechowywać wszystkie wartości typu źródła, konwersja jest niejawna. W przeciwnym razie należy użyć [wyrażenia rzutowego](../operators/type-testing-and-cast.md#cast-expression) do wykonania konwersji jawnej. Aby uzyskać więcej informacji, zobacz [Wbudowane konwersje numeryczne](numeric-conversions.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Typy integralne](~/_csharplang/spec/types.md#integral-types)
- [Literały liczby całkowitej](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Typy wartości](value-types.md)
- [Typy zmiennoprzecinowe](floating-point-numeric-types.md)
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
