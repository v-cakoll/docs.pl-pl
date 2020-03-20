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
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="b8d6a-102">Zastępowanie metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="b8d6a-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="b8d6a-103">Podstawowe kroki zastępowania dowolnego zdarzenia zdefiniowanego w platformie .NET Framework są identyczne i są podsumowane na poniższej liście.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="b8d6a-104">Aby zastąpić zdarzenie dziedziczone</span><span class="sxs-lookup"><span data-stu-id="b8d6a-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="b8d6a-105">Zastąpuj `On`chroniona metoda *EventName.*</span><span class="sxs-lookup"><span data-stu-id="b8d6a-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="b8d6a-106">Wywołanie `On` *Metody EventName* klasy podstawowej z `On`metody Overridden *EventName,* tak aby zarejestrowani delegaci odbierali zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="b8d6a-107">Zdarzenie <xref:System.Windows.Forms.Control.Paint> zostało szczegółowo omówione w tym miejscu, ponieważ <xref:System.Windows.Forms.Control.Paint> każdy formant Windows <xref:System.Windows.Forms.Control>Forms musi zastąpić zdarzenie, które dziedziczy po .</span><span class="sxs-lookup"><span data-stu-id="b8d6a-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="b8d6a-108">Klasa <xref:System.Windows.Forms.Control> podstawowa nie wie, jak formant pochodny musi zostać narysowany <xref:System.Windows.Forms.Control.OnPaint%2A> i nie zapewnia żadnej logiki malowania w metodzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b8d6a-109">Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control> po prostu wysyła <xref:System.Windows.Forms.Control.Paint> zdarzenie do zarejestrowanych odbiorników zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="b8d6a-110">Jeśli przepracowano za pośrednictwem przykładu w [Jak: Opracowanie prostego formantu formularzy systemu Windows](how-to-develop-a-simple-windows-forms-control.md), widzieliśmy przykład zastąpienia <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="b8d6a-111">Poniższy fragment kodu jest pobierany z tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="b8d6a-112">Klasa <xref:System.Windows.Forms.PaintEventArgs> zawiera dane <xref:System.Windows.Forms.Control.Paint> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="b8d6a-113">Ma dwie właściwości, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="b8d6a-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>jest prostokątem do malowania, a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> właściwość odnosi <xref:System.Drawing.Graphics> się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="b8d6a-115">Klasy w <xref:System.Drawing?displayProperty=nameWithType> obszarze nazw są klasami zarządzanymi, które zapewniają dostęp do funkcji GDI+, nowej biblioteki grafiki systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="b8d6a-116">Obiekt <xref:System.Drawing.Graphics> ma metody rysowania punktów, ciągów, linii, łuków, elips i wielu innych kształtów.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="b8d6a-117">Formant wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> jego metody, gdy trzeba zmienić jego wyświetlania wizualnego.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="b8d6a-118">Ta metoda z kolei <xref:System.Windows.Forms.Control.Paint> podnosi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b8d6a-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d6a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8d6a-119">See also</span></span>

- [<span data-ttu-id="b8d6a-120">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b8d6a-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="b8d6a-121">Renderowanie formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8d6a-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="b8d6a-122">Dodawanie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b8d6a-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
