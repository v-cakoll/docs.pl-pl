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
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu — Informacje o składniku (Formularze systemu Windows)
> [!IMPORTANT]
>  Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontrolki z poprzednich wersji <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Za pomocą interfejsu Windows Forms <xref:System.Windows.Forms.ContextMenu> składnik, można zapewnić użytkownikom za pomocą menu skrótów łatwo dostępna z najczęściej używanymi poleceniami, które są skojarzone z wybranego obiektu. Elementy w menu skrótów są często podzbiór elementów menu głównego, które pojawiają się w innych miejscach w aplikacji. Użytkownik zwykle można uzyskać dostęp do menu skrótów przez kliknięcie prawym przyciskiem myszy. Na formularzach Windows Forms menu skrótów są skojarzone z formantów.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Menu skrótów można skojarzyć z formantu przez ustawienie jego <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwość <xref:System.Windows.Forms.ContextMenu> składnika. Menu skrótów jednego można skojarzyć z wieloma formantami, ale każdy formant może mieć tylko jeden menu skrótów.  
  
 Właściwość klucza <xref:System.Windows.Forms.ContextMenu> składnik to <xref:System.Windows.Forms.Menu.MenuItems%2A> właściwości. Możesz dodać elementy menu, programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów oraz dodać je do <xref:System.Windows.Forms.Menu.MenuItemCollection> w menu skrótów. Ponieważ elementy w menu skrótów jest zazwyczaj rysowany z innych menu, będzie najczęściej dodaniu elementów do menu skrótów, kopiując je.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
