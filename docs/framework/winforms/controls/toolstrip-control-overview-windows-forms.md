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
ms.openlocfilehash: 3e532b040d3c7859220b7f73958b63e7208b988c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144576"
---
# <a name="toolstrip-control-overview-windows-forms"></a>ToolStrip — Informacje o formancie [Formularze systemu Windows]
Formularze Windows <xref:System.Windows.Forms.ToolStrip> kontrolki i ich skojarzonych klas zapewniają wspólną platformę łączenie elementów interfejsu użytkownika w paski narzędzi, paski stanu i menu. <xref:System.Windows.Forms.ToolStrip> kontrolki oferują bogate środowisko czasu projektowania, która obejmuje aktywacji w miejscu i edytowanie, układu niestandardowego i rafting, który jest możliwość udostępniania poziomej lub pionowej przestrzeni pasków narzędzi.  
  
 Mimo że <xref:System.Windows.Forms.ToolStrip> zastępuje i dodaje funkcjonalność do kontroli w poprzednich wersjach <xref:System.Windows.Forms.ToolBar> został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości w razie potrzeby.  
  
## <a name="features-of-the-toolstrip-controls"></a>Funkcje kontrolek ToolStrip  
 Użyj <xref:System.Windows.Forms.ToolStrip> kontrolę:  
  
-   Przedstawia wspólnego interfejsu użytkownika różnych kontenerów.  
  
-   Tworzenie łatwo dostosować, powszechnie wykorzystywane paski narzędzi, które obsługują zaawansowane funkcje interfejsu i układ użytkownika, takie jak przyciski dokowania, rafting, za pomocą tekstu i obrazów, przyciski i formanty overflow przycisków i zmiana kolejności środowiska wykonawczego <xref:System.Windows.Forms.ToolStrip> elementy.  
  
-   Obsługuje przepełnienie i zmiany kolejności elementów w czasie wykonywania. Funkcja przepełnienie przenosi elementy do menu rozwijanego, gdy nie jest wystarczająco dużo miejsca, aby wyświetlić je w <xref:System.Windows.Forms.ToolStrip>.  
  
-   Obsługiwać typowego wyglądu i zachowania systemu operacyjnego za pomocą wspólnego modelu renderowania.  
  
-   Obsługa zdarzeń spójne dla wszystkich kontenerów i zawartych w niej elementów, w taki sam sposób obsługi zdarzeń dla innych kontrolek.  
  
-   Przeciągnij elementy z jednego <xref:System.Windows.Forms.ToolStrip> do innego lub w ramach <xref:System.Windows.Forms.ToolStrip>.  
  
-   Tworzenie kontrolki listy rozwijanej i użytkownika edytory typów interfejsu przy użyciu zaawansowanych układów w <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Użyj <xref:System.Windows.Forms.ToolStripControlHost> klasy na korzystanie z innych formantów <xref:System.Windows.Forms.ToolStrip> i uzyskanie <xref:System.Windows.Forms.ToolStrip> funkcjonalność dla nich.  
  
 Możesz rozszerzyć funkcjonalność i modyfikować wygląd i zachowanie za pomocą <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, i <xref:System.Windows.Forms.ToolStripManager> wraz z <xref:System.Windows.Forms.ToolStripRenderMode> i <xref:System.Windows.Forms.ToolStripManagerRenderMode> wyliczenia.  
  
 <xref:System.Windows.Forms.ToolStrip> Formant jest wysoce konfigurowalne i rozszerzalny i udostępnia wiele właściwości, metod i zdarzeń, aby dostosować wygląd i zachowanie. Poniżej przedstawiono niektóre warte zauważenia elementy członkowskie:  
  
### <a name="important-toolstrip-members"></a>ToolStrip ważne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Pobiera lub ustawia które krawędzią kontenera nadrzędnego <xref:System.Windows.Forms.ToolStrip> jest zadokowany do.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Pobiera lub ustawia wartość wskazującą, czy przeciągania i upuszczania oraz zmianę kolejności elementów są obsługiwane przez użytkowników dzięki <xref:System.Windows.Forms.ToolStrip> klasy.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Pobiera lub ustawia wartość wskazującą sposób, w jaki <xref:System.Windows.Forms.ToolStrip> wychodzi poza jego elementów.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Pobiera lub ustawia czy <xref:System.Windows.Forms.ToolStripItem> jest dołączony do <xref:System.Windows.Forms.ToolStrip> lub <xref:System.Windows.Forms.ToolStripOverflowButton> lub poruszać się między nimi.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Pobiera wartość wskazującą czy <xref:System.Windows.Forms.ToolStripItem> inne elementy są wyświetlane w menu rozwijane listy, kiedy <xref:System.Windows.Forms.ToolStripItem> kliknięciu.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Pobiera <xref:System.Windows.Forms.ToolStripItem> czyli przepełnienie przycisk <xref:System.Windows.Forms.ToolStrip> z przepełnienia włączone.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Pobiera lub ustawia <xref:System.Windows.Forms.ToolStripRenderer> służące do dostosowywania wyglądu i zachowania (wyglądu i działania) <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Pobiera lub ustawia styl rysowania mają być stosowane do <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Wywołane, gdy <xref:System.Windows.Forms.ToolStrip.Renderer%2A> zmiany właściwości.|  
  
 <xref:System.Windows.Forms.ToolStrip> Elastyczność kontrolki odbywa się przy użyciu numeru klasy pomocnika. Poniżej przedstawiono niektóre z najbardziej warte zauważenia:  
  
### <a name="important-toolstrip-companion-classes"></a>Klasy ważne pomocnika ToolStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.MainMenu> klasy.|  
|<xref:System.Windows.Forms.StatusStrip>|Zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.StatusBar> klasy.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ContextMenu> klasy.|  
|<xref:System.Windows.Forms.ToolStripItem>|Abstrakcyjna klasa bazowa, zarządza zdarzeń i układ dla wszystkich elementów, które <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, lub <xref:System.Windows.Forms.ToolStripDropDown> może zawierać.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Udostępnia kontener za pomocą panelu po każdej stronie formularza, w którym formanty mogą być ułożone na różne sposoby.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Obsługuje funkcje malowania <xref:System.Windows.Forms.ToolStrip> obiektów.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Udostępnia wygląd stylu pakietu Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Formanty <xref:System.Windows.Forms.ToolStrip> renderowania i rafting i scalania <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, i <xref:System.Windows.Forms.ToolStripMenuItem> obiektów.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Określa styl rysowania (niestandardowe, Windows XP lub Microsoft Office Professional) stosowane do wielu <xref:System.Windows.Forms.ToolStrip> obiekty znajdujące się w formularzu.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Określa styl rysowania (niestandardowe, Windows XP lub Microsoft Office Professional) stosowane do <xref:System.Windows.Forms.ToolStrip> obiektów znajdujących się w formularzu.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Obsługuje inne formanty, które nie są specjalnie <xref:System.Windows.Forms.ToolStrip> kontrolek, ale dla którego ma <xref:System.Windows.Forms.ToolStrip> funkcji.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Określa, czy <xref:System.Windows.Forms.ToolStripItem> ma być rozmieszczony w głównym <xref:System.Windows.Forms.ToolStrip>, przy przepełnieniu <xref:System.Windows.Forms.ToolStrip>, żaden z tych.|  
  
 Aby uzyskać więcej informacji, zobacz [ToolStrip — podsumowanie informacji o technologii](toolstrip-technology-summary.md) i [ToolStrip — architektura formantu](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
