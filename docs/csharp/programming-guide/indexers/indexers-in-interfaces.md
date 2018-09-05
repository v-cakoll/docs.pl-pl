---
title: Indeksatory w interfejsach (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c3ddb48590087d49402482e8cbf3760027da1a2a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673465"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="61b8a-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="61b8a-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="61b8a-103">Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="61b8a-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="61b8a-104">Metody dostępu interfejsu indeksatorów różnią się od metod dostępu [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="61b8a-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="61b8a-105">Metody dostępu interfejsu należy używać modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="61b8a-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="61b8a-106">Metody dostępu interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="61b8a-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="61b8a-107">W związku z tym metody dostępu ma na celu wskazać indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="61b8a-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="61b8a-108">Oto przykład metody dostępu interfejsu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="61b8a-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="61b8a-109">Podpis indeksatora musi się różnić od podpisy innymi indeksatorami zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="61b8a-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61b8a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="61b8a-110">Example</span></span>  
 <span data-ttu-id="61b8a-111">Poniższy przykład pokazuje, jak zaimplementować interfejs indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="61b8a-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="61b8a-112">W poprzednim przykładzie można użyć jawną implementacją członków przy użyciu w pełni kwalifikowana nazwa składowej interfejsu.</span><span class="sxs-lookup"><span data-stu-id="61b8a-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="61b8a-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="61b8a-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="61b8a-114">Jednak w pełni kwalifikowana nazwa jest wymagane tylko aby uniknąć niejednoznaczności, implementując klasy jest więcej niż jeden interfejs, za pomocą tego samego podpisu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="61b8a-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="61b8a-115">Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taki sam podpis indeksatora, niezbędne jest jawną implementacją członków.</span><span class="sxs-lookup"><span data-stu-id="61b8a-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="61b8a-116">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="61b8a-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="61b8a-117">implementuje indeksatora na `IEmployee` interfejsu podczas następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="61b8a-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="61b8a-118">implementuje indeksatora na `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="61b8a-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b8a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61b8a-119">See Also</span></span>

- [<span data-ttu-id="61b8a-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="61b8a-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="61b8a-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="61b8a-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="61b8a-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="61b8a-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="61b8a-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="61b8a-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
