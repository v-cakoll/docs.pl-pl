---
title: ?? Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 153accdc4995065563b00da0fd62992341c06cf1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241882"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0b689-103">??</span><span class="sxs-lookup"><span data-stu-id="0b689-103">??</span></span> <span data-ttu-id="0b689-104">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0b689-104">Operator (C# Reference)</span></span>
<span data-ttu-id="0b689-105">`??` Operator jest nazywany operatorem łączenia wartości null.</span><span class="sxs-lookup"><span data-stu-id="0b689-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="0b689-106">Zwraca argument operacji z lewej strony, jeśli ma on wartość inną niż null; w przeciwnym razie zwraca argument operacji po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0b689-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b689-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b689-107">Remarks</span></span>  
 <span data-ttu-id="0b689-108">Typ dopuszczający wartość null może reprezentować wartość z domeny typu albo wartość może być niezdefiniowana (w tym przypadku wartość jest równa null).</span><span class="sxs-lookup"><span data-stu-id="0b689-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="0b689-109">Możesz użyć `??` wyrazistość składni operatora zwracać odpowiednią wartość (argument operacji po prawej stronie) kiedy Lewy argument operacji ma typ dopuszczający wartość null, którego wartość jest równa null.</span><span class="sxs-lookup"><span data-stu-id="0b689-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="0b689-110">Jeśli użytkownik próbuje przypisać typem wartościowym z typem wartości niedopuszczającym wartości bez korzystania z `??` operatora, spowoduje wygenerowanie błędu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0b689-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="0b689-111">Jeśli używane rzutowanie, a typem wartościowym jest obecnie zdefiniowany `InvalidOperationException` zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0b689-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="0b689-112">Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b689-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="0b689-113">Wynik?</span><span class="sxs-lookup"><span data-stu-id="0b689-113">The result of a ??</span></span> <span data-ttu-id="0b689-114">operator nie uznaje się za stałą, nawet jeśli oba argumenty są stałymi.</span><span class="sxs-lookup"><span data-stu-id="0b689-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b689-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b689-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0b689-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0b689-116">C# Language Specification</span></span>  

<span data-ttu-id="0b689-117">Aby uzyskać więcej informacji, zobacz [null operatora łączącego](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b689-117">For more information, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="0b689-118">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="0b689-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b689-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b689-119">See Also</span></span>

- [<span data-ttu-id="0b689-120">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0b689-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0b689-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0b689-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0b689-122">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0b689-122">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="0b689-123">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="0b689-123">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
- [<span data-ttu-id="0b689-124">Jakie dokładnie jest oznacza "Podniesiony"?</span><span class="sxs-lookup"><span data-stu-id="0b689-124">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
