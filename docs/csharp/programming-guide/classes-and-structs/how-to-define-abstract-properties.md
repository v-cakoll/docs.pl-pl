---
title: 'Instrukcje: Definiowanie właściwości abstrakcyjnych - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 70f344fb4e5a74940219688190324beb8183d32b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237314"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="922b5-102">Instrukcje: Definiowanie właściwości abstrakcyjnych (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="922b5-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="922b5-103">Poniższy przykład pokazuje jak zdefiniować [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md) właściwości.</span><span class="sxs-lookup"><span data-stu-id="922b5-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="922b5-104">Deklaracja właściwości abstrakcyjne nie zawiera implementacji metody dostępu właściwości, ponieważ relacja ta stwierdza, że obsługuje właściwości klasy, ale pozostawia implementacji metody dostępu dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="922b5-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="922b5-105">Poniższy przykład demonstruje sposób implementacji właściwości abstrakcyjnych dziedziczone z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="922b5-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="922b5-106">Ten przykład obejmuje trzy pliki, z których każdy jest kompilowany oddzielnie, a jego Wynikowy zestaw odwołuje się do następnej kompilacji:</span><span class="sxs-lookup"><span data-stu-id="922b5-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="922b5-107">abstractshape.CS: `Shape` klasę, która zawiera abstrakcyjną `Area` właściwości.</span><span class="sxs-lookup"><span data-stu-id="922b5-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="922b5-108">Shapes.CS: Podklasy `Shape` klasy.</span><span class="sxs-lookup"><span data-stu-id="922b5-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="922b5-109">shapetest.CS: Program test, aby wyświetlić obszary niektórych `Shape`-obiektami wywodzącymi.</span><span class="sxs-lookup"><span data-stu-id="922b5-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="922b5-110">Aby skompilować przykład, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="922b5-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="922b5-111">Spowoduje to utworzenie shapetest.exe pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="922b5-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="922b5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="922b5-112">Example</span></span>  
 <span data-ttu-id="922b5-113">Ten plik deklaruje `Shape` klasę, która zawiera `Area` właściwość typu `double`.</span><span class="sxs-lookup"><span data-stu-id="922b5-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="922b5-114">Modyfikatory we właściwości są umieszczane w sama deklaracja właściwości.</span><span class="sxs-lookup"><span data-stu-id="922b5-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="922b5-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="922b5-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="922b5-116">Podczas deklarowania właściwość abstrakcyjną (takie jak `Area` w tym przykładzie), możesz po prostu wskazują, jakie metody dostępu właściwości są dostępne, ale nie ich wdrażania.</span><span class="sxs-lookup"><span data-stu-id="922b5-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="922b5-117">W tym przykładzie, tylko [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu jest dostępna, więc właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="922b5-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="922b5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="922b5-118">Example</span></span>  
 <span data-ttu-id="922b5-119">Poniższy kod pokazuje trzy podklasy `Shape` i jak zastąpić `Area` właściwość zapewniali własną implementację.</span><span class="sxs-lookup"><span data-stu-id="922b5-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="922b5-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="922b5-120">Example</span></span>  
 <span data-ttu-id="922b5-121">Poniższy kod przedstawia program test, który tworzy szereg `Shape`-pochodnych obiektów i drukuje ich obszarów.</span><span class="sxs-lookup"><span data-stu-id="922b5-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="922b5-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="922b5-122">See Also</span></span>

- [<span data-ttu-id="922b5-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="922b5-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="922b5-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="922b5-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="922b5-125">Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="922b5-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [<span data-ttu-id="922b5-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="922b5-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="922b5-127">Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="922b5-127">How to: Create and Use Assemblies Using the Command Line</span></span>](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
