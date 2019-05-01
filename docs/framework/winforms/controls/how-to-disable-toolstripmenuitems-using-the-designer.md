---
title: 'Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954248"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="c5e1c-102">Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c5e1c-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="c5e1c-103">Można ograniczyć lub rozszerzenia poleceń, które użytkownik może wprowadzić, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="c5e1c-104">Elementy menu są włączone domyślnie, gdy są one tworzone, ale to może być regulowany poprzez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="c5e1c-105">Tę właściwość można manipulować w czasie projektowania w **właściwości** okna lub ustawiając je programowo w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="c5e1c-106">Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie kontrolki ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="c5e1c-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5e1c-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c5e1c-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c5e1c-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c5e1c-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="c5e1c-110">Aby wyłączyć element menu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c5e1c-110">To disable a menu item at design time</span></span>  
  
1. <span data-ttu-id="c5e1c-111">W menu elementu wybranego w formularzu, ustawiać <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="c5e1c-112">Wyłączanie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="c5e1c-113">Podobnie wyłączenie element menu, który zawiera elementy podmenu powoduje wyłączenie elementów podmenu.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="c5e1c-114">Jeśli wszystkie polecenia w danym menu są dostępne dla użytkownika, uważa się dobrą praktyką programowania, aby ukryć i wyłączyć całe menu, jak to stanowi interfejs użytkownika czyste.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="c5e1c-115">Należy zarówno ukryć i Wyłącz menu, zgodnie z ukrywanie samodzielnie nie uniemożliwia dostępu do polecenia menu za pomocą klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="c5e1c-116">Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości elementu menu najwyższego poziomu do `false` ukryć całe menu.</span><span class="sxs-lookup"><span data-stu-id="c5e1c-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e1c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5e1c-117">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="c5e1c-118">Instrukcje: Ukrywanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c5e1c-118">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="c5e1c-119">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c5e1c-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
