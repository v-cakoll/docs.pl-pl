---
title: 'Instrukcje: Przenoszenie kontrolki ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 12554ee2225dbb186392b910ddfd7c2f69695e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660219"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="2aee4-102">Instrukcje: Przenoszenie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="2aee4-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="2aee4-103">W czasie projektowania, można przenieść cały menu najwyższego poziomu i ich elementów menu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="2aee4-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="2aee4-104">Możesz również przenieść elementy menu poszczególnych między menu najwyższego poziomu lub zmiana położenia elementów menu w menu.</span><span class="sxs-lookup"><span data-stu-id="2aee4-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aee4-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="2aee4-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2aee4-106">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="2aee4-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2aee4-107">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2aee4-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="2aee4-108">Aby przenieść jej elementy menu i menu najwyższego poziomu do innej lokalizacji najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="2aee4-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="2aee4-109">Kliknij i przytrzymaj naciśnięty przycisk myszy po lewej stronie, w menu, które chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="2aee4-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="2aee4-110">Przeciągnij kursor do menu najwyższego poziomu, które jest wcześniejsza niż zamierzony nowej lokalizacji, a następnie zwolnij przycisk myszy po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2aee4-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="2aee4-111">Przenosi wybrane menu z prawej strony punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="2aee4-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="2aee4-112">Aby przenieść menu najwyższego poziomu i jego elementów menu w lokalizacji z listy rozwijanej</span><span class="sxs-lookup"><span data-stu-id="2aee4-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="2aee4-113">Kliknij lewym przyciskiem myszy menu, który chcesz przenieść i naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy menu i wybierz **Wytnij** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2aee4-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2aee4-114">W menu najwyższego poziomu docelowego kliknij lewym przyciskiem myszy element menu powyżej zamierzony nowej lokalizacji naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu powyżej zamierzony nowej lokalizacji i wybierz pozycję **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2aee4-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="2aee4-115">Menu, które można wyciąć dodaje się po wybranego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="2aee4-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="2aee4-116">Aby przenieść element menu w menu przy użyciu edytora kolekcji elementów</span><span class="sxs-lookup"><span data-stu-id="2aee4-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="2aee4-117">Kliknij prawym przyciskiem myszy menu, który zawiera element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="2aee4-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="2aee4-118">Z menu skrótów wybierz polecenie **Edytuj vlastnost DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="2aee4-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="2aee4-119">W **Edytor kolekcji elementów**, kliknij lewym przyciskiem myszy element menu, którą chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="2aee4-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="2aee4-120">Kliknij przycisk klawiszy strzałek w górę i w dół, aby przenieść element menu w menu.</span><span class="sxs-lookup"><span data-stu-id="2aee4-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="2aee4-121">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="2aee4-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="2aee4-122">Aby przenieść element menu w menu za pomocą klawiatury</span><span class="sxs-lookup"><span data-stu-id="2aee4-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="2aee4-123">Naciśnij i przytrzymaj naciśnięty klawisz ALT.</span><span class="sxs-lookup"><span data-stu-id="2aee4-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="2aee4-124">Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="2aee4-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="2aee4-125">Przeciągnij element menu do nowej lokalizacji, a następnie zwolnij przycisk myszy po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2aee4-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="2aee4-126">Aby przenieść element menu do menu inny</span><span class="sxs-lookup"><span data-stu-id="2aee4-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="2aee4-127">Kliknij lewym przyciskiem myszy element menu, który chcesz przenieść i naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy element menu i wybrać **Wytnij** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2aee4-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="2aee4-128">Kliknij lewym przyciskiem myszy menu, który będzie zawierać element menu, który można wyciąć.</span><span class="sxs-lookup"><span data-stu-id="2aee4-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="2aee4-129">Kliknij lewym przyciskiem myszy element menu, który jest wcześniejsza niż zamierzony nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu, który jest wcześniejsza niż zamierzony nową lokalizację i wybierz pozycję **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="2aee4-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="2aee4-130">Element menu, który można wyciąć dodaje się po wybranego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="2aee4-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aee4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2aee4-131">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="2aee4-132">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2aee4-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
