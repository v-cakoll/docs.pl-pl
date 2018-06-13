---
title: Przegląd Użyj automatycznego układu
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 8693150099559ca09541eb790c134ca3d5277e78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548318"
---
# <a name="use-automatic-layout-overview"></a>Przegląd Użyj automatycznego układu
W tym temacie przedstawiono wskazówki dla deweloperów dotyczące programowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji za pomocą Lokalizowalny [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. W przeszłości, lokalizacja [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] został czasochłonny proces. Każdego języka, który [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] została dostosowana dla wymagane dostosowanie poszczególne piksele. Dzisiaj z prawej projektu i prawej standardy, kodowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] można skonstruować tak, aby wiadomość dla lokalizatorów mają mniejsze zmiana rozmiaru i położenia zrobić. Podejście do pisania aplikacji, które mogą być łatwo po zmianie rozmiaru i zmienionym jest nazywana automatyczny układ i może zostać osiągnięty przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikacji.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Zalety korzystania z automatycznego układu  
 Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentacji system jest wystarczająco wydajny i elastyczny, zapewnia możliwość układ elementów w aplikacji, którą można dostosować do wymagań różnych języków. Poniższa lista wskazuje niektóre zalety automatyczny układ.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Wyświetla również w dowolnym języku.  
  
-   Ogranicza potrzebę Dopasuj położenie i rozmiar kontrolki po przetłumaczono tekstu.  
  
-   Ogranicza potrzebę Dopasuj rozmiar okna.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] układu renderuje prawidłowo w dowolnym języku.  
  
-   Lokalizacja, można zmniejszyć do punktu się nieco więcej niż ciąg tłumaczenia.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Automatyczny układ i kontrolek  
 Automatyczny układ umożliwia aplikacji w celu automatycznego dopasowania rozmiaru formantu. Na przykład formantu można zmienić celu uwzględnienia długość ciągu. Ta funkcja umożliwia wiadomość dla lokalizatorów można przetłumaczyć ciągu; potrzebna jest już rozmiar formantu w celu dopasowania przetłumaczonego tekstu. Poniższy przykład tworzy przycisk o zawartości w języku angielskim.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 W tym przykładzie wszystko, co należy zrobić, aby przycisk hiszpańskim jest zmiana tekstu. Na przykład  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe przykładów kodu.  
  
 ![Ten sam przycisk z tekstem w różnych językach](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Przycisk o zmiennym rozmiarze automatycznie  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Automatyczny układ i standardy kodowania  
 W sposób automatyczny układ wymaga zestawu kodowania i projektowania oraz reguł do utworzenia w pełni Lokalizowalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Poniższe wskazówki pomoże kodowania automatyczny układ.  
  
|Standardy kodowania|Opis|  
|----------------------|-----------------|  
|Nie należy używać położenia bezwzględne.|— Nie używaj <xref:System.Windows.Controls.Canvas> ponieważ umieszcza elementy absolutnie.<br />-Użyj <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, i <xref:System.Windows.Controls.Grid> do Umieść formanty.<br />— Aby uzyskać informacje o różnych typach panele, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md).|  
|Nie ustawiaj o stałym rozmiarze okna.|-Użyj <xref:System.Windows.Window.SizeToContent%2A>.<br />— Na przykład:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A>.|<ul><li>Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A> do elementu głównego aplikacji.</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia to wygodny sposób obsługiwać poziomej, dwukierunkowego i układy pionowy. W ramach prezentacji <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości może służyć do definiowania układu. Wzorce kierunek przepływu to:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight> (LrTb) — układ poziomy Latin, wschodnioazjatyckich i tak dalej.</li><li><xref:System.Windows.FlowDirection.RightToLeft> (RlTb) — dwukierunkowy dla arabskiego, hebrajskiego i tak dalej.</li></ul></li></ul>|  
|Użyj czcionki zamiast fizycznej czcionki.|<ul><li>W przypadku złożonego czcionek <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości nie musi być lokalizowany.</li><li>Deweloperzy można użyć jednej z następujących czcionek lub utworzyć własne.<br /><br /> <ul><li>Interfejs użytkownika globalne</li><li>Serif globalnej sieci San</li><li>Globalne Serif</li></ul></li></ul>|  
|Dodaj XML: lang.|-Dodaj `xml:lang` atrybutu w elemencie głównym Twojego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], takich jak `xml:lang="en-US"` dla aplikacji w języku angielskim.<br />-Ponieważ Użyj czcionki `xml:lang` Aby ustalić, jakie czcionki do użycia, ustaw tę właściwość obsługi wielu języków.|  
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Automatyczny układ i siatki  
 <xref:System.Windows.Controls.Grid> Elementu, jest przydatne w przypadku automatycznego układu, ponieważ umożliwia ona deweloperom położenie elementów. A <xref:System.Windows.Controls.Grid> formant jest w stanie dystrybucji dostępna ilość miejsca między jego elementy podrzędne, przy użyciu w układzie wierszy i kolumn. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementów może obejmować wielu komórek, a użytkownik może mieć siatki wewnątrz siatki. Siatki są przydatne, ponieważ umożliwiają one tworzenie i umieść złożonych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W poniższym przykładzie pokazano, używając siatka do umieszczenia niektórych przycisków i tekst. Należy zauważyć, że ustawiono wysokość i szerokość komórek <xref:System.Windows.GridUnitType.Auto>; w związku z tym komórki, która zawiera przycisk Obraz jest dopasowywany obrazu.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono siatki utworzonego przez poprzedni kod.  
  
 ![Przykład siatka](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Siatka  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatyczny układ i za pomocą właściwości IsSharedSizeScope siatki  
 A <xref:System.Windows.Controls.Grid> element jest przydatny do zlokalizowania aplikacji do tworzenia kontrolek, które Dopasuj do zawartości. Jednak w czasie ma służy do obsługi określonego rozmiaru niezależnie od zawartości. Na przykład jeśli masz "OK", "Anuluj" i "Przeglądaj" prawdopodobnie nie ma przyciski dopasowana zawartość przycisków. W takim przypadku <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> dołączona właściwość jest przydatna do udostępniania tego samego rozmiaru między wiele elementów siatki. W poniższym przykładzie pokazano, jak udostępniać dane między wieloma rozmiaru wierszy i kolumn <xref:System.Windows.Controls.Grid> elementów.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Uwaga** przykładowej kompletny kod, zobacz [udziału zmiany rozmiaru właściwości między siatki](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Globalizacja dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Używanie automatycznego układu do utworzenia przycisku](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Używanie siatki do automatycznego układu](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
