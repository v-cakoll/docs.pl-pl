---
title: 'Porady: ukrywanie formantu ToolStripMenuItems'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f5491cfbfc312b2ce3e35170ddc4edc8ee39a61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="4cc33-102">Porady: ukrywanie formantu ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="4cc33-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="4cc33-103">Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika, aplikacji i ograniczyć poleceń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cc33-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="4cc33-104">Często chcesz ukryć całe menu, gdy wszystkich elementów menu na nim są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="4cc33-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="4cc33-105">Przedstawia informacje o tym przeszkadzał dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cc33-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="4cc33-106">Ponadto możesz chcieć zarówno Ukryj i Wyłącz menu lub elementu menu, jak ukrywanie wyłącznie nie uniemożliwia użytkownikowi uzyskiwanie dostępu do polecenia menu za pomocą klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="4cc33-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="4cc33-107">Aby programowo ukryć dowolny element menu</span><span class="sxs-lookup"><span data-stu-id="4cc33-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="4cc33-108">W metodzie można ustawić właściwości elementu menu, Dodaj kod, aby ustawić <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="4cc33-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4cc33-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cc33-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="4cc33-110">MenuStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="4cc33-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="4cc33-111">Instrukcje: wyłączanie kontrolki ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="4cc33-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
