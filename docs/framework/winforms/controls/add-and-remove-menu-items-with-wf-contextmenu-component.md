---
title: 'Instrukcje: Dodawanie i usuwanie elementów Menu za pomocą składnika ContextMenu formularzy Windows'
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
ms.openlocfilehash: 8b63182bdb37e47a71bee2d22500263cd4889ac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725067"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="adc3c-102">Instrukcje: Dodawanie i usuwanie elementów Menu za pomocą składnika ContextMenu formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="adc3c-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="adc3c-103">Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="adc3c-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="adc3c-104">Formularze Windows <xref:System.Windows.Forms.ContextMenu> składnik zapewnia menu często używanych poleceń, które są istotne dla wybranego obiektu.</span><span class="sxs-lookup"><span data-stu-id="adc3c-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="adc3c-105">Możesz dodać elementy do menu skrótów, dodając <xref:System.Windows.Forms.MenuItem> obiekty do <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="adc3c-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="adc3c-106">Użytkownik może trwałe usuwanie elementów z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie ukryć lub zamiast tego Wyłącz elementy.</span><span class="sxs-lookup"><span data-stu-id="adc3c-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="adc3c-107">Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontrolki z poprzednich wersji <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="adc3c-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="adc3c-108">Aby usunąć elementy z menu skrótów</span><span class="sxs-lookup"><span data-stu-id="adc3c-108">To remove items from a shortcut menu</span></span>  
  
1.  <span data-ttu-id="adc3c-109">Użyj <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> lub <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.Menu.MenuItems%2A> zbiór <xref:System.Windows.Forms.ContextMenu> składnika, aby usunąć element menu określonej.</span><span class="sxs-lookup"><span data-stu-id="adc3c-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="adc3c-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="adc3c-110">-or-</span></span>  
  
2.  <span data-ttu-id="adc3c-111">Użyj `Clear` metody `MenuItems` zbiór <xref:System.Windows.Forms.ContextMenu> składnika, aby usunąć wszystkie elementy menu.</span><span class="sxs-lookup"><span data-stu-id="adc3c-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="adc3c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adc3c-112">See also</span></span>
- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="adc3c-113">ContextMenu, składnik</span><span class="sxs-lookup"><span data-stu-id="adc3c-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="adc3c-114">ContextMenu, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="adc3c-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
