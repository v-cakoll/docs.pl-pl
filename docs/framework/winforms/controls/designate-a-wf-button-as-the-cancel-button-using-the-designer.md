---
title: 'Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: faffeafc0cbe67c3b40297144ec85acd94956da9
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366807"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="4a507-102">Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="4a507-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="4a507-103">W każdym formularzu Windows, można wyznaczyć <xref:System.Windows.Forms.Button> formantu przycisk Anuluj.</span><span class="sxs-lookup"><span data-stu-id="4a507-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="4a507-104">Kliknięto przycisk Anuluj w każdym przypadku, gdy użytkownik naciśnie klawisz ESC, niezależnie od tego, którego fokus ma inne kontrolki na formularzu.</span><span class="sxs-lookup"><span data-stu-id="4a507-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="4a507-105">Taki przycisk jest zwykle zaprogramowane umożliwia użytkownikowi szybkie zakończyć operację bez zobowiązania do dowolnej akcji.</span><span class="sxs-lookup"><span data-stu-id="4a507-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a507-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="4a507-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4a507-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="4a507-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4a507-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4a507-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="4a507-109">Aby wyznaczyć przycisk Anuluj</span><span class="sxs-lookup"><span data-stu-id="4a507-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="4a507-110">Wybierz formularz, w którym znajduje się przycisk.</span><span class="sxs-lookup"><span data-stu-id="4a507-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="4a507-111">W **właściwości** okna, ustaw dla formularza <xref:System.Windows.Forms.Form.CancelButton%2A> właściwość <xref:System.Windows.Forms.Button> jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="4a507-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a507-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a507-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="4a507-113">Button, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4a507-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="4a507-114">Sposoby wyboru kontrolki przycisku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a507-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="4a507-115">Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a507-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="4a507-116">Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="4a507-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="4a507-117">Button, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4a507-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
