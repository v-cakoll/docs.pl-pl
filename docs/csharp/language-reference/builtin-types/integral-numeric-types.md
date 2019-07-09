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
ms.openlocfilehash: 141475c4d92278be02d6a832a93cd8553a4bcbd8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661136"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="59bd0-103">Całkowite typy liczbowe (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="59bd0-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="59bd0-104">**Całkowite typy liczbowe** stanowią podzestaw **typów prostych** i mogą być zainicjowane z [ *literały*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="59bd0-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="59bd0-105">Wszystkie typy zintegrowane są również typy wartości.</span><span class="sxs-lookup"><span data-stu-id="59bd0-105">All integral types are also value types.</span></span>

<span data-ttu-id="59bd0-106">Całkowite typy liczbowe obsługuje [arytmetyczne](../operators/arithmetic-operators.md), [bitowe logicznej](../operators/bitwise-and-shift-operators.md), [porównania i równości](../operators/equality-operators.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="59bd0-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="sizes-and-ranges"></a><span data-ttu-id="59bd0-107">Rozmiary i zakresy</span><span class="sxs-lookup"><span data-stu-id="59bd0-107">Sizes and ranges</span></span>

<span data-ttu-id="59bd0-108">W poniższej tabeli przedstawiono rozmiary i zakresy typów całkowitych:</span><span class="sxs-lookup"><span data-stu-id="59bd0-108">The following table shows the sizes and ranges of the integral types:</span></span>

|<span data-ttu-id="59bd0-109">Typ</span><span class="sxs-lookup"><span data-stu-id="59bd0-109">Type</span></span>|<span data-ttu-id="59bd0-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="59bd0-110">Range</span></span>|<span data-ttu-id="59bd0-111">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="59bd0-111">Size</span></span>|  
|----------|-----------|----------|  
|`sbyte`|<span data-ttu-id="59bd0-112">-128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="59bd0-112">-128 to 127</span></span>|<span data-ttu-id="59bd0-113">8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="59bd0-113">Signed 8-bit integer</span></span>|  
|`byte`|<span data-ttu-id="59bd0-114">od 0 do 255</span><span class="sxs-lookup"><span data-stu-id="59bd0-114">0 to 255</span></span>|<span data-ttu-id="59bd0-115">Liczba całkowita bez znaku 8-bitowa</span><span class="sxs-lookup"><span data-stu-id="59bd0-115">Unsigned 8-bit integer</span></span>|  
|`short`|<span data-ttu-id="59bd0-116">-32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="59bd0-116">-32,768 to 32,767</span></span>|<span data-ttu-id="59bd0-117">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="59bd0-117">Signed 16-bit integer</span></span>|  
|`ushort`|<span data-ttu-id="59bd0-118">0 do 65 535.</span><span class="sxs-lookup"><span data-stu-id="59bd0-118">0 to 65,535</span></span>|<span data-ttu-id="59bd0-119">Liczba całkowita bez znaku 16-bitowych</span><span class="sxs-lookup"><span data-stu-id="59bd0-119">Unsigned 16-bit integer</span></span>|  
|`int`|<span data-ttu-id="59bd0-120">-2 147 483 2 147 483 648 do 647</span><span class="sxs-lookup"><span data-stu-id="59bd0-120">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="59bd0-121">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="59bd0-121">Signed 32-bit integer</span></span>|  
|`uint`|<span data-ttu-id="59bd0-122">4 294 967 0 Aby 295</span><span class="sxs-lookup"><span data-stu-id="59bd0-122">0 to 4,294,967,295</span></span>|<span data-ttu-id="59bd0-123">Liczba całkowita bez znaku 32-bitowy</span><span class="sxs-lookup"><span data-stu-id="59bd0-123">Unsigned 32-bit integer</span></span>|  
|`long`|<span data-ttu-id="59bd0-124">-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="59bd0-124">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="59bd0-125">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="59bd0-125">Signed 64-bit integer</span></span>|  
|`ulong`|<span data-ttu-id="59bd0-126">0 — 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="59bd0-126">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="59bd0-127">Liczba całkowita bez znaku 64-bitowych</span><span class="sxs-lookup"><span data-stu-id="59bd0-127">Unsigned 64-bit integer</span></span>|  

<span data-ttu-id="59bd0-128">Jest wartością domyślną dla wszystkich typów całkowitych `0`.</span><span class="sxs-lookup"><span data-stu-id="59bd0-128">The default value for all integral types is `0`.</span></span> <span data-ttu-id="59bd0-129">Każdy z typów całkowitych ma nazwanych stałych `MinValue` i `MaxValue` minimalne i maksymalne wartości dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="59bd0-129">Each of the integral types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span>

<span data-ttu-id="59bd0-130">Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> struktury do reprezentowania liczby całkowitej ze znakiem z nie górnego lub dolne granice.</span><span class="sxs-lookup"><span data-stu-id="59bd0-130">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="59bd0-131">Literały całkowite</span><span class="sxs-lookup"><span data-stu-id="59bd0-131">Integral literals</span></span>

<span data-ttu-id="59bd0-132">Literały całkowite może być określony jako *dziesiętna literały*, *literały szesnastkowe*, lub *literały binarne*.</span><span class="sxs-lookup"><span data-stu-id="59bd0-132">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="59bd0-133">Poniżej przedstawiono przykład każdego z nich:</span><span class="sxs-lookup"><span data-stu-id="59bd0-133">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="59bd0-134">Literały dziesiętną nie wymagają dowolnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="59bd0-134">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="59bd0-135">`x` Lub `X` oznacza prefiks *szesnastkowy literał*.</span><span class="sxs-lookup"><span data-stu-id="59bd0-135">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="59bd0-136">`b` Lub `B` oznacza prefiks *pliku binarnego literału*.</span><span class="sxs-lookup"><span data-stu-id="59bd0-136">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="59bd0-137">Deklaracja `binaryLiteral` demonstruje użycie `_` jako *separator cyfr*.</span><span class="sxs-lookup"><span data-stu-id="59bd0-137">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="59bd0-138">Separator cyfr może służyć za pomocą wszystkich literałach numerycznych.</span><span class="sxs-lookup"><span data-stu-id="59bd0-138">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="59bd0-139">Literały binarne oraz separator cyfr `_` są obsługiwane, począwszy od C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="59bd0-139">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

## <a name="literal-suffixes"></a><span data-ttu-id="59bd0-140">Sufiksów literałów</span><span class="sxs-lookup"><span data-stu-id="59bd0-140">Literal suffixes</span></span> 

<span data-ttu-id="59bd0-141">`l` Lub `L` sufiks Określa, że powinien być typu całkowitego literał `long` typu.</span><span class="sxs-lookup"><span data-stu-id="59bd0-141">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="59bd0-142">`ul` Lub `UL` Określa sufiks `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="59bd0-142">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="59bd0-143">Jeśli `L` sufiks jest używany na literał, która jest większa niż 9,223,372,036,854,775,807 (maksymalna wartość `long`), wartość jest konwertowana na `ulong` typu.</span><span class="sxs-lookup"><span data-stu-id="59bd0-143">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="59bd0-144">Jeśli wartości w postaci literału typu integer przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, błąd kompilatora [CS1021](../../misc/cs1021.md) występuje.</span><span class="sxs-lookup"><span data-stu-id="59bd0-144">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="59bd0-145">Mała litera "l" można użyć jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="59bd0-145">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="59bd0-146">Jednakże spowoduje to wygenerowanie ostrzeżenia kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1".</span><span class="sxs-lookup"><span data-stu-id="59bd0-146">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="59bd0-147">Użyj "L" w celu uściślenia.</span><span class="sxs-lookup"><span data-stu-id="59bd0-147">Use "L" for clarity.</span></span>

## <a name="type-of-an-integral-literal"></a><span data-ttu-id="59bd0-148">Typ literału typu całkowitego</span><span class="sxs-lookup"><span data-stu-id="59bd0-148">Type of an integral literal</span></span>

<span data-ttu-id="59bd0-149">Jeśli literał całkowity brak przyrostka, jego typ jest pierwszy następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="59bd0-149">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="59bd0-150">Literał typu całkowitego można konwertować na typ o mniejszym zakresie niż domyślny, za pomocą przydziałów i rzutowania:</span><span class="sxs-lookup"><span data-stu-id="59bd0-150">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="59bd0-151">Literał typu całkowitego można konwertować na typ o większym zakresie niż domyślne przy użyciu przypisania, rzutowania lub sufiksu na literału:</span><span class="sxs-lookup"><span data-stu-id="59bd0-151">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="59bd0-152">Konwersje</span><span class="sxs-lookup"><span data-stu-id="59bd0-152">Conversions</span></span>

<span data-ttu-id="59bd0-153">Istnieje niejawna konwersja (o nazwie *poszerzenie konwersji*) między dwoma typami całkowitego gdzie docelowy typ można przechowywać wszystkie wartości typu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="59bd0-153">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="59bd0-154">Na przykład istnieje niejawna konwersja z `int` do `long` ponieważ zakres `int` wartości jest podzestawem odpowiednie `long`.</span><span class="sxs-lookup"><span data-stu-id="59bd0-154">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="59bd0-155">Ma niejawne konwersje z elementu mniejszy typ bez znaku typu całkowitego na większych typ całkowity ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="59bd0-155">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="59bd0-156">Istnieje również niejawna konwersja z dowolnego typu całkowitoliczbowego do dowolnego typu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="59bd0-156">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="59bd0-157">Istnieje niejawna konwersja z dowolnym typ całkowity ze znakiem do dowolnego typu całkowitoliczbowego bez znaku.</span><span class="sxs-lookup"><span data-stu-id="59bd0-157">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="59bd0-158">Aby przekonwertować co typ całkowity innego typu całkowitego, gdy niejawna konwersja nie jest zdefiniowany z typu źródłowego na typ docelowy należy użyć jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="59bd0-158">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="59bd0-159">Jest to nazywane *konwersja zawężająca*.</span><span class="sxs-lookup"><span data-stu-id="59bd0-159">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="59bd0-160">Jawne przypadek jest wymagana, ponieważ konwersja może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="59bd0-160">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="59bd0-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59bd0-161">See also</span></span>

- [<span data-ttu-id="59bd0-162">C#Specyfikacja języka — typy całkowite</span><span class="sxs-lookup"><span data-stu-id="59bd0-162">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="59bd0-163">C#Odwołanie</span><span class="sxs-lookup"><span data-stu-id="59bd0-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="59bd0-164">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="59bd0-164">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="59bd0-165">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="59bd0-165">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="59bd0-166">Formatowanie tabeli wyników liczbowych</span><span class="sxs-lookup"><span data-stu-id="59bd0-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="59bd0-167">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="59bd0-167">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="59bd0-168">Wartości numeryczne na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="59bd0-168">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
