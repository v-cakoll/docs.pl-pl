---
title: Parametry typu ogólnego - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 48fa90226b7a8a36f5f432921cf5d999e76c6fa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681641"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="0f000-102">Parametry typu ogólnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0f000-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="0f000-103">W ogólnym typie lub definicję metody parametry typu jest symbolem zastępczym dla określonego typu, że klient określa podczas ich tworzenia wystąpienia zmienną typu rodzajowego.</span><span class="sxs-lookup"><span data-stu-id="0f000-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="0f000-104">Klasy ogólnej, takich jak `GenericList<T>` na liście [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md), nie można użyć jako — ponieważ nie jest tak naprawdę typu; więcej podobna do planu dla typu.</span><span class="sxs-lookup"><span data-stu-id="0f000-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="0f000-105">Aby użyć `GenericList<T>`, kod klienta należy zadeklarować i tworzenia wystąpienia typu skonstruowany, określając argument typu w nawiasach ostrych.</span><span class="sxs-lookup"><span data-stu-id="0f000-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="0f000-106">Typ argumentu dla tej konkretnej klasy mogą być dowolnego typu, rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="0f000-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="0f000-107">Dowolną liczbę wystąpień skonstruowanego typu mogą być tworzone, każdy z nich przy użyciu argumentu innego typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0f000-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 <span data-ttu-id="0f000-108">W każdym z tych wystąpień `GenericList<T>`, każde wystąpienie `T` w klasie, zostaną zastąpione w czasie wykonywania z argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="0f000-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="0f000-109">Za pomocą tego podstawienia przygotowaliśmy trzy oddzielne obiekty bezpieczny i efektywny przy użyciu definicji pojedynczą klasę.</span><span class="sxs-lookup"><span data-stu-id="0f000-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="0f000-110">Aby uzyskać więcej informacji na temat sposobu to zastąpienie jest wykonywane przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="0f000-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="0f000-111">Parametr typu wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="0f000-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="0f000-112">**Czy** nazw parametrów typu ogólnego przy użyciu nazw opisowych, chyba, że nazwa pojedynczą literą jest całkowicie własnym objaśniający i nazwę opisową nie wprowadziłaby dodatkowej wartości.</span><span class="sxs-lookup"><span data-stu-id="0f000-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   <span data-ttu-id="0f000-113">**Należy wziąć pod uwagę** przy użyciu języka T jako nazwę parametru typu dla typów, z jednym parametrem typu pojedynczą literą.</span><span class="sxs-lookup"><span data-stu-id="0f000-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   <span data-ttu-id="0f000-114">**Czy** prefiks nazwy parametrów typu opisowy z "T".</span><span class="sxs-lookup"><span data-stu-id="0f000-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   <span data-ttu-id="0f000-115">**Należy wziąć pod uwagę** wskazujący ograniczenia umieścić w parametrze typu nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="0f000-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="0f000-116">Na przykład parametr ograniczone do `ISession` może być wywołana `TSession`.</span><span class="sxs-lookup"><span data-stu-id="0f000-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f000-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f000-117">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="0f000-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0f000-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0f000-119">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0f000-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="0f000-120">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="0f000-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
