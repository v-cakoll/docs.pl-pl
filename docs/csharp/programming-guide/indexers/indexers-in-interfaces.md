---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: cea8d157e89597ddf4633cf7f7d3df7044db9ec7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589442"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="622d1-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="622d1-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="622d1-103">Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="622d1-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="622d1-104">Metody dostępu indeksatorów interfejsów różnią się od metod dostępu indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="622d1-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="622d1-105">Metody dostępu interfejsów nie używają modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="622d1-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="622d1-106">Metoda dostępu do interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="622d1-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="622d1-107">W tym celu metoda dostępu wskazuje, czy indeksator jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="622d1-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="622d1-108">Oto przykład metody dostępu indeksatora interfejsu:</span><span class="sxs-lookup"><span data-stu-id="622d1-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="622d1-109">Podpis indeksatora musi różnić się od sygnatur wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="622d1-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="622d1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="622d1-110">Example</span></span>  
 <span data-ttu-id="622d1-111">Poniższy przykład pokazuje, jak zaimplementować indeksatory interfejsów.</span><span class="sxs-lookup"><span data-stu-id="622d1-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="622d1-112">W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="622d1-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="622d1-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="622d1-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="622d1-114">Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora.</span><span class="sxs-lookup"><span data-stu-id="622d1-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="622d1-115">Na przykład jeśli `Employee` Klasa implementuje dwa interfejsy `IEmployee`, `ICitizen` a oba interfejsy mają tę samą sygnaturę indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="622d1-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="622d1-116">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="622d1-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="622d1-117">implementuje indeksator w `IEmployee` interfejsie, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="622d1-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="622d1-118">implementuje indeksator w `ICitizen` interfejsie.</span><span class="sxs-lookup"><span data-stu-id="622d1-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622d1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="622d1-119">See also</span></span>

- [<span data-ttu-id="622d1-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="622d1-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="622d1-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="622d1-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="622d1-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="622d1-122">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="622d1-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="622d1-123">Interfaces</span></span>](../interfaces/index.md)
