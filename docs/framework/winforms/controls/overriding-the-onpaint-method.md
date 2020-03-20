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
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182036"
---
# <a name="overriding-the-onpaint-method"></a>Zastępowanie metody OnPaint
Podstawowe kroki zastępowania dowolnego zdarzenia zdefiniowanego w platformie .NET Framework są identyczne i są podsumowane na poniższej liście.  
  
#### <a name="to-override-an-inherited-event"></a>Aby zastąpić zdarzenie dziedziczone  
  
1. Zastąpuj `On`chroniona metoda *EventName.*  
  
2. Wywołanie `On` *Metody EventName* klasy podstawowej z `On`metody Overridden *EventName,* tak aby zarejestrowani delegaci odbierali zdarzenie.  
  
 Zdarzenie <xref:System.Windows.Forms.Control.Paint> zostało szczegółowo omówione w tym miejscu, ponieważ <xref:System.Windows.Forms.Control.Paint> każdy formant Windows <xref:System.Windows.Forms.Control>Forms musi zastąpić zdarzenie, które dziedziczy po . Klasa <xref:System.Windows.Forms.Control> podstawowa nie wie, jak formant pochodny musi zostać narysowany <xref:System.Windows.Forms.Control.OnPaint%2A> i nie zapewnia żadnej logiki malowania w metodzie. Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control> po prostu wysyła <xref:System.Windows.Forms.Control.Paint> zdarzenie do zarejestrowanych odbiorników zdarzeń.  
  
 Jeśli przepracowano za pośrednictwem przykładu w [Jak: Opracowanie prostego formantu formularzy systemu Windows](how-to-develop-a-simple-windows-forms-control.md), widzieliśmy przykład zastąpienia <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Poniższy fragment kodu jest pobierany z tego przykładu.  
  
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
  
 Klasa <xref:System.Windows.Forms.PaintEventArgs> zawiera dane <xref:System.Windows.Forms.Control.Paint> dla zdarzenia. Ma dwie właściwości, jak pokazano w poniższym kodzie.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>jest prostokątem do malowania, a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odnosi <xref:System.Drawing.Graphics> się do obiektu. Klasy w <xref:System.Drawing?displayProperty=nameWithType> obszarze nazw są klasami zarządzanymi, które zapewniają dostęp do funkcji GDI+, nowej biblioteki grafiki systemu Windows. Obiekt <xref:System.Drawing.Graphics> ma metody rysowania punktów, ciągów, linii, łuków, elips i wielu innych kształtów.  
  
 Formant wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> jego metody, gdy trzeba zmienić jego wyświetlania wizualnego. Ta metoda z kolei <xref:System.Windows.Forms.Control.Paint> podnosi zdarzenie.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../standard/events/index.md)
- [Renderowanie formantu formularzy systemu Windows](rendering-a-windows-forms-control.md)
- [Dodawanie zdarzenia](defining-an-event-in-windows-forms-controls.md)
