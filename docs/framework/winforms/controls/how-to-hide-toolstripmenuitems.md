---
title: 'Instrukcje: ukrywanie kontrolki ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: dc9daa945f2a546548f2cc6ea033378bd9ceff93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127429"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="1ea25-102">Instrukcje: ukrywanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="1ea25-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="1ea25-103">Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika aplikacji i ograniczyć polecenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1ea25-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="1ea25-104">Często chcesz ukryć całe menu, gdy wszystkie elementy menu na nim są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="1ea25-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="1ea25-105">Przedstawia informacje o przeszkadzał dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1ea25-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="1ea25-106">Ponadto warto ukryć i Wyłącz menu lub elementu menu, jak samodzielnie ukrywanie nie uniemożliwia użytkownikowi dostęp do poleceń menu przy użyciu klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="1ea25-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="1ea25-107">Aby ukryć programowo dowolny element menu</span><span class="sxs-lookup"><span data-stu-id="1ea25-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="1ea25-108">W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="1ea25-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1ea25-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ea25-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="1ea25-110">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1ea25-110">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="1ea25-111">Instrukcje: Wyłączanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="1ea25-111">How to: Disable ToolStripMenuItems</span></span>](how-to-disable-toolstripmenuitems.md)
