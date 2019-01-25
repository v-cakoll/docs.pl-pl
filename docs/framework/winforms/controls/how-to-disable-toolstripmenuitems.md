---
title: 'Instrukcje: Wyłączanie kontrolki ToolStripMenuItems'
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
ms.openlocfilehash: 2516080708bba207c3a1d028f2e5a2411974ae5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705339"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="de1b3-102">Instrukcje: Wyłączanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="de1b3-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="de1b3-103">Można ograniczyć lub rozszerzenia poleceń, które użytkownik może wprowadzić, włączanie i wyłączanie elementów menu w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de1b3-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="de1b3-104">Elementy menu są włączone domyślnie, gdy są one tworzone, ale to może być regulowany poprzez <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="de1b3-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="de1b3-105">Tę właściwość można manipulować w czasie projektowania w **właściwości** okna lub ustawiając je programowo w kodzie.</span><span class="sxs-lookup"><span data-stu-id="de1b3-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="de1b3-106">Aby programowo wyłączyć element menu</span><span class="sxs-lookup"><span data-stu-id="de1b3-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="de1b3-107">W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="de1b3-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    >  <span data-ttu-id="de1b3-108">Wyłączanie elementu menu pierwszy lub najwyższego poziomu w menu powoduje ukrycie wszystkich elementów menu zawartych w menu, ale nie je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="de1b3-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="de1b3-109">Podobnie wyłączenie element menu, który zawiera elementy podmenu ukrywa elementy podmenu, ale nie je wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="de1b3-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="de1b3-110">Jeśli wszystkie polecenia w danym menu są dostępne dla użytkownika, uważa się dobrą praktyką programowania, aby ukryć i wyłączyć całe menu, jak to stanowi interfejs użytkownika czyste.</span><span class="sxs-lookup"><span data-stu-id="de1b3-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="de1b3-111">Należy ukrywać i Wyłącz menu i wyłączyć każdego elementu i elementu podmenu w menu, ponieważ ukrycie samodzielnie nie uniemożliwia dostęp do polecenia menu za pomocą klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="de1b3-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="de1b3-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości elementu menu najwyższego poziomu do `false` ukryć całe menu.</span><span class="sxs-lookup"><span data-stu-id="de1b3-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1b3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de1b3-113">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="de1b3-114">Instrukcje: Ukrywanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="de1b3-114">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="de1b3-115">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="de1b3-115">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
