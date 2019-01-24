---
title: Przegląd obsługi zdarzeń (formularze systemu Windows)
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
ms.openlocfilehash: cab35250f4fedf0a08dc7198430a668c7428c207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567756"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="1a4e2-102">Przegląd obsługi zdarzeń (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="1a4e2-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="1a4e2-103">Program obsługi zdarzeń jest metodą, która jest powiązana ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="1a4e2-104">Gdy zdarzenie jest wywoływane, kod wewnątrz procedury obsługi zdarzeń jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="1a4e2-105">Każdy program obsługi zdarzeń zawiera dwa parametry, które pozwalają na poprawnie obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="1a4e2-106">W poniższym przykładzie pokazano program obsługi zdarzeń dla <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="1a4e2-107">Pierwszy parametr`sender`, zawiera odwołanie do obiektu, który spowodował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="1a4e2-108">Drugi parametr `e`, w powyższym przykładzie przekazuje obiekt określone zdarzenie, które jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="1a4e2-109">Odwołując się do właściwości obiektu (a czasami jego metod), można uzyskać informacje, takie jak lokalizacja myszy dla zdarzenia myszy lub danych przesyłanych w zdarzeniach przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="1a4e2-110">Zazwyczaj każde zdarzenie tworzy program obsługi zdarzeń z typem obiektu innego zdarzenia dla drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="1a4e2-111">Niektóre procedury obsługi zdarzeń, takich jak te dotyczące <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia, mają ten sam typ obiektu, ich drugi parametr.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="1a4e2-112">Dla tych typów zdarzeń można użyć tego samego programu obsługi zdarzeń do obsługi zarówno zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="1a4e2-113">Umożliwia także tę samą procedurę obsługi zdarzeń do obsługi tego samego zdarzenia dla różnych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="1a4e2-114">Na przykład, jeśli istnieje grupa <xref:System.Windows.Forms.RadioButton> kontrolek w formularzu, można utworzyć jedną procedurą obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzeń i mieć każdy formant <xref:System.Windows.Forms.Control.Click> zdarzenia powiązane z jedną procedurą obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1a4e2-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="1a4e2-115">Aby uzyskać więcej informacji, zobacz [jak: Łączenie wielu zdarzeń jedną procedurą obsługi zdarzeń w formularzach Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1a4e2-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4e2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a4e2-116">See also</span></span>
- [<span data-ttu-id="1a4e2-117">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a4e2-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="1a4e2-118">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="1a4e2-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
