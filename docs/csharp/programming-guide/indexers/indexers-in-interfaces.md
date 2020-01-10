---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 4ac51589ed1680f8484fde797c045d15beed3af9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712120"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="8f89e-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8f89e-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="8f89e-103">Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="8f89e-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="8f89e-104">Metody dostępu indeksatorów interfejsów różnią się od metod dostępu indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f89e-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="8f89e-105">Metody dostępu interfejsów nie używają modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="8f89e-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="8f89e-106">Metoda dostępu do interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="8f89e-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="8f89e-107">W tym celu metoda dostępu wskazuje, czy indeksator jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="8f89e-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="8f89e-108">Oto przykład metody dostępu indeksatora interfejsu:</span><span class="sxs-lookup"><span data-stu-id="8f89e-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="8f89e-109">Podpis indeksatora musi różnić się od sygnatur wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8f89e-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f89e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8f89e-110">Example</span></span>  
 <span data-ttu-id="8f89e-111">Poniższy przykład pokazuje, jak zaimplementować indeksatory interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8f89e-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="8f89e-112">W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8f89e-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="8f89e-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8f89e-113">For example:</span></span>  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="8f89e-114">Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora.</span><span class="sxs-lookup"><span data-stu-id="8f89e-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="8f89e-115">Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy, `ICitizen` i `IEmployee`, a oba interfejsy mają ten sam podpis indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8f89e-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="8f89e-116">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="8f89e-116">That is, the following indexer declaration:</span></span>  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="8f89e-117">implementuje indeksator w interfejsie `IEmployee`, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="8f89e-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="8f89e-118">implementuje indeksator w interfejsie `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="8f89e-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f89e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f89e-119">See also</span></span>

- [<span data-ttu-id="8f89e-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8f89e-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8f89e-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="8f89e-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="8f89e-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8f89e-122">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="8f89e-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8f89e-123">Interfaces</span></span>](../interfaces/index.md)
