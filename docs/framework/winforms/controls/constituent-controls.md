---
title: Formanty składników
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182415"
---
# <a name="constituent-controls"></a>Formanty składników
Formanty, które tworzą formant użytkownika lub *formantów składników,* jak są one określane jako, są stosunkowo nieelastyczne, jeśli chodzi o niestandardowe renderowania grafiki. Wszystkie formanty formularzy systemu Windows <xref:System.Windows.Forms.Control.OnPaint%2A> obsługują własne renderowanie za pomocą własnej metody. Ponieważ ta metoda jest chroniona, nie jest dostępna dla dewelopera i w związku z tym nie można uniemożliwić wykonywania, gdy formant jest malowany. Nie oznacza to jednak, że nie można dodać kodu, aby wpłynąć na wygląd formantów składowych. Dodatkowe renderowanie można wykonać, dodając program obsługi zdarzeń. Załóżmy na przykład, <xref:System.Windows.Forms.UserControl> że byłeś `MyButton`autorem przycisku o nazwie . Jeśli chcesz mieć dodatkowe renderowanie poza <xref:System.Web.UI.WebControls.Button>to, co zostało dostarczone przez program , należy dodać kod do formantu użytkownika podobne do następujących:  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> Niektóre formanty formularzy systemu Windows, takie jak <xref:System.Windows.Forms.TextBox>, są malowane bezpośrednio przez system Windows. W takich przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> metoda nigdy nie jest wywoływana, a zatem powyższy przykład nigdy nie zostanie wywołana.  
  
 Spowoduje to utworzenie metody, która `MyButton.Paint` wykonuje za każdym razem, gdy zdarzenie wykonuje, dodając w ten sposób dodatkową reprezentację graficzną do formantu. Należy pamiętać, że nie `MyButton.OnPaint`przeszkadza to w wykonaniu , a tym samym wszystkie obrazy zwykle wykonywane za pomocą przycisku będą nadal wykonywane oprócz niestandardowego malowania. Aby uzyskać szczegółowe informacje na temat technologii GDI+ i renderowania niestandardowego, zobacz [Tworzenie obrazów graficznych za pomocą GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Jeśli chcesz mieć unikatową reprezentację formantu, najlepszym sposobem działania jest utworzenie formantu dziedziczonego i napisanie niestandardowego kodu renderowania dla niego. Aby uzyskać szczegółowe informacje, zobacz [Formanty rysowane przez użytkownika](user-drawn-controls.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Formanty rysowane przez użytkownika](user-drawn-controls.md)
- [Instrukcje: tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
