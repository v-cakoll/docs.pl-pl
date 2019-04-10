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
ms.openlocfilehash: 76a5a4f9b02a71616d247a1bb0f03cc0aec1d70d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224880"
---
# <a name="constituent-controls"></a>Formanty składników
Formanty, które tworzą kontrolkę użytkownika lub *formanty składników* są określane jako, są stosunkowo mało Jeśli chodzi o renderowania grafiki niestandardowych. Wszystkie kontrolki Windows Forms obsługiwać własne renderowania za pośrednictwem ich własnych <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów, a więc nie można zablokować wykonywanie, gdy kontrolka jest malowane. Nie oznacza to, jednak, że nie można dodać kod, aby wpłynąć na wygląd kontrolek składowych. Dodatkowe renderowania można osiągnąć przez dodanie obsługi zdarzeń. Załóżmy, że zostały tworzenia <xref:System.Windows.Forms.UserControl> za pomocą przycisku o nazwie `MyButton`. Jeśli chcieliby mieć dodatkowe renderowania poza została podana przez <xref:System.Web.UI.WebControls.Button>, można dodać kod do formantu użytkownika podobnego do następującego:  
  
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
>  Niektóre formy Windows pod kontrolą, takich jak <xref:System.Windows.Forms.TextBox>, są rysowane bezpośrednio przez Windows. W tych przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> nigdy nie zostanie wywołana metoda, a zatem powyższy przykład nigdy nie zostaną wywołane.  
  
 Spowoduje to utworzenie metodę, która wykonuje każdym `MyButton.Paint` wykonuje zdarzeń, a tym samym dodaje dodatkowe graficzną reprezentację do formantu. Należy pamiętać, że nie uniemożliwia wykonanie `MyButton.OnPaint`, i dlatego wszystkie malowania zazwyczaj wykonywane przez przycisk będzie nadal można wykonać oprócz Twojego niestandardowego rysowania. Aby uzyskać szczegółowe informacje o technologii GDI + i niestandardowe renderowanie, zobacz [tworzenie graficzne obrazów za pomocą GDI +](../advanced/how-to-create-graphics-objects-for-drawing.md). Jeśli chcesz mieć unikatowe reprezentacja kontroli nad swoje najlepszy plan działania jest utworzenie odziedziczoną kontrolkę, do pisania kodu niestandardowego renderowania dla niego. Aby uzyskać więcej informacji, zobacz [kontrolki User-Drawn](user-drawn-controls.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Formanty rysowane przez użytkownika](user-drawn-controls.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Różne typy formantów niestandardowych](varieties-of-custom-controls.md)
