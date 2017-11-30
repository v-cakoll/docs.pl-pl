---
title: "ContextMenu — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6c2542ca7ee27bec96bb5010bcdb2fcd7416f72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu — Informacje o składniku (Formularze systemu Windows)
> [!IMPORTANT]
>  Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> formanty poprzednie wersje <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> składnika, mogą udostępnić użytkownikom z menu skrótów łatwo dostępne często używanych poleceń, które są skojarzone z wybranego obiektu. Elementy menu skrótów są często podzbioru elementów, z menu głównego, które pojawiają się w innym miejscu w aplikacji. Użytkownik zwykle można uzyskać dostępu do menu skrótów przez kliknięcie prawym przyciskiem myszy. W formularzach systemu Windows są skojarzone z formantami menu skrótów.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Menu skrótów można skojarzyć z formantem, ustawiając formantu <xref:System.Windows.Forms.Control.ContextMenu%2A> właściwości <xref:System.Windows.Forms.ContextMenu> składnika. Menu skrótów pojedynczego może być skojarzony z wielu formantów, ale każdego formantu można mieć tylko jeden menu skrótów.  
  
 Właściwość klucza <xref:System.Windows.Forms.ContextMenu> składnik jest <xref:System.Windows.Forms.Menu.MenuItems%2A> właściwości. Można dodawać elementów menu programowe tworzenie <xref:System.Windows.Forms.MenuItem> obiektów oraz dodanie ich do <xref:System.Windows.Forms.Menu.MenuItemCollection> menu skrótów. Ponieważ elementy w menu skrótów zazwyczaj są pobierane z innych menu, najczęściej będzie będzie Dodaj elementy do menu skrótów, kopiując je.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
