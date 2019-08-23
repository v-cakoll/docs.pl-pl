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
# <a name="constituent-controls"></a><span data-ttu-id="dceec-102">Formanty składników</span><span class="sxs-lookup"><span data-stu-id="dceec-102">Constituent Controls</span></span>
<span data-ttu-id="dceec-103">Kontrolki, które składają się na kontrolkę użytkownika lub kontrolki składowe w miarę ich określania, są stosunkowo elastyczne, gdy nastąpi do niestandardowego renderowania grafiki.</span><span class="sxs-lookup"><span data-stu-id="dceec-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="dceec-104">Wszystkie kontrolki Windows Forms obsługują własne renderowanie za ich <xref:System.Windows.Forms.Control.OnPaint%2A> własnymi metodami.</span><span class="sxs-lookup"><span data-stu-id="dceec-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="dceec-105">Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów i w związku z tym nie można jej wykonać po narysowaniu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="dceec-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="dceec-106">Nie oznacza to jednak, że nie można dodać kodu, aby mieć wpływ na wygląd kontrolek składników.</span><span class="sxs-lookup"><span data-stu-id="dceec-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="dceec-107">Dodatkowe renderowanie można wykonać, dodając procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dceec-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="dceec-108">Załóżmy na przykład, że tworzysz obiekt <xref:System.Windows.Forms.UserControl> z przyciskiem o nazwie. `MyButton`</span><span class="sxs-lookup"><span data-stu-id="dceec-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="dceec-109">Jeśli chcesz mieć dodatkowe renderowanie wykraczające poza to <xref:System.Web.UI.WebControls.Button>, co zostało dostarczone przez, Dodaj kod do kontrolki użytkownika podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="dceec-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="dceec-110">Niektóre kontrolki Windows Forms, takie <xref:System.Windows.Forms.TextBox>jak, są rysowane bezpośrednio przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="dceec-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="dceec-111">W tych przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda nie jest nigdy wywoływana i w rezultacie powyższego przykładu nigdy nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="dceec-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="dceec-112">Tworzy to metodę, która jest wykonywana za każdym `MyButton.Paint` razem, gdy zdarzenie zostanie wykonane, w związku z tym dodając do formantu dodatkową graficzną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="dceec-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="dceec-113">Należy zauważyć, że nie uniemożliwia to wykonywania `MyButton.OnPaint`i w ten sposób wszystkie malowania zwykle wykonywane przez przycisk nadal będą wykonywane obok niestandardowego malowania.</span><span class="sxs-lookup"><span data-stu-id="dceec-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="dceec-114">Aby uzyskać szczegółowe informacje na temat technologii GDI+ i renderowania niestandardowego, zobacz [Tworzenie graficznych obrazów przy użyciu interfejsu GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="dceec-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="dceec-115">Jeśli chcesz mieć unikatową reprezentację formantu, najlepszym sposobem działania jest utworzenie dziedziczonej kontrolki i zapisanie niestandardowego kodu renderowania dla niego.</span><span class="sxs-lookup"><span data-stu-id="dceec-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="dceec-116">Aby uzyskać szczegółowe informacje, zobacz [Formanty rysowane przez użytkownika](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dceec-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dceec-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dceec-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="dceec-118">Kontrolki rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="dceec-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="dceec-119">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="dceec-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="dceec-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="dceec-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
