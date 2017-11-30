---
title: "Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="5cd69-102">Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5cd69-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="5cd69-103">Poniższy przykład przedstawia sposób definiowania [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cd69-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="5cd69-104">Deklaracja właściwości abstrakcyjne nie dostarcza implementację metody dostępu właściwości — deklaruje obsługuje właściwości klasy, ale pozostawia implementacji metody dostępu dla klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="5cd69-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="5cd69-105">W poniższym przykładzie pokazano sposób implementacji właściwości abstrakcyjne dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5cd69-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="5cd69-106">W tym przykładzie składa się z trzech plików, z których każdy jest kompilowany indywidualnie i jego Wynikowy zestaw odwołuje się do niego następnej kompilacji:</span><span class="sxs-lookup"><span data-stu-id="5cd69-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="5cd69-107">abstractshape.CS: `Shape` klasę, która zawiera abstrakcyjnego `Area` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5cd69-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="5cd69-108">Shapes.CS: podklasy `Shape` klasy.</span><span class="sxs-lookup"><span data-stu-id="5cd69-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="5cd69-109">shapetest.CS: program test, aby wyświetlić obszary niektórych `Shape`-pochodnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cd69-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="5cd69-110">Aby skompilować w przykładzie, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5cd69-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="5cd69-111">Spowoduje to utworzenie shapetest.exe pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="5cd69-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd69-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cd69-112">Example</span></span>  
 <span data-ttu-id="5cd69-113">Ten plik deklaruje `Shape` klasę, która zawiera `Area` właściwość typu `double`.</span><span class="sxs-lookup"><span data-stu-id="5cd69-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="5cd69-114">Modyfikatory we właściwości są umieszczane w deklaracji właściwości samej siebie.</span><span class="sxs-lookup"><span data-stu-id="5cd69-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="5cd69-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5cd69-115">For example:</span></span>  
  
    ```  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="5cd69-116">Gdy deklarowanie właściwości abstrakcyjnych (takich jak `Area` w tym przykładzie), możesz po prostu wskazują, jakie metody dostępu właściwości są dostępne, ale nie ich wdrażania.</span><span class="sxs-lookup"><span data-stu-id="5cd69-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="5cd69-117">W tym przykładzie, tylko [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu jest dostępna, więc właściwość jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="5cd69-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd69-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cd69-118">Example</span></span>  
 <span data-ttu-id="5cd69-119">Poniższy kod przedstawia trzy podklasy `Shape` i jak zastąpienie `Area` właściwości do własnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="5cd69-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="5cd69-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cd69-120">Example</span></span>  
 <span data-ttu-id="5cd69-121">Poniższy kod przedstawia program test, który tworzy szereg `Shape`-pochodnych obiektów i drukuje ich obszarów.</span><span class="sxs-lookup"><span data-stu-id="5cd69-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5cd69-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cd69-122">See Also</span></span>  
 [<span data-ttu-id="5cd69-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5cd69-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5cd69-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="5cd69-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="5cd69-125">Klasy abstrakcyjne i zapieczętowane oraz członkowie klas</span><span class="sxs-lookup"><span data-stu-id="5cd69-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="5cd69-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5cd69-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="5cd69-127">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5cd69-127">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
