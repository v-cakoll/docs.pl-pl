---
title: Podsumowanie informacji o technologii formantów ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: d447f78a6b6d8a71ea2e67d4c991655eb4712199
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654705"
---
# <a name="toolstrip-technology-summary"></a>Podsumowanie informacji o technologii formantów ToolStrip
Ten temat zawiera podsumowanie informacji o `ToolStrip` kontroli i klas, które obsługują jego użycia.  
  
 `ToolStrip` Kontrolki i ich skojarzonych klas zapewnić kompletne rozwiązanie do tworzenia paski narzędzi, paski stanu i menu.  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Tło  
 Za pomocą `ToolStrip` kontrolki i ich skojarzonych klas, można utworzyć funkcji zaawansowanych narzędzi, który ma spójny i profesjonalny wygląd i zachowanie. `ToolStrip` Kontrolki i klasy oferują następujące udoskonalenia przez poprzednie kontrolki:  
  
- Bardziej spójny model zdarzeń.  
  
- Bardziej spójne zachowanie czasu projektowania, który zawiera listy zadań i edytory kolekcji elementów.  
  
- Niestandardowe renderowanie z `ToolStripManager` i `ToolStripRenderer`.  
  
- Rafting (udostępnianie poziomą lub pionową miejsca w obszarze Narzędzia, gdy jest zadokowany) za pomocą wbudowanego `ToolStripContainer` i `ToolStripPanel`.  
  
- W czasie projektowania i środowiska wykonawczego zmiany kolejności elementów mających <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwości.  
  
- Relokacja elementów, które mają menu przepełnienia z <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> właściwości.  
  
- Lokalizacja formantu całkowicie można skonfigurować za pomocą `ToolStripContainer`, `ToolStripPanel`, i `ToolStripContentPanel`.  
  
- Hosting `ToolStrip`, tradycyjnych lub niestandardowych formantów, za pomocą `ToolStripControlHost`.  
  
- Scalanie `ToolStrip` kontrolki przy użyciu `ToolStripPanel`.  
  
 `ToolStrip` jest rozszerzalny klasę bazową dla `MenuStrip`, `ContextMenuStrip`, i `StatusStrip`. Kontrolki te są <xref:System.Windows.Forms.ToolStripItem> kontenerów, które dziedziczą wspólnego zachowania i obsługa zdarzeń rozszerzonych tak, aby każda implementacja zajmuje się zachowanie, które jest odpowiednie dla niego. Formanty, które wynikają z <xref:System.Windows.Forms.ToolStripItem> są wymienione w poniższej tabeli. Podstawa `ToolStrip` klasa obsługuje zdarzenia przeciągania i upuszczania dla tych formantów, dane wejściowe użytkownika i rysowania.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, I `StatusStrip` formantów zastąpić poprzedni pasek narzędzi, menu, menu skrótów i formanty paska stanu, mimo że te kontrolki zostaną zachowane dla zgodności z poprzednimi wersjami.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Klasy ToolStrip w skrócie  
 W poniższej tabeli przedstawiono klasy ToolStrip, pogrupowane według obszaru technologii.  
  
|Obszar technologiczny|Class|  
|---------------------|-----------|  
|Pasek narzędzi, stanu i Menu kontenerów|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Elementów ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Lokalizacja|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Prezentacja i renderowania|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>Funkcje czasu projektowania ToolStrip  
 <xref:System.Windows.Forms.ToolStrip> Rodziny formanty zapewnia bogaty zestaw narzędzi i szablonów w miejscu do edycji i definiowanie podstawę interfejsu użytkownika, dzięki czemu można szybko utworzyć działającą aplikację.  
  
### <a name="task-dialog-boxes"></a>Okno dialogowe zadań  
 W programie Visual Studio kliknięcie tagu inteligentnego na formantu w Projektancie Wyświetla listę zadań wygodny dostęp do wielu często używanych poleceń.  
  
- [MenuStrip — okno dialogowe zadań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233645(v=vs.100))  
  
- [ToolStrip — okno dialogowe zadań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233648(v=vs.100))  
  
- [ContextMenuStrip — okno dialogowe zadań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233646(v=vs.100))  
  
- [StatusStrip — okno dialogowe zadań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100))  
  
- [ToolStripContainer — okno dialogowe zadań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233647(v=vs.100))  
  
### <a name="items-collection-editors"></a>Edytory kolekcji elementów  
 W programie Visual Studio, po kliknięciu **Edytuj elementy** zadania listy lub kliknij prawym przyciskiem myszy formant, a następnie wybierz pozycję **Edytuj elementy** w menu skrótów edytora kolekcji dla formantu jest wyświetlany. Edytory kolekcji umożliwiają dodawanie, usuwanie i zmienić kolejność elementów, które zawierają kontrolki. Można również wyświetlanie i zmiana właściwości formantu i kontrolki elementów.  
  
- [MenuStrip — Edytor kolekcji elementów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233625(v=vs.100))  
  
- [StatusStrip — Edytor kolekcji elementów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100))  
  
- [ContextMenuStrip — Edytor kolekcji elementów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233641(v=vs.100))  
  
- [Edytor kolekcji elementów ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))  
  
## <a name="hosting-controls"></a>Hosting kontrolek  
 <xref:System.Windows.Forms.ToolStripControlHost> Klasa udostępnia wbudowane otoki <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki. Możesz również hostować innych istniejących lub kontrolki COM w <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Aby uzyskać przykład hosting kontrolki, zobacz [jak: OPAKOWYWANIE formant programu Windows Forms za pomocą elementu ToolStripControlHost](how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Renderowanie  
 <xref:System.Windows.Forms.ToolStrip> klasy implementować schemat renderowania, który znacznie różni się od innych kontrolek Windows Forms. Ten schemat można łatwo zastosować stylów i motywów.  
  
 Aby zastosować styl do <xref:System.Windows.Forms.ToolStrip> i wszystkie <xref:System.Windows.Forms.ToolStripItem> w nim obiekty, nie trzeba obsługiwać <xref:System.Windows.Forms.ToolStripItem.Paint> zdarzenie dla każdego elementu. Zamiast tego można ustawić <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> jedną z właściwości <xref:System.Windows.Forms.ToolStripRenderMode> wartości innych niż <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternatywnie, można ustawić <xref:System.Windows.Forms.ToolStrip.Renderer%2A> bezpośrednio do każdej klasy, która dziedziczy <xref:System.Windows.Forms.ToolStripRenderer> klasy. Ustawienie tej właściwości jest automatycznie ustawia <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Ten styl można zastosować do wielu <xref:System.Windows.Forms.ToolStrip> obiektów w tej samej aplikacji, ustawiając <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> do <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> i ustawienie <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> lub <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> właściwości <xref:System.Windows.Forms.ToolStripManagerRenderMode> przewidzianą lub <xref:System.Windows.Forms.ToolStripRenderer> wartości odpowiednio.  
  
 Aby uzyskać przykłady renderowania, zobacz [jak: Tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Style i motywów  
 <xref:System.Windows.Forms.ToolStrip> i skojarzonych klas umożliwiają łatwe do obsługi funkcji stylów wizualnych i wygląd niestandardowych, które nie wymagają zastępowanie <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> metody dla każdego elementu. Użyj <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> i <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> i <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.  
  
## <a name="rafting-and-docking"></a>Rafting i dokowanie  
 Możesz tratwie, dokowanie lub całkowicie pozycji <xref:System.Windows.Forms.ToolStrip> kontrolki. <xref:System.Windows.Forms.ToolStrip> elementy są ułożone <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kontenera.  
  
 *Rafting* jest możliwość udostępniania poziomej lub pionowej przestrzeni pasków narzędzi. Formularz Windows może mieć <xref:System.Windows.Forms.ToolStripContainer> który z kolei ma paneli w formularza po lewej stronie, po prawej stronie, górnej i dolne krawędzie, pozycjonowanie i rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki. Wiele <xref:System.Windows.Forms.ToolStrip> kontrolki w pionie stosu umieszczenie w lewo lub w prawo <xref:System.Windows.Forms.ToolStripContainer>. One ułożone poziomo, jeśli umieść je w górę lub w dół <xref:System.Windows.Forms.ToolStripContainer>. Możesz użyć centralnej <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> do pozycji tradycyjne formanty formularza.  
  
 Any lub all <xref:System.Windows.Forms.ToolStripContainer> formanty są bezpośrednio można wybierać w czasie projektowania i można je usunąć. Element <xref:System.Windows.Forms.ToolStripContainer> jest rozwijane i zwijane i zmienia rozmiar z kontrolkami, które zawiera.  
  
 *Dokowanie* jest określenie proste położenie formantu formularza po lewej stronie, po prawej stronie, top lub dolna część.  
  
 Zaletą rafting za pośrednictwem dokowanie jest to, że <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki mogą udostępniać miejsce na poziomą lub pionową innych kontrolek.  
  
 Większość <xref:System.Windows.Forms.ToolStrip> może być zadokowane formantów do formularza, podobnie jak inne kontrolki, zamiast rafting. Można również określić, że <xref:System.Windows.Forms.ToolStrip> kontroli swobodnie rozmieszczone na formularzu, usuwając go z jego <xref:System.Windows.Forms.ToolStripContainer> i ustawienie jej `Dock` właściwości `None`, lub można określić położenia bezwzględne, ustawiając do odpowiednich <xref:System.Windows.Forms.Control.Location%2A> Właściwość. Zobacz [jak: Przenoszenie elementu ToolStrip z ToolStripContainer na formularz](how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Użyj co najmniej jeden <xref:System.Windows.Forms.ToolStripPanel> formantów większej elastyczności, szczególnie w przypadku aplikacji wielu interfejsu dokumentów (MDI), lub jeśli nie potrzebujesz <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> dokowalne miejsce do lokalizowania i rafting <xref:System.Windows.Forms.ToolStrip> formanty, ale nie tradycyjne formanty. Domyślnie <xref:System.Windows.Forms.ToolStripPanel> nie jest wyświetlana w Projektancie **przybornika**, ale można umieścić ją w tym miejscu, klikając prawym przyciskiem myszy **przybornika**, a następnie kliknij przycisk **wybierz elementy**. Możesz też programowo uzyskać dostęp <xref:System.Windows.Forms.ToolStripPanel> , takich jak inne klasy.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, I <xref:System.Windows.Forms.StatusStrip> umożliwiają przepełnienie elementów. Jest to podobne do sposób, w jaki te elementy działają na paskach narzędzi Microsoft Office.  
  
## <a name="see-also"></a>Zobacz także

- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
