---
title: 'Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317678"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="e58ec-102">Instrukcje: ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e58ec-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="e58ec-103">Ukrywanie elementów menu jest sposób sterowania interfejsem użytkownika (UI), aplikacji i ograniczyć polecenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e58ec-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="e58ec-104">Często chcesz ukryć całe menu, gdy wszystkie elementy menu na nim są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="e58ec-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="e58ec-105">Przedstawia informacje o przeszkadzał dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e58ec-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="e58ec-106">Ponadto warto ukryć i Wyłącz menu lub elementu menu, jak samodzielnie ukrywanie nie uniemożliwia użytkownikowi dostęp do poleceń menu przy użyciu klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="e58ec-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="e58ec-107">Aby uzyskać więcej informacji na temat Wyłączanie elementów menu, zobacz [jak: Wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant](how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e58ec-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58ec-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="e58ec-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e58ec-109">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="e58ec-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e58ec-110">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="e58ec-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="e58ec-111">Aby ukryć menu najwyższego poziomu i jego elementów do podmenu</span><span class="sxs-lookup"><span data-stu-id="e58ec-111">To hide a top-level menu and its submenu items</span></span>  
  
1. <span data-ttu-id="e58ec-112">Wybierz element menu najwyższego poziomu i ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> lub <xref:System.Windows.Forms.ToolStripItem.Available%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="e58ec-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="e58ec-113">Po ukryciu element menu najwyższego poziomu wszystkich elementów menu w menu również są ukryte.</span><span class="sxs-lookup"><span data-stu-id="e58ec-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="e58ec-114">Po kliknięciu w innym miejscu niż na <xref:System.Windows.Forms.MenuStrip> po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Visible%2A> do `false`, element całego menu najwyższego poziomu i jego elementów podmenu są usuwane z formularza, w związku z tym przedstawiający efekt czasu wykonywania akcji.</span><span class="sxs-lookup"><span data-stu-id="e58ec-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="e58ec-115">Aby wyświetlić element ukryty menu najwyższego poziomu w czasie projektowania, kliknij pozycję <xref:System.Windows.Forms.MenuStrip> w **zasobniku składnika**w **konspekt dokumentu**, lub w górnej części siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="e58ec-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58ec-116">Rzadko spowoduje ukrycie całe menu z wyjątkiem wielu menu podrzędne w przypadku scalania dokument interfejsu (MDI).</span><span class="sxs-lookup"><span data-stu-id="e58ec-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="e58ec-117">Aby ukryć element podmenu</span><span class="sxs-lookup"><span data-stu-id="e58ec-117">To hide a submenu item</span></span>  
  
1. <span data-ttu-id="e58ec-118">Wybierz element podmenu, a następnie ustaw jego <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="e58ec-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="e58ec-119">Po ukryciu elementu podmenu pozostaje widoczna w formularzu w czasie projektowania, aby można go łatwo wybrać dalszej pracy.</span><span class="sxs-lookup"><span data-stu-id="e58ec-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="e58ec-120">Zostanie on faktycznie ukryty w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e58ec-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58ec-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e58ec-121">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="e58ec-122">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e58ec-122">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e58ec-123">Instrukcje: Wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="e58ec-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
