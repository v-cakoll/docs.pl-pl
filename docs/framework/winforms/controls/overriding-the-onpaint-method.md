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
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="411e0-102">Zastępowanie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="411e0-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="411e0-103">Podstawowe czynności w przypadku przesłaniania żadnych zdarzeń zdefiniowanych w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] są identyczne i przedstawiono na poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="411e0-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="411e0-104">Aby zastąpić zdarzenia odziedziczone</span><span class="sxs-lookup"><span data-stu-id="411e0-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="411e0-105">Zastąpienie chronionej `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="411e0-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="411e0-106">Wywołanie `On` *EventName* metody klasy podstawowej z przesłoniętych `On` *EventName* — metoda, która zarejestrowana delegatów odbierać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="411e0-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="411e0-107"><xref:System.Windows.Forms.Control.Paint> Zdarzeń została szczegółowo opisana w tym miejscu ponieważ przesłonięcie każdego formantu formularzy systemu Windows <xref:System.Windows.Forms.Control.Paint> zdarzeń dziedziczący z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="411e0-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="411e0-108">Podstawowym <xref:System.Windows.Forms.Control> klasy nie może określić, jak pochodnej formantu potrzebne jest narysowanie i nie zapewnia wszelka logika malowania w <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="411e0-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="411e0-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Metody <xref:System.Windows.Forms.Control> po prostu wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenia zarejestrowane odbiorników.</span><span class="sxs-lookup"><span data-stu-id="411e0-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="411e0-110">Jeśli pracy za pośrednictwem próbki w [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), przejrzane przykładem zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="411e0-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="411e0-111">Poniższy fragment kodu jest pobierana z tej próbki.</span><span class="sxs-lookup"><span data-stu-id="411e0-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="411e0-112"><xref:System.Windows.Forms.PaintEventArgs> Klasa zawiera dane dla <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="411e0-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="411e0-113">Ma dwie właściwości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="411e0-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="411e0-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ma zostać narysowany prostokąt i <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odwołuje się do <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="411e0-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="411e0-115">Klasy w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw są zarządzane klasy, które zapewniają dostęp do funkcji [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nową bibliotekę grafiki systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="411e0-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="411e0-116"><xref:System.Drawing.Graphics> Obiekt ma metody do rysowania punktów, ciągi wiersze, łuki, elipsy i wiele innych kształtów.</span><span class="sxs-lookup"><span data-stu-id="411e0-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="411e0-117">Wywołuje formantu jego <xref:System.Windows.Forms.Control.OnPaint%2A> metody zawsze, gdy trzeba zmienić jego wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="411e0-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="411e0-118">Ta metoda z kolei wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="411e0-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411e0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="411e0-119">See Also</span></span>  
 [<span data-ttu-id="411e0-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="411e0-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="411e0-121">Renderowanie kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="411e0-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="411e0-122">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="411e0-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
