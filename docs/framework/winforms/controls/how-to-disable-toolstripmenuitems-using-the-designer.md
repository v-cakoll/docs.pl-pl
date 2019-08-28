---
title: 'Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 692b6c11f6d58c52a0af29ed04ada45c48cae058
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046237"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="32ca3-102">Instrukcje: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="32ca3-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="32ca3-103">Można ograniczyć lub rozszerzyć polecenia, które użytkownik może wprowadzić, włączając i wyłączając elementy menu w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="32ca3-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="32ca3-104">Elementy menu są domyślnie włączone, gdy są tworzone, ale można je dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="32ca3-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="32ca3-105">Tę właściwość można manipulować w czasie projektowania w oknie **Właściwości** lub programowo przez ustawienie jej w kodzie.</span><span class="sxs-lookup"><span data-stu-id="32ca3-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="32ca3-106">Aby uzyskać więcej informacji, zobacz [jak: Wyłącz kontrolki ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="32ca3-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>

## <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="32ca3-107">Aby wyłączyć element menu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="32ca3-107">To disable a menu item at design time</span></span>

1. <span data-ttu-id="32ca3-108">Z elementem menu wybranym w formularzu Ustaw <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość na. `false`</span><span class="sxs-lookup"><span data-stu-id="32ca3-108">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>

    > [!TIP]
    > <span data-ttu-id="32ca3-109">Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje wyłączenie wszystkich elementów menu zawartych w menu.</span><span class="sxs-lookup"><span data-stu-id="32ca3-109">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="32ca3-110">Analogicznie, wyłączenie elementu menu zawierającego elementy podmenu powoduje wyłączenie elementów podmenu.</span><span class="sxs-lookup"><span data-stu-id="32ca3-110">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="32ca3-111">Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest on uznawany za dobry sposób programowania, aby ukryć i wyłączyć całe menu, ponieważ prezentuje to czysty interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="32ca3-111">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="32ca3-112">Należy ukryć i wyłączyć menu, ponieważ ukrywanie samo nie uniemożliwia dostępu do polecenia menu za pośrednictwem klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="32ca3-112">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="32ca3-113">Ustaw właściwość elementu menu najwyższego poziomu, aby `false` ukryć całe menu. <xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="32ca3-113">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>

## <a name="see-also"></a><span data-ttu-id="32ca3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32ca3-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="32ca3-115">Instrukcje: Ukryj kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="32ca3-115">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="32ca3-116">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="32ca3-116">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
