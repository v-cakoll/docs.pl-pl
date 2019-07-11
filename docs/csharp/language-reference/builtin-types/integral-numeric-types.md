---
title: Całkowite typy liczbowe - C# odwołania
description: Dowiedz się, rozmiar magazynu, po czym używa dla każdego całkowite typy liczbowe.
ms.date: 06/25/2019
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
ms.openlocfilehash: 0a1ed01d9e6cb86ea177e8b947627f9dc02eedae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744215"
---
# <a name="integral-numeric-types--c-reference"></a>Całkowite typy liczbowe (C# odwołania)

**Całkowite typy liczbowe** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#integral-literals). Wszystkie typy zintegrowane są również typy wartości.

Całkowite typy liczbowe obsługuje [arytmetyczne](../operators/arithmetic-operators.md), [bitowe logicznej](../operators/bitwise-and-shift-operators.md), [porównania i równości](../operators/equality-operators.md) operatorów.

## <a name="sizes-and-ranges"></a>Rozmiary i zakresy

W poniższej tabeli przedstawiono rozmiary i zakresy typów całkowitych:

|Typ|Zakres|Rozmiar|  
|----------|-----------|----------|  
|`sbyte`|-128 do 127 znaków.|8-bitową liczbę całkowitą ze znakiem|  
|`byte`|od 0 do 255|Liczba całkowita bez znaku 8-bitowa|  
|`short`|-32768 do 32767.|16-bitową liczbę całkowitą ze znakiem|  
|`ushort`|0 do 65 535.|Liczba całkowita bez znaku 16-bitowych|  
|`int`|-2 147 483 2 147 483 648 do 647|32-bitowa liczba całkowita ze znakiem|  
|`uint`|4 294 967 0 Aby 295|Liczba całkowita bez znaku 32-bitowy|  
|`long`|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|64-bitowa liczba całkowita ze znakiem|  
|`ulong`|0 — 18,446,744,073,709,551,615|Liczba całkowita bez znaku 64-bitowych|  

Jest wartością domyślną dla wszystkich typów całkowitych `0`. Każdy z typów całkowitych ma nazwanych stałych `MinValue` i `MaxValue` minimalne i maksymalne wartości dla tego typu.

Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania liczby całkowitej ze znakiem z nie górnego lub dolne granice.

## <a name="integral-literals"></a>Literały całkowite

Literały całkowite może być określony jako *dziesiętna literały*, *literały szesnastkowe*, lub *literały binarne*. Poniżej przedstawiono przykład każdego z nich:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Literały dziesiętną nie wymagają dowolnego prefiksu. `x` Lub `X` oznacza prefiks *szesnastkowy literał*. `b` Lub `B` oznacza prefiks *pliku binarnego literału*. Deklaracja `binaryLiteral` demonstruje użycie `_` jako *separator cyfr*. Separator cyfr może służyć za pomocą wszystkich literałach numerycznych. Literały binarne oraz separator cyfr `_` są obsługiwane, począwszy od C# 7.0.

### <a name="literal-suffixes"></a>Sufiksów literałów 

`l` Lub `L` sufiks Określa, że powinien być typu całkowitego literał `long` typu. `ul` Lub `UL` Określa sufiks `ulong` typu. Jeśli `L` sufiks jest używany na literał, która jest większa niż 9,223,372,036,854,775,807 (maksymalna wartość `long`), wartość jest konwertowana na `ulong` typu. Jeśli wartości w postaci literału typu całkowitego przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, błąd kompilatora [CS1021](../../misc/cs1021.md) występuje. 

> [!NOTE]
> Mała litera "l" można użyć jako sufiks. Jednakże spowoduje to wygenerowanie ostrzeżenia kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1". Użyj "L" w celu uściślenia.

### <a name="type-of-an-integral-literal"></a>Typ literału typu całkowitego

Jeśli literał całkowity brak przyrostka, jego typ jest pierwszy następujące typy, w których jej wartość może być reprezentowana:

1. `int`
1. `uint`
1. `long`
1. `ulong`

Literał typu całkowitego można konwertować na typ o mniejszym zakresie niż domyślny, za pomocą przydziałów i rzutowania:

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

Literał typu całkowitego można konwertować na typ o większym zakresie niż domyślne przy użyciu przypisania, rzutowania lub sufiksu na literału:

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>Konwersje

Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) między dwoma typami całkowitego gdzie docelowy typ można przechowywać wszystkie wartości typu źródłowego. Na przykład istnieje niejawna konwersja z `int` do `long` ponieważ zakres `int` wartości jest podzestawem odpowiednie `long`. Ma niejawne konwersje z elementu mniejszy typ bez znaku typu całkowitego na większych typ całkowity ze znakiem. Istnieje również niejawna konwersja z dowolnego typu całkowitoliczbowego do dowolnego typu zmiennoprzecinkowego.  Istnieje niejawna konwersja z dowolnym typ całkowity ze znakiem do dowolnego typu całkowitoliczbowego bez znaku.

Aby przekonwertować co typ całkowity innego typu całkowitego, gdy niejawna konwersja nie jest zdefiniowany z typu źródłowego na typ docelowy należy użyć jawnego rzutowania. Jest to nazywane *konwersja zawężająca*. Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych.

## <a name="see-also"></a>Zobacz także

- [C#Specyfikacja języka — typy całkowite](~/_csharplang/spec/types.md#integral-types)
- [C#Odwołanie](../index.md)
- [Typy zmiennoprzecinkowe](floating-point-numeric-types.md)
- [Tabela wartości domyślnych](../keywords/default-values-table.md)
- [Formatowanie tabeli wyników liczbowych](../keywords/formatting-numeric-results-table.md)
- [Tabela typów wbudowanych](../keywords/built-in-types-table.md)
- [Wartości numeryczne na platformie .NET](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
