---
title: 'Instrukcje: przenoszenie ToolStripMenuItems'
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
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039794"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="3e211-102">Instrukcje: przenoszenie ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="3e211-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="3e211-103">W czasie projektowania można przenieść całe menu najwyższego poziomu i ich elementy menu do innego miejsca na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3e211-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="3e211-104">Można również przenosić poszczególne elementy menu między menu najwyższego poziomu lub zmieniać pozycję elementów menu w menu.</span><span class="sxs-lookup"><span data-stu-id="3e211-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="3e211-105">Aby przenieść menu najwyższego poziomu i jego elementy menu do innej lokalizacji najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="3e211-105">To move a top-level menu and its menu items to another top-level location</span></span>

1. <span data-ttu-id="3e211-106">Kliknij i przytrzymaj lewy przycisk myszy w menu, które chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="3e211-106">Click and hold down the left mouse button on the menu that you want to move.</span></span>

2. <span data-ttu-id="3e211-107">Przeciągnij punkt wstawiania do menu najwyższego poziomu, które jest przed zamierzoną nową lokalizacją i zwolnij lewy przycisk myszy.</span><span class="sxs-lookup"><span data-stu-id="3e211-107">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>

     <span data-ttu-id="3e211-108">Wybrane menu przenosi się na prawo od punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="3e211-108">The selected menu moves to the right of the insertion point.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="3e211-109">Aby przenieść menu najwyższego poziomu i jego elementy menu do lokalizacji rozwijanej</span><span class="sxs-lookup"><span data-stu-id="3e211-109">To move a top-level menu and its menu items to a drop-down location</span></span>

1. <span data-ttu-id="3e211-110">Kliknij prawym przyciskiem myszy menu, które chcesz przenieść, a następnie naciśnij klawisze CTRL + X lub kliknij menu, a następnie wybierz polecenie Wytnij z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3e211-110">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="3e211-111">W docelowym menu najwyższego poziomu kliknij lewym przyciskiem myszy element menu powyżej zamierzonej nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem element menu powyżej zamierzonej nowej lokalizacji i wybierz polecenie **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3e211-111">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="3e211-112">Wycięte menu jest wstawiane po wybranym elemencie menu.</span><span class="sxs-lookup"><span data-stu-id="3e211-112">The menu that you cut is inserted after the selected menu item.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="3e211-113">Aby przenieść element menu w menu przy użyciu edytora kolekcji Items</span><span class="sxs-lookup"><span data-stu-id="3e211-113">To move a menu item within a menu using the Items Collection Editor</span></span>

1. <span data-ttu-id="3e211-114">Kliknij prawym przyciskiem myszy menu, które zawiera element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="3e211-114">Right-click the menu that contains the menu item you want to move.</span></span>

2. <span data-ttu-id="3e211-115">Z menu skrótów wybierz polecenie **Edytuj DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="3e211-115">From the shortcut menu, choose **Edit DropDownItems**.</span></span>

3. <span data-ttu-id="3e211-116">W **edytorze kolekcji elementów**kliknij lewym przyciskiem myszy element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="3e211-116">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>

4. <span data-ttu-id="3e211-117">Kliknij klawisze strzałek w górę i w dół, aby przenieść element menu w menu.</span><span class="sxs-lookup"><span data-stu-id="3e211-117">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>

5. <span data-ttu-id="3e211-118">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3e211-118">Click **OK**.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="3e211-119">Aby przenieść element menu w menu przy użyciu klawiatury</span><span class="sxs-lookup"><span data-stu-id="3e211-119">To move a menu item within a menu using the keyboard</span></span>

1. <span data-ttu-id="3e211-120">Naciśnij i przytrzymaj klawisz ALT.</span><span class="sxs-lookup"><span data-stu-id="3e211-120">Press and hold down the ALT key.</span></span>

2. <span data-ttu-id="3e211-121">Kliknij i przytrzymaj lewym przyciskiem myszy element menu, który chcesz przenieść.</span><span class="sxs-lookup"><span data-stu-id="3e211-121">Click and hold the left mouse button on the menu item that you want to move.</span></span>

3. <span data-ttu-id="3e211-122">Przeciągnij element menu do nowej lokalizacji i zwolnij lewym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="3e211-122">Drag the menu item to the new location and release the left mouse button.</span></span>

## <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="3e211-123">Aby przenieść element menu do innego menu</span><span class="sxs-lookup"><span data-stu-id="3e211-123">To move a menu item to another menu</span></span>

1. <span data-ttu-id="3e211-124">Kliknij lewym przyciskiem myszy element menu, który chcesz przenieść, a następnie naciśnij klawisze CTRL + X lub kliknij prawym przyciskiem myszy element menu, a następnie wybierz polecenie Wytnij z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3e211-124">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="3e211-125">Kliknij menu po lewej stronie, które będzie zawierać wycięte elementy menu.</span><span class="sxs-lookup"><span data-stu-id="3e211-125">Left-click the menu that will contain the menu item that you cut.</span></span>

3. <span data-ttu-id="3e211-126">Kliknij prawym przyciskiem myszy element menu, który jest przed zamierzoną nową lokalizacją, a następnie naciśnij klawisze CTRL + V lub kliknij element menu znajdujący się przed zamierzoną nową lokalizacją i wybierz polecenie **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3e211-126">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="3e211-127">Wycięty element menu jest wstawiany po wybranym elemencie menu.</span><span class="sxs-lookup"><span data-stu-id="3e211-127">The menu item that you cut is inserted after the selected menu item.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e211-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e211-128">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="3e211-129">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="3e211-129">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
