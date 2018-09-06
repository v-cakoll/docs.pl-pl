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
ms.openlocfilehash: 60ae01ca63f895bfb1c7aabbe3337596cd13933d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732978"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Definiowanie zdarzeń w formantach formularzy systemu Windows
Aby uzyskać szczegółowe informacje na temat definiowania zdarzenia niestandardowe, zobacz [zdarzenia](../../../../docs/standard/events/index.md). Jeśli zdefiniujesz zdarzenie, które nie ma żadnych skojarzonych danych, należy użyć typu podstawowego danych zdarzenia <xref:System.EventArgs>i użyj <xref:System.EventHandler> jako delegat wydarzenia. Celu pozostaje tylko zdefiniować element członkowski zdarzenia i chronioną `On` *EventName* metody, która wywołuje zdarzenia.  
  
 Poniższy kod fragment przedstawia sposób, w jaki `FlashTrackBar` formant niestandardowy definiuje niestandardowe zdarzenie `ValueChanged`. Aby uzyskać kompletny kod dla `FlashTrackBar` przykładowe, zobacz [jak: utworzyć Windows Forms kontroli, pokazuje postępu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Zdarzenia](../../../../docs/standard/events/index.md)
