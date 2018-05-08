---
title: MenuStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b09d653210c72a38bbc4dc0858ae2553ad9cbeef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip — Informacje o formancie [Formularze systemu Windows]
Menu udostępniać funkcje dla użytkowników, przytrzymując poleceń, które są pogrupowane według wspólnej kompozycji.  
  
 <xref:System.Windows.Forms.MenuStrip> Formant jest nowe w tej wersji programu Visual Studio i .NET Framework. Za pomocą formantu można łatwo utworzyć menu, podobnie jak w programie Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Formantu obsługuje interfejs dokumentu wielokrotnego (MDI) i scalanie menu, etykietki narzędzi i przepełnienia. Użyteczność i czytelność menu można zwiększyć przez dodanie klucze dostępu, klawiszy skrótów znaczników zaznaczenia, obrazy i pasków separatorów.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.MainMenu> kontrolować; jednak <xref:System.Windows.Forms.MainMenu> formant został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości po wybraniu.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Sposoby używania MenuStrip — formant  
 Użyj <xref:System.Windows.Forms.MenuStrip> formant:  
  
-   Tworzenie łatwo dostosować, często rachunek menu, które obsługują zaawansowane użytkownika interfejsu i układu funkcje, takie jak tekst i kolejność obrazu i wyrównania, operacji przeciągania i upuszczania MDI, przepełnienie i alternatywne metody uzyskiwania dostępu do poleceń menu.  
  
-   Obsługuje typowe wyglądu i zachowania systemu operacyjnego.  
  
-   Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych formantów.  
  
 W poniższej tabeli przedstawiono niektóre właściwości szczególnie ważne <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> używany do wyświetlania listy formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Pobiera lub ustawia sposób scalania menu podrzędnego z menu nadrzędne w aplikacjach MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Pobiera lub Ustawia położenie elementu scalonego menu MDI aplikacji.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Pobiera lub ustawia wartość wskazującą, czy etykietki narzędzi są wyświetlane dla <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.MenuStrip> obsługuje przepełnienie funkcji.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Pobiera lub ustawia klawisze skrótu skojarzony z <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Pobiera lub ustawia wartość wskazującą, czy klawisze skrótów, które są skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok pozycji <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> pomocniczy klasy.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Reprezentuje wybór opcji, wyświetlany na <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Reprezentuje menu skrótów.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie pojedynczego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> lub wyższego poziomu elementu menu.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Zapewnia podstawowe funkcje dla kontrolek pochodzące z <xref:System.Windows.Forms.ToolStripItem> wyświetlający elementów listy rozwijanej, po kliknięciu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
