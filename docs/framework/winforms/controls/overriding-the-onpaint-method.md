---
title: "Zastępowanie metody OnPaint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41205f7f0ec21e27b97d0b12415fca89ae526552
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="13ab9-102">Zastępowanie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="13ab9-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="13ab9-103">Podstawowe czynności w przypadku przesłaniania żadnych zdarzeń zdefiniowanych w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] są identyczne i przedstawiono na poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="13ab9-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="13ab9-104">Aby zastąpić zdarzenia odziedziczone</span><span class="sxs-lookup"><span data-stu-id="13ab9-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="13ab9-105">Zastąpienie chronionej `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="13ab9-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="13ab9-106">Wywołanie `On` *EventName* metody klasy podstawowej z przesłoniętych `On` *EventName* — metoda, która zarejestrowana delegatów odbierać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13ab9-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="13ab9-107"><xref:System.Windows.Forms.Control.Paint> Zdarzeń została szczegółowo opisana w tym miejscu ponieważ przesłonięcie każdego formantu formularzy systemu Windows <xref:System.Windows.Forms.Control.Paint> zdarzeń dziedziczący z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="13ab9-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="13ab9-108">Podstawowym <xref:System.Windows.Forms.Control> klasy nie może określić, jak pochodnej formantu potrzebne jest narysowanie i nie zapewnia wszelka logika malowania w <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="13ab9-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="13ab9-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Metody <xref:System.Windows.Forms.Control> po prostu wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenia zarejestrowane odbiorników.</span><span class="sxs-lookup"><span data-stu-id="13ab9-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="13ab9-110">Jeśli pracy za pośrednictwem próbki w [porady: opracowywanie prostego formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), przejrzane przykładem zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="13ab9-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="13ab9-111">Poniższy fragment kodu jest pobierana z tej próbki.</span><span class="sxs-lookup"><span data-stu-id="13ab9-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="13ab9-112"><xref:System.Windows.Forms.PaintEventArgs> Klasa zawiera dane dla <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13ab9-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="13ab9-113">Ma dwie właściwości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="13ab9-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="13ab9-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>ma zostać narysowany prostokąt i <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odwołuje się do <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="13ab9-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="13ab9-115">Klasy w <xref:System.Drawing?displayProperty=nameWithType> przestrzeni nazw są zarządzane klasy, które zapewniają dostęp do funkcji [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nową bibliotekę grafiki systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="13ab9-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="13ab9-116"><xref:System.Drawing.Graphics> Obiekt ma metody do rysowania punktów, ciągi wiersze, łuki, elipsy i wiele innych kształtów.</span><span class="sxs-lookup"><span data-stu-id="13ab9-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="13ab9-117">Wywołuje formantu jego <xref:System.Windows.Forms.Control.OnPaint%2A> metody zawsze, gdy trzeba zmienić jego wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="13ab9-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="13ab9-118">Ta metoda z kolei wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13ab9-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ab9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ab9-119">See Also</span></span>  
 [<span data-ttu-id="13ab9-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="13ab9-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="13ab9-121">Renderowanie formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="13ab9-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="13ab9-122">Dodawanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="13ab9-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
