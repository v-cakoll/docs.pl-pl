---
title: "Porady: tworzenie warstw obiektów na formularzach systemu Windows"
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
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d956ae8fb643d616bc0e5dc514f21ca95fa50a48
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="a0386-102">Porady: tworzenie warstw obiektów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a0386-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="a0386-103">Tworzenie interfejsu użytkownika złożonych lub praca wielu dokumentów (MDI) interfejsu, często można warstwy zarówno kontroli, jak i formularze podrzędne, aby utworzyć bardziej złożoną interfejsy użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="a0386-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="a0386-104">Aby przenieść i śledzenie kontrolek i systemu windows w ramach grupy, manipulować ich porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="a0386-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="a0386-105">*Porządek osi* jest visual warstwy formantów w formularzu wzdłuż osi z formularza (głębokość).</span><span class="sxs-lookup"><span data-stu-id="a0386-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="a0386-106">Okno w górnej części porządek nakłada się na wszystkich innych okien.</span><span class="sxs-lookup"><span data-stu-id="a0386-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="a0386-107">Wszystkie inne okna nakładać się na okna w dolnej części porządek osi z.</span><span class="sxs-lookup"><span data-stu-id="a0386-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0386-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="a0386-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a0386-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="a0386-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a0386-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a0386-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="a0386-111">Do warstwy formantów w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="a0386-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="a0386-112">Wybierz kontrolkę, która ma być warstwy.</span><span class="sxs-lookup"><span data-stu-id="a0386-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="a0386-113">Na **Format** menu wskaż **kolejności**, a następnie kliknij przycisk **Przesuń na wierzch** lub **Wyślij ponownie**.</span><span class="sxs-lookup"><span data-stu-id="a0386-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="a0386-114">Aby programowo warstwy formantów</span><span class="sxs-lookup"><span data-stu-id="a0386-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="a0386-115">Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> metoda manipulowania porządek osi z kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a0386-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="a0386-116">Na przykład jeśli <xref:System.Windows.Forms.TextBox> kontroli, `txtFirstName`, jest underneath inny formant i chcesz ma go w górnej części, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a0386-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a0386-117">Formularze systemu Windows obsługuje *zawieranie kontrolek*.</span><span class="sxs-lookup"><span data-stu-id="a0386-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="a0386-118">Zawierania formantów obejmuje umieszczenie kontrolki w formancie zawierającego, takie jak liczba <xref:System.Windows.Forms.RadioButton> steruje w obrębie <xref:System.Windows.Forms.GroupBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="a0386-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="a0386-119">Następnie można warstwy kontrolki wewnątrz formantu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="a0386-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="a0386-120">Przenoszenie pole grupy przenosi również formanty, ponieważ są one zawarte w nim.</span><span class="sxs-lookup"><span data-stu-id="a0386-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0386-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0386-121">See Also</span></span>  
 [<span data-ttu-id="a0386-122">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0386-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a0386-123">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0386-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a0386-124">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="a0386-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="a0386-125">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0386-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="a0386-126">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="a0386-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
