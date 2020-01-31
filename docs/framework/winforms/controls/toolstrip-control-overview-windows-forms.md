---
title: ToolStrip — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741079"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip — Informacje o formancie [Formularze systemu Windows]
Kontrolka <xref:System.Windows.Forms.ToolStrip> Windows Forms i skojarzone z nią klasy zapewniają wspólną strukturę służącą do łączenia elementów interfejsu użytkownika w paski narzędzi, paski stanu i menu. kontrolki <xref:System.Windows.Forms.ToolStrip> oferują bogate środowisko projektowania, które obejmuje aktywację w miejscu i edytowanie, układ niestandardowy i spływ, który jest możliwością pasków narzędzi do udostępniania w poziomie lub w pionie.  
  
 Mimo że <xref:System.Windows.Forms.ToolStrip> zamienia i dodaje funkcje do formantu w poprzednich wersjach, <xref:System.Windows.Forms.ToolBar> jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w razie potrzeby.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkcje formantów ToolStrip  
 Użyj kontrolki <xref:System.Windows.Forms.ToolStrip>, aby:  
  
- Zaprezentowanie wspólnego interfejsu użytkownika w kontenerach.  
  
- Twórz łatwo dostosowane, powszechnie używane paski narzędzi, które obsługują zaawansowane funkcje interfejsu użytkownika i układu, takie jak dokowanie, spływanie, przyciski z tekstem i obrazami, przyciski listy rozwijanej i kontrolki, przepełnienie przycisków i zmiana kolejności w czasie wykonywania elementów <xref:System.Windows.Forms.ToolStrip>.  
  
- Obsługa przepełnienia i zmiany kolejności elementów w czasie wykonywania. Funkcja przepełniania przenosi elementy do menu rozwijanego, gdy nie ma wystarczająco dużo miejsca, aby wyświetlić je w <xref:System.Windows.Forms.ToolStrip>.  
  
- Obsługa typowego wyglądu i zachowania systemu operacyjnego za pomocą wspólnego modelu renderowania.  
  
- Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych elementów w ten sam sposób, w jaki są obsługiwane zdarzenia dla innych formantów.  
  
- Przeciągnij elementy z jednego <xref:System.Windows.Forms.ToolStrip> do innego lub wewnątrz <xref:System.Windows.Forms.ToolStrip>.  
  
- Tworzenie kontrolek rozwijanych i edytorów typów interfejsu użytkownika przy użyciu zaawansowanych układów w <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Użyj klasy <xref:System.Windows.Forms.ToolStripControlHost>, aby użyć innych formantów na <xref:System.Windows.Forms.ToolStrip> i uzyskać dla nich funkcję <xref:System.Windows.Forms.ToolStrip>.  
  
 Można zwiększyć funkcjonalność i zmodyfikować wygląd i zachowanie przy użyciu <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>i <xref:System.Windows.Forms.ToolStripManager> wraz z wyliczeniami <xref:System.Windows.Forms.ToolStripRenderMode> i <xref:System.Windows.Forms.ToolStripManagerRenderMode>.  
  
 Formant <xref:System.Windows.Forms.ToolStrip> jest wysoce konfigurowalny i rozszerzalny oraz zawiera wiele właściwości, metod i zdarzeń, aby dostosować wygląd i zachowanie. Poniżej znajdują się następujące elementy członkowskie:  
  
### <a name="important-toolstrip-members"></a>Ważne elementy członkowskie elementu ToolStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Pobiera lub ustawia krawędź kontenera nadrzędnego, do której jest zadokowany <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Pobiera lub ustawia wartość wskazującą, czy przeciąganie i upuszczanie oraz zmiana kolejności elementów są obsługiwane prywatnie przez klasę <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Pobiera lub ustawia wartość wskazującą sposób, w jaki <xref:System.Windows.Forms.ToolStrip> ustalają elementy.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Pobiera lub ustawia czy <xref:System.Windows.Forms.ToolStripItem> jest dołączona do <xref:System.Windows.Forms.ToolStrip> lub <xref:System.Windows.Forms.ToolStripOverflowButton> lub może przepływać między nimi.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Pobiera wartość wskazującą, czy <xref:System.Windows.Forms.ToolStripItem> wyświetla inne elementy na liście rozwijanej po kliknięciu <xref:System.Windows.Forms.ToolStripItem>.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Pobiera <xref:System.Windows.Forms.ToolStripItem>, który jest przyciskiem przepełnienia dla <xref:System.Windows.Forms.ToolStrip> z włączonym przepełnieniem.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripRenderer> używany do dostosowywania wyglądu i zachowania (wyglądu i działania) <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Pobiera lub ustawia style rysowania, które mają zostać zastosowane do <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Uruchamiany po zmianie właściwości <xref:System.Windows.Forms.ToolStrip.Renderer%2A>.|  
  
 Elastyczność formantu <xref:System.Windows.Forms.ToolStrip> jest realizowana za pomocą wielu klas pomocnika. Poniżej przedstawiono niektóre z najważniejszych:  
  
### <a name="important-toolstrip-companion-classes"></a>Ważne klasy pomocników elementu ToolStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Zamienia i dodaje funkcje do klasy <xref:System.Windows.Forms.MainMenu>.|  
|<xref:System.Windows.Forms.StatusStrip>|Zamienia i dodaje funkcje do klasy <xref:System.Windows.Forms.StatusBar>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Zamienia i dodaje funkcje do klasy <xref:System.Windows.Forms.ContextMenu>.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstrakcyjna klasa bazowa, która zarządza zdarzeniami i układem dla wszystkich elementów, które <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>lub <xref:System.Windows.Forms.ToolStripDropDown> mogą zawierać.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Oferuje kontener z panelem po każdej stronie formularza, w którym formanty mogą być ułożone na różne sposoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Obsługuje funkcję malowania dla obiektów <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Zapewnia Microsoft Office wyglądu.|  
|<xref:System.Windows.Forms.ToolStripManager>|Kontroluje <xref:System.Windows.Forms.ToolStrip> renderingu i spływu oraz scalanie <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>i <xref:System.Windows.Forms.ToolStripMenuItem> obiektów.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Określa styl rysowania (niestandardowy, Windows XP lub Microsoft Office Professional) stosowany do wielu <xref:System.Windows.Forms.ToolStrip> obiektów zawartych w formularzu.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Określa styl rysowania (niestandardowy, Windows XP lub Microsoft Office Professional) stosowany do jednego <xref:System.Windows.Forms.ToolStrip> obiektu zawartego w formularzu.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hostuje inne kontrolki, które nie <xref:System.Windows.Forms.ToolStrip>ją formantów, ale dla których chcesz <xref:System.Windows.Forms.ToolStrip> funkcje.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Określa, czy <xref:System.Windows.Forms.ToolStripItem> ma być określony na głównym <xref:System.Windows.Forms.ToolStrip>, na <xref:System.Windows.Forms.ToolStrip>przepełnienia, czy nie.|  
  
 Aby uzyskać więcej informacji, zobacz [Podsumowanie technologii ToolStrip](toolstrip-technology-summary.md) i [Architektura formantów ToolStrip](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
