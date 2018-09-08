---
title: 'Porady: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e16270fd900c1c786cfd74f484455481d91e5b52
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198676"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="f8732-102">Porady: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f8732-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="f8732-103">Aby użyć właściwości zdarzeń należy zdefiniować właściwości zdarzenia w klasie, która wywołuje zdarzenia, a następnie ustawić delegatów dla właściwości zdarzenia w klasach, które obsługują zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="f8732-104">Aby zaimplementować w klasie wiele właściwości zdarzeń, klasa musi wewnętrznie przechowywać i zachowywać zdefiniowanego delegata dla każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="f8732-105">Typowym podejściem jest implementacja kolekcji delegata, która jest indeksowana przy użyciu klucza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="f8732-106">Aby przechowywać delegatów dla każdego zdarzenia, można użyć klasy <xref:System.ComponentModel.EventHandlerList> lub zaimplementować własną kolekcję.</span><span class="sxs-lookup"><span data-stu-id="f8732-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="f8732-107">Klasa kolekcji musi dostarczać metody do ustawiania, uzyskiwania dostępu i pobierania delegata obsługi zdarzeń opartego na kluczu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f8732-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="f8732-108">Na przykład można użyć klasy <xref:System.Collections.Hashtable> lub pochodnej niestandardowej klasy na podstawie klasy <xref:System.Collections.DictionaryBase>.</span><span class="sxs-lookup"><span data-stu-id="f8732-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="f8732-109">Szczegóły implementacji kolekcji delegata nie muszą być udostępniane poza klasą.</span><span class="sxs-lookup"><span data-stu-id="f8732-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="f8732-110">Każda właściwość zdarzenia w klasie definiuje metody dodawania i usuwania akcesora.</span><span class="sxs-lookup"><span data-stu-id="f8732-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="f8732-111">Dodanie akcesora do właściwości zdarzenia dodaje wystąpienie delegata wejściowego do kolekcji delegata.</span><span class="sxs-lookup"><span data-stu-id="f8732-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="f8732-112">Usunięcie akcesora właściwości zdarzenia usuwa wystąpienie delegata wejściowego z kolekcji delegata.</span><span class="sxs-lookup"><span data-stu-id="f8732-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="f8732-113">Akcesory właściwości zdarzenia używają wstępnie zdefiniowanego klucza dla właściwości zdarzenia do dodawania i usuwania wystąpień z kolekcji delegata.</span><span class="sxs-lookup"><span data-stu-id="f8732-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="f8732-114">Do obsługi wielu zdarzeń przy użyciu właściwości zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f8732-114">To handle multiple events using event properties</span></span>  
  
1.  <span data-ttu-id="f8732-115">Zdefiniuj kolekcje delegata w klasie, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2.  <span data-ttu-id="f8732-116">Zdefiniuj klucz dla każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-116">Define a key for each event.</span></span>  
  
3.  <span data-ttu-id="f8732-117">Zdefiniuj właściwości zdarzenia w klasie, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-117">Define the event properties in the class that raises the events.</span></span>  
  
4.  <span data-ttu-id="f8732-118">Użyj kolekcji delegata do implementacji metod dodawania i usuwania akcesora dla właściwości zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5.  <span data-ttu-id="f8732-119">Użyj publicznych zdarzeń właściwości, aby dodawać i usuwać delegatów obsługi zdarzeń w klasach, które obsługują zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f8732-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8732-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8732-120">Example</span></span>  
 <span data-ttu-id="f8732-121">Poniższy przykład napisany w języku C# implementuje właściwości zdarzenia `MouseDown` i `MouseUp`, z wykorzystaniem <xref:System.ComponentModel.EventHandlerList> do przechowywania każdego zdarzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="f8732-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="f8732-122">Słowa kluczowe w konstrukcji właściwości zdarzenia są pogrubione.</span><span class="sxs-lookup"><span data-stu-id="f8732-122">The keywords of the event property constructs are in bold type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8732-123">Właściwości zdarzenia nie są obsługiwane w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8732-123">Event properties are not supported in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="f8732-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8732-124">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
- [<span data-ttu-id="f8732-125">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f8732-125">Events</span></span>](../../../docs/standard/events/index.md)  
- <xref:System.Web.UI.Control.Events%2A>  
- [<span data-ttu-id="f8732-126">Instrukcje: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci</span><span class="sxs-lookup"><span data-stu-id="f8732-126">How to: Declare Custom Events To Conserve Memory</span></span>](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
