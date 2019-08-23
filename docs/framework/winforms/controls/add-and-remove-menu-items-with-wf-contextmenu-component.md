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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957016"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Instrukcje: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows
Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w Windows Forms.  
  
 Składnik Windows Forms <xref:System.Windows.Forms.ContextMenu> zawiera menu często używanych poleceń, które są istotne dla zaznaczonego obiektu. Możesz dodać elementy do menu skrótów, <xref:System.Windows.Forms.MenuItem> dodając obiekty <xref:System.Windows.Forms.Menu.MenuItems%2A> do kolekcji.  
  
 Można trwale usunąć elementy z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie do ukrycia lub wyłączenia elementów.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu> Chociaż i Zastąp<xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> Dodaj funkcje do kontrolekwcześniejszychwersjiisąonezachowywanewceluzapewnieniazgodnościzpoprzednimiwersjamiiwprzyszłości,jeśliwybierzeszopcję.<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Aby usunąć elementy z menu skrótów  
  
1. Użyj metody <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> lubkolekcji<xref:System.Windows.Forms.ContextMenu>składnika , aby usunąć określony element menu. <xref:System.Windows.Forms.Menu.MenuItems%2A> <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>  
  
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
  
2. `Clear` Użyj metody `MenuItems` kolekcji składnika,abyusunąćwszystkieelementyzmenu.<xref:System.Windows.Forms.ContextMenu>  
  
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
