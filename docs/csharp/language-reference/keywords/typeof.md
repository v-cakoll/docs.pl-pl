---
title: typeof (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: be79fa4f2cfb1119a50201bf6c18a144726f2f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="typeof-c-reference"></a><span data-ttu-id="58c1b-102">typeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="58c1b-102">typeof (C# Reference)</span></span>
<span data-ttu-id="58c1b-103">Uzywany do uzyskania obiektu `System.Type` dla typu.</span><span class="sxs-lookup"><span data-stu-id="58c1b-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="58c1b-104">Wyrazenie `typeof` ma nastepujaca postac:</span><span class="sxs-lookup"><span data-stu-id="58c1b-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="58c1b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58c1b-105">Remarks</span></span>  
 <span data-ttu-id="58c1b-106">Aby uzyskac typ srodowiska wykonawczego wyrazenia, mozna uzyc metody .NET Framework <xref:System.Object.GetType%2A> — jak w ponizszym przykladzie:</span><span class="sxs-lookup"><span data-stu-id="58c1b-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="58c1b-107">Operator `typeof` nie moze byc przeciazony.</span><span class="sxs-lookup"><span data-stu-id="58c1b-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="58c1b-108">Operatora `typeof` mozna tez uzywac na otwartych typach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="58c1b-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="58c1b-109">Typy z wiecej niz jednym parametrem typu musza zawierac odpowiednia liczbe przecinków w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="58c1b-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="58c1b-110">W przykladzie ponizej pokazujemy, jak ustalic, czy zwracanym typem metody jest ogólny typ <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="58c1b-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="58c1b-111">Zalózmy, ze metoda jest wystapieniem typu MethodInfo:</span><span class="sxs-lookup"><span data-stu-id="58c1b-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="58c1b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="58c1b-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="58c1b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="58c1b-113">Example</span></span>  
 <span data-ttu-id="58c1b-114">W przykladzie uzyto metody <xref:System.Object.GetType%2A>, aby okreslic typ, który jest zwracany jako wynik obliczenia.</span><span class="sxs-lookup"><span data-stu-id="58c1b-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="58c1b-115">Zalezy to od wymagan przechowywania zwiazanych z wynikowa liczba.</span><span class="sxs-lookup"><span data-stu-id="58c1b-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="58c1b-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="58c1b-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58c1b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58c1b-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="58c1b-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="58c1b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="58c1b-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58c1b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="58c1b-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="58c1b-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="58c1b-121">is</span><span class="sxs-lookup"><span data-stu-id="58c1b-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="58c1b-122">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="58c1b-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
