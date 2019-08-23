---
title: ContextMenu — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962186"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="6ee60-102">ContextMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6ee60-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="6ee60-103"><xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu> Chociaż i Zastąp<xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> Dodaj funkcje do kontrolekwcześniejszychwersjiisąonezachowywanewceluzapewnieniazgodnościzpoprzednimiwersjamiiwprzyszłości,jeśliwybierzeszopcję.<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="6ee60-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="6ee60-104">Za pomocą składnika <xref:System.Windows.Forms.ContextMenu> Windows Forms można zapewnić użytkownikom łatwy dostęp do menu skrótów z często używanymi poleceniami, które są skojarzone z wybranym obiektem.</span><span class="sxs-lookup"><span data-stu-id="6ee60-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="6ee60-105">Elementy w menu skrótów są często podzbiorem elementów z menu głównego, które pojawiają się w innym miejscu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6ee60-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="6ee60-106">Użytkownik może zazwyczaj uzyskać dostęp do menu skrótów, klikając prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="6ee60-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="6ee60-107">Na Windows Forms menu skrótów są skojarzone z kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="6ee60-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="6ee60-108">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="6ee60-108">Key Properties</span></span>  
 <span data-ttu-id="6ee60-109">Możesz skojarzyć menu skrótów z kontrolką, ustawiając <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwość kontrolki <xref:System.Windows.Forms.ContextMenu> na składnik.</span><span class="sxs-lookup"><span data-stu-id="6ee60-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="6ee60-110">Pojedyncze menu skrótów może być skojarzone z wieloma kontrolkami, ale każda kontrolka może mieć tylko jedno menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="6ee60-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="6ee60-111">Właściwość <xref:System.Windows.Forms.ContextMenu> klucza składnika <xref:System.Windows.Forms.Menu.MenuItems%2A> jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="6ee60-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="6ee60-112">Elementy menu można dodawać przez programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów i dodawanie ich <xref:System.Windows.Forms.Menu.MenuItemCollection> do menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="6ee60-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="6ee60-113">Ponieważ elementy w menu skrótów są zwykle rysowane z innych menu, najczęściej można dodać elementy do menu skrótów, kopiując je.</span><span class="sxs-lookup"><span data-stu-id="6ee60-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee60-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ee60-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
