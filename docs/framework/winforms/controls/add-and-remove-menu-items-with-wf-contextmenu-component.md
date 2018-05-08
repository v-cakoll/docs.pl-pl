---
title: 'Porady: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows'
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
ms.openlocfilehash: 7cc11eaf4a671c76933c2705b41a4df6c35c0536
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Porady: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows
Wyjaśniono, jak dodawać i usuwać elementy menu skrótów w formularzach systemu Windows.  
  
 Formularze systemu Windows <xref:System.Windows.Forms.ContextMenu> stanowi menu często używanych poleceń, które mają zastosowanie do zaznaczonego obiektu. Można dodać elementy do menu skrótów, dodając <xref:System.Windows.Forms.MenuItem> obiekty do <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekcji.  
  
 Elementy menu skrótów można usunąć trwale; Jednak w czasie wykonywania może być bardziej odpowiednie do ukrywania lub wyłącz zamiast tego elementów.  
  
> [!IMPORTANT]
>  Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> formanty poprzednie wersje <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Aby usunąć elementy menu skrótów  
  
1.  Użyj <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> lub <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.Menu.MenuItems%2A> kolekcję <xref:System.Windows.Forms.ContextMenu> składnika, aby usunąć element z określonym menu.  
  
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
  
2.  Użyj `Clear` metody `MenuItems` Kolekcja <xref:System.Windows.Forms.ContextMenu> składnik, aby usunąć wszystkie elementy z menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContextMenu>  
 [ContextMenu, składnik](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [ContextMenu, składnik — omówienie](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
