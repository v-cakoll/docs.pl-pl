---
title: 'Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039743"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="715e9-102">Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="715e9-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="715e9-103">Ukrywanie elementów menu to sposób sterowania interfejsem użytkownika aplikacji i ograniczania poleceń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="715e9-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="715e9-104">Często warto ukryć całe menu, gdy wszystkie elementy menu są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="715e9-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="715e9-105">Spowoduje to zmniejszenie liczby odniesień użytkownika.</span><span class="sxs-lookup"><span data-stu-id="715e9-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="715e9-106">Ponadto możesz chcieć ukryć i wyłączyć menu lub element menu, ponieważ samo ukrywanie nie uniemożliwia użytkownikowi uzyskania dostępu do polecenia menu przy użyciu klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="715e9-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="715e9-107">Aby uzyskać więcej informacji na temat wyłączania [elementów menu, zobacz How to: Wyłącz kontrolki ToolStripMenuItems przy użyciu narzędzia](how-to-disable-toolstripmenuitems-using-the-designer.md)Projektant.</span><span class="sxs-lookup"><span data-stu-id="715e9-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="715e9-108">Aby ukryć menu najwyższego poziomu i jego elementy podmenu</span><span class="sxs-lookup"><span data-stu-id="715e9-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="715e9-109">Wybierz element menu najwyższego poziomu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> Właściwość <xref:System.Windows.Forms.ToolStripItem.Available%2A> or na `false`.</span><span class="sxs-lookup"><span data-stu-id="715e9-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="715e9-110">Ukrycie elementu menu najwyższego poziomu spowoduje również ukrycie wszystkich elementów menu w tym menu.</span><span class="sxs-lookup"><span data-stu-id="715e9-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="715e9-111">Jeśli klikniesz pozycję inna niż w przypadku <xref:System.Windows.Forms.MenuStrip> `false`ustawienia <xref:System.Windows.Forms.ToolStripItem.Visible%2A> na, cały element menu najwyższego poziomu i jego elementy podmenu znikną z formularza, w ten sposób pokazujesz efekt czasu wykonywania akcji.</span><span class="sxs-lookup"><span data-stu-id="715e9-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="715e9-112">Aby wyświetlić ukryty element menu najwyższego poziomu w czasie projektowania, kliknij na <xref:System.Windows.Forms.MenuStrip> pasku **składnika**, w menu **Konspekt dokumentu**lub u góry siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="715e9-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
>  <span data-ttu-id="715e9-113">W scenariuszu scalania nie będzie rzadko ukrywane całe menu poza menu podrzędnym wielu dokumentów (MDI).</span><span class="sxs-lookup"><span data-stu-id="715e9-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="715e9-114">Aby ukryć element podmenu</span><span class="sxs-lookup"><span data-stu-id="715e9-114">To hide a submenu item</span></span>

1. <span data-ttu-id="715e9-115">Wybierz element podmenu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość na. `false`</span><span class="sxs-lookup"><span data-stu-id="715e9-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="715e9-116">Ukrycie elementu podmenu pozostanie widoczny w formularzu w czasie projektowania, aby można było łatwo wybrać go do dalszej pracy.</span><span class="sxs-lookup"><span data-stu-id="715e9-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="715e9-117">Będzie ona faktycznie ukryta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="715e9-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="715e9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="715e9-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="715e9-119">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="715e9-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="715e9-120">Instrukcje: Wyłączanie kontrolki ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="715e9-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
