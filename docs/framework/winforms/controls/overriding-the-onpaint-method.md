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
ms.openlocfilehash: fbc0a82f82afcc59384246b58437d521d56d708b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646960"
---
# <a name="overriding-the-onpaint-method"></a>Zastępowanie metody OnPaint
Podstawowe kroki zastąpienie dowolnego zdarzenia, zdefiniowany w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] są identyczne i są podsumowane w poniższej liście.  
  
#### <a name="to-override-an-inherited-event"></a>Aby zastąpić zdarzenia odziedziczone  
  
1.  Zastąp chronionego `On` *EventName* metody.  
  
2.  Wywołaj `On` *EventName* metody klasy bazowej ze zgodnym z przesłoniętą `On` *EventName* metody, która zarejestrowana delegaci otrzymają zdarzenie.  
  
 <xref:System.Windows.Forms.Control.Paint> Zdarzeń została szczegółowo opisana w tym miejscu ponieważ przesłonięcie każdego formantu Windows Forms <xref:System.Windows.Forms.Control.Paint> zdarzeń, która jest dziedziczona z <xref:System.Windows.Forms.Control>. Podstawa <xref:System.Windows.Forms.Control> klasy nie wie, jak pochodnej kontrolki musi zostać narysowany i nie zapewnia dowolnej logiki malowania w <xref:System.Windows.Forms.Control.OnPaint%2A> metody. <xref:System.Windows.Forms.Control.OnPaint%2A> Metody <xref:System.Windows.Forms.Control> po prostu wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenie, aby odbiorcy zarejestrowanych zdarzeń.  
  
 W przypadku pracy przy użyciu przykładu w [jak: opracowywanie prostego formantu formularzy Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), przejrzane przykładem zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Poniższy fragment kodu jest pobierana z tej próbki.  
  
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
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs> Klasy zawiera dane dla <xref:System.Windows.Forms.Control.Paint> zdarzeń. Posiada dwie właściwości, jak pokazano w poniższym kodzie.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ma prostokąt do narysowania i <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odwołuje się do <xref:System.Drawing.Graphics> obiektu. Klasy w <xref:System.Drawing?displayProperty=nameWithType> odbywa się przestrzeń nazw klas, które zapewniają dostęp do funkcji [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nową bibliotekę grafiki Windows. <xref:System.Drawing.Graphics> Obiekt posiada metody do rysowania punkty, ciągi, wiersze, łuki, wielokropek i wiele innych kształtów.  
  
 Kontrolki wywołuje jego <xref:System.Windows.Forms.Control.OnPaint%2A> metody zawsze wtedy, gdy trzeba zmienić jego wizualizacji do wyświetlenia. Z kolei wywołuje tę metodę <xref:System.Windows.Forms.Control.Paint> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../../docs/standard/events/index.md)  
 [Renderowanie kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Definiowanie zdarzenia](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
