---
title: "Porady: wyświetlanie pomocy podręcznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d139c283d002ac76005f22385d83190144c5082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="e1c14-102">Porady: wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="e1c14-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="e1c14-103">Jednym ze sposobów Wyświetla Pomoc w formularzach systemu Windows odbywa się za pośrednictwem **pomocy** przycisk znajdujący się po prawej stronie paska tytułu dostępny za pośrednictwem <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1c14-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="e1c14-104">Ten typ wyświetlania Pomocy jest dobrze nadaje się do użytku z okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="e1c14-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="e1c14-105">Okna dialogowe wyświetlane w trybie modalnym (z <xref:System.Windows.Forms.Form.ShowDialog%2A> — metoda) ma problem otworzeniem zewnętrzna Pomoc systemów, ponieważ muszą być zamknięte przed fokus można przejść do innego okna modalne okna dialogowe.</span><span class="sxs-lookup"><span data-stu-id="e1c14-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="e1c14-106">Ponadto przy użyciu **pomocy** przycisk wymóg nie **Minimalizuj** przycisk lub **Maksymalizuj** przycisku znajdującego się na pasku tytułu.</span><span class="sxs-lookup"><span data-stu-id="e1c14-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="e1c14-107">Jest to standardowe okno dialogowe Konwencja, formularze zazwyczaj mają **Minimalizuj** i **Maksymalizuj** przycisków.</span><span class="sxs-lookup"><span data-stu-id="e1c14-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="e1c14-108">Należy pamiętać, że można również użyć <xref:System.Windows.Forms.HelpProvider> składnika, aby połączyć formanty do plików w systemie pomocy, nawet jeśli zaimplementowano pomoc wyskakująca.</span><span class="sxs-lookup"><span data-stu-id="e1c14-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="e1c14-109">Aby uzyskać więcej informacji, zobacz [zapewnianie pomocy w aplikacji Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="e1c14-109">For more information, see [Providing Help in a Windows Application](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1c14-110">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="e1c14-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e1c14-111">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="e1c14-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e1c14-112">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e1c14-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="e1c14-113">Aby wyświetlić Pomoc wyskakująca</span><span class="sxs-lookup"><span data-stu-id="e1c14-113">To display pop-up Help</span></span>  
  
1.  <span data-ttu-id="e1c14-114">Przeciągnij [helpprovider —](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) składnika z przybornika do formularza.</span><span class="sxs-lookup"><span data-stu-id="e1c14-114">Drag a [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="e1c14-115">Będzie ona sit na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e1c14-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="e1c14-116">W oknie właściwości ustaw <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="e1c14-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="e1c14-117">Spowoduje to wyświetlenie w niej przycisk ze znakiem zapytania po prawej stronie paska tytułu formularza.</span><span class="sxs-lookup"><span data-stu-id="e1c14-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3.  <span data-ttu-id="e1c14-118">Aby <xref:System.Windows.Forms.Form.HelpButton%2A> do wyświetlania formularza <xref:System.Windows.Forms.Form.MinimizeBox%2A> i <xref:System.Windows.Forms.Form.MaximizeBox%2A> musi mieć wartość właściwości `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> ustawioną właściwość `true`i <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość na jedną z następujących wartości: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> lub <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="e1c14-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4.  <span data-ttu-id="e1c14-119">Wybierz kontrolkę, dla którego chcesz wyświetlić pomocy w formularzu i ustaw ciąg pomocy w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1c14-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="e1c14-120">Jest to ciąg tekstowy, który będzie wyświetlany w oknie podobny do [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e1c14-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span></span>  
  
5.  <span data-ttu-id="e1c14-121">Naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="e1c14-121">Press **F5**.</span></span>  
  
6.  <span data-ttu-id="e1c14-122">Naciśnij klawisz **pomocy** znajdującego się na pasku tytułu, a następnie kliknij przycisk kontrolki, w którym można ustawić ciąg pomocy.</span><span class="sxs-lookup"><span data-stu-id="e1c14-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c14-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1c14-123">See Also</span></span>  
 [<span data-ttu-id="e1c14-124">Pomoc do kontrolek przy użyciu etykietek narzędzi</span><span class="sxs-lookup"><span data-stu-id="e1c14-124">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="e1c14-125">Integrowanie pomocy użytkownika z formularzami Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1c14-125">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="e1c14-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1c14-126">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
