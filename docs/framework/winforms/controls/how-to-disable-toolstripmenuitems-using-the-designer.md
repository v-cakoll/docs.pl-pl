---
title: "Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f704e99622900d8c37c8ddd5054a3c5ad920bc6b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="977eb-102">Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="977eb-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="977eb-103">Można ograniczyć lub rozszerzyć poleceń, które mogą spowodować, że użytkownik, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="977eb-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="977eb-104">Elementy menu są włączone domyślnie, gdy są one tworzone, ale to można dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="977eb-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="977eb-105">Tej właściwości można manipulować w czasie projektowania w **właściwości** okna lub programowo przez ustawienie dla niego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="977eb-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="977eb-106">Aby uzyskać więcej informacji, zobacz [porady: wyłączanie ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="977eb-106">For more information, see [How to: Disable ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="977eb-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="977eb-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="977eb-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="977eb-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="977eb-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="977eb-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="977eb-110">Aby wyłączyć element menu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="977eb-110">To disable a menu item at design time</span></span>  
  
1.  <span data-ttu-id="977eb-111">Z elementem menu wybranego w formularzu, należy ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="977eb-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="977eb-112">Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu.</span><span class="sxs-lookup"><span data-stu-id="977eb-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="977eb-113">Podobnie wyłączenie elementu menu, który zawiera elementy podmenu wyłącza elementów podmenu.</span><span class="sxs-lookup"><span data-stu-id="977eb-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="977eb-114">Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest uznawany dobrze programowania zarówno Ukryj i Wyłącz całe menu, za stwarza czystą interfejs.</span><span class="sxs-lookup"><span data-stu-id="977eb-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="977eb-115">Należy zarówno Ukryj i Wyłącz menu, jak ukrywanie wyłącznie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="977eb-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="977eb-116">Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość element menu najwyższego poziomu do `false` ukrycia całego menu.</span><span class="sxs-lookup"><span data-stu-id="977eb-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="977eb-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="977eb-117">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="977eb-118">Instrukcje: ukrywanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="977eb-118">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="977eb-119">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="977eb-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
