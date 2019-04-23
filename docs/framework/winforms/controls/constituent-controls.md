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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224880"
---
# <a name="constituent-controls"></a><span data-ttu-id="39110-102">Formanty składników</span><span class="sxs-lookup"><span data-stu-id="39110-102">Constituent Controls</span></span>
<span data-ttu-id="39110-103">Formanty, które tworzą kontrolkę użytkownika lub *formanty składników* są określane jako, są stosunkowo mało Jeśli chodzi o renderowania grafiki niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="39110-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="39110-104">Wszystkie kontrolki Windows Forms obsługiwać własne renderowania za pośrednictwem ich własnych <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="39110-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="39110-105">Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów, a więc nie można zablokować wykonywanie, gdy kontrolka jest malowane.</span><span class="sxs-lookup"><span data-stu-id="39110-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="39110-106">Nie oznacza to, jednak, że nie można dodać kod, aby wpłynąć na wygląd kontrolek składowych.</span><span class="sxs-lookup"><span data-stu-id="39110-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="39110-107">Dodatkowe renderowania można osiągnąć przez dodanie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="39110-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="39110-108">Załóżmy, że zostały tworzenia <xref:System.Windows.Forms.UserControl> za pomocą przycisku o nazwie `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="39110-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="39110-109">Jeśli chcieliby mieć dodatkowe renderowania poza została podana przez <xref:System.Web.UI.WebControls.Button>, można dodać kod do formantu użytkownika podobnego do następującego:</span><span class="sxs-lookup"><span data-stu-id="39110-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
>  <span data-ttu-id="39110-110">Niektóre formy Windows pod kontrolą, takich jak <xref:System.Windows.Forms.TextBox>, są rysowane bezpośrednio przez Windows.</span><span class="sxs-lookup"><span data-stu-id="39110-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="39110-111">W tych przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> nigdy nie zostanie wywołana metoda, a zatem powyższy przykład nigdy nie zostaną wywołane.</span><span class="sxs-lookup"><span data-stu-id="39110-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="39110-112">Spowoduje to utworzenie metodę, która wykonuje każdym `MyButton.Paint` wykonuje zdarzeń, a tym samym dodaje dodatkowe graficzną reprezentację do formantu.</span><span class="sxs-lookup"><span data-stu-id="39110-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="39110-113">Należy pamiętać, że nie uniemożliwia wykonanie `MyButton.OnPaint`, i dlatego wszystkie malowania zazwyczaj wykonywane przez przycisk będzie nadal można wykonać oprócz Twojego niestandardowego rysowania.</span><span class="sxs-lookup"><span data-stu-id="39110-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="39110-114">Aby uzyskać szczegółowe informacje o technologii GDI + i niestandardowe renderowanie, zobacz [tworzenie graficzne obrazów za pomocą GDI +](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="39110-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="39110-115">Jeśli chcesz mieć unikatowe reprezentacja kontroli nad swoje najlepszy plan działania jest utworzenie odziedziczoną kontrolkę, do pisania kodu niestandardowego renderowania dla niego.</span><span class="sxs-lookup"><span data-stu-id="39110-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="39110-116">Aby uzyskać więcej informacji, zobacz [kontrolki User-Drawn](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="39110-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39110-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39110-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="39110-118">Kontrolki rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="39110-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="39110-119">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="39110-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="39110-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="39110-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
