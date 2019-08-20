---
title: Parametry typu ogólnego — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 27cd89c8e82036bf6353030b4f235c2ebe738e6d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589684"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="a5fc5-102">Parametry typu ogólnego (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a5fc5-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="a5fc5-103">W przypadku typu ogólnego lub definicji metody parametr typu jest symbolem zastępczym określonego typu, który klient określa podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="a5fc5-104">Klasa generyczna, taka jak `GenericList<T>` wymieniona w temacie [wprowadzenie do typów ogólnych](./index.md), nie może być używana jako-jest, ponieważ nie jest w rzeczywistości typem; jest to bardziej podobne do planu dla typu.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="a5fc5-105">Aby użyć `GenericList<T>`kodu klienta, należy zadeklarować i utworzyć wystąpienie złożonego typu przez określenie argumentu typu wewnątrz nawiasów kątowych.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="a5fc5-106">Argument typu dla tej konkretnej klasy może być dowolnym typem rozpoznawanym przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="a5fc5-107">Można utworzyć dowolną liczbę wystąpień typu złożonego, każdy z nich przy użyciu innego argumentu typu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a5fc5-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="a5fc5-108">W każdym z tych wystąpień `GenericList<T>`, każde `T` wystąpienie w klasie jest zastępowane w czasie wykonywania z argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="a5fc5-109">Zgodnie z tym podstawianiem zostały utworzone trzy osobne, bezpieczne obiekty typu za pomocą jednej definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="a5fc5-110">Aby uzyskać więcej informacji o tym, jak to podstawienie jest wykonywane przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="a5fc5-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="a5fc5-111">Wskazówki dotyczące nazewnictwa parametrów typu</span><span class="sxs-lookup"><span data-stu-id="a5fc5-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="a5fc5-112">**Należy** nazywać parametry typu ogólnego z nazwami opisowymi, chyba że nazwa pojedynczej litery nie jest całkowicie oczywista, a nazwa opisowa nie będzie dodawać wartości.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="a5fc5-113">**Rozważ** użycie T jako nazwy parametru typu dla typów z jednym pojedynczym parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="a5fc5-114">**Wykonaj** prefiks nazwy parametrów typu opisowego z "T".</span><span class="sxs-lookup"><span data-stu-id="a5fc5-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="a5fc5-115">**Rozważ** wskazanie ograniczeń umieszczanych na parametrze typu w nazwie parametru.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="a5fc5-116">Na przykład parametr ograniczony do `ISession` może być wywoływany. `TSession`</span><span class="sxs-lookup"><span data-stu-id="a5fc5-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="a5fc5-117">Reguły analizy kodu [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) można użyć, aby upewnić się, że parametry typu są odpowiednio nazwane.</span><span class="sxs-lookup"><span data-stu-id="a5fc5-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5fc5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5fc5-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="a5fc5-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5fc5-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5fc5-120">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="a5fc5-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="a5fc5-121">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="a5fc5-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
