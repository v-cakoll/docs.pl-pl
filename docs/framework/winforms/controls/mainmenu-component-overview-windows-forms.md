---
title: "MainMenu — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f5cfe3a97bbbd4d5ba2d3ba089736599b6a2190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="86643-102">MainMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="86643-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="86643-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> formanty poprzednie wersje <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="86643-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="86643-104">Formularze systemu Windows <xref:System.Windows.Forms.MainMenu> składnik wyświetla menu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86643-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="86643-105">Wszystkie podmenu w menu głównym i poszczególne elementy są <xref:System.Windows.Forms.MenuItem> obiektów.</span><span class="sxs-lookup"><span data-stu-id="86643-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="86643-106">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="86643-106">Key Properties</span></span>  
 <span data-ttu-id="86643-107">Element menu może zostać wyznaczony jako domyślnego elementu, ustawiając <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="86643-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="86643-108">Element domyślny zostanie wyświetlony pogrubioną czcionką, po kliknięciu menu.</span><span class="sxs-lookup"><span data-stu-id="86643-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="86643-109">Element menu <xref:System.Windows.Forms.MenuItem.Checked%2A> właściwości `true` lub `false`oraz wskazuje, czy element menu zostanie zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="86643-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="86643-110">Element menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> właściwości dostosowuje wygląd wybranego elementu: Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ustawiono `true`, przycisku radiowego jest wyświetlany obok elementu; Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ma ustawioną wartość `false`, pojawia się znacznik wyboru obok elementu.</span><span class="sxs-lookup"><span data-stu-id="86643-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86643-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86643-111">See Also</span></span>  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="86643-112">Informacje o formancie MenuStrip</span><span class="sxs-lookup"><span data-stu-id="86643-112">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
