---
title: "Definiowanie zdarzeń w formantach formularzy systemu Windows"
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
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 592efefecb0428f87e5ac612c8fb162aa2fe85dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="b5481-102">Definiowanie zdarzeń w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b5481-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="b5481-103">Aby uzyskać szczegółowe informacje na temat definiowania niestandardowych zdarzeń, zobacz [zdarzenia](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5481-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="b5481-104">W przypadku definiowania zdarzenie, które nie ma żadnych skojarzonych danych, użyj typu podstawowego dla danych zdarzenia <xref:System.EventArgs>i użyj <xref:System.EventHandler> jako delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b5481-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="b5481-105">Wszystkie opcje, które pozostanie w celu jest określenie elementu członkowskiego zdarzenia i chronione `On` *EventName* metodę, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b5481-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="b5481-106">Poniższy kod fragmentu pokazuje sposób `FlashTrackBar` kontrolki niestandardowej definiuje niestandardowe zdarzenie `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="b5481-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="b5481-107">Dla kompletny kod dla `FlashTrackBar` przykładowe, zobacz [porady: tworzenie systemu Windows Forms kontroli czy pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="b5481-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5481-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5481-108">See Also</span></span>  
 [<span data-ttu-id="b5481-109">Zdarzenia w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b5481-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="b5481-110">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b5481-110">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="b5481-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b5481-111">Events</span></span>](../../../../docs/standard/events/index.md)
