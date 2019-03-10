---
title: Definiowanie zdarzeń w formantach formularzy systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 4235c8b3c513509023388112071e78cfd079ec6f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705383"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="278bb-102">Definiowanie zdarzeń w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="278bb-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="278bb-103">Aby uzyskać szczegółowe informacje na temat definiowania zdarzenia niestandardowe, zobacz [zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="278bb-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="278bb-104">Jeśli zdefiniujesz zdarzenie, które nie ma żadnych skojarzonych danych, należy użyć typu podstawowego danych zdarzenia <xref:System.EventArgs>i użyj <xref:System.EventHandler> jako delegat wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="278bb-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="278bb-105">Celu pozostaje tylko zdefiniować element członkowski zdarzenia i chronioną `On` *EventName* metody, która wywołuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="278bb-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="278bb-106">Poniższy kod fragment przedstawia sposób, w jaki `FlashTrackBar` formant niestandardowy definiuje niestandardowe zdarzenie `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="278bb-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="278bb-107">Aby uzyskać kompletny kod dla `FlashTrackBar` przykładowe, zobacz [jak: Utwórz formant programu Windows Forms pokazującej postęp](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="278bb-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="278bb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="278bb-108">See also</span></span>

- [<span data-ttu-id="278bb-109">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="278bb-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="278bb-110">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="278bb-110">Events</span></span>](../../../standard/events/index.md)
