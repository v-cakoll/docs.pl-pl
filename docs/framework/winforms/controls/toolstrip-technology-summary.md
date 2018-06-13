---
title: Podsumowanie informacji o technologii formantów ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: c4f7b13590457623bbdfd6e4c07317f3a0285fd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541914"
---
# <a name="toolstrip-technology-summary"></a>Podsumowanie informacji o technologii formantów ToolStrip
Ten temat zawiera podsumowanie informacji o `ToolStrip` kontroli i klasy, które obsługują jej zastosowania.  
  
 `ToolStrip` Kontroli i jego skojarzonych klas zawiera kompletnego rozwiązania do tworzenia, pasków narzędzi, pasków stanu i menu.  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Tło  
 Z `ToolStrip` formant i jego skojarzonych klas, można utworzyć funkcji zaawansowanych narzędzi, które ma spójny i profesjonalny wygląd i zachowanie. `ToolStrip` Kontroli i klasy oferują następujące udoskonalenia przez poprzednie kontrole:  
  
-   Bardziej spójny model zdarzeń.  
  
-   Bardziej spójny zachowanie czasu projektowania, które zawiera listy zadań i edytory kolekcji elementów.  
  
-   Niestandardowe renderowanie z `ToolStripManager` i `ToolStripRenderer`.  
  
-   Rafting (udostępnianie poziomą lub pionową miejsca w obszarze Narzędzia, gdy jest zadokowany) z wbudowanych `ToolStripContainer` i `ToolStripPanel`.  
  
-   W czasie projektowania i środowiska wykonawczego zmiany kolejności elementów z <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwości.  
  
-   Przenoszenie elementów do menu przeciążenia z <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> właściwości.  
  
-   Lokalizacja formantu całkowicie można skonfigurować z `ToolStripContainer`, `ToolStripPanel`, i `ToolStripContentPanel`.  
  
-   Hosting `ToolStrip`, tradycyjnych lub niestandardowych formantów za pomocą `ToolStripControlHost`.  
  
-   Scalanie `ToolStrip` steruje przy użyciu `ToolStripPanel`.  
  
 `ToolStrip` jest rozszerzalny klasę podstawową dla `MenuStrip`, `ContextMenuStrip`, i `StatusStrip`. Te procedury są <xref:System.Windows.Forms.ToolStripItem> kontenerów, które dziedziczą wspólnego zachowania i obsługa zdarzeń rozszerzony tak, aby każda implementacja podchodzi do zachowania, które jest odpowiednie dla niego. Formanty, które pochodzą z <xref:System.Windows.Forms.ToolStripItem> są wymienione w poniższej tabeli. Podstawowym `ToolStrip` klasa obsługuje malowanie, dane wejściowe użytkownika i przeciągnij i upuść zdarzenia dla tych kontrolek.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, I `StatusStrip` formanty zastąpienie poprzednich narzędzi, menu, menu skrótów i formanty paska stanu, mimo że te rozwiązania, zostaną zachowane dla zgodności z poprzednimi wersjami.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Klasy ToolStrip w skrócie  
 W poniższej tabeli przedstawiono klasy ToolStrip pogrupowane według obszaru technologii.  
  
|Obszar technologii|Class|  
|---------------------|-----------|  
|Kontenery narzędzi, stanu i Menu|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Elementów ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Lokalizacja|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Prezentacja i renderowania|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>Funkcje czasu projektowania ToolStrip  
 <xref:System.Windows.Forms.ToolStrip> Rodziny formantów zapewnia bogaty zestaw narzędzi i szablonów w miejscu edytowania oraz definiowania podstawę interfejsu użytkownika, dzięki czemu można szybko utworzyć działającą aplikację.  
  
### <a name="task-dialog-boxes"></a>Zadanie okien dialogowych  
 W programie Visual Studio klikając tagów inteligentnych na formancie w Projektancie Wyświetla listę zadań dla najwygodniejszy dostęp do wielu często używanych poleceń.  
  
-   [Okno dialogowe zadania MenuStrip](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [Okno dialogowe zadania ToolStrip](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [Okno dialogowe zadania ContextMenuStrip](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [Okno dialogowe zadania StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [Okno dialogowe zadania ToolStripContainer](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Edytory kolekcji elementów  
 W programie Visual Studio, po kliknięciu **edytowanie elementów** w zadaniu listy lub kliknij prawym przyciskiem myszy sterowania i wybierz **edytowanie elementów** w menu skrótów wyświetlane jest Edytor kolekcji dla formantu. Edytory kolekcji umożliwiają dodawanie, usuwanie i zmienić kolejność elementów, które zawiera kontrolki. Można również wyświetlanie i zmiana właściwości formantu i elementów formantu.  
  
-   [Edytor kolekcji elementów MenuStrip](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [Edytor kolekcji elementów StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [Edytor kolekcji elementów ContextMenuStrip](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [Edytor kolekcji elementów ToolStrip](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Kontrolki hostingu  
 <xref:System.Windows.Forms.ToolStripControlHost> Klasa udostępnia wbudowane otoki dla <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki. Można również hostować innych istniejących lub kontrolki COM w <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Przykład hosting formatów, zobacz [porady: zawijanie formantu formularzy systemu Windows za pomocą elementu ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Renderowanie  
 <xref:System.Windows.Forms.ToolStrip> klasy implementować schemat renderowania, który znacznie różni się od innych formantów formularzy systemu Windows. Ten schemat można łatwo zastosować stylów i motywów.  
  
 Aby zastosować styl <xref:System.Windows.Forms.ToolStrip> i wszystkie <xref:System.Windows.Forms.ToolStripItem> zawarte w nim obiekty, nie trzeba obsłużyć <xref:System.Windows.Forms.ToolStripItem.Paint> zdarzeń dla każdego elementu. Zamiast tego można ustawić <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> jedną z właściwości <xref:System.Windows.Forms.ToolStripRenderMode> wartości innych niż <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternatywnie, można ustawić <xref:System.Windows.Forms.ToolStrip.Renderer%2A> bezpośrednio do dowolnej klasy, która dziedziczy <xref:System.Windows.Forms.ToolStripRenderer> klasy. Ustawienie tej właściwości automatycznie ustawia <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Ten styl można stosować do wielu <xref:System.Windows.Forms.ToolStrip> obiektów w tej samej aplikacji, ustawiając <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> do <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> i ustawienie <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> właściwości <xref:System.Windows.Forms.ToolStripManagerRenderMode> przewidzianą lub <xref:System.Windows.Forms.ToolStripRenderer> wartość odpowiednio.  
  
 Przykłady renderowania można znaleźć [jak: utworzyć i ustawić niestandardowego modułu renderowania dla formantu ToolStrip w formularzach systemu Windows](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Style i motywów  
 <xref:System.Windows.Forms.ToolStrip> i skojarzonych klas umożliwiają łatwe do obsługi style wizualne i wyglądu niestandardowych, które nie wymagają zastępowanie <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> metody dla każdego elementu. Użyj <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> i <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> i <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.  
  
## <a name="rafting-and-docking"></a>Rafting i dokowanie  
 Można raft, dock lub umieść absolutnie <xref:System.Windows.Forms.ToolStrip> kontrolki. <xref:System.Windows.Forms.ToolStrip> układ elementów <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kontenera.  
  
 *Rafting* jest możliwość udostępniania miejsca pozioma lub pionowa pasków narzędzi. Formularz systemu Windows może mieć <xref:System.Windows.Forms.ToolStripContainer> która z kolei ma panele na formularza lewo, prawo górnej i dolnej krawędzi pozycjonowanie i rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki. Wiele <xref:System.Windows.Forms.ToolStrip> formanty pionowo stosu umieszczenie w lewo lub w prawo <xref:System.Windows.Forms.ToolStripContainer>. One poziomie stosu umieszczenie w górny lub dolny <xref:System.Windows.Forms.ToolStripContainer>. Można użyć centralną <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> do tradycyjnych formanty pozycji na formularzu.  
  
 Dowolnych lub wszystkich <xref:System.Windows.Forms.ToolStripContainer> formanty są bezpośrednio wybieranych w czasie projektowania i można go usunąć. A <xref:System.Windows.Forms.ToolStripContainer> jest rozwijanej i zwijanej i zmienia rozmiar z formantami, które zawiera.  
  
 *Dokowanie* jest określenie lokalizacji prostego formantu w lewo, prawo, top lub dolnej formularza.  
  
 Zaletą rafting za pośrednictwem dokowanie jest to, że <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> formanty można udostępnić miejsca pozioma lub pionowa inne formanty.  
  
 Większość <xref:System.Windows.Forms.ToolStrip> może być zadokowany formantów do formularza, podobnie jak inne formanty zamiast rafting. Można również określić, że <xref:System.Windows.Forms.ToolStrip> kontrolki dystrybuowany za darmo być umieszczony w formularzu przez usunięcie go z jego <xref:System.Windows.Forms.ToolStripContainer> i ustawienie jej `Dock` właściwości `None`, lub można określić położenia bezwzględne, ustawiając odpowiednio <xref:System.Windows.Forms.Control.Location%2A> Właściwość. Zobacz [porady: Przenowszenie ToolStrip z ToolStripContainer na formularz](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Użyj co najmniej jeden <xref:System.Windows.Forms.ToolStripPanel> formantów w celu zapewnienia większej elastyczności, szczególnie w przypadku wielu interfejsu dokumentów (MDI) aplikacji lub jeśli nie ma potrzeby <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> dokującego miejsce do lokalizowania i rafting <xref:System.Windows.Forms.ToolStrip> formanty, ale nie tradycyjnych kontrolki. Domyślnie <xref:System.Windows.Forms.ToolStripPanel> w projektancie nie ma **przybornika**, ale można ją w tym miejscu umieścić klikając prawym przyciskiem myszy **przybornika**, a następnie kliknij przycisk **wybierz elementy**. Można również programowo dostęp <xref:System.Windows.Forms.ToolStripPanel> , takich jak innej klasy.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, I <xref:System.Windows.Forms.StatusStrip> let przepełnienie elementów. Efekt jest podobny do sposobu te elementy działają na paskach narzędzi Microsoft Office.  
  
## <a name="see-also"></a>Zobacz też  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
