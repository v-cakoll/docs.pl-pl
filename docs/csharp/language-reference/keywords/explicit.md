---
title: Explicit — słowo kluczowe (odwołanie w C#)
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 3567a2c5aa549aa3141ed59c3e93e7b07975da70
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525464"
---
# <a name="explicit-c-reference"></a><span data-ttu-id="15e50-102">explicit (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="15e50-102">explicit (C# Reference)</span></span>

<span data-ttu-id="15e50-103">`explicit` — Słowo kluczowe deklaruje operator konwersji typu zdefiniowanego przez użytkownika, który musi być wywołana z rzutowania.</span><span class="sxs-lookup"><span data-stu-id="15e50-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span>

<span data-ttu-id="15e50-104">W poniższym przykładzie zdefiniowano operator, który konwertuje `Fahrenheit` klasy `Celsius` klasy.</span><span class="sxs-lookup"><span data-stu-id="15e50-104">The following example defines the operator that converts from a `Fahrenheit` class to a `Celsius` class.</span></span> <span data-ttu-id="15e50-105">Operator musi być zdefiniowana wewnątrz `Fahrenheit` klasy lub `Celsius` klasy:</span><span class="sxs-lookup"><span data-stu-id="15e50-105">The operator must be defined either inside a `Fahrenheit` class or a `Celsius` class:</span></span>

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

<span data-ttu-id="15e50-106">Operator konwersji zdefiniowanej przy użyciu rzutowania, wywołuje się, jak w poniższym przykładzie pokazano:</span><span class="sxs-lookup"><span data-stu-id="15e50-106">You invoke the defined conversion operator with a cast, as the following example shows:</span></span>

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

<span data-ttu-id="15e50-107">Operator konwersji konwertuje typu źródłowego na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="15e50-107">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="15e50-108">Typ źródłowy zawiera operator konwersji.</span><span class="sxs-lookup"><span data-stu-id="15e50-108">The source type provides the conversion operator.</span></span> <span data-ttu-id="15e50-109">W odróżnieniu od niejawnej konwersji operatory konwersji jawnej musi wywołać poprzez rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="15e50-109">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="15e50-110">Jeśli operacji konwersji może spowodować, że wyjątki lub utratę informacji, należy go oznaczyć `explicit`.</span><span class="sxs-lookup"><span data-stu-id="15e50-110">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="15e50-111">Zapobiega to dyskretnie wywoływanie operacji konwersji z prawdopodobnie nieprzewidziane skutki przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="15e50-111">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>

<span data-ttu-id="15e50-112">Pominięcie rzutowania spowoduje błąd kompilacji CS0266.</span><span class="sxs-lookup"><span data-stu-id="15e50-112">Omitting the cast results in compile-time error CS0266.</span></span>

<span data-ttu-id="15e50-113">Aby uzyskać więcej informacji, zobacz [Używanie operatorów konwersji](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="15e50-113">For more information, see [Using Conversion Operators](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="example"></a><span data-ttu-id="15e50-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="15e50-114">Example</span></span>

<span data-ttu-id="15e50-115">W poniższym przykładzie przedstawiono `Fahrenheit` i `Celsius` klasy, z których każdy zawiera operator jawnej konwersji do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="15e50-115">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a><span data-ttu-id="15e50-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="15e50-116">Example</span></span>

<span data-ttu-id="15e50-117">W poniższym przykładzie zdefiniowano struktury, `Digit`, który reprezentuje pojedynczą cyfrą dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="15e50-117">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="15e50-118">Operator jest zdefiniowany dla konwersji z `byte` do `Digit`, ale ponieważ nie wszystkie wartości bajtowe mogą być konwertowane na `Digit`, konwersja jest jawne.</span><span class="sxs-lookup"><span data-stu-id="15e50-118">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="15e50-119">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15e50-119">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="15e50-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15e50-120">See also</span></span>

- [<span data-ttu-id="15e50-121">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15e50-121">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="15e50-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="15e50-122">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="15e50-123">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="15e50-123">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="15e50-124">implicit</span><span class="sxs-lookup"><span data-stu-id="15e50-124">implicit</span></span>](implicit.md)  
- [<span data-ttu-id="15e50-125">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="15e50-125">operator (C# Reference)</span></span>](operator.md)  
- [<span data-ttu-id="15e50-126">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="15e50-126">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
- [<span data-ttu-id="15e50-127">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="15e50-127">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  
