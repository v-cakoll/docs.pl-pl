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
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182415"
---
# <a name="constituent-controls"></a><span data-ttu-id="f08e9-102">Formanty składników</span><span class="sxs-lookup"><span data-stu-id="f08e9-102">Constituent Controls</span></span>
<span data-ttu-id="f08e9-103">Formanty, które tworzą formant użytkownika lub *formantów składników,* jak są one określane jako, są stosunkowo nieelastyczne, jeśli chodzi o niestandardowe renderowania grafiki.</span><span class="sxs-lookup"><span data-stu-id="f08e9-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="f08e9-104">Wszystkie formanty formularzy systemu Windows <xref:System.Windows.Forms.Control.OnPaint%2A> obsługują własne renderowanie za pomocą własnej metody.</span><span class="sxs-lookup"><span data-stu-id="f08e9-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="f08e9-105">Ponieważ ta metoda jest chroniona, nie jest dostępna dla dewelopera i w związku z tym nie można uniemożliwić wykonywania, gdy formant jest malowany.</span><span class="sxs-lookup"><span data-stu-id="f08e9-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="f08e9-106">Nie oznacza to jednak, że nie można dodać kodu, aby wpłynąć na wygląd formantów składowych.</span><span class="sxs-lookup"><span data-stu-id="f08e9-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="f08e9-107">Dodatkowe renderowanie można wykonać, dodając program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f08e9-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="f08e9-108">Załóżmy na przykład, <xref:System.Windows.Forms.UserControl> że byłeś `MyButton`autorem przycisku o nazwie .</span><span class="sxs-lookup"><span data-stu-id="f08e9-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="f08e9-109">Jeśli chcesz mieć dodatkowe renderowanie poza <xref:System.Web.UI.WebControls.Button>to, co zostało dostarczone przez program , należy dodać kod do formantu użytkownika podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f08e9-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="f08e9-110">Niektóre formanty formularzy systemu Windows, takie jak <xref:System.Windows.Forms.TextBox>, są malowane bezpośrednio przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="f08e9-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="f08e9-111">W takich przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> metoda nigdy nie jest wywoływana, a zatem powyższy przykład nigdy nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="f08e9-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="f08e9-112">Spowoduje to utworzenie metody, która `MyButton.Paint` wykonuje za każdym razem, gdy zdarzenie wykonuje, dodając w ten sposób dodatkową reprezentację graficzną do formantu.</span><span class="sxs-lookup"><span data-stu-id="f08e9-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="f08e9-113">Należy pamiętać, że nie `MyButton.OnPaint`przeszkadza to w wykonaniu , a tym samym wszystkie obrazy zwykle wykonywane za pomocą przycisku będą nadal wykonywane oprócz niestandardowego malowania.</span><span class="sxs-lookup"><span data-stu-id="f08e9-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="f08e9-114">Aby uzyskać szczegółowe informacje na temat technologii GDI+ i renderowania niestandardowego, zobacz [Tworzenie obrazów graficznych za pomocą GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="f08e9-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="f08e9-115">Jeśli chcesz mieć unikatową reprezentację formantu, najlepszym sposobem działania jest utworzenie formantu dziedziczonego i napisanie niestandardowego kodu renderowania dla niego.</span><span class="sxs-lookup"><span data-stu-id="f08e9-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="f08e9-116">Aby uzyskać szczegółowe informacje, zobacz [Formanty rysowane przez użytkownika](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f08e9-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08e9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f08e9-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="f08e9-118">Formanty rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="f08e9-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="f08e9-119">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="f08e9-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="f08e9-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f08e9-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
