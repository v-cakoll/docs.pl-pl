---
title: "Indeksatory w interfejsach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 304f2e037d8df025376d06f229ddd1584f8713b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="f79e0-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f79e0-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="f79e0-103">Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="f79e0-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="f79e0-104">Metod dostępu interfejsu indeksatory różnią się od metod dostępu z [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f79e0-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="f79e0-105">Metody dostępu interfejsu nie należy używać modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="f79e0-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="f79e0-106">Metody dostępu interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="f79e0-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="f79e0-107">W związku z tym celem metody dostępu jest informujące o powodzeniu indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="f79e0-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="f79e0-108">Poniżej przedstawiono przykład metody dostępu interfejsu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="f79e0-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="f79e0-109">Podpis indeksatora musi różnić się od podpisy innymi indeksatorami zadeklarowany w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="f79e0-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f79e0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f79e0-110">Example</span></span>  
 <span data-ttu-id="f79e0-111">Poniższy przykład pokazuje, jak do zaimplementowania interfejsu indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="f79e0-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="f79e0-112">W poprzednim przykładzie możesz użyć implementacja interfejsu jawnego członka za pomocą w pełni kwalifikowana nazwa elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f79e0-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="f79e0-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f79e0-113">For example:</span></span>  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 <span data-ttu-id="f79e0-114">Jednak w pełni kwalifikowana nazwa wymagana jest tylko do uniknąć niejednoznaczności, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora.</span><span class="sxs-lookup"><span data-stu-id="f79e0-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="f79e0-115">Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taką samą sygnaturę indeksatora, konieczne jest jawną implementacją elementu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f79e0-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="f79e0-116">Oznacza to, że następujące oświadczenie indeksatora:</span><span class="sxs-lookup"><span data-stu-id="f79e0-116">That is, the following indexer declaration:</span></span>  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 <span data-ttu-id="f79e0-117">implementuje indeksatora na `IEmployee` interfejsu podczas następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="f79e0-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 <span data-ttu-id="f79e0-118">implementuje indeksatora na `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f79e0-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79e0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f79e0-119">See Also</span></span>  
 [<span data-ttu-id="f79e0-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f79e0-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f79e0-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="f79e0-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="f79e0-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f79e0-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="f79e0-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f79e0-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
