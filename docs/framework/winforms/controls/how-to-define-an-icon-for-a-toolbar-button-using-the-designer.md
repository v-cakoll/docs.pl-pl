---
title: 'Instrukcje: Określanie ikony dla przycisku kontrolki ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 2099738d5b666aa305d678c962c0b203d3ab67b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717742"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="1f37a-102">Instrukcje: Określanie ikony dla przycisku kontrolki ToolBar przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="1f37a-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="1f37a-103"><xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="1f37a-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1f37a-104"><xref:System.Windows.Forms.ToolBar> przyciski będą mogli wyświetlać ikony w ich obrębie, ułatwiający identyfikację przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1f37a-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="1f37a-105">Jest to realizowane poprzez dodawanie obrazów do <xref:System.Windows.Forms.ImageList> składnika i kojarząc ją z <xref:System.Windows.Forms.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f37a-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="1f37a-106">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.ToolBar> kontroli i <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="1f37a-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="1f37a-107">Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1f37a-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f37a-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="1f37a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1f37a-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="1f37a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1f37a-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1f37a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="1f37a-111">Aby ustawić ikony dla przycisku kontrolki toolbar w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="1f37a-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="1f37a-112">Dodawanie obrazów do <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="1f37a-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="1f37a-113">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="1f37a-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="1f37a-114">Wybierz <xref:System.Windows.Forms.ToolBar> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1f37a-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="1f37a-115">W **właściwości** oknie <xref:System.Windows.Forms.ToolBar> kontrolki <xref:System.Windows.Forms.ToolBar.ImageList%2A> właściwość <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="1f37a-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="1f37a-116">Kliknij przycisk <xref:System.Windows.Forms.ToolBar> kontrolki <xref:System.Windows.Forms.ToolBar.Buttons%2A> właściwość, aby go zaznaczyć, a następnie kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) przycisk, aby otworzyć **ToolBarButton — Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="1f37a-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="1f37a-117">Użyj **Dodaj** przycisk, aby dodać przyciski do <xref:System.Windows.Forms.ToolBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="1f37a-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="1f37a-118">W **właściwości** wyświetlone w okienku po prawej stronie okno **ToolBarButton — Edytor kolekcji**ustaw <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> właściwości przycisku paska narzędzi na jedną z wartości na liście, który jest rysowana od obrazy dodane do <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="1f37a-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f37a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f37a-119">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="1f37a-120">Instrukcje: Wyzwalacz zdarzenia Menu dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="1f37a-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="1f37a-121">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1f37a-121">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="1f37a-122">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="1f37a-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
