---
title: MenuStrip — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734467"
---
# <a name="menustrip-control-overview-windows-forms"></a>MenuStrip — Informacje o formancie [Formularze systemu Windows]
Menu uwidacznia funkcjonalność użytkownikom, umieszczając polecenia, które są pogrupowane według typowego motywu.  
  
 Formant <xref:System.Windows.Forms.MenuStrip> został wprowadzony w wersji 2,0 .NET Framework. Za pomocą kontrolki <xref:System.Windows.Forms.MenuStrip> można łatwo tworzyć menu, takie jak te, które znajdują się w Microsoft Office.  
  
 Kontrolka <xref:System.Windows.Forms.MenuStrip> obsługuje interfejs wielu dokumentów (MDI) i scalanie menu, etykiet narzędzi i przepełnienia. Można zwiększyć użyteczność i czytelność Twoich menu, dodając klucze dostępu, skróty klawiaturowe, znaczniki wyboru, obrazy i paski separatora.  
  
 Formant <xref:System.Windows.Forms.MenuStrip> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.MainMenu>; jednak kontrolka <xref:System.Windows.Forms.MainMenu> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Sposoby korzystania z formantu MenuStrip  
 Użyj kontrolki <xref:System.Windows.Forms.MenuStrip>, aby:  
  
- Twórz łatwo dostosowane, powszechnie używane menu, które obsługują zaawansowane funkcje interfejsu użytkownika i układu, takie jak porządkowanie tekstu i obrazów oraz wyrównanie, operacje przeciągania i upuszczania, elementy MDI, przepełnienie i alternatywne tryby dostępu do poleceń menu.  
  
- Obsługa typowego wyglądu i zachowania systemu operacyjnego.  
  
- Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych elementów w ten sam sposób, w jaki są obsługiwane zdarzenia dla innych formantów.  
  
 W poniższej tabeli przedstawiono niektóre szczególnie ważne właściwości <xref:System.Windows.Forms.MenuStrip> i skojarzonych klas.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripMenuItem>, który jest używany do wyświetlania listy formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Pobiera lub ustawia sposób scalania menu podrzędnych z menu nadrzędnymi w aplikacjach MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Pobiera lub ustawia pozycję scalonego elementu w menu w aplikacjach MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Pobiera lub ustawia wartość wskazującą, czy formularz jest kontenerem dla formularzy podrzędnych MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Pobiera lub ustawia wartość wskazującą, czy dla <xref:System.Windows.Forms.MenuStrip>są wyświetlane etykietki narzędzi.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą, czy <xref:System.Windows.Forms.MenuStrip> obsługuje funkcję przepełnienia.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Pobiera lub ustawia klawisze skrótów skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Pobiera lub ustawia wartość wskazującą, czy klawisze skrótów, które są skojarzone z <xref:System.Windows.Forms.ToolStripMenuItem> są wyświetlane obok <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 W poniższej tabeli przedstawiono ważne klasy pomocników <xref:System.Windows.Forms.MenuStrip>.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Reprezentuje wybraną opcję wyświetlaną w <xref:System.Windows.Forms.MenuStrip> lub <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Reprezentuje menu skrótów.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Reprezentuje kontrolkę umożliwiającą użytkownikowi wybranie pojedynczego elementu z listy, która jest wyświetlana, gdy użytkownik kliknie <xref:System.Windows.Forms.ToolStripDropDownButton> lub element menu wyższego poziomu.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Zapewnia podstawowe funkcje formantów pochodzących z <xref:System.Windows.Forms.ToolStripItem>, które wyświetlają elementy rozwijane po kliknięciu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
