---
title: 'Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 2f200ff00534bde1fa0d016d64099e3ca28535a8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585843"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="98ad7-102">Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="98ad7-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="98ad7-103">Poniższym prostym przykładzie pokazano standardowy sposób, aby zadeklarować zdarzenia w klasie bazowej, dzięki czemu mogą one również inicjowane z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="98ad7-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="98ad7-104">Ten wzorzec jest często używane klasy formularzy Windows w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98ad7-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="98ad7-105">Kiedy tworzysz klasę, która może służyć jako klasa bazowa innych klas, należy rozważyć fakt, że zdarzenia są specjalnym typem delegata, który można wywołać tylko z w obrębie klasy, która je zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="98ad7-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="98ad7-106">Klasy pochodne nie można bezpośrednio wywołać zdarzenia, które są zadeklarowane w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="98ad7-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="98ad7-107">Chociaż czasami możesz chcieć zdarzenie, które tylko będzie zgłaszany przez klasę bazową, w większości przypadków, należy włączyć klasy pochodnej w celu wywoływanie zdarzeń klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98ad7-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="98ad7-108">Aby to zrobić, można utworzyć chronionych wywołania metody w klasie bazowej, która otacza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="98ad7-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="98ad7-109">Przez wywołanie lub zastąpienie tego wywołania metody, klasy pochodne mogą być wywoływane zdarzenie pośrednio.</span><span class="sxs-lookup"><span data-stu-id="98ad7-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98ad7-110">Deklarowanie zdarzeń wirtualnych w klasie bazowej i nie je zastąpić w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="98ad7-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="98ad7-111">Kompilator języka C# nie obsługują one poprawnie i jest nieprzewidywalne czy subskrybent zdarzenia pochodnej faktycznie będzie subskrybowanie zdarzeń klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="98ad7-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98ad7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="98ad7-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98ad7-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98ad7-113">See also</span></span>

- [<span data-ttu-id="98ad7-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="98ad7-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="98ad7-115">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="98ad7-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="98ad7-116">Delegaty</span><span class="sxs-lookup"><span data-stu-id="98ad7-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="98ad7-117">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="98ad7-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="98ad7-118">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98ad7-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
