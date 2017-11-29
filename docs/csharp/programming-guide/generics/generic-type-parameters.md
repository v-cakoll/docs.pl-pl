---
title: "Parametry typu ogólnego (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b32db7eb6e7788167e110a91726e9dbfe19f31ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="3a8b5-102">Parametry typu ogólnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3a8b5-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="3a8b5-103">W ogólnym typie lub metoda definicji parametry typu jest symbolem zastępczym dla klienta określa, po ich wystąpienia zmiennej typu ogólnego określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="3a8b5-104">Klasy ogólnego, takich jak `GenericList<T>` na liście [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md), nie można użyć jako — ponieważ nie jest naprawdę typu, lecz więcej podobny do planu dla typu.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="3a8b5-105">Aby użyć `GenericList<T>`, kod klienta należy zadeklarować i tworzenia wystąpienia typu utworzone przez określenie argumentu typu w nawiasach ostrych.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="3a8b5-106">Typ argumentu dla tej konkretnej klasy mogą być dowolnego typu, rozpoznany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="3a8b5-107">Dowolną liczbę wystąpień skonstruowanego typu mogą być tworzone, każda z nich przy użyciu argumentu innego typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a8b5-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="3a8b5-108">W każdym z tych wystąpień `GenericList<T>`, każde wystąpienie `T` klasy zostaną zastąpione w czasie wykonywania z argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="3a8b5-109">Za pomocą tego podstawienia utworzono trzech oddzielnych obiektów bezpieczny i skuteczny przy użyciu definicji jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="3a8b5-110">Aby uzyskać więcej informacji dotyczących sposobu to zastąpienie odbywa się przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="3a8b5-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="3a8b5-111">Parametr typu zasady nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="3a8b5-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="3a8b5-112">**Czy** nazwy parametrów typu ogólnego z nazw opisowych, jeśli nazwa pojedyncze litery jest całkowicie self objaśniający i nazwę opisową nie może dodać wartość.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="3a8b5-113">**Należy wziąć pod uwagę** przy użyciu T jako nazwę parametru typu dla typów z jednym parametrem typu pojedyncze litery.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="3a8b5-114">**Czy** prefiksu nazwy parametrów opisowe typu z "T".</span><span class="sxs-lookup"><span data-stu-id="3a8b5-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="3a8b5-115">**Należy wziąć pod uwagę** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="3a8b5-116">Na przykład parametr ograniczone do `ISession` może zostać wywołana `TSession`.</span><span class="sxs-lookup"><span data-stu-id="3a8b5-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8b5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a8b5-117">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="3a8b5-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3a8b5-119">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="3a8b5-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="3a8b5-120">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="3a8b5-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
