---
title: Jak zdefiniować właściwości abstrakcyjne - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705616"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="b96c8-102">Jak zdefiniować właściwości abstrakcyjne (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="b96c8-102">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="b96c8-103">W poniższym przykładzie pokazano, jak zdefiniować właściwości [abstrakcyjne.](../../language-reference/keywords/abstract.md)</span><span class="sxs-lookup"><span data-stu-id="b96c8-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="b96c8-104">Abstrakcyjna deklaracja właściwości nie zapewnia implementacji akcesorów właściwości — deklaruje, że klasa obsługuje właściwości, ale pozostawia implementacji akcesora do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b96c8-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="b96c8-105">W poniższym przykładzie pokazano, jak zaimplementować właściwości abstrakcyjne dziedziczone z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="b96c8-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="b96c8-106">Ten przykład składa się z trzech plików, z których każdy jest kompilowany indywidualnie, a jego wynikowy zestaw odwołuje się do następnej kompilacji:</span><span class="sxs-lookup"><span data-stu-id="b96c8-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="b96c8-107">abstractshape.cs: `Shape` klasa, która `Area` zawiera właściwość abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="b96c8-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="b96c8-108">shapes.cs: Podklasy `Shape` klasy.</span><span class="sxs-lookup"><span data-stu-id="b96c8-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="b96c8-109">shapetest.cs: Program testowy do wyświetlania obszarów niektórych `Shape`obiektów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b96c8-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="b96c8-110">Aby skompilować przykład, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b96c8-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="b96c8-111">Spowoduje to utworzenie pliku wykonywalnego shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="b96c8-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b96c8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b96c8-112">Example</span></span>  
 <span data-ttu-id="b96c8-113">Ten plik deklaruje `Shape` klasę, `Area` która zawiera `double`właściwość typu .</span><span class="sxs-lookup"><span data-stu-id="b96c8-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="b96c8-114">Modyfikatory na nieruchomości są umieszczane na samym oświadczeniu majątkowym.</span><span class="sxs-lookup"><span data-stu-id="b96c8-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="b96c8-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b96c8-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="b96c8-116">Podczas deklarowania właściwości abstrakcyjnej `Area` (na przykład w tym przykładzie), wystarczy wskazać, jakie akcesory właściwości są dostępne, ale nie implementują ich.</span><span class="sxs-lookup"><span data-stu-id="b96c8-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="b96c8-117">W tym przykładzie dostępna jest tylko akcesor [get,](../../language-reference/keywords/get.md) więc właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b96c8-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b96c8-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b96c8-118">Example</span></span>  
 <span data-ttu-id="b96c8-119">Poniższy kod przedstawia trzy `Shape` podklasy i jak `Area` zastępują właściwość, aby zapewnić własną implementację.</span><span class="sxs-lookup"><span data-stu-id="b96c8-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="b96c8-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b96c8-120">Example</span></span>  
 <span data-ttu-id="b96c8-121">Poniższy kod przedstawia program testowy, `Shape`który tworzy wiele obiektów pochodnych i drukuje ich obszary.</span><span class="sxs-lookup"><span data-stu-id="b96c8-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b96c8-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b96c8-122">See also</span></span>

- [<span data-ttu-id="b96c8-123">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="b96c8-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b96c8-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="b96c8-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b96c8-125">Klasy abstrakcyjne i zapieczętowane oraz członkowie klas</span><span class="sxs-lookup"><span data-stu-id="b96c8-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="b96c8-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b96c8-126">Properties</span></span>](./properties.md)
