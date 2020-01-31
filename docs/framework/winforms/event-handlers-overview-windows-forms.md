---
title: Przegląd programów obsługi zdarzeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743496"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="27cbf-102">Przegląd obsługi zdarzeń (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="27cbf-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="27cbf-103">Program obsługi zdarzeń to metoda, która jest powiązana ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="27cbf-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="27cbf-104">Po wywołaniu zdarzenia kod w ramach programu obsługi zdarzeń jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="27cbf-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="27cbf-105">Każdy program obsługi zdarzeń zawiera dwa parametry, które umożliwiają prawidłowe obsłużenie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="27cbf-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="27cbf-106">Poniższy przykład pokazuje procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> formantu <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="27cbf-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="27cbf-107">Pierwszy parametr,`sender`, zawiera odwołanie do obiektu, który wywołał zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="27cbf-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="27cbf-108">Drugi parametr, `e`w powyższym przykładzie przekazuje obiekt specyficzny dla zdarzenia, które jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="27cbf-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="27cbf-109">Odwołując się do właściwości obiektu (i, czasami, jego metody), można uzyskać informacje takie jak lokalizacja myszy dla zdarzeń myszy lub danych transferowanych w zdarzeniach przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="27cbf-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="27cbf-110">Zwykle każde zdarzenie generuje procedurę obsługi zdarzeń z innym typem obiektu zdarzenia dla drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="27cbf-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="27cbf-111">Niektóre programy obsługi zdarzeń, takie jak te dla zdarzeń <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp>, mają ten sam typ obiektu dla drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="27cbf-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="27cbf-112">W przypadku tych typów zdarzeń można użyć tego samego programu obsługi zdarzeń do obsługi obu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="27cbf-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="27cbf-113">Można również użyć tego samego programu obsługi zdarzeń, aby obsłużyć to samo zdarzenie dla różnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="27cbf-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="27cbf-114">Na przykład jeśli masz grupę formantów <xref:System.Windows.Forms.RadioButton> na formularzu, można utworzyć pojedynczy program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Click> i mieć zdarzenie <xref:System.Windows.Forms.Control.Click> poszczególnych kontrolek powiązane z obsługą pojedynczego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="27cbf-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="27cbf-115">Aby uzyskać więcej informacji, zobacz [jak: łączenie wielu zdarzeń z obsługą pojedynczego zdarzenia w Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="27cbf-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cbf-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27cbf-116">See also</span></span>

- [<span data-ttu-id="27cbf-117">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27cbf-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="27cbf-118">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="27cbf-118">Events Overview</span></span>](events-overview-windows-forms.md)
