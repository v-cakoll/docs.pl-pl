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
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918427"
---
# <a name="constituent-controls"></a>Formanty składników
Kontrolki, które składają się na kontrolkę użytkownika lub kontrolki składowe w miarę ich określania, są stosunkowo elastyczne, gdy nastąpi do niestandardowego renderowania grafiki. Wszystkie kontrolki Windows Forms obsługują własne renderowanie za ich <xref:System.Windows.Forms.Control.OnPaint%2A> własnymi metodami. Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów i w związku z tym nie można jej wykonać po narysowaniu kontrolki. Nie oznacza to jednak, że nie można dodać kodu, aby mieć wpływ na wygląd kontrolek składników. Dodatkowe renderowanie można wykonać, dodając procedurę obsługi zdarzeń. Załóżmy na przykład, że tworzysz obiekt <xref:System.Windows.Forms.UserControl> z przyciskiem o nazwie. `MyButton` Jeśli chcesz mieć dodatkowe renderowanie wykraczające poza to <xref:System.Web.UI.WebControls.Button>, co zostało dostarczone przez, Dodaj kod do kontrolki użytkownika podobny do poniższego:  
  
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
> Niektóre kontrolki Windows Forms, takie <xref:System.Windows.Forms.TextBox>jak, są rysowane bezpośrednio przez system Windows. W tych przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda nie jest nigdy wywoływana i w rezultacie powyższego przykładu nigdy nie zostanie wywołana.  
  
 Tworzy to metodę, która jest wykonywana za każdym `MyButton.Paint` razem, gdy zdarzenie zostanie wykonane, w związku z tym dodając do formantu dodatkową graficzną reprezentację. Należy zauważyć, że nie uniemożliwia to wykonywania `MyButton.OnPaint`i w ten sposób wszystkie malowania zwykle wykonywane przez przycisk nadal będą wykonywane obok niestandardowego malowania. Aby uzyskać szczegółowe informacje na temat technologii GDI+ i renderowania niestandardowego, zobacz [Tworzenie graficznych obrazów przy użyciu interfejsu GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Jeśli chcesz mieć unikatową reprezentację formantu, najlepszym sposobem działania jest utworzenie dziedziczonej kontrolki i zapisanie niestandardowego kodu renderowania dla niego. Aby uzyskać szczegółowe informacje, zobacz [Formanty rysowane przez użytkownika](user-drawn-controls.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Kontrolki rysowane przez użytkownika](user-drawn-controls.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
