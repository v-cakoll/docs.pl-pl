---
title: Parametry typu ogólnego - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 10feb47ce3dfe9e356da381e0d62e6d220c9452a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677425"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="30d54-102">Parametry typu ogólnego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="30d54-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="30d54-103">W ogólnym typie lub definicję metody parametr typu jest symbolem zastępczym dla określonego typu, że klient określa podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="30d54-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="30d54-104">Klasy ogólnej, takich jak `GenericList<T>` na liście [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md), nie można użyć jako — ponieważ nie jest tak naprawdę typu; więcej podobna do planu dla typu.</span><span class="sxs-lookup"><span data-stu-id="30d54-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="30d54-105">Aby użyć `GenericList<T>`, kod klienta należy zadeklarować i tworzenia wystąpienia typu skonstruowany, określając argument typu w nawiasach ostrych.</span><span class="sxs-lookup"><span data-stu-id="30d54-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="30d54-106">Typ argumentu dla tej konkretnej klasy mogą być dowolnego typu, rozpoznawane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="30d54-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="30d54-107">Dowolną liczbę wystąpień skonstruowanego typu mogą być tworzone, każdy z nich przy użyciu argumentu innego typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="30d54-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="30d54-108">W każdym z tych wystąpień `GenericList<T>`, każde wystąpienie `T` w klasie zastąpić w czasie wykonywania z argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="30d54-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="30d54-109">Za pomocą tego podstawienia przygotowaliśmy trzy oddzielne obiekty bezpieczny i efektywny przy użyciu definicji pojedynczą klasę.</span><span class="sxs-lookup"><span data-stu-id="30d54-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="30d54-110">Aby uzyskać więcej informacji na temat sposobu to zastąpienie jest wykonywane przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="30d54-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="30d54-111">Parametr typu wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="30d54-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="30d54-112">**Czy** nazw parametrów typu ogólnego przy użyciu nazw opisowych, chyba, że nazwa pojedynczą literą jest całkowicie własnym objaśniający i nazwę opisową nie wprowadziłaby dodatkowej wartości.</span><span class="sxs-lookup"><span data-stu-id="30d54-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="30d54-113">**Należy wziąć pod uwagę** przy użyciu języka T jako nazwę parametru typu dla typów, z jednym parametrem typu pojedynczą literą.</span><span class="sxs-lookup"><span data-stu-id="30d54-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="30d54-114">**Czy** prefiks nazwy parametrów typu opisowy z "T".</span><span class="sxs-lookup"><span data-stu-id="30d54-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="30d54-115">**Należy wziąć pod uwagę** wskazujący ograniczenia umieścić w parametrze typu nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="30d54-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="30d54-116">Na przykład parametr ograniczone do `ISession` może być wywołana `TSession`.</span><span class="sxs-lookup"><span data-stu-id="30d54-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="30d54-117">Reguł analizy kodu [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) może służyć do zapewnienia, że parametry typu są nazywane odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="30d54-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30d54-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30d54-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="30d54-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30d54-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="30d54-120">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="30d54-120">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="30d54-121">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="30d54-121">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
