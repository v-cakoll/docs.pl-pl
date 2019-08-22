---
title: 'Instrukcje: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666201"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="e7184-102">Instrukcje: określanie ikony dla przycisku ToolBar przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e7184-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="e7184-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip></span><span class="sxs-lookup"><span data-stu-id="e7184-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="e7184-104"><xref:System.Windows.Forms.ToolBar>przyciski mogą wyświetlać w nich ikony umożliwiające łatwą identyfikację użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e7184-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="e7184-105">Jest to realizowane poprzez dodanie obrazów do <xref:System.Windows.Forms.ImageList> składnika i skojarzenie go <xref:System.Windows.Forms.ToolBar> z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="e7184-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>

<span data-ttu-id="e7184-106">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ToolBar> formant i <xref:System.Windows.Forms.ImageList> składnik.</span><span class="sxs-lookup"><span data-stu-id="e7184-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="e7184-107">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e7184-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="e7184-108">Aby ustawić ikonę dla przycisku paska narzędzi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e7184-108">To set an icon for a toolbar button at design time</span></span>

1. <span data-ttu-id="e7184-109">Dodaj obrazy do <xref:System.Windows.Forms.ImageList> składnika.</span><span class="sxs-lookup"><span data-stu-id="e7184-109">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="e7184-110">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia](how-to-add-or-remove-imagelist-images-with-the-designer.md)Projektant.</span><span class="sxs-lookup"><span data-stu-id="e7184-110">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>

2. <span data-ttu-id="e7184-111"><xref:System.Windows.Forms.ToolBar> Zaznacz kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e7184-111">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>

3. <span data-ttu-id="e7184-112">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ImageList%2A> właściwość kontrolki na <xref:System.Windows.Forms.ImageList> składnik.</span><span class="sxs-lookup"><span data-stu-id="e7184-112">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>

4. <span data-ttu-id="e7184-113">![](./media/visual-studio-ellipsis-button.png)Kliknij właściwość kontrolki,abyjązaznaczyć,anastępniekliknijprzyciskwielokropka(...)woknowłaściwościprogramuVisualStudio.),abyotworzyćEdytorkolekcjiToolBarButton.<xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.Buttons%2A></span><span class="sxs-lookup"><span data-stu-id="e7184-113">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

5. <span data-ttu-id="e7184-114">Użyj przycisku **Dodaj** , aby dodać przyciski do <xref:System.Windows.Forms.ToolBar> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e7184-114">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>

6. <span data-ttu-id="e7184-115">W oknie **Właściwości** , które pojawia się w okienku po prawej stronie **edytora kolekcji ToolBarButton** <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> , ustaw właściwość każdego przycisku paska narzędzi na jedną z wartości na liście, która jest rysowana na podstawie obrazów dodanych do <xref:System.Windows.Forms.ImageList> składnik.</span><span class="sxs-lookup"><span data-stu-id="e7184-115">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7184-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7184-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="e7184-117">Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="e7184-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="e7184-118">ToolBar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e7184-118">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="e7184-119">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="e7184-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
