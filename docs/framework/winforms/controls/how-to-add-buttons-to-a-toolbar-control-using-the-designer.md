---
title: "Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5339d946f771b7ba187813dd67860aaa63a21eb3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="8718e-102">Porady: dodawanie przycisków do formantu ToolBar przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="8718e-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="8718e-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="8718e-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="8718e-104">Integralną częścią <xref:System.Windows.Forms.ToolBar> formant jest przycisków, Dodaj do niej.</span><span class="sxs-lookup"><span data-stu-id="8718e-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="8718e-105">Te mogą służyć do zapewnienia łatwy dostęp do poleceń menu lub alternatywnie mogą być umieszczane w innym miejscu interfejsu użytkownika aplikacji do udostępnienia poleceń, aby użytkownicy nie są dostępne w strukturze menu.</span><span class="sxs-lookup"><span data-stu-id="8718e-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="8718e-106">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ToolBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="8718e-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="8718e-107">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8718e-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8718e-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="8718e-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8718e-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="8718e-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8718e-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8718e-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="8718e-111">Aby dodać przyciski w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8718e-111">To add buttons at design time</span></span>  
  
1.  <span data-ttu-id="8718e-112">Wybierz <xref:System.Windows.Forms.ToolBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="8718e-112">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="8718e-113">W **właściwości** okna, kliknij przycisk <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwości, aby go zaznaczyć, a następnie kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) przycisk, aby otworzyć **edytora kolekcji ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="8718e-113">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="8718e-114">Użyj **Dodaj** i **Usuń** przyciski dodawania i usuwania przycisków z <xref:System.Windows.Forms.ToolBar> formantu.</span><span class="sxs-lookup"><span data-stu-id="8718e-114">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
4.  <span data-ttu-id="8718e-115">Skonfiguruj właściwości poszczególnych przycisków w **właściwości** oknie, w którym zostanie wyświetlony w okienku po prawej stronie edytora.</span><span class="sxs-lookup"><span data-stu-id="8718e-115">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="8718e-116">W poniższej tabeli przedstawiono niektóre ważne właściwości wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="8718e-116">The following table shows some important properties to consider.</span></span>  
  
    |<span data-ttu-id="8718e-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="8718e-117">Property</span></span>|<span data-ttu-id="8718e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8718e-118">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="8718e-119">Ustawia menu, który będzie wyświetlany na przycisku paska narzędzi z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="8718e-119">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="8718e-120">Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="8718e-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="8718e-121">Ta właściwość ma wystąpienie <xref:System.Windows.Forms.ContextMenu> klasy jako odwołanie.</span><span class="sxs-lookup"><span data-stu-id="8718e-121">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="8718e-122">Określa, czy częściowo spoczywa Przełącz styl przycisku paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8718e-122">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="8718e-123">Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="8718e-123">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="8718e-124">Określa, czy Przełącz styl przycisku paska narzędzi jest obecnie w stanie włożony.</span><span class="sxs-lookup"><span data-stu-id="8718e-124">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="8718e-125">Przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> musi mieć ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> lub <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span><span class="sxs-lookup"><span data-stu-id="8718e-125">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="8718e-126">Ustawia styl przycisku paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8718e-126">Sets the style of the toolbar button.</span></span> <span data-ttu-id="8718e-127">Musi być jedną z wartości w <xref:System.Windows.Forms.ToolBarButtonStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8718e-127">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="8718e-128">Ciąg tekstowy wyświetlany przez przycisk.</span><span class="sxs-lookup"><span data-stu-id="8718e-128">The text string displayed by the button.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="8718e-129">Tekst wyświetlany jako etykietka narzędzia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="8718e-129">The text that appears as a ToolTip for the button.</span></span>|  
  
5.  <span data-ttu-id="8718e-130">Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć panele określony.</span><span class="sxs-lookup"><span data-stu-id="8718e-130">Click **OK** to close the dialog box and create the panels you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8718e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8718e-131">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="8718e-132">Instrukcje: określanie ikony dla przycisku kontrolki ToolBar</span><span class="sxs-lookup"><span data-stu-id="8718e-132">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [<span data-ttu-id="8718e-133">Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar</span><span class="sxs-lookup"><span data-stu-id="8718e-133">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="8718e-134">ToolBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8718e-134">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="8718e-135">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8718e-135">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
