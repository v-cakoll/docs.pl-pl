---
title: MenuStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 7cd761697a09205294727043efc6cf73816803ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975601"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip — Informacje o formancie [Formularze systemu Windows]
Menu ujawnienie funkcji przez użytkowników przez wstrzymywanie poleceń, które są pogrupowane według wspólnego motywu.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontroli jest nowym składnikiem w tej wersji programu Visual Studio i .NET Framework. Za pomocą kontrolki można łatwo utworzyć menu, podobnie jak w programie Microsoft Office.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontrolka obsługuje interfejsu wielu dokumentów (MDI) i scalanie menu, etykietki narzędzi i przepełnienia. Można zwiększyć użyteczność i czytelności menu, dodając klucze dostępu, klawiszy skrótów, znaczniki, obrazy i pasków separatorów.  
  
 <xref:System.Windows.Forms.MenuStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.MainMenu> kontrolować; jednak <xref:System.Windows.Forms.MainMenu> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości wybranie opcji.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Sposoby na wykorzystanie MenuStrip, kontrolka  
 Użyj <xref:System.Windows.Forms.MenuStrip> kontrolę:  
  
-   Utwórz łatwo dostosować, powszechnie wykorzystywane menu, które obsługują interfejs i układ funkcje, takie jak tekst i obraz porządkowanie i wyrównanie, operacji przeciągania i upuszczania, MDI, przepełnienie i alternatywne metody uzyskiwania dostępu do poleceń menu zaawansowanych użytkowników.  
  
-   Obsługiwać typowego wyglądu i zachowania systemu operacyjnego.  
  
-   Obsługa zdarzeń spójne dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych kontrolek.  
  
 W poniższej tabeli przedstawiono niektóre szczególnie ważne właściwości <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem> używany do wyświetlania listy formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Pobiera lub ustawia, jak menu podrzędne są scalane z nadrzędnego menu w aplikacji MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Pobiera lub Ustawia położenie scalony element menu w aplikacji MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Pobiera lub ustawia wartość wskazującą, czy etykietek narzędzi są wyświetlane dla <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.MenuStrip> obsługuje przepełnienie funkcji.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Pobiera lub ustawia klawisze skrótów skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Pobiera lub ustawia wartość wskazującą, czy kluczy skrótu, które są skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok pozycji <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 W poniższej tabeli przedstawiono ważne <xref:System.Windows.Forms.MenuStrip> pomocnika klasy.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Reprezentuje opcję wyboru wyświetlane na <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Reprezentuje menu skrótów.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie jednego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> lub wyższego poziomu elementu menu.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Zapewnia podstawowe funkcje dla kontrolek pochodną <xref:System.Windows.Forms.ToolStripItem> , wyświetlać elementy listy rozwijanej, po kliknięciu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
