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
ms.openlocfilehash: 6fb708b81089b4fcd3678b35d1bcf7da2244c6d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525565"
---
# <a name="constituent-controls"></a>Formanty składników
Formanty, które tworzą kontrolkę użytkownika lub *formanty składników* są określane jako, są stosunkowo sztywne po przejściu do renderowania grafiki niestandardowych. Odwzorowanie za pośrednictwem ich własnych obsłużyć wszystkie formanty formularzy systemu Windows <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów, a w związku z tym nie można zablokować wykonywanie, gdy jest malowany formantu. Nie oznacza to, że nie można dodać kod, aby mieć wpływ na wygląd formantów składowych. Dodatkowe renderowania można osiągnąć przez dodawanie obsługi zdarzeń. Na przykład, załóżmy, że zostały tworzenia <xref:System.Windows.Forms.UserControl> z przycisk o nazwie `MyButton`. Zamierza ma dodatkowe renderowania poza została podana przez <xref:System.Web.UI.WebControls.Button>, należy dodać kodu do formantu użytkownika podobny do następującego:  
  
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
>  Formanty niektórych formularzy systemu Windows, takich jak <xref:System.Windows.Forms.TextBox>, są rysowane bezpośrednio w systemie Windows. W takich przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> nigdy wywoływana jest metoda i w związku z tym powyższy przykład nigdy nie zostanie wywołana.  
  
 Spowoduje to utworzenie metodę, która wykonuje zawsze `MyButton.Paint` wykonuje zdarzeń, a tym samym dodaje dodatkowe graficzną reprezentację do formantu. Należy pamiętać, że nie uniemożliwia wykonanie `MyButton.OnPaint`, i dlatego wszystkie rysowania zazwyczaj wykonywane przez przycisk będzie nadal można wykonać oprócz Twoje niestandardowe malowania. Aby uzyskać więcej informacji o technologii interfejsu GDI + i niestandardowe renderowanie, zobacz [tworzenia graficznego obrazów za pomocą GDI +](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Jeśli chcesz mieć unikatowe reprezentację formantu użytkownika najlepszy plan działania jest można utworzyć formantu dziedziczone, a następnie zapisać niestandardowe renderowanie kodu. Aby uzyskać więcej informacji, zobacz [formanty User-Drawn](../../../../docs/framework/winforms/controls/user-drawn-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Kontrolki rysowane przez użytkownika](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [Instrukcje: tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
