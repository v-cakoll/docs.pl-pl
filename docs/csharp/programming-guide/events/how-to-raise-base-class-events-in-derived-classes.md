---
title: Jak podnieść zdarzenia klasy podstawowej w klasach pochodnych — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712328"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="4f9d5-102">Jak podnieść zdarzenia klasy podstawowej w klasach pochodnych (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="4f9d5-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="4f9d5-103">Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie podstawowej, dzięki czemu mogą być również wywoływane z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="4f9d5-104">Ten wzorzec jest szeroko stosowany w klasach formularzy systemu Windows w bibliotece klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="4f9d5-105">Podczas tworzenia klasy, która może służyć jako klasa podstawowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z wewnątrz klasy, która je zadeklarowała.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="4f9d5-106">Klasy pochodne nie można bezpośrednio wywołać zdarzenia, które są zadeklarowane w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="4f9d5-107">Chociaż czasami może chcesz zdarzenie, które mogą być wywoływane tylko przez klasę podstawową, w większości czasu, należy włączyć klasy pochodnej do wywoływania zdarzeń klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="4f9d5-108">Aby to zrobić, można utworzyć metodę wywoływania chronione w klasie podstawowej, która otacza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="4f9d5-109">Wywołując lub zastępując tę metodę wywoływania, klasy pochodne można wywołać zdarzenie pośrednio.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f9d5-110">Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i nie należy je zastępować w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="4f9d5-111">Kompilator Języka C# nie obsługuje tych poprawnie i jest nieprzewidywalne, czy subskrybent akcesorii do zdarzenia pochodnego będzie faktycznie subskrybowania zdarzenia klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4f9d5-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f9d5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f9d5-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4f9d5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f9d5-113">See also</span></span>

- [<span data-ttu-id="4f9d5-114">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="4f9d5-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4f9d5-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4f9d5-115">Events</span></span>](./index.md)
- [<span data-ttu-id="4f9d5-116">Delegaty</span><span class="sxs-lookup"><span data-stu-id="4f9d5-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="4f9d5-117">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="4f9d5-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="4f9d5-118">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f9d5-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
