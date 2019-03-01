---
title: Wprowadzenie do typów ogólnych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: d09cc686e934f722193cb4671d25671f7f4ef5f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978517"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="3e99b-102">Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3e99b-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="3e99b-103">Ogólne klasy i metody łączenia możliwość ponownego wykorzystania, bezpieczeństwa i wydajności w taki sposób, że nie można ich odpowiedniki nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="3e99b-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="3e99b-104">Najczęściej używanych typów ogólnych za pomocą metod, które działają na nich i kolekcje.</span><span class="sxs-lookup"><span data-stu-id="3e99b-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="3e99b-105">Biblioteki klas .NET Framework w wersji 2.0 oferuje nową przestrzeń nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="3e99b-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="3e99b-106">Zalecane jest, że wszystkie aplikacje przeznaczone na platformę .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnej klasy zamiast starszych odpowiedniki nieogólnego, takich jak <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="3e99b-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="3e99b-107">Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e99b-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="3e99b-108">Oczywiście można również utworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązań i wzorców projektowych, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="3e99b-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="3e99b-109">Poniższy przykład kodu pokazuje prosty klasy połączonej listy ogólnej dla celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="3e99b-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="3e99b-110">(W większości przypadków należy używać <xref:System.Collections.Generic.List%601> klasy biblioteki klas .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretny typ byłyby zwykle używane do wskazać typ elementu przechowywane na liście.</span><span class="sxs-lookup"><span data-stu-id="3e99b-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="3e99b-111">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3e99b-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="3e99b-112">Jako typ parametru metody w `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="3e99b-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="3e99b-113">Jako typ zwracany `Data` właściwość w zagnieżdżonej `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="3e99b-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="3e99b-114">Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="3e99b-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="3e99b-115">Należy pamiętać, że T jest dostępny do zagnieżdżonego `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="3e99b-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="3e99b-116">Gdy `GenericList<T>` zostanie uruchomiony przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.</span><span class="sxs-lookup"><span data-stu-id="3e99b-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="3e99b-117">Poniższy przykład kodu pokazuje, jak kod klienta korzysta z ogólnego `GenericList<T>` klasy, aby utworzyć listę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="3e99b-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="3e99b-118">Po prostu zmieniając argument typu, poniższy kod można łatwo można zmodyfikować, aby utworzyć listę ciągów lub dowolny inny typ niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="3e99b-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3e99b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e99b-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="3e99b-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3e99b-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3e99b-121">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="3e99b-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
