---
title: "Formanty składników"
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
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d03b69c334148313b0cd495fad1b2dfd13df833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="constituent-controls"></a><span data-ttu-id="05bc2-102">Formanty składników</span><span class="sxs-lookup"><span data-stu-id="05bc2-102">Constituent Controls</span></span>
<span data-ttu-id="05bc2-103">Formanty, które tworzą kontrolkę użytkownika lub *formanty składników* są określane jako, są stosunkowo sztywne po przejściu do renderowania grafiki niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="05bc2-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="05bc2-104">Odwzorowanie za pośrednictwem ich własnych obsłużyć wszystkie formanty formularzy systemu Windows <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="05bc2-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="05bc2-105">Ponieważ ta metoda jest chroniona, nie jest dostępna dla deweloperów, a w związku z tym nie można zablokować wykonywanie, gdy jest malowany formantu.</span><span class="sxs-lookup"><span data-stu-id="05bc2-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="05bc2-106">Nie oznacza to, że nie można dodać kod, aby mieć wpływ na wygląd formantów składowych.</span><span class="sxs-lookup"><span data-stu-id="05bc2-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="05bc2-107">Dodatkowe renderowania można osiągnąć przez dodawanie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="05bc2-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="05bc2-108">Na przykład, załóżmy, że zostały tworzenia <xref:System.Windows.Forms.UserControl> z przycisk o nazwie `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="05bc2-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="05bc2-109">Zamierza ma dodatkowe renderowania poza została podana przez <xref:System.Web.UI.WebControls.Button>, należy dodać kodu do formantu użytkownika podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="05bc2-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
>  <span data-ttu-id="05bc2-110">Formanty niektórych formularzy systemu Windows, takich jak <xref:System.Windows.Forms.TextBox>, są rysowane bezpośrednio w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="05bc2-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="05bc2-111">W takich przypadkach <xref:System.Windows.Forms.Control.OnPaint%2A> nigdy wywoływana jest metoda i w związku z tym powyższy przykład nigdy nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="05bc2-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="05bc2-112">Spowoduje to utworzenie metodę, która wykonuje zawsze `MyButton.Paint` wykonuje zdarzeń, a tym samym dodaje dodatkowe graficzną reprezentację do formantu.</span><span class="sxs-lookup"><span data-stu-id="05bc2-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="05bc2-113">Należy pamiętać, że nie uniemożliwia wykonanie `MyButton.OnPaint`, i dlatego wszystkie rysowania zazwyczaj wykonywane przez przycisk będzie nadal można wykonać oprócz Twoje niestandardowe malowania.</span><span class="sxs-lookup"><span data-stu-id="05bc2-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="05bc2-114">Aby uzyskać więcej informacji o technologii interfejsu GDI + i niestandardowe renderowanie, zobacz [tworzenia graficznego obrazów za pomocą GDI +](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="05bc2-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="05bc2-115">Jeśli chcesz mieć unikatowe reprezentację formantu użytkownika najlepszy plan działania jest można utworzyć formantu dziedziczone, a następnie zapisać niestandardowe renderowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="05bc2-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="05bc2-116">Aby uzyskać więcej informacji, zobacz [formanty User-Drawn](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="05bc2-116">For details, see [User-Drawn Controls](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bc2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05bc2-117">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="05bc2-118">Kontrolki rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="05bc2-118">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [<span data-ttu-id="05bc2-119">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="05bc2-119">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="05bc2-120">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="05bc2-120">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
