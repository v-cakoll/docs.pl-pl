---
title: "Porady: dodawanie i usuwanie kart za pomocą formularzy systemu Windows TabControl przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02bcf434baee0c27ca2674817df0e4033effb125
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="66ccb-102">Porady: dodawanie i usuwanie kart za pomocą formularzy systemu Windows TabControl przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="66ccb-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="66ccb-103">Po umieszczeniu <xref:System.Windows.Forms.TabControl> formantu w formularzu, zawiera dwie karty domyślnie.</span><span class="sxs-lookup"><span data-stu-id="66ccb-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="66ccb-104">Można dodawać i usuwać kart przy użyciu narzędzia Projektant.</span><span class="sxs-lookup"><span data-stu-id="66ccb-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="66ccb-105">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.TabControl> formantu.</span><span class="sxs-lookup"><span data-stu-id="66ccb-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="66ccb-106">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="66ccb-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66ccb-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="66ccb-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="66ccb-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="66ccb-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="66ccb-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="66ccb-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="66ccb-110">Aby dodać lub usunąć kartę, przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="66ccb-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="66ccb-111">W tagu formantu, kliknij polecenie **Dodaj kartę** lub **Usuń kartę**</span><span class="sxs-lookup"><span data-stu-id="66ccb-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="66ccb-112">—lub—</span><span class="sxs-lookup"><span data-stu-id="66ccb-112">-or-</span></span>  
  
     <span data-ttu-id="66ccb-113">W **właściwości** okna, kliknij przycisk **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TabControl.TabPages%2A> właściwości, aby otworzyć **edytora kolekcji TabPage**.</span><span class="sxs-lookup"><span data-stu-id="66ccb-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="66ccb-114">Kliknij przycisk **Dodaj** lub **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="66ccb-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ccb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66ccb-115">See Also</span></span>  
 [<span data-ttu-id="66ccb-116">TabControl — formant</span><span class="sxs-lookup"><span data-stu-id="66ccb-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="66ccb-117">Informacje o formancie TabControl</span><span class="sxs-lookup"><span data-stu-id="66ccb-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="66ccb-118">Porady: Dodawanie formantu do strony karty</span><span class="sxs-lookup"><span data-stu-id="66ccb-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="66ccb-119">Porady: wyłączanie kart</span><span class="sxs-lookup"><span data-stu-id="66ccb-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="66ccb-120">Porady: Zmienianie wyglądu składnika TabControl formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="66ccb-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
