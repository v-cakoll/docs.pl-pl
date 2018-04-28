---
title: Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 30184edbcba47203d8416609b5a28648adf7cbaa
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="d81d1-102">Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d81d1-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="d81d1-103">Ogólne klasy i metody łączyć możliwość ponownego wykorzystania, zabezpieczeń i wydajności w taki sposób, aby ich odpowiedniki nierodzajową nie.</span><span class="sxs-lookup"><span data-stu-id="d81d1-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="d81d1-104">Typy ogólne są najczęściej używane przez kolekcje i metod, które działają na nich.</span><span class="sxs-lookup"><span data-stu-id="d81d1-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="d81d1-105">Biblioteka klas programu .NET Framework w wersji 2.0 zapewnia nowy obszar nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcję na podstawie ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d81d1-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="d81d1-106">Zaleca się, że wszystkie aplikacje których docelowe .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnych klasy zamiast starsze odpowiedników nierodzajową takich jak <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="d81d1-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="d81d1-107">Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d81d1-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="d81d1-108">Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązania i wzorce projektowe, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="d81d1-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="d81d1-109">Poniższy przykład kodu pokazuje proste klasy ogólnej listy połączone dla celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="d81d1-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="d81d1-110">(W większości przypadków należy użyć <xref:System.Collections.Generic.List%601> klasy w bibliotece klas programu .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretnego typu zazwyczaj będzie używać do określenia typ elementu przechowywane na liście.</span><span class="sxs-lookup"><span data-stu-id="d81d1-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="d81d1-111">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d81d1-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="d81d1-112">Typ parametru metody w `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="d81d1-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="d81d1-113">Jako typ zwracany `Data` właściwości w zagnieżdżonych `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="d81d1-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="d81d1-114">Jako typ prywatnego elementu członkowskiego `data` klasy zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="d81d1-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="d81d1-115">Należy pamiętać, że T jest dostępny dla zagnieżdżone `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="d81d1-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="d81d1-116">Gdy `GenericList<T>` zostanie uruchomiony z konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.</span><span class="sxs-lookup"><span data-stu-id="d81d1-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="d81d1-117">Poniższy przykład kodu pokazuje, jak kod klienta używa ogólnego `GenericList<T>` klasy w celu utworzenia listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d81d1-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="d81d1-118">Po prostu zmieniając argument typu następujący kod można łatwo można zmodyfikować utworzyć listę ciągów lub dowolnego niestandardowego typu:</span><span class="sxs-lookup"><span data-stu-id="d81d1-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d81d1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d81d1-119">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="d81d1-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d81d1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d81d1-121">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d81d1-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
