---
title: MenuStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733460"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip — Informacje o formancie [Formularze systemu Windows]
Menu uwidacznia funkcjonalność użytkownikom, umieszczając polecenia, które są pogrupowane według typowego motywu.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontrolka została wprowadzona w wersji 2,0 .NET Framework. Za pomocą <xref:System.Windows.Forms.MenuStrip> formantu można łatwo tworzyć menu, takie jak te, które znajdują się w Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontrolka obsługuje interfejs wielu dokumentów (MDI) i scalanie menu, etykiet narzędzi i przepełnienia. Można zwiększyć użyteczność i czytelność Twoich menu, dodając klucze dostępu, skróty klawiaturowe, znaczniki wyboru, obrazy i paski separatora.  
  
 Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.MainMenu> do <xref:System.Windows.Forms.MainMenu> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.MenuStrip>  
  
## <a name="ways-to-use-the-menustrip-control"></a>Sposoby korzystania z formantu MenuStrip  
 Użyj kontrolki, <xref:System.Windows.Forms.MenuStrip> aby:  
  
- Twórz łatwo dostosowane, powszechnie używane menu, które obsługują zaawansowane funkcje interfejsu użytkownika i układu, takie jak porządkowanie tekstu i obrazów oraz wyrównanie, operacje przeciągania i upuszczania, elementy MDI, przepełnienie i alternatywne tryby dostępu do poleceń menu.  
  
- Obsługa typowego wyglądu i zachowania systemu operacyjnego.  
  
- Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych elementów w ten sam sposób, w jaki są obsługiwane zdarzenia dla innych formantów.  
  
 W poniższej tabeli przedstawiono niektóre szczególnie ważne właściwości <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> obiekt, który jest używany do wyświetlania listy formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Pobiera lub ustawia sposób scalania menu podrzędnych z menu nadrzędnymi w aplikacjach MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Pobiera lub ustawia pozycję scalonego elementu w menu w aplikacjach MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Pobiera lub ustawia wartość wskazującą, <xref:System.Windows.Forms.MenuStrip>czy dla elementu są wyświetlane etykietki narzędzi.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą, <xref:System.Windows.Forms.MenuStrip> czy obsługuje funkcje przepełnienia.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Pobiera lub ustawia klawisze skrótów skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Pobiera lub ustawia wartość wskazującą, czy klawisze skrótów, które są skojarzone z, <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok <xref:System.Windows.Forms.ToolStripMenuItem>elementu.|  
  
 W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> klasy pomocnika.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Reprezentuje wybraną opcję wyświetlaną w <xref:System.Windows.Forms.MenuStrip> lub. <xref:System.Windows.Forms.ContextMenuStrip>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Reprezentuje menu skrótów.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie pojedynczego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> element menu lub wyższego poziomu.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Oferuje podstawowe funkcje dla kontrolek pochodzących <xref:System.Windows.Forms.ToolStripItem> z wyświetlanych elementów listy rozwijanej po kliknięciu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
