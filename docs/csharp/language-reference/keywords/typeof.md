---
title: "typeof (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a><span data-ttu-id="583ab-102">typeof (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="583ab-102">typeof (C# Reference)</span></span>
<span data-ttu-id="583ab-103">Używany do uzyskania `System.Type` obiektu dla typu.</span><span class="sxs-lookup"><span data-stu-id="583ab-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="583ab-104">A `typeof` wyrażenie ma następującą postać:</span><span class="sxs-lookup"><span data-stu-id="583ab-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="583ab-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="583ab-105">Remarks</span></span>  
 <span data-ttu-id="583ab-106">Aby uzyskać typu run-time wyrażenia, można użyć metody .NET Framework <xref:System.Object.GetType%2A>, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="583ab-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="583ab-107">`typeof` Operator nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="583ab-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="583ab-108">`typeof` Operatora można używać na otwieranie typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="583ab-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="583ab-109">Typy z więcej niż jeden parametr typu musi mieć odpowiednią liczbę przecinków w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="583ab-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="583ab-110">Poniższy przykład przedstawia sposób ustalić, czy typ zwracany metody jest rodzajowy <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="583ab-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="583ab-111">Załóżmy, że metoda jest wystąpieniem typu MethodInfo:</span><span class="sxs-lookup"><span data-stu-id="583ab-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="583ab-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="583ab-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="583ab-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="583ab-113">Example</span></span>  
 <span data-ttu-id="583ab-114">W przykładzie użyto <xref:System.Object.GetType%2A> metodę, aby określić typ, który zawiera wynik obliczenia liczbowych.</span><span class="sxs-lookup"><span data-stu-id="583ab-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="583ab-115">Zależy to od liczby wynikowy wymagania dotyczące magazynu.</span><span class="sxs-lookup"><span data-stu-id="583ab-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="583ab-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="583ab-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="583ab-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="583ab-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="583ab-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="583ab-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="583ab-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="583ab-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="583ab-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="583ab-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="583ab-121">jest</span><span class="sxs-lookup"><span data-stu-id="583ab-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="583ab-122">Słowa kluczowe operatora</span><span class="sxs-lookup"><span data-stu-id="583ab-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
