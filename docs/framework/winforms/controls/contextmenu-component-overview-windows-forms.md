---
title: ContextMenu, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746199"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu — Informacje o składniku (Formularze systemu Windows)
> [!IMPORTANT]
> Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.  
  
 Za pomocą składnika <xref:System.Windows.Forms.ContextMenu> Windows Forms można udostępnić użytkownikom łatwo dostępne menu skrótów często używanych poleceń, które są skojarzone z wybranym obiektem. Elementy w menu skrótów są często podzbiorem elementów z menu głównego, które pojawiają się w innym miejscu aplikacji. Użytkownik może zazwyczaj uzyskać dostęp do menu skrótów, klikając prawym przyciskiem myszy. Na Windows Forms menu skrótów są skojarzone z kontrolkami.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Możesz skojarzyć menu skrótów z kontrolką, ustawiając właściwość <xref:System.Windows.Forms.Control.ContextMenu%2A> kontrolki na składnik <xref:System.Windows.Forms.ContextMenu>. Pojedyncze menu skrótów może być skojarzone z wieloma kontrolkami, ale każda kontrolka może mieć tylko jedno menu skrótów.  
  
 Właściwość Key składnika <xref:System.Windows.Forms.ContextMenu> jest właściwością <xref:System.Windows.Forms.Menu.MenuItems%2A>. Elementy menu można dodawać przez programowe tworzenie obiektów <xref:System.Windows.Forms.MenuItem> i dodawanie ich do <xref:System.Windows.Forms.Menu.MenuItemCollection> menu skrótów. Ponieważ elementy w menu skrótów są zwykle rysowane z innych menu, najczęściej można dodać elementy do menu skrótów, kopiując je.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
