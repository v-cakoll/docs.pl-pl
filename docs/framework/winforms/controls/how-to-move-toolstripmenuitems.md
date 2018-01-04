---
title: 'Porady: przenoszenie ToolStripMenuItems'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1cb718b3738ac93b284b0b438b08d1e721349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="aa619-102">Porady: przenoszenie ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="aa619-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="aa619-103">W czasie projektowania, można przenieść całej menu najwyższego poziomu i ich elementów menu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="aa619-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="aa619-104">Można również przenieść poszczególnych elementów menu między menu najwyższego poziomu lub zmienić jego położenie elementów menu w menu.</span><span class="sxs-lookup"><span data-stu-id="aa619-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa619-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="aa619-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aa619-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="aa619-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aa619-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="aa619-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="aa619-108">Aby przenieść do innej lokalizacji najwyższego poziomu menu najwyższego poziomu i jego elementów menu</span><span class="sxs-lookup"><span data-stu-id="aa619-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="aa619-109">Kliknij i przytrzymaj lewy przycisk myszy w menu, które chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="aa619-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="aa619-110">Przeciągnij punkt wstawiania do menu najwyższego poziomu, które jest przed zamierzone nowej lokalizacji i zwolnij lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="aa619-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="aa619-111">Przenosi wybrane menu z prawej strony punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="aa619-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="aa619-112">Aby przenieść lokalizację z listy rozwijanej menu najwyższego poziomu i jej elementów menu</span><span class="sxs-lookup"><span data-stu-id="aa619-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="aa619-113">Lewym przyciskiem myszy menu, które chcesz przenieść i naciśnij klawisze CTRL + X, lub kliknij prawym przyciskiem myszy menu i wybierz **Wytnij** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="aa619-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aa619-114">W menu najwyższego poziomu docelowego lewym przyciskiem myszy element menu powyżej zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu powyżej zamierzone nowej lokalizacji i wybierz **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="aa619-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="aa619-115">Menu Wycinanie są wstawiane po wybranego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="aa619-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="aa619-116">Aby przenieść element menu w menu za pomocą edytora kolekcji elementy</span><span class="sxs-lookup"><span data-stu-id="aa619-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="aa619-117">Kliknij prawym przyciskiem myszy menu, które zawiera element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="aa619-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="aa619-118">Z menu skrótów wybierz **Edytuj elementy DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="aa619-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="aa619-119">W **edytora kolekcji elementy**, lewym przyciskiem myszy element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="aa619-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="aa619-120">Kliknij przycisk klawiszy strzałek w górę i w dół, można przenieść elementu menu w menu.</span><span class="sxs-lookup"><span data-stu-id="aa619-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="aa619-121">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="aa619-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="aa619-122">Aby przenieść element menu w menu za pomocą klawiatury</span><span class="sxs-lookup"><span data-stu-id="aa619-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="aa619-123">Naciśnij i przytrzymaj klawisz ALT.</span><span class="sxs-lookup"><span data-stu-id="aa619-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="aa619-124">Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="aa619-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="aa619-125">Przeciągnij element menu do nowej lokalizacji i zwolnij lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="aa619-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="aa619-126">Aby przenieść element menu innym menu</span><span class="sxs-lookup"><span data-stu-id="aa619-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="aa619-127">Lewym przyciskiem myszy element menu, który chcesz przenieść i naciśnij klawisze CTRL + X, lub kliknij prawym przyciskiem myszy element menu i wybierz **Wytnij** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="aa619-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="aa619-128">W lewym przyciskiem myszy menu, która będzie zawierać element menu, który Wycinanie.</span><span class="sxs-lookup"><span data-stu-id="aa619-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="aa619-129">Lewym przyciskiem myszy element menu, który jest przed zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu, który jest przed zamierzone nowej lokalizacji, a następnie wybierz **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="aa619-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="aa619-130">Element menu, który Wycinanie są wstawiane po wybranego elementu menu.</span><span class="sxs-lookup"><span data-stu-id="aa619-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa619-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa619-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="aa619-132">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="aa619-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
