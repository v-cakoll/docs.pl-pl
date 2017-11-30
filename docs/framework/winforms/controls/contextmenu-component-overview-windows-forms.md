---
title: "ContextMenu — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6c2542ca7ee27bec96bb5010bcdb2fcd7416f72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="1c04d-102">ContextMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="1c04d-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="1c04d-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> formanty poprzednie wersje <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="1c04d-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="1c04d-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> składnika, mogą udostępnić użytkownikom z menu skrótów łatwo dostępne często używanych poleceń, które są skojarzone z wybranego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1c04d-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="1c04d-105">Elementy menu skrótów są często podzbioru elementów, z menu głównego, które pojawiają się w innym miejscu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c04d-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="1c04d-106">Użytkownik zwykle można uzyskać dostępu do menu skrótów przez kliknięcie prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="1c04d-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="1c04d-107">W formularzach systemu Windows są skojarzone z formantami menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="1c04d-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1c04d-108">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="1c04d-108">Key Properties</span></span>  
 <span data-ttu-id="1c04d-109">Menu skrótów można skojarzyć z formantem, ustawiając formantu <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwości <xref:System.Windows.Forms.ContextMenu> składnika.</span><span class="sxs-lookup"><span data-stu-id="1c04d-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="1c04d-110">Menu skrótów pojedynczego może być skojarzony z wielu formantów, ale każdego formantu można mieć tylko jeden menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="1c04d-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="1c04d-111">Właściwość klucza <xref:System.Windows.Forms.ContextMenu> składnik jest <xref:System.Windows.Forms.Menu.MenuItems%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c04d-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="1c04d-112">Można dodawać elementów menu programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów oraz dodanie ich do <xref:System.Windows.Forms.Menu.MenuItemCollection> menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="1c04d-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="1c04d-113">Ponieważ elementy w menu skrótów zazwyczaj są pobierane z innych menu, najczęściej będzie będzie Dodaj elementy do menu skrótów, kopiując je.</span><span class="sxs-lookup"><span data-stu-id="1c04d-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c04d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c04d-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
