---
title: 'Instrukcje: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows'
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
ms.openlocfilehash: cf70a5cc426b6c6075d1deb11aa2685c39a065c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640338"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Instrukcje: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows
Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w formularzach Windows Forms.  
  
 Formularze Windows <xref:System.Windows.Forms.ContextMenu> składnik zapewnia menu często używanych poleceń, które są istotne dla wybranego obiektu. Możesz dodać elementy do menu skrótów, dodając <xref:System.Windows.Forms.MenuItem> obiekty do <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekcji.  
  
 Użytkownik może trwałe usuwanie elementów z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie ukryć lub zamiast tego Wyłącz elementy.  
  
> [!IMPORTANT]
>  Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontrolki z poprzednich wersji <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Aby usunąć elementy z menu skrótów  
  
1. Użyj <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> lub <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.Menu.MenuItems%2A> zbiór <xref:System.Windows.Forms.ContextMenu> składnika, aby usunąć element menu określonej.  
  
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
  
     —lub—  
  
2. Użyj `Clear` metody `MenuItems` zbiór <xref:System.Windows.Forms.ContextMenu> składnika, aby usunąć wszystkie elementy menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu, składnik](contextmenu-component-windows-forms.md)
- [ContextMenu, składnik — omówienie](contextmenu-component-overview-windows-forms.md)
