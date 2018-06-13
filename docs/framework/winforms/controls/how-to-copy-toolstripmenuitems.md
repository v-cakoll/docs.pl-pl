---
title: 'Porady: kopiowanie ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: 238516f18037a75b1d254d95086e22a970fadf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530484"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="8b50e-102">Porady: kopiowanie ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="8b50e-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="8b50e-103">W czasie projektowania, możesz skopiować cały menu najwyższego poziomu i ich elementy podmenu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="8b50e-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="8b50e-104">Można również skopiować poszczególnych elementów menu między menu najwyższego poziomu lub zmienić jego położenie elementów menu w menu.</span><span class="sxs-lookup"><span data-stu-id="8b50e-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="8b50e-105">Aby skopiować menu najwyższego poziomu i jego podmenu w innej lokalizacji najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="8b50e-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="8b50e-106">Lewym przyciskiem myszy menu, które chcesz skopiować i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy menu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="8b50e-107">Lewym menu najwyższego poziomu, które po zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu najwyższego poziomu, który jest przed zamierzone nowej lokalizacji, a następnie wybierz **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="8b50e-108">Menu, które zostały skopiowane dodaje się przed zaznaczone menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8b50e-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="8b50e-109">Aby skopiować menu najwyższego poziomu, a jego podmenu na lokalizację z listy rozwijanej</span><span class="sxs-lookup"><span data-stu-id="8b50e-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="8b50e-110">Lewym przyciskiem myszy menu, które chcesz przenieść i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy menu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="8b50e-111">W menu najwyższego poziomu docelowego lewym przyciskiem myszy element podmenu powyżej zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element podmenu powyżej zamierzone nowej lokalizacji, a następnie wybierz **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="8b50e-112">Menu, które zostały skopiowane zostanie wstawiony przed elementem wybranym podmenu.</span><span class="sxs-lookup"><span data-stu-id="8b50e-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="8b50e-113">Aby skopiować element podmenu do innego menu</span><span class="sxs-lookup"><span data-stu-id="8b50e-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="8b50e-114">Lewym przyciskiem myszy element podmenu, który chcesz skopiować i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy element podmenu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="8b50e-115">W lewym przyciskiem myszy menu, która będzie zawierać Wycinanie element podmenu.</span><span class="sxs-lookup"><span data-stu-id="8b50e-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="8b50e-116">Lewym przyciskiem myszy element podmenu przed zamierzone nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element podmenu przed zamierzone nowej lokalizacji, a następnie wybierz **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="8b50e-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="8b50e-117">Element podmenu skopiowany zostanie wstawiony przed elementem wybranym podmenu.</span><span class="sxs-lookup"><span data-stu-id="8b50e-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b50e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b50e-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="8b50e-119">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8b50e-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
