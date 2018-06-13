---
title: Zastępowanie metody OnPaint
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: fc41158e9a3d5d331b391f0f28701612012becf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537219"
---
# <a name="overriding-the-onpaint-method"></a>Zastępowanie metody OnPaint
Podstawowe czynności w przypadku przesłaniania żadnych zdarzeń zdefiniowanych w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] są identyczne i przedstawiono na poniższej liście.  
  
#### <a name="to-override-an-inherited-event"></a>Aby zastąpić zdarzenia odziedziczone  
  
1.  Zastąpienie chronionej `On` *EventName* metody.  
  
2.  Wywołanie `On` *EventName* metody klasy podstawowej z przesłoniętych `On` *EventName* — metoda, która zarejestrowana delegatów odbierać zdarzenia.  
  
 <xref:System.Windows.Forms.Control.Paint> Zdarzeń została szczegółowo opisana w tym miejscu ponieważ przesłonięcie każdego formantu formularzy systemu Windows <xref:System.Windows.Forms.Control.Paint> zdarzeń dziedziczący z <xref:System.Windows.Forms.Control>. Podstawowym <xref:System.Windows.Forms.Control> klasy nie może określić, jak pochodnej formantu potrzebne jest narysowanie i nie zapewnia wszelka logika malowania w <xref:System.Windows.Forms.Control.OnPaint%2A> metody. <xref:System.Windows.Forms.Control.OnPaint%2A> Metody <xref:System.Windows.Forms.Control> po prostu wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenia zarejestrowane odbiorników.  
  
 Jeśli pracy za pośrednictwem próbki w [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), przejrzane przykładem zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> — metoda. Poniższy fragment kodu jest pobierana z tej próbki.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs> Klasa zawiera dane dla <xref:System.Windows.Forms.Control.Paint> zdarzeń. Ma dwie właściwości, jak pokazano w poniższym kodzie.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ma zostać narysowany prostokąt i <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odwołuje się do <xref:System.Drawing.Graphics> obiektu. Klasy w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw są zarządzane klasy, które zapewniają dostęp do funkcji [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nową bibliotekę grafiki systemu Windows. <xref:System.Drawing.Graphics> Obiekt ma metody do rysowania punktów, ciągi wiersze, łuki, elipsy i wiele innych kształtów.  
  
 Wywołuje formantu jego <xref:System.Windows.Forms.Control.OnPaint%2A> metody zawsze, gdy trzeba zmienić jego wyświetlania. Ta metoda z kolei wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Renderowanie kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Definiowanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
