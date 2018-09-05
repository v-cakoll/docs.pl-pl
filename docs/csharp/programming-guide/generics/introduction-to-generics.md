---
title: Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 17f4c67792732be7a678ec858b6627fa712194c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671713"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="4ef9c-102">Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4ef9c-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="4ef9c-103">Ogólne klasy i metody łączenia możliwość ponownego wykorzystania, bezpieczeństwa i wydajności w taki sposób, że nie można ich odpowiedniki nieogólnego.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="4ef9c-104">Najczęściej używanych typów ogólnych za pomocą metod, które działają na nich i kolekcje.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="4ef9c-105">Biblioteki klas .NET Framework w wersji 2.0 oferuje nową przestrzeń nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcji ogólnej.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="4ef9c-106">Zalecane jest, że wszystkie aplikacje przeznaczone na platformę .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnej klasy zamiast starszych odpowiedniki nieogólnego, takich jak <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="4ef9c-107">Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ef9c-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="4ef9c-108">Oczywiście można również utworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązań i wzorców projektowych, które są bezpieczne i wydajne.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="4ef9c-109">Poniższy przykład kodu pokazuje prosty klasy połączonej listy ogólnej dla celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="4ef9c-110">(W większości przypadków należy używać <xref:System.Collections.Generic.List%601> klasy biblioteki klas .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretny typ byłyby zwykle używane do wskazać typ elementu przechowywane na liście.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="4ef9c-111">Jest on używany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4ef9c-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="4ef9c-112">Jako typ parametru metody w `AddHead` metody.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="4ef9c-113">Jako typ zwracany `Data` właściwość w zagnieżdżonej `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="4ef9c-114">Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="4ef9c-115">Należy pamiętać, że T jest dostępny do zagnieżdżonego `Node` klasy.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="4ef9c-116">Gdy `GenericList<T>` zostanie uruchomiony przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="4ef9c-117">Poniższy przykład kodu pokazuje, jak kod klienta korzysta z ogólnego `GenericList<T>` klasy, aby utworzyć listę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="4ef9c-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="4ef9c-118">Po prostu zmieniając argument typu, poniższy kod można łatwo można zmodyfikować, aby utworzyć listę ciągów lub dowolny inny typ niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="4ef9c-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4ef9c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ef9c-119">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="4ef9c-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4ef9c-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4ef9c-121">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="4ef9c-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
