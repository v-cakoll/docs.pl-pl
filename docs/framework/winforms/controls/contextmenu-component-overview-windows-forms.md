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
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090566"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="0f1df-102">ContextMenu — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="0f1df-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="0f1df-103">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontrolki z poprzednich wersji <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="0f1df-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="0f1df-104">Za pomocą interfejsu Windows Forms <xref:System.Windows.Forms.ContextMenu> składnik, można zapewnić użytkownikom za pomocą menu skrótów łatwo dostępna z najczęściej używanymi poleceniami, które są skojarzone z wybranego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0f1df-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="0f1df-105">Elementy w menu skrótów są często podzbiór elementów menu głównego, które pojawiają się w innych miejscach w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f1df-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="0f1df-106">Użytkownik zwykle można uzyskać dostęp do menu skrótów przez kliknięcie prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="0f1df-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="0f1df-107">Na formularzach Windows Forms menu skrótów są skojarzone z formantów.</span><span class="sxs-lookup"><span data-stu-id="0f1df-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="0f1df-108">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="0f1df-108">Key Properties</span></span>  
 <span data-ttu-id="0f1df-109">Menu skrótów można skojarzyć z formantu przez ustawienie jego <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwość <xref:System.Windows.Forms.ContextMenu> składnika.</span><span class="sxs-lookup"><span data-stu-id="0f1df-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="0f1df-110">Menu skrótów jednego można skojarzyć z wieloma formantami, ale każdy formant może mieć tylko jeden menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="0f1df-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="0f1df-111">Właściwość klucza <xref:System.Windows.Forms.ContextMenu> składnik to <xref:System.Windows.Forms.Menu.MenuItems%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f1df-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="0f1df-112">Możesz dodać elementy menu, programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów oraz dodać je do <xref:System.Windows.Forms.Menu.MenuItemCollection> w menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="0f1df-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="0f1df-113">Ponieważ elementy w menu skrótów jest zazwyczaj rysowany z innych menu, będzie najczęściej dodaniu elementów do menu skrótów, kopiując je.</span><span class="sxs-lookup"><span data-stu-id="0f1df-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1df-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f1df-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
