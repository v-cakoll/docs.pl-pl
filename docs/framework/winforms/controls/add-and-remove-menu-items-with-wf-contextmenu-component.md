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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Porady: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows
Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w Windows Forms.  
  
 Składnik <xref:System.Windows.Forms.ContextMenu> Windows Forms zawiera menu często używanych poleceń, które są istotne dla zaznaczonego obiektu. Możesz dodać elementy do menu skrótów, dodając <xref:System.Windows.Forms.MenuItem> obiektów do kolekcji <xref:System.Windows.Forms.Menu.MenuItems%2A>.  
  
 Można trwale usunąć elementy z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie do ukrycia lub wyłączenia elementów.  
  
> [!IMPORTANT]
> Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Aby usunąć elementy z menu skrótów  
  
1. Użyj metody <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> lub <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> kolekcji <xref:System.Windows.Forms.Menu.MenuItems%2A> składnika <xref:System.Windows.Forms.ContextMenu>, aby usunąć konkretny element menu.  
  
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
  
     lub  
  
2. Aby usunąć wszystkie elementy z menu, należy użyć metody `Clear` `MenuItems` kolekcji składnika <xref:System.Windows.Forms.ContextMenu>.  
  
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
