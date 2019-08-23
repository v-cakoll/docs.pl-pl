---
title: 'Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach C# pochodnych — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 820bdcb895a1c3eb7c56db55b298c1a9636f2f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921876"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="9ae8f-102">Instrukcje: Wywołaj zdarzenia klasy podstawowej w klasachC# pochodnych (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="9ae8f-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="9ae8f-103">Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie bazowej, aby mogły być również wywoływane z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="9ae8f-104">Ten wzorzec jest szeroko używany w klasach Windows Forms w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="9ae8f-105">Podczas tworzenia klasy, która może być używana jako klasa bazowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z klasy, która je zadeklaruje.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="9ae8f-106">Klasy pochodne nie mogą bezpośrednio wywoływać zdarzeń, które są zadeklarowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="9ae8f-107">Chociaż czasami można chcieć, aby zdarzenie, które może zostać wywołane tylko przez klasę bazową, w większości przypadków należy włączyć klasę pochodną, aby wywoływać zdarzenia klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="9ae8f-108">W tym celu można utworzyć chronioną metodę wywołującą w klasie bazowej, która otacza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="9ae8f-109">Wywołując lub zastępując tę metodę wywołującą, klasy pochodne mogą wywołać zdarzenie pośrednio.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ae8f-110">Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i zastąp je w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="9ae8f-111">C# Kompilator nie obsługuje tych poprawnie i jest nieprzewidywalne, niezależnie od tego, czy subskrybent zdarzenia pochodnego rzeczywiście zasubskrybuje zdarzenie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="9ae8f-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ae8f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ae8f-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9ae8f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ae8f-113">See also</span></span>

- [<span data-ttu-id="9ae8f-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9ae8f-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ae8f-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="9ae8f-115">Events</span></span>](./index.md)
- [<span data-ttu-id="9ae8f-116">Delegaty</span><span class="sxs-lookup"><span data-stu-id="9ae8f-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="9ae8f-117">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="9ae8f-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="9ae8f-118">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ae8f-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
