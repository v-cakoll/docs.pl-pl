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
ms.openlocfilehash: 89440b083aa6b2dc3f95e0878075a20aeac65b32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525271"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="22988-102">Porady: dodawanie i usuwanie kart za pomocą formularzy systemu Windows TabControl przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="22988-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="22988-103">Po umieszczeniu <xref:System.Windows.Forms.TabControl> formantu w formularzu, zawiera dwie karty domyślnie.</span><span class="sxs-lookup"><span data-stu-id="22988-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="22988-104">Można dodawać i usuwać kart przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="22988-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="22988-105">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.TabControl> formantu.</span><span class="sxs-lookup"><span data-stu-id="22988-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="22988-106">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="22988-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22988-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="22988-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="22988-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="22988-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="22988-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="22988-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="22988-110">Aby dodać lub usunąć kartę, przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="22988-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="22988-111">W tagu formantu, kliknij polecenie **Dodaj kartę** lub **Usuń kartę**</span><span class="sxs-lookup"><span data-stu-id="22988-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="22988-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="22988-112">-or-</span></span>  
  
     <span data-ttu-id="22988-113">W **właściwości** okna, kliknij przycisk **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości, aby otworzyć **edytora kolekcji TabPage**.</span><span class="sxs-lookup"><span data-stu-id="22988-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="22988-114">Kliknij przycisk **Dodaj** lub **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="22988-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22988-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22988-115">See Also</span></span>  
 [<span data-ttu-id="22988-116">TabControl, kontrolka</span><span class="sxs-lookup"><span data-stu-id="22988-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="22988-117">TabControl, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="22988-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="22988-118">Instrukcje: dodawanie kontrolki do karty</span><span class="sxs-lookup"><span data-stu-id="22988-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="22988-119">Instrukcje: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="22988-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="22988-120">Instrukcje: zmienianie wyglądu kontrolki TabControl formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22988-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
