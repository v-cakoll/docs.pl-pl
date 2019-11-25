---
title: Jak definiować właściwości abstrakcyjne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 1b6dc1dfe932ffff161b0eef667bd35a75b66cf9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971003"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="9bbba-102">Jak definiować właściwości abstrakcyjne (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="9bbba-102">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="9bbba-103">Poniższy przykład pokazuje, jak definiować właściwości [abstrakcyjne](../../language-reference/keywords/abstract.md) .</span><span class="sxs-lookup"><span data-stu-id="9bbba-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="9bbba-104">Deklaracja właściwości abstrakcyjnej nie zapewnia implementacji metod dostępu do właściwości — deklaruje, że Klasa obsługuje właściwości, ale pozostawia implementację metody dostępu do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="9bbba-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="9bbba-105">W poniższym przykładzie pokazano, jak zaimplementować właściwości abstrakcyjne dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="9bbba-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="9bbba-106">Ten przykład składa się z trzech plików, z których każdy jest kompilowany indywidualnie, a jego wynikający z nich zestaw jest przywoływany przez następną kompilację:</span><span class="sxs-lookup"><span data-stu-id="9bbba-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="9bbba-107">abstractshape.cs: Klasa `Shape`, która zawiera właściwość abstrakcyjnej `Area`.</span><span class="sxs-lookup"><span data-stu-id="9bbba-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="9bbba-108">shapes.cs: podklasy klasy `Shape`.</span><span class="sxs-lookup"><span data-stu-id="9bbba-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="9bbba-109">shapetest.cs: Program testowy do wyświetlania obszarów niektórych obiektów pochodnych `Shape`.</span><span class="sxs-lookup"><span data-stu-id="9bbba-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="9bbba-110">Aby skompilować przykład, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9bbba-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="9bbba-111">Spowoduje to utworzenie pliku wykonywalnego shapetest. exe.</span><span class="sxs-lookup"><span data-stu-id="9bbba-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbba-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bbba-112">Example</span></span>  
 <span data-ttu-id="9bbba-113">Ten plik deklaruje klasę `Shape`, która zawiera właściwość `Area` typu `double`.</span><span class="sxs-lookup"><span data-stu-id="9bbba-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="9bbba-114">Modyfikatory we właściwości są umieszczane na samej deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="9bbba-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="9bbba-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="9bbba-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="9bbba-116">W przypadku deklarowania właściwości abstrakcyjnej (takiej jak `Area` w tym przykładzie) można po prostu wskazać, jakie metody dostępu do właściwości są dostępne, ale nie należy ich wdrażać.</span><span class="sxs-lookup"><span data-stu-id="9bbba-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="9bbba-117">W tym przykładzie dostępna jest tylko metoda dostępu [Get](../../language-reference/keywords/get.md) , więc właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9bbba-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bbba-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bbba-118">Example</span></span>  
 <span data-ttu-id="9bbba-119">Poniższy kod przedstawia trzy podklasy `Shape` i sposób przesłania właściwości `Area` w celu zapewnienia własnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="9bbba-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="9bbba-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bbba-120">Example</span></span>  
 <span data-ttu-id="9bbba-121">Poniższy kod przedstawia program testowy, który tworzy wiele obiektów pochodnych `Shape`i drukuje obszary.</span><span class="sxs-lookup"><span data-stu-id="9bbba-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9bbba-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bbba-122">See also</span></span>

- [<span data-ttu-id="9bbba-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9bbba-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9bbba-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="9bbba-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9bbba-125">Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="9bbba-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="9bbba-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9bbba-126">Properties</span></span>](./properties.md)
