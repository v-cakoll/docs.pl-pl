---
title: Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712328"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="00bfb-102">Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnychC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="00bfb-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="00bfb-103">Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie bazowej, aby mogły być również wywoływane z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="00bfb-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="00bfb-104">Ten wzorzec jest szeroko używany w klasach Windows Forms w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00bfb-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="00bfb-105">Podczas tworzenia klasy, która może być używana jako klasa bazowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z klasy, która je zadeklaruje.</span><span class="sxs-lookup"><span data-stu-id="00bfb-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="00bfb-106">Klasy pochodne nie mogą bezpośrednio wywoływać zdarzeń, które są zadeklarowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="00bfb-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="00bfb-107">Chociaż czasami można chcieć, aby zdarzenie, które może zostać wywołane tylko przez klasę bazową, w większości przypadków należy włączyć klasę pochodną, aby wywoływać zdarzenia klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="00bfb-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="00bfb-108">W tym celu można utworzyć chronioną metodę wywołującą w klasie bazowej, która otacza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="00bfb-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="00bfb-109">Wywołując lub zastępując tę metodę wywołującą, klasy pochodne mogą wywołać zdarzenie pośrednio.</span><span class="sxs-lookup"><span data-stu-id="00bfb-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00bfb-110">Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i zastąp je w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="00bfb-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="00bfb-111">C# Kompilator nie obsługuje tych poprawnie i jest nieprzewidywalne, niezależnie od tego, czy subskrybent zdarzenia pochodnego rzeczywiście zasubskrybuje zdarzenie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="00bfb-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00bfb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="00bfb-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="00bfb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00bfb-113">See also</span></span>

- [<span data-ttu-id="00bfb-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="00bfb-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="00bfb-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="00bfb-115">Events</span></span>](./index.md)
- [<span data-ttu-id="00bfb-116">Delegaci</span><span class="sxs-lookup"><span data-stu-id="00bfb-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="00bfb-117">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="00bfb-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="00bfb-118">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00bfb-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
