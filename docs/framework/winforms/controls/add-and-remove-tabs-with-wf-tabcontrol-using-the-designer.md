---
title: 'Porady: dodawanie i usuwanie kart za pomocą formularzy systemu Windows TabControl przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: 51f84a1272749b92f8ef4a74771c84e01511a678
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481653"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="3e2de-102">Porady: dodawanie i usuwanie kart za pomocą formularzy systemu Windows TabControl przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e2de-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="3e2de-103">Po umieszczeniu <xref:System.Windows.Forms.TabControl> formantu w formularzu, zawiera dwie karty domyślnie.</span><span class="sxs-lookup"><span data-stu-id="3e2de-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="3e2de-104">Można dodawać lub usuwanie kart za pomocą projektanta.</span><span class="sxs-lookup"><span data-stu-id="3e2de-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="3e2de-105">Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.TabControl> kontroli.</span><span class="sxs-lookup"><span data-stu-id="3e2de-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="3e2de-106">Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3e2de-106">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e2de-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="3e2de-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3e2de-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="3e2de-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3e2de-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3e2de-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="3e2de-110">Aby dodać lub usunąć kartę, przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="3e2de-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="3e2de-111">W tagu inteligentnego formantu, kliknij polecenie **Dodaj zakładkę** lub **Usuń kartę**</span><span class="sxs-lookup"><span data-stu-id="3e2de-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="3e2de-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="3e2de-112">-or-</span></span>  
  
     <span data-ttu-id="3e2de-113">W **właściwości** okna, kliknij przycisk **wielokropka** przycisku (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości, aby otworzyć **TabPage — Edytor kolekcji**.</span><span class="sxs-lookup"><span data-stu-id="3e2de-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="3e2de-114">Kliknij przycisk **Dodaj** lub **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3e2de-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2de-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e2de-115">See Also</span></span>  
 [<span data-ttu-id="3e2de-116">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3e2de-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="3e2de-117">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="3e2de-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="3e2de-118">Instrukcje: dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="3e2de-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="3e2de-119">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="3e2de-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="3e2de-120">Instrukcje: zmienianie wyglądu kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3e2de-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
