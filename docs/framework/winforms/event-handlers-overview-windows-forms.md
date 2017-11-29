---
title: "Przegląd obsługi zdarzeń (formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="d598c-102">Przegląd obsługi zdarzeń (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="d598c-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="d598c-103">Program obsługi zdarzeń jest to metoda, która jest powiązany ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="d598c-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="d598c-104">Gdy zdarzenie jest zgłaszane, wykonywany jest kod wewnątrz obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d598c-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="d598c-105">Każdy program obsługi zdarzeń zawiera dwa parametry, które umożliwiają obsługę zdarzenia poprawnie.</span><span class="sxs-lookup"><span data-stu-id="d598c-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="d598c-106">W poniższym przykładzie przedstawiono program obsługi zdarzeń dla <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d598c-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="d598c-107">Pierwszy parametr`sender`, zawiera odwołanie do obiektu, który wywołał zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d598c-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="d598c-108">Drugi parametr `e`, w powyższym przykładzie przekazuje obiekt określone zdarzenie, które jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d598c-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="d598c-109">Za pomocą odwołań do właściwości obiektu (i jego metody), możesz uzyskać informacje, takie jak lokalizacja myszy dla zdarzenia myszy lub danych przesyłanych w przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="d598c-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="d598c-110">Zazwyczaj każde zdarzenie tworzy program obsługi zdarzeń typu inny obiekt zdarzenia dla drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="d598c-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="d598c-111">Niektóre programy obsługi zdarzeń, takich jak te dotyczące <xref:System.Windows.Forms.Control.MouseDown> i <xref:System.Windows.Forms.Control.MouseUp> zdarzenia, mają ten sam typ obiektu dla ich drugiego parametru.</span><span class="sxs-lookup"><span data-stu-id="d598c-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="d598c-112">W przypadku tych typów zdarzeń można użyć tej procedury obsługi zdarzeń do obsługi zarówno zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d598c-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="d598c-113">Umożliwia także tej procedury obsługi zdarzeń do obsługi tego samego zdarzenia dla inne formanty.</span><span class="sxs-lookup"><span data-stu-id="d598c-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="d598c-114">Na przykład, jeśli istnieje grupa <xref:System.Windows.Forms.RadioButton> formantów w formularzu, można utworzyć jednym programem obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzeń i każdej kontrolki <xref:System.Windows.Forms.Control.Click> zdarzenia powiązane z obsługą jednego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d598c-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="d598c-115">Aby uzyskać więcej informacji, zobacz [porady: łączenie wielu zdarzeń pojedynczego obsługi zdarzeń w formularzach systemu Windows](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d598c-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d598c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d598c-116">See Also</span></span>  
 [<span data-ttu-id="d598c-117">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d598c-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="d598c-118">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d598c-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
