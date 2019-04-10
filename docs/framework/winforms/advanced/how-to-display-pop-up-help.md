---
title: 'Instrukcje: Wyświetlanie pomocy podręcznej'
ms.date: 03/30/2017
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
ms.openlocfilehash: f805840ea3b1a8aef6a289dba064c468a4da0cb0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331484"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="40762-102">Instrukcje: Wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="40762-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="40762-103">Jest jednym ze sposobów, aby wyświetlić Pomoc na formularzach Windows Forms **pomocy** przycisk znajdujący się po prawej stronie paska tytułu, dostępne za pośrednictwem <xref:System.Windows.Forms.Form.HelpButton%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="40762-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="40762-104">Ten typ ekranu Pomocy jest dobrze nadaje się do użytku z okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="40762-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="40762-105">Okna dialogowe wyświetlane w trybie modalnym (przy użyciu <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda) mają problemy z wyświetlania zewnętrzna Pomoc systemów, ponieważ modalnych okien dialogowych, które muszą zostać zamknięte przed fokus można przejść do innego okna.</span><span class="sxs-lookup"><span data-stu-id="40762-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="40762-106">Ponadto za pomocą **pomocy** przycisk wymaga, że istnieje nie **Minimalizuj** przycisk lub **Maksymalizuj** przycisk na pasku tytułu.</span><span class="sxs-lookup"><span data-stu-id="40762-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="40762-107">To Konwencji standardowe okno dialogowe, formularze, zwykle mają **Minimalizuj** i **Maksymalizuj** przycisków.</span><span class="sxs-lookup"><span data-stu-id="40762-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="40762-108">Należy pamiętać, że można również użyć <xref:System.Windows.Forms.HelpProvider> składnika formanty łączy do plików w systemie pomocy, nawet jeśli udało Ci się wdrożyć Pomoc podręczną.</span><span class="sxs-lookup"><span data-stu-id="40762-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="40762-109">Aby uzyskać więcej informacji, zobacz [zapewnianie pomocy w aplikacji Windows](how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="40762-109">For more information, see [Providing Help in a Windows Application](how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40762-110">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="40762-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="40762-111">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="40762-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="40762-112">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="40762-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="40762-113">Aby Wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="40762-113">To display pop-up Help</span></span>  
  
1. <span data-ttu-id="40762-114">Przeciągnij [HelpProvider](../controls/helpprovider-component-windows-forms.md) składnika z przybornika do formularza.</span><span class="sxs-lookup"><span data-stu-id="40762-114">Drag a [HelpProvider](../controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="40762-115">Będzie ona znajdują się w pasku w dolnej części projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40762-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="40762-116">W oknie właściwości ustaw <xref:System.Windows.Forms.Form.HelpButton%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="40762-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="40762-117">Spowoduje to wyświetlenie w niej przycisk ze znakiem zapytania po prawej stronie paska tytułu formularza.</span><span class="sxs-lookup"><span data-stu-id="40762-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3. <span data-ttu-id="40762-118">Aby <xref:System.Windows.Forms.Form.HelpButton%2A> do wyświetlania formularza <xref:System.Windows.Forms.Form.MinimizeBox%2A> i <xref:System.Windows.Forms.Form.MaximizeBox%2A> właściwości musi być równa `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> właściwością `true`i <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwość na jedną z następujących wartości: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> lub <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="40762-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4. <span data-ttu-id="40762-119">Wybierz kontrolkę, dla którego chcesz wyświetlić pomocy w formularzu i ustaw ciąg pomocy w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="40762-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="40762-120">Jest to ciąg tekstowy, który będzie wyświetlany w oknie podobne do [etykietki narzędzia](../controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="40762-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../controls/tooltip-component-windows-forms.md).</span></span>  
  
5. <span data-ttu-id="40762-121">Naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="40762-121">Press **F5**.</span></span>  
  
6. <span data-ttu-id="40762-122">Naciśnij klawisz **pomocy** znajdujący się na pasku tytułu, a następnie kliknij przycisk kontrolki, na którym można ustawić parametrów pomocy.</span><span class="sxs-lookup"><span data-stu-id="40762-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40762-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40762-123">See also</span></span>

- [<span data-ttu-id="40762-124">Pomoc w kontroli przy użyciu ToolTips</span><span class="sxs-lookup"><span data-stu-id="40762-124">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="40762-125">Integrowanie pomocy użytkownika z formularzami systemu Windows</span><span class="sxs-lookup"><span data-stu-id="40762-125">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="40762-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40762-126">Windows Forms</span></span>](../index.md)
