---
title: Dodawanie i usuwanie elementów menu za pomocą składnika dodawaj
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746271"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="dc51f-102">Porady: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dc51f-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="dc51f-103">Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc51f-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="dc51f-104">Składnik <xref:System.Windows.Forms.ContextMenu> Windows Forms zawiera menu często używanych poleceń, które są istotne dla zaznaczonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="dc51f-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="dc51f-105">Możesz dodać elementy do menu skrótów, dodając <xref:System.Windows.Forms.MenuItem> obiektów do kolekcji <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc51f-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="dc51f-106">Można trwale usunąć elementy z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie do ukrycia lub wyłączenia elementów.</span><span class="sxs-lookup"><span data-stu-id="dc51f-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dc51f-107">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="dc51f-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="dc51f-108">Aby usunąć elementy z menu skrótów</span><span class="sxs-lookup"><span data-stu-id="dc51f-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="dc51f-109">Użyj metody <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> lub <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> kolekcji <xref:System.Windows.Forms.Menu.MenuItems%2A> składnika <xref:System.Windows.Forms.ContextMenu>, aby usunąć konkretny element menu.</span><span class="sxs-lookup"><span data-stu-id="dc51f-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     <span data-ttu-id="dc51f-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="dc51f-110">-or-</span></span>  
  
2. <span data-ttu-id="dc51f-111">Aby usunąć wszystkie elementy z menu, należy użyć metody `Clear` `MenuItems` kolekcji składnika <xref:System.Windows.Forms.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="dc51f-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc51f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc51f-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="dc51f-113">ContextMenu, składnik</span><span class="sxs-lookup"><span data-stu-id="dc51f-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="dc51f-114">ContextMenu, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="dc51f-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
