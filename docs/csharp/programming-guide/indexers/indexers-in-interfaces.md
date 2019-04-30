---
title: Indeksatory w interfejsach - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c56369b28f8e1bab1ca8e8c13ebd9710c8f1d9fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61679833"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="b21a3-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b21a3-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="b21a3-103">Można zadeklarować indeksatorów w [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="b21a3-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="b21a3-104">Metody dostępu interfejsu indeksatorów różnią się od metod dostępu [klasy](../../../csharp/language-reference/keywords/class.md) indeksatorów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b21a3-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="b21a3-105">Metody dostępu interfejsu należy używać modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="b21a3-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="b21a3-106">Metody dostępu interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="b21a3-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="b21a3-107">W związku z tym metody dostępu ma na celu wskazać indeksatora odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b21a3-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="b21a3-108">Oto przykład metody dostępu interfejsu indeksatora:</span><span class="sxs-lookup"><span data-stu-id="b21a3-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="b21a3-109">Podpis indeksatora musi się różnić od podpisy innymi indeksatorami zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="b21a3-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b21a3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b21a3-110">Example</span></span>  
 <span data-ttu-id="b21a3-111">Poniższy przykład pokazuje, jak zaimplementować interfejs indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="b21a3-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="b21a3-112">W poprzednim przykładzie można użyć jawną implementacją członków przy użyciu w pełni kwalifikowana nazwa składowej interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b21a3-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="b21a3-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b21a3-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="b21a3-114">Jednak w pełni kwalifikowana nazwa jest wymagane tylko aby uniknąć niejednoznaczności, implementując klasy jest więcej niż jeden interfejs, za pomocą tego samego podpisu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="b21a3-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="b21a3-115">Na przykład jeśli `Employee` klasa implementuje dwa interfejsy `ICitizen` i `IEmployee`, i dotyczą obu interfejsów mają taki sam podpis indeksatora, niezbędne jest jawną implementacją członków.</span><span class="sxs-lookup"><span data-stu-id="b21a3-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="b21a3-116">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="b21a3-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="b21a3-117">implementuje indeksatora na `IEmployee` interfejsu podczas następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="b21a3-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="b21a3-118">implementuje indeksatora na `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b21a3-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21a3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b21a3-119">See also</span></span>

- [<span data-ttu-id="b21a3-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b21a3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b21a3-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="b21a3-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="b21a3-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b21a3-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="b21a3-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b21a3-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
