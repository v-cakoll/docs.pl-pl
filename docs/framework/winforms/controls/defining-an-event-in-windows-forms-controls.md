---
title: Zdefiniuj zdarzenie w kontrolkach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: d45c369e1fc82ee009a85b5b35fe6aa754873436
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746075"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="e5d47-102">Definiowanie zdarzeń w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e5d47-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="e5d47-103">Aby uzyskać szczegółowe informacje o definiowaniu niestandardowych zdarzeń, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5d47-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="e5d47-104">W przypadku zdefiniowania zdarzenia, które nie ma żadnych skojarzonych danych, należy użyć typu podstawowego dla danych zdarzenia, <xref:System.EventArgs>i użyć <xref:System.EventHandler> jako delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e5d47-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="e5d47-105">Wszystko, co pozostało do wykonania, definiuje element członkowski zdarzenia i chronioną metodę `On`*EventName* , która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e5d47-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="e5d47-106">Poniższy fragment kodu przedstawia sposób, w jaki formant niestandardowy `FlashTrackBar` definiuje zdarzenie niestandardowe, `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="e5d47-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="e5d47-107">Pełny kod przykładu `FlashTrackBar` można znaleźć w temacie How to [: Create a Windows Forms Control, który pokazuje postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="e5d47-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
   protected virtual void OnValueChanged(EventArgs e) 
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5d47-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5d47-108">See also</span></span>

- [<span data-ttu-id="e5d47-109">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5d47-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="e5d47-110">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e5d47-110">Events</span></span>](../../../standard/events/index.md)
