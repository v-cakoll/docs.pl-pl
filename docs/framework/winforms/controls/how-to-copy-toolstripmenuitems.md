---
title: 'Instrukcje: kopiowanie ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: c59af175a6ee23395e19247efd8fa15e6d19ae66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334344"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="faf52-102">Instrukcje: kopiowanie ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="faf52-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="faf52-103">W czasie projektowania, możesz skopiować cały menu najwyższego poziomu i ich elementów podmenu w inne miejsce na <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="faf52-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="faf52-104">Możesz również skopiować poszczególnych elementów menu między menu najwyższego poziomu lub zmiana położenia elementów menu w menu.</span><span class="sxs-lookup"><span data-stu-id="faf52-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="faf52-105">Aby skopiować menu najwyższego poziomu i jego elementów podmenu do innej lokalizacji najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="faf52-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1. <span data-ttu-id="faf52-106">Kliknij lewym przyciskiem myszy menu, który chcesz skopiować i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy menu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="faf52-107">Kliknij lewym przyciskiem myszy menu najwyższego poziomu, które po zamierzony nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element menu najwyższego poziomu, który jest wcześniejsza niż zamierzony nową lokalizację i wybierz pozycję **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="faf52-108">Menu, który został skopiowany jest wstawiany przed wybrane menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="faf52-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="faf52-109">Aby skopiować menu najwyższego poziomu i jego elementów podmenu do lokalizacji listy rozwijanej</span><span class="sxs-lookup"><span data-stu-id="faf52-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1. <span data-ttu-id="faf52-110">Kliknij lewym przyciskiem myszy menu, który chcesz przenieść i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy menu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="faf52-111">W menu najwyższego poziomu docelowego kliknij lewym przyciskiem myszy element podmenu, który przekracza zamierzony nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element podmenu, który przekracza zamierzony nową lokalizację i wybierz pozycję **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="faf52-112">Menu, który został skopiowany jest wstawiany przed elementem wybranym podmenu.</span><span class="sxs-lookup"><span data-stu-id="faf52-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="faf52-113">Aby skopiować element podmenu do menu inny</span><span class="sxs-lookup"><span data-stu-id="faf52-113">To copy a submenu item to another menu</span></span>  
  
1. <span data-ttu-id="faf52-114">Kliknij lewym przyciskiem myszy element podmenu, który chcesz skopiować i naciśnij klawisze CTRL + C, lub kliknij prawym przyciskiem myszy element podmenu i wybierz **kopiowania** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="faf52-115">Kliknij lewym przyciskiem myszy menu, który będzie zawierać element podmenu, który można wyciąć.</span><span class="sxs-lookup"><span data-stu-id="faf52-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3. <span data-ttu-id="faf52-116">Kliknij lewym przyciskiem myszy element podmenu poprzedzającą zamierzony nowej lokalizacji i naciśnij klawisze CTRL + V lub kliknij prawym przyciskiem myszy element podmenu poprzedzającą zamierzony nową lokalizację i wybierz pozycję **Wklej** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="faf52-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="faf52-117">Element podmenu, który został skopiowany jest wstawiany przed elementem wybranym podmenu.</span><span class="sxs-lookup"><span data-stu-id="faf52-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf52-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf52-118">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="faf52-119">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="faf52-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
