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
ms.openlocfilehash: b1eb24aaa9ed3bfede41fc5a9a80fcbdc9f749a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936451"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="17694-102">Zastępowanie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="17694-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="17694-103">Podstawowe kroki zastąpienie dowolnego zdarzenia, zdefiniowany w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] są identyczne i są podsumowane w poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="17694-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="17694-104">Aby zastąpić zdarzenia odziedziczone</span><span class="sxs-lookup"><span data-stu-id="17694-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="17694-105">Zastąp chronionego `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="17694-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="17694-106">Wywołaj `On` *EventName* metody klasy bazowej ze zgodnym z przesłoniętą `On` *EventName* metody, która zarejestrowana delegaci otrzymają zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="17694-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="17694-107"><xref:System.Windows.Forms.Control.Paint> Zdarzeń została szczegółowo opisana w tym miejscu ponieważ przesłonięcie każdego formantu Windows Forms <xref:System.Windows.Forms.Control.Paint> zdarzeń, która jest dziedziczona z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="17694-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="17694-108">Podstawa <xref:System.Windows.Forms.Control> klasy nie wie, jak pochodnej kontrolki musi zostać narysowany i nie zapewnia dowolnej logiki malowania w <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17694-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="17694-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Metody <xref:System.Windows.Forms.Control> po prostu wywołuje <xref:System.Windows.Forms.Control.Paint> zdarzenie, aby odbiorcy zarejestrowanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17694-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="17694-110">W przypadku pracy przy użyciu przykładu w [jak: Tworzenie prostego formantu formularzy Windows](how-to-develop-a-simple-windows-forms-control.md), jak już wspomniano przykładem zastępowanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17694-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="17694-111">Poniższy fragment kodu jest pobierana z tej próbki.</span><span class="sxs-lookup"><span data-stu-id="17694-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="17694-112"><xref:System.Windows.Forms.PaintEventArgs> Klasy zawiera dane dla <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17694-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="17694-113">Posiada dwie właściwości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="17694-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="17694-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ma prostokąt do narysowania i <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odwołuje się do <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="17694-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="17694-115">Klasy w <xref:System.Drawing?displayProperty=nameWithType> odbywa się przestrzeń nazw klas, które zapewniają dostęp do funkcji [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nową bibliotekę grafiki Windows.</span><span class="sxs-lookup"><span data-stu-id="17694-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="17694-116"><xref:System.Drawing.Graphics> Obiekt posiada metody do rysowania punkty, ciągi, wiersze, łuki, wielokropek i wiele innych kształtów.</span><span class="sxs-lookup"><span data-stu-id="17694-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="17694-117">Kontrolki wywołuje jego <xref:System.Windows.Forms.Control.OnPaint%2A> metody zawsze wtedy, gdy trzeba zmienić jego wizualizacji do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="17694-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="17694-118">Z kolei wywołuje tę metodę <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="17694-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17694-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17694-119">See also</span></span>

- [<span data-ttu-id="17694-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="17694-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="17694-121">Renderowanie kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17694-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="17694-122">Definiowanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="17694-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
