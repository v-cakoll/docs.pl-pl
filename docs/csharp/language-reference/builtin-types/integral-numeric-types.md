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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236073"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="33f6e-103">Całkowite typy liczbowe (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="33f6e-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="33f6e-104">**Całkowite typy liczbowe** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="33f6e-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="33f6e-105">Wszystkie typy zintegrowane są również typy wartości.</span><span class="sxs-lookup"><span data-stu-id="33f6e-105">All integral types are also value types.</span></span> <span data-ttu-id="33f6e-106">Całkowite typy liczbowe obsługuje [arytmetyczne](../operators/arithmetic-operators.md), [bitowe logicznej](../operators/bitwise-and-shift-operators.md), [porównania i równości](../operators/equality-operators.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="33f6e-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="33f6e-107">Właściwości typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="33f6e-107">Characteristics of the integral types</span></span>

<span data-ttu-id="33f6e-108">C#obsługuje następujące wstępnie zdefiniowanych typów całkowitych:</span><span class="sxs-lookup"><span data-stu-id="33f6e-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="33f6e-109">C#Wpisz/słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="33f6e-109">C# type/keyword</span></span>|<span data-ttu-id="33f6e-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="33f6e-110">Range</span></span>|<span data-ttu-id="33f6e-111">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="33f6e-111">Size</span></span>|<span data-ttu-id="33f6e-112">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="33f6e-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="33f6e-113">-128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="33f6e-113">-128 to 127</span></span>|<span data-ttu-id="33f6e-114">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="33f6e-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="33f6e-115">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="33f6e-115">0 to 255</span></span>|<span data-ttu-id="33f6e-116">Liczba całkowita bez znaku 8-bitowa</span><span class="sxs-lookup"><span data-stu-id="33f6e-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="33f6e-117">-32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="33f6e-117">-32,768 to 32,767</span></span>|<span data-ttu-id="33f6e-118">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="33f6e-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="33f6e-119">0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="33f6e-119">0 to 65,535</span></span>|<span data-ttu-id="33f6e-120">Liczba całkowita bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="33f6e-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="33f6e-121">-2 147 483 2 147 483 648 do 647</span><span class="sxs-lookup"><span data-stu-id="33f6e-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="33f6e-122">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="33f6e-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="33f6e-123">4 294 967 0 Aby 295</span><span class="sxs-lookup"><span data-stu-id="33f6e-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="33f6e-124">Liczba całkowita bez znaku 32-bitowy</span><span class="sxs-lookup"><span data-stu-id="33f6e-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="33f6e-125">-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="33f6e-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="33f6e-126">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="33f6e-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="33f6e-127">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="33f6e-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="33f6e-128">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="33f6e-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="33f6e-129">W powyższej tabeli każdego C# wpisz słowo kluczowe z lewej strony kolumny jest aliasem dla danego typu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="33f6e-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="33f6e-130">Są one wymienne.</span><span class="sxs-lookup"><span data-stu-id="33f6e-130">They are interchangeable.</span></span> <span data-ttu-id="33f6e-131">Na przykład następujące deklaracje deklarowanie zmiennych tego samego typu:</span><span class="sxs-lookup"><span data-stu-id="33f6e-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="33f6e-132">Wartością domyślną każdego typu całkowitego wynosi zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="33f6e-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="33f6e-133">Każdy z typów całkowitych ma `MinValue` i `MaxValue` stałe, które zapewniają minimalną i maksymalną wartość tego typu.</span><span class="sxs-lookup"><span data-stu-id="33f6e-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="33f6e-134">Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania liczby całkowitej ze znakiem z nie górnego lub dolne granice.</span><span class="sxs-lookup"><span data-stu-id="33f6e-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="33f6e-135">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="33f6e-135">Integral literals</span></span>

<span data-ttu-id="33f6e-136">Literały całkowite może być określony jako *dziesiętna literały*, *literały szesnastkowe*, lub *literały binarne*.</span><span class="sxs-lookup"><span data-stu-id="33f6e-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="33f6e-137">Poniżej przedstawiono przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="33f6e-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="33f6e-138">Literały dziesiętną nie wymagają dowolnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="33f6e-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="33f6e-139">`x` Lub `X` oznacza prefiks *szesnastkowy literał*.</span><span class="sxs-lookup"><span data-stu-id="33f6e-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="33f6e-140">`b` Lub `B` oznacza prefiks *pliku binarnego literału*.</span><span class="sxs-lookup"><span data-stu-id="33f6e-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="33f6e-141">Deklaracja `binaryLiteral` demonstruje użycie `_` jako *separator cyfr*.</span><span class="sxs-lookup"><span data-stu-id="33f6e-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="33f6e-142">Separator cyfr może służyć za pomocą wszystkich literałach numerycznych.</span><span class="sxs-lookup"><span data-stu-id="33f6e-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="33f6e-143">Literały binarne oraz separator cyfr `_` są obsługiwane, począwszy od C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="33f6e-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="33f6e-144">Sufiksów literałów</span><span class="sxs-lookup"><span data-stu-id="33f6e-144">Literal suffixes</span></span>

<span data-ttu-id="33f6e-145">`l` Lub `L` sufiks Określa, że powinien być typu całkowitego literał `long` typu.</span><span class="sxs-lookup"><span data-stu-id="33f6e-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="33f6e-146">`ul` Lub `UL` Określa sufiks `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="33f6e-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="33f6e-147">Jeśli `L` sufiks jest używany na literał, która jest większa niż 9,223,372,036,854,775,807 (maksymalna wartość `long`), wartość jest konwertowana na `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="33f6e-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="33f6e-148">Jeśli wartości w postaci literału typu całkowitego przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, błąd kompilatora [CS1021](../../misc/cs1021.md) występuje.</span><span class="sxs-lookup"><span data-stu-id="33f6e-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="33f6e-149">Mała litera "l" można użyć jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="33f6e-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="33f6e-150">Jednakże spowoduje to wygenerowanie ostrzeżenia kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1".</span><span class="sxs-lookup"><span data-stu-id="33f6e-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="33f6e-151">Użyj "L" w celu uściślenia.</span><span class="sxs-lookup"><span data-stu-id="33f6e-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="33f6e-152">Typ literału typu całkowitego</span><span class="sxs-lookup"><span data-stu-id="33f6e-152">Type of an integral literal</span></span>

<span data-ttu-id="33f6e-153">Jeśli literał całkowity brak przyrostka, jego typ jest pierwszy następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="33f6e-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="33f6e-154">Literał typu całkowitego można konwertować na typ o mniejszym zakresie niż domyślny, za pomocą przydziałów i rzutowania:</span><span class="sxs-lookup"><span data-stu-id="33f6e-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="33f6e-155">Literał typu całkowitego można konwertować na typ o większym zakresie niż domyślne przy użyciu przypisania, rzutowania lub sufiksu na literału:</span><span class="sxs-lookup"><span data-stu-id="33f6e-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="33f6e-156">Konwersje</span><span class="sxs-lookup"><span data-stu-id="33f6e-156">Conversions</span></span>

<span data-ttu-id="33f6e-157">Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) między dwoma typami całkowitego gdzie docelowy typ można przechowywać wszystkie wartości typu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="33f6e-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="33f6e-158">Na przykład istnieje niejawna konwersja z `int` do `long` ponieważ zakres `int` wartości jest podzestawem odpowiednie `long`.</span><span class="sxs-lookup"><span data-stu-id="33f6e-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="33f6e-159">Ma niejawne konwersje z elementu mniejszy typ bez znaku typu całkowitego na większych typ całkowity ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="33f6e-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="33f6e-160">Istnieje również niejawna konwersja z dowolnego typu całkowitoliczbowego do dowolnego typu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="33f6e-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="33f6e-161">Istnieje niejawna konwersja z dowolnym typ całkowity ze znakiem do dowolnego typu całkowitoliczbowego bez znaku.</span><span class="sxs-lookup"><span data-stu-id="33f6e-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="33f6e-162">Aby przekonwertować co typ całkowity innego typu całkowitego, gdy niejawna konwersja nie jest zdefiniowany z typu źródłowego na typ docelowy należy użyć jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="33f6e-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="33f6e-163">Jest to nazywane *konwersja zawężająca*.</span><span class="sxs-lookup"><span data-stu-id="33f6e-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="33f6e-164">Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="33f6e-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="33f6e-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f6e-165">See also</span></span>

- [<span data-ttu-id="33f6e-166">C#Specyfikacja języka — typy całkowite</span><span class="sxs-lookup"><span data-stu-id="33f6e-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="33f6e-167">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="33f6e-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="33f6e-168">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="33f6e-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="33f6e-169">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="33f6e-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="33f6e-170">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="33f6e-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="33f6e-171">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="33f6e-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="33f6e-172">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="33f6e-172">Numerics in .NET</span></span>](../../../standard/numerics.md)
