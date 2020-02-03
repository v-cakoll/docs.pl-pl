---
title: ContextMenu, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746199"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="3079e-102">ContextMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="3079e-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="3079e-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="3079e-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="3079e-104">Za pomocą składnika <xref:System.Windows.Forms.ContextMenu> Windows Forms można udostępnić użytkownikom łatwo dostępne menu skrótów często używanych poleceń, które są skojarzone z wybranym obiektem.</span><span class="sxs-lookup"><span data-stu-id="3079e-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="3079e-105">Elementy w menu skrótów są często podzbiorem elementów z menu głównego, które pojawiają się w innym miejscu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3079e-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="3079e-106">Użytkownik może zazwyczaj uzyskać dostęp do menu skrótów, klikając prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="3079e-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="3079e-107">Na Windows Forms menu skrótów są skojarzone z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="3079e-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="3079e-108">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="3079e-108">Key Properties</span></span>  
 <span data-ttu-id="3079e-109">Możesz skojarzyć menu skrótów z kontrolką, ustawiając właściwość <xref:System.Windows.Forms.Control.ContextMenu%2A> kontrolki na składnik <xref:System.Windows.Forms.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="3079e-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="3079e-110">Pojedyncze menu skrótów może być skojarzone z wieloma kontrolkami, ale każda kontrolka może mieć tylko jedno menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3079e-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="3079e-111">Właściwość Key składnika <xref:System.Windows.Forms.ContextMenu> jest właściwością <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="3079e-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="3079e-112">Elementy menu można dodawać przez programowe tworzenie obiektów <xref:System.Windows.Forms.MenuItem> i dodawanie ich do <xref:System.Windows.Forms.Menu.MenuItemCollection> menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="3079e-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="3079e-113">Ponieważ elementy w menu skrótów są zwykle rysowane z innych menu, najczęściej można dodać elementy do menu skrótów, kopiując je.</span><span class="sxs-lookup"><span data-stu-id="3079e-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3079e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3079e-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
