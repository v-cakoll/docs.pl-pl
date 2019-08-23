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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="fdbd1-102">Instrukcje: dodawanie i usuwanie elementów menu za pomocą składnika ContextMenu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fdbd1-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="fdbd1-103">Wyjaśnia, jak dodawać i usuwać elementy menu skrótów w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="fdbd1-104">Składnik Windows Forms <xref:System.Windows.Forms.ContextMenu> zawiera menu często używanych poleceń, które są istotne dla zaznaczonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="fdbd1-105">Możesz dodać elementy do menu skrótów, <xref:System.Windows.Forms.MenuItem> dodając obiekty <xref:System.Windows.Forms.Menu.MenuItems%2A> do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="fdbd1-106">Można trwale usunąć elementy z menu skrótów; Jednak w czasie wykonywania może być bardziej odpowiednie do ukrycia lub wyłączenia elementów.</span><span class="sxs-lookup"><span data-stu-id="fdbd1-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fdbd1-107"><xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu> Chociaż i Zastąp<xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> Dodaj funkcje do kontrolekwcześniejszychwersjiisąonezachowywanewceluzapewnieniazgodnościzpoprzednimiwersjamiiwprzyszłości,jeśliwybierzeszopcję.<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="fdbd1-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="fdbd1-108">Aby usunąć elementy z menu skrótów</span><span class="sxs-lookup"><span data-stu-id="fdbd1-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="fdbd1-109">Użyj metody <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> lubkolekcji<xref:System.Windows.Forms.ContextMenu>składnika , aby usunąć określony element menu. <xref:System.Windows.Forms.Menu.MenuItems%2A> <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="fdbd1-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="fdbd1-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="fdbd1-110">-or-</span></span>  
  
2. <span data-ttu-id="fdbd1-111">`Clear` Użyj metody `MenuItems` kolekcji składnika,abyusunąćwszystkieelementyzmenu.<xref:System.Windows.Forms.ContextMenu></span><span class="sxs-lookup"><span data-stu-id="fdbd1-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fdbd1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdbd1-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="fdbd1-113">ContextMenu, składnik</span><span class="sxs-lookup"><span data-stu-id="fdbd1-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="fdbd1-114">ContextMenu, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="fdbd1-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
