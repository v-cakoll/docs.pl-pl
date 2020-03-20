---
title: Definiowanie zdarzenia w formantach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 6799b229de8e8eb49dd3b8bbaffe0d08a32b7208
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142293"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="d5d88-102">Definiowanie zdarzeń w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5d88-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="d5d88-103">Aby uzyskać szczegółowe informacje na temat definiowania zdarzeń niestandardowych, zobacz [Zdarzenia](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="d5d88-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="d5d88-104">Jeśli zdefiniujesz zdarzenie, które nie ma żadnych skojarzonych danych, użyj typu podstawowego dla danych <xref:System.EventArgs>zdarzenia i użyj <xref:System.EventHandler> jako pełnomocnika zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5d88-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="d5d88-105">Wszystko, co pozostaje do zrobienia, to zdefiniować `On`element członkowski zdarzenia i chroniona metoda *EventName,* która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d5d88-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="d5d88-106">Poniższy fragment kodu `FlashTrackBar` pokazuje, jak formant `ValueChanged`niestandardowy definiuje zdarzenie niestandardowe, .</span><span class="sxs-lookup"><span data-stu-id="d5d88-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="d5d88-107">Aby uzyskać pełny `FlashTrackBar` kod przykładu, zobacz [How to: Create a Windows Forms Control that Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="d5d88-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5d88-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5d88-108">See also</span></span>

- [<span data-ttu-id="d5d88-109">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5d88-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="d5d88-110">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d5d88-110">Events</span></span>](../../../standard/events/index.md)
