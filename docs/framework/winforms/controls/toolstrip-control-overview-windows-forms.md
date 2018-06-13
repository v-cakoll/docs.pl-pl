---
title: ToolStrip — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3927f180e738541f2f2f8af6d03d281f6a601167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542054"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip — Informacje o formancie [Formularze systemu Windows]
Formularze systemu Windows <xref:System.Windows.Forms.ToolStrip> kontroli i jego skojarzonych klas podanie łączenie elementy interfejsu użytkownika w paskach narzędzi, pasków stanu i menu wspólnej struktury. <xref:System.Windows.Forms.ToolStrip> Formanty zapewniają bogate środowisko czasu projektowania, zawierającą Aktywacja w miejscu i edytowanie niestandardowego układu i rafting, czyli paski narzędzi umożliwiają udostępnianie miejsca pozioma lub pionowa.  
  
 Mimo że <xref:System.Windows.Forms.ToolStrip> zastępuje i dodaje do formantu w poprzednich wersjach, funkcje <xref:System.Windows.Forms.ToolBar> są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli to konieczne.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkcje formantów ToolStrip  
 Użyj <xref:System.Windows.Forms.ToolStrip> formant:  
  
-   Przedstawia wspólnego interfejsu użytkownika w kontenerach.  
  
-   Tworzenie łatwo dostosować, często rachunek pasków narzędzi, które obsługuje zaawansowane funkcje, a układ interfejsu użytkownika, takie jak przyciski dokowania, raftingu, tekst i obrazy, przycisków listy rozwijanej i formanty przepełnienie przycisków i środowiska wykonawczego kolejności <xref:System.Windows.Forms.ToolStrip> elementy.  
  
-   Obsługuje przepełnienie i zmianę kolejności elementów czasu wykonania. Funkcja przepełnienie przenosi elementy do menu rozwijanego, gdy nie ma wystarczającej ilości miejsca, aby wyświetlić je w <xref:System.Windows.Forms.ToolStrip>.  
  
-   Obsługuje typowe wyglądu i zachowania systemu operacyjnego za pomocą wspólnego modelu renderowania.  
  
-   Obsługa zdarzeń spójnie dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych formantów.  
  
-   Przeciągnij elementy z jednego <xref:System.Windows.Forms.ToolStrip> do innego lub w <xref:System.Windows.Forms.ToolStrip>.  
  
-   Tworzenie kontrolki listy rozwijanej i użytkownika edytory typu interfejsu przy użyciu zaawansowanych układów w <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Użyj <xref:System.Windows.Forms.ToolStripControlHost> klasy do używania innych kontrolek na <xref:System.Windows.Forms.ToolStrip> i uzyskanie <xref:System.Windows.Forms.ToolStrip> funkcje dla nich.  
  
 Można rozszerzyć funkcjonalność i zmodyfikować wygląd i zachowanie przy użyciu <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, i <xref:System.Windows.Forms.ToolStripManager> wraz z <xref:System.Windows.Forms.ToolStripRenderMode> i <xref:System.Windows.Forms.ToolStripManagerRenderMode> wyliczenia.  
  
 <xref:System.Windows.Forms.ToolStrip> Formant jest wysoce można konfigurować i rozszerzalny i oferuje wiele właściwości, metod i zdarzeń w celu dostosowania wyglądu i zachowania. Poniżej przedstawiono niektóre warte wymienienia członków:  
  
### <a name="important-toolstrip-members"></a>Elementy członkowskie ważne ToolStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Pobiera lub ustawia które krawędzią kontenera nadrzędnego <xref:System.Windows.Forms.ToolStrip> jest zadokowane.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Pobiera lub ustawia wartość wskazującą, czy przeciągania i upuszczania oraz zmianę kolejności elementów są obsługiwane przez użytkowników przez <xref:System.Windows.Forms.ToolStrip> klasy.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Pobiera lub ustawia wartość wskazującą sposób <xref:System.Windows.Forms.ToolStrip> wychodzi poza jej elementów.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Pobiera lub ustawia czy <xref:System.Windows.Forms.ToolStripItem> jest dołączony do <xref:System.Windows.Forms.ToolStrip> lub <xref:System.Windows.Forms.ToolStripOverflowButton> lub poruszać się między nimi.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Pobiera wartość wskazującą czy <xref:System.Windows.Forms.ToolStripItem> inne elementy są wyświetlane w listy rozwijanej liście kiedy <xref:System.Windows.Forms.ToolStripItem> zostanie kliknięty.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Pobiera <xref:System.Windows.Forms.ToolStripItem> czyli przycisku przeciążenia dla <xref:System.Windows.Forms.ToolStrip> z przepełnienie włączone.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripRenderer> używane do dostosowywania wyglądu i zachowania (wygląd i działanie) <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Pobiera lub ustawia styl rysowania ma zostać zastosowany do <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Wywoływane, gdy <xref:System.Windows.Forms.ToolStrip.Renderer%2A> zmiany właściwości.|  
  
 <xref:System.Windows.Forms.ToolStrip> Elastyczność formantu odbywa się przy użyciu szereg klas pomocnika. Poniżej przedstawiono niektóre z najczęściej warte wymienienia:  
  
### <a name="important-toolstrip-companion-classes"></a>Klasy ważnym dodatkiem ToolStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Zastępuje i dodaje funkcje do <xref:System.Windows.Forms.MainMenu> klasy.|  
|<xref:System.Windows.Forms.StatusStrip>|Zastępuje i dodaje funkcje do <xref:System.Windows.Forms.StatusBar> klasy.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ContextMenu> klasy.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstrakcyjna klasa podstawowa, która zarządza zdarzeń i układu dla wszystkich elementów, które <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, lub <xref:System.Windows.Forms.ToolStripDropDown> może zawierać.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Udostępnia kontener z panelem po obu stronach formularza, w którym można uporządkować formantów na różne sposoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Obsługuje funkcje rysowania <xref:System.Windows.Forms.ToolStrip> obiektów.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Udostępnia wygląd stylu pakietu Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Formanty <xref:System.Windows.Forms.ToolStrip> renderowania i rafting i scalanie <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, i <xref:System.Windows.Forms.ToolStripMenuItem> obiektów.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Określa styl rysowania (niestandardowe, Windows XP lub Microsoft Office Professional) stosowany do wielu <xref:System.Windows.Forms.ToolStrip> obiektów zawartych w formularzu.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Określa styl rysowania (niestandardowe, Windows XP lub Microsoft Office Professional) stosowany do jednego <xref:System.Windows.Forms.ToolStrip> obiektów zawartych w formularzu.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Obsługuje inne formanty, które nie są specjalnie <xref:System.Windows.Forms.ToolStrip> formantów, ale dla którego ma <xref:System.Windows.Forms.ToolStrip> funkcji.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Określa, czy <xref:System.Windows.Forms.ToolStripItem> ma zostać uwzględnione w głównym <xref:System.Windows.Forms.ToolStrip>, na przeciążenia <xref:System.Windows.Forms.ToolStrip>, albo nie.|  
  
 Aby uzyskać więcej informacji, zobacz [podsumowanie informacji o technologii ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) i [architektura formantu ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
