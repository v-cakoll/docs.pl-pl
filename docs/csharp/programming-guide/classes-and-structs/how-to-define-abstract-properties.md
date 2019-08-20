---
title: 'Instrukcje: Definiowanie właściwości abstrakcyjnych C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: fae526f5dcd452fbc381ee86c892b72e61956f0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596868"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="b3a79-102">Instrukcje: Definiowanie właściwości abstrakcyjnychC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="b3a79-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="b3a79-103">Poniższy przykład pokazuje, jak definiować właściwości [abstrakcyjne](../../language-reference/keywords/abstract.md) .</span><span class="sxs-lookup"><span data-stu-id="b3a79-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="b3a79-104">Deklaracja właściwości abstrakcyjnej nie zapewnia implementacji metod dostępu do właściwości — deklaruje, że Klasa obsługuje właściwości, ale pozostawia implementację metody dostępu do klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b3a79-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="b3a79-105">W poniższym przykładzie pokazano, jak zaimplementować właściwości abstrakcyjne dziedziczone z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="b3a79-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="b3a79-106">Ten przykład składa się z trzech plików, z których każdy jest kompilowany indywidualnie, a jego wynikający z nich zestaw jest przywoływany przez następną kompilację:</span><span class="sxs-lookup"><span data-stu-id="b3a79-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="b3a79-107">abstractshape.cs: `Shape` Klasa, która zawiera właściwość abstrakcyjną `Area` .</span><span class="sxs-lookup"><span data-stu-id="b3a79-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="b3a79-108">shapes.cs: Podklasy `Shape` klasy.</span><span class="sxs-lookup"><span data-stu-id="b3a79-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="b3a79-109">shapetest.cs: Program testowy do wyświetlania obszarów niektórych `Shape`obiektów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b3a79-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="b3a79-110">Aby skompilować przykład, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="b3a79-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="b3a79-111">Spowoduje to utworzenie pliku wykonywalnego shapetest. exe.</span><span class="sxs-lookup"><span data-stu-id="b3a79-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3a79-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3a79-112">Example</span></span>  
 <span data-ttu-id="b3a79-113">Ten plik deklaruje `Shape` klasę, która `Area` zawiera właściwość typu `double`.</span><span class="sxs-lookup"><span data-stu-id="b3a79-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="b3a79-114">Modyfikatory we właściwości są umieszczane na samej deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="b3a79-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="b3a79-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b3a79-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="b3a79-116">Podczas deklarowania właściwości abstrakcyjnej ( `Area` na przykład w tym przykładzie) można po prostu wskazać, jakie metody dostępu do właściwości są dostępne, ale nie należy ich wdrażać.</span><span class="sxs-lookup"><span data-stu-id="b3a79-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="b3a79-117">W tym przykładzie dostępna jest tylko metoda dostępu [Get](../../language-reference/keywords/get.md) , więc właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="b3a79-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3a79-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3a79-118">Example</span></span>  
 <span data-ttu-id="b3a79-119">Poniższy kod przedstawia trzy podklasy `Shape` i sposób, w jaki `Area` zastępują właściwość w celu zapewnienia własnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="b3a79-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="b3a79-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3a79-120">Example</span></span>  
 <span data-ttu-id="b3a79-121">Poniższy kod przedstawia program testowy, który tworzy wiele `Shape`obiektów pochodnych i drukuje ich obszary.</span><span class="sxs-lookup"><span data-stu-id="b3a79-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b3a79-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3a79-122">See also</span></span>

- [<span data-ttu-id="b3a79-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b3a79-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3a79-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="b3a79-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b3a79-125">Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="b3a79-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="b3a79-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b3a79-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b3a79-127">Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b3a79-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
