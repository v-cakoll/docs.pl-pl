---
title: Indeksatory w interfejsach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: cb039755b7440cbfd1f782cc118d11a03b47da04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331126"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="db05e-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="db05e-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="db05e-103">Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="db05e-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="db05e-104">Metod dostępu interfejsu indeksatory różnią się od metod dostępu z [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="db05e-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="db05e-105">Metody dostępu interfejsu nie należy używać modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="db05e-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="db05e-106">Metody dostępu interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="db05e-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="db05e-107">W związku z tym celem metody dostępu jest informujące o powodzeniu indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="db05e-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="db05e-108">Poniżej przedstawiono przykład metody dostępu interfejsu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="db05e-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="db05e-109">Podpis indeksatora musi różnić się od podpisy innymi indeksatorami zadeklarowany w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="db05e-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db05e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="db05e-110">Example</span></span>  
 <span data-ttu-id="db05e-111">Poniższy przykład pokazuje, jak do zaimplementowania interfejsu indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="db05e-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="db05e-112">W poprzednim przykładzie możesz użyć implementacja interfejsu jawnego członka za pomocą w pełni kwalifikowana nazwa elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db05e-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="db05e-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="db05e-113">For example:</span></span>  
  
```  
public string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="db05e-114">Jednak w pełni kwalifikowana nazwa wymagana jest tylko do uniknąć niejednoznaczności, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora.</span><span class="sxs-lookup"><span data-stu-id="db05e-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="db05e-115">Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taką samą sygnaturę indeksatora, konieczne jest jawną implementacją elementu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db05e-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="db05e-116">Oznacza to, że następujące oświadczenie indeksatora:</span><span class="sxs-lookup"><span data-stu-id="db05e-116">That is, the following indexer declaration:</span></span>  
  
```  
public string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="db05e-117">implementuje indeksatora na `IEmployee` interfejsu podczas następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="db05e-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
public string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="db05e-118">implementuje indeksatora na `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="db05e-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db05e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db05e-119">See Also</span></span>  
 [<span data-ttu-id="db05e-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="db05e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db05e-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="db05e-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="db05e-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="db05e-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="db05e-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="db05e-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
