---
title: 'Instrukcje: wyłączanie ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046225"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="6e076-102">Instrukcje: wyłączanie ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6e076-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="6e076-103">Można ograniczyć lub rozszerzyć polecenia, które użytkownik może wprowadzić, włączając i wyłączając elementy menu w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e076-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="6e076-104">Elementy menu są domyślnie włączone, gdy są tworzone, ale można je dostosować za pomocą <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e076-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="6e076-105">Tę właściwość można manipulować w czasie projektowania w oknie **Właściwości** lub programowo przez ustawienie jej w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6e076-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="6e076-106">Aby programowo wyłączyć element menu</span><span class="sxs-lookup"><span data-stu-id="6e076-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="6e076-107">W metodzie, w której ustawiasz właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> `false`właściwość.</span><span class="sxs-lookup"><span data-stu-id="6e076-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="6e076-108">Wyłączenie elementu menu pierwszy lub najwyższego poziomu w menu powoduje ukrycie wszystkich elementów menu zawartych w menu, ale nie powoduje ich wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="6e076-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="6e076-109">Analogicznie, wyłączenie elementu menu zawierającego elementy podmenu powoduje ukrycie elementów podmenu, ale nie powoduje ich wyłączenia.</span><span class="sxs-lookup"><span data-stu-id="6e076-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="6e076-110">Jeśli wszystkie polecenia w danym menu są niedostępne dla użytkownika, jest on uznawany za dobry sposób programowania, aby ukryć i wyłączyć całe menu, ponieważ prezentuje to czysty interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6e076-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="6e076-111">Należy ukryć i wyłączyć menu, a następnie wyłączyć każdy element i podmenu w menu, ponieważ ukrywanie samo nie uniemożliwia dostępu do polecenia menu za pośrednictwem klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="6e076-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="6e076-112">Ustaw właściwość elementu menu najwyższego poziomu, aby `false` ukryć całe menu. <xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="6e076-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e076-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e076-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="6e076-114">Instrukcje: Ukryj kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6e076-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="6e076-115">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6e076-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
