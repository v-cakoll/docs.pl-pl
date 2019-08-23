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
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu — Informacje o składniku (Formularze systemu Windows)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu> Chociaż i Zastąp<xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> Dodaj funkcje do kontrolekwcześniejszychwersjiisąonezachowywanewceluzapewnieniazgodnościzpoprzednimiwersjamiiwprzyszłości,jeśliwybierzeszopcję.<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip>  
  
 Za pomocą składnika <xref:System.Windows.Forms.ContextMenu> Windows Forms można zapewnić użytkownikom łatwy dostęp do menu skrótów z często używanymi poleceniami, które są skojarzone z wybranym obiektem. Elementy w menu skrótów są często podzbiorem elementów z menu głównego, które pojawiają się w innym miejscu aplikacji. Użytkownik może zazwyczaj uzyskać dostęp do menu skrótów, klikając prawym przyciskiem myszy. Na Windows Forms menu skrótów są skojarzone z kontrolkami.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Możesz skojarzyć menu skrótów z kontrolką, ustawiając <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwość kontrolki <xref:System.Windows.Forms.ContextMenu> na składnik. Pojedyncze menu skrótów może być skojarzone z wieloma kontrolkami, ale każda kontrolka może mieć tylko jedno menu skrótów.  
  
 Właściwość <xref:System.Windows.Forms.ContextMenu> klucza składnika <xref:System.Windows.Forms.Menu.MenuItems%2A> jest właściwością. Elementy menu można dodawać przez programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów i dodawanie ich <xref:System.Windows.Forms.Menu.MenuItemCollection> do menu skrótów. Ponieważ elementy w menu skrótów są zwykle rysowane z innych menu, najczęściej można dodać elementy do menu skrótów, kopiując je.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
