---
title: "explicit (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords: explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2661f46d79b13808bfb169bfbfffc1a17b866b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-c-reference"></a><span data-ttu-id="f6046-102">explicit (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6046-102">explicit (C# Reference)</span></span>
<span data-ttu-id="f6046-103">`explicit` — Słowo kluczowe deklaruje typ zdefiniowany przez użytkownika operatora konwersji, które muszą być wywoływane z rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="f6046-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="f6046-104">Na przykład tego operatora konwertuje z klasy o nazwie f do klasy o nazwie c:</span><span class="sxs-lookup"><span data-stu-id="f6046-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 <span data-ttu-id="f6046-105">Można wywołać tego operatora konwersji następująco:</span><span class="sxs-lookup"><span data-stu-id="f6046-105">This conversion operator can be invoked like this:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 <span data-ttu-id="f6046-106">Operator konwersji konwertuje typu źródłowego na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="f6046-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="f6046-107">Typ źródłowy zawiera operator konwersji.</span><span class="sxs-lookup"><span data-stu-id="f6046-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="f6046-108">W odróżnieniu od niejawna konwersja operatory jawnej konwersji muszą być wywoływane za pomocą rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="f6046-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="f6046-109">Jeśli operacja konwersji może spowodować wyjątków lub utratę informacji, należy oznaczyć go `explicit`.</span><span class="sxs-lookup"><span data-stu-id="f6046-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="f6046-110">Zapobiega to dyskretnie wywoływania operacji konwersji z prawdopodobnie nieprzewidziane skutki przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f6046-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="f6046-111">Pominięcie rzutowania spowoduje błąd kompilacji CS0266.</span><span class="sxs-lookup"><span data-stu-id="f6046-111">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="f6046-112">Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f6046-112">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6046-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6046-113">Example</span></span>  
 <span data-ttu-id="f6046-114">W poniższym przykładzie przedstawiono `Fahrenheit` i `Celsius` klasy, z których każdy zawiera operator jawnej konwersji do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="f6046-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f6046-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6046-115">Example</span></span>  
 <span data-ttu-id="f6046-116">W poniższym przykładzie zdefiniowano strukturę, `Digit`, który reprezentuje pojedynczą cyfrą dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="f6046-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="f6046-117">Operator jest zdefiniowany dla konwersji z `byte` do `Digit`, ale ponieważ nie wszystkie bajty można przekonwertować na `Digit`, konwersja jest jawne.</span><span class="sxs-lookup"><span data-stu-id="f6046-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f6046-118">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f6046-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6046-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6046-119">See Also</span></span>  
 [<span data-ttu-id="f6046-120">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f6046-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f6046-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6046-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6046-122">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f6046-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f6046-123">niejawne</span><span class="sxs-lookup"><span data-stu-id="f6046-123">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="f6046-124">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6046-124">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="f6046-125">Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="f6046-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [<span data-ttu-id="f6046-126">Tworzenie łańcucha zdefiniowane przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6046-126">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)
