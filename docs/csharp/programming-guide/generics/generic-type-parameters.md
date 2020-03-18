---
title: Ogólne parametry typu — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712185"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="06c69-102">Ogólne parametry typu (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="06c69-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="06c69-103">W definicji typu ogólnego lub metody parametr typu jest symbolem zastępczym dla określonego typu, który klient określa podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06c69-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="06c69-104">Klasy ogólnej, `GenericList<T>` takich jak wymienione w [wprowadzenie do leków ogólnych](./index.md), nie można używać jako- jest, ponieważ nie jest to naprawdę typ; jest bardziej jak plan dla typu.</span><span class="sxs-lookup"><span data-stu-id="06c69-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="06c69-105">Aby `GenericList<T>`użyć , kod klienta musi zadeklarować i utworzyć wystąpienie skonstruowanego typu, określając argument typu wewnątrz nawiasów kątowych.</span><span class="sxs-lookup"><span data-stu-id="06c69-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="06c69-106">Argument typu dla tej określonej klasy może być dowolny typ rozpoznawany przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="06c69-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="06c69-107">Można utworzyć dowolną liczbę skonstruowanych wystąpień typu, z których każdy przy użyciu innego typu argumentu, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="06c69-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="06c69-108">W każdym z tych `GenericList<T>`wystąpień `T` , każde wystąpienie w klasie jest zastępowane w czasie wykonywania argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="06c69-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="06c69-109">Za pomocą tej podstawienia utworzyliśmy trzy oddzielne obiekty bezpieczne dla typów i wydajne przy użyciu definicji jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="06c69-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="06c69-110">Aby uzyskać więcej informacji na temat sposobu wykonywania tego podstawienia przez clr, zobacz [Generyków w czasie wykonywania](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="06c69-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="06c69-111">Wskazówki dotyczące nazewnictwa parametrów typu</span><span class="sxs-lookup"><span data-stu-id="06c69-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="06c69-112">**Czy** nazwać ogólne parametry typu z nazwami opisowymi, chyba że nazwa pojedynczej litery jest całkowicie oczywiste i nazwa opisowa nie doda wartości.</span><span class="sxs-lookup"><span data-stu-id="06c69-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="06c69-113">**Należy rozważyć** użycie T jako nazwy parametru typu dla typów z jednym parametrem typu litery.</span><span class="sxs-lookup"><span data-stu-id="06c69-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="06c69-114">**Wykonaj** nazwy parametrów typu opisowego prefiksu z "T".</span><span class="sxs-lookup"><span data-stu-id="06c69-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="06c69-115">**Należy wziąć pod uwagę** wskazując ograniczenia umieszczone na parametr typu w nazwie parametru.</span><span class="sxs-lookup"><span data-stu-id="06c69-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="06c69-116">Na przykład parametr ograniczony do `ISession` może `TSession`być wywoływana .</span><span class="sxs-lookup"><span data-stu-id="06c69-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="06c69-117">Reguła analizy kodu [CA1715](/visualstudio/code-quality/ca1715) może służyć do zapewnienia, że parametry typu są odpowiednio nazwane.</span><span class="sxs-lookup"><span data-stu-id="06c69-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06c69-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06c69-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="06c69-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="06c69-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06c69-120">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="06c69-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="06c69-121">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="06c69-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
