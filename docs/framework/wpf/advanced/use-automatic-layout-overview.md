---
title: Przegląd Użyj automatycznego układu
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 4cb351b0db83bd83c17aa4aca004b310dc957437
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609606"
---
# <a name="use-automatic-layout-overview"></a>Przegląd Użyj automatycznego układu
W tym temacie przedstawiono wskazówki dla deweloperów dotyczące programowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji przy użyciu możliwych do zlokalizowania [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. W przeszłości lokalizacja interfejs użytkownika był czasochłonny proces. Każdego z języków interfejsu użytkownika została dostosowana do wymagana korekta poszczególne piksele. Dzisiaj z właściwy projekt i po prawej stronie standardy, kodowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] można skonstruować tak, aby lokalizatorzy mają mniejsza Zmienianie rozmiaru i położenia celu. Podejścia do pisania aplikacji, które można łatwiej o zmienionym rozmiarze i zmienionym nosi nazwę automatycznego układu oraz można osiągnąć za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projektowania aplikacji.  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Korzyści wynikające z używania automatycznego układu  
 Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system prezentacji jest wydajny i elastyczny, daje możliwość elementów układu w aplikacji, którą można dostosować zgodnie z wymaganiami w różnych językach. Poniższa lista wskazuje niektóre korzyści wynikające z układem automatycznym.  

-   Interfejs użytkownika wyświetla się także w dowolnym języku.  

-   Ogranicza potrzebę ponownie dopasować położenie i rozmiar kontrolki po jest przetłumaczony tekst.  
  
-   Ogranicza potrzebę Dopasuj rozmiar okna.  

-   Układ interfejsu użytkownika poprawnie renderowany w dowolnym języku.  

-   Lokalizacja można zmniejszyć do punktu, jest on nieco więcej niż ciąg tłumaczenia.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Automatyczny układ i kontrolek  
 Układ automatyczny umożliwia aplikacji automatyczne dopasowanie rozmiaru formantu. Na przykład kontrolki można zmienić celu uwzględnienia długość ciągu. Ta funkcja umożliwia lokalizatorzy do tłumaczenia ciągów; muszą już nie zmienia rozmiar formantu w celu dopasowania do przetłumaczonego tekstu. Poniższy przykład tworzy przycisk z zawartości w języku angielskim.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 W tym przykładzie jest wszystko, co trzeba zrobić, aby przycisk hiszpańskim, zmienianie tekstu. Na przykład  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe z przykładów kodu.  
  
 ![Ten sam przycisk z tekstem w różnych językach](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Zmienny rozmiar przycisku automatycznie  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Automatyczny układ i standardy kodowania  
 Przy użyciu metody automatycznego układu wymaga zestawu kodowania i projektowania standardów i zasad do produkcji w pełni Lokalizowalny interfejsu użytkownika. Poniższe wskazówki będą pomocy kodowania automatycznego układu.  

**Nie używaj położenia bezwzględne**

- Nie używaj <xref:System.Windows.Controls.Canvas> ponieważ umieszcza elementy absolutnie.

- Użyj <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, i <xref:System.Windows.Controls.Grid> położenie kontrolki.

Aby uzyskać informacje o różnych typach paneli, zobacz [Przegląd panele](../../../../docs/framework/wpf/controls/panels-overview.md).

**Nie należy ustawiać o stałym rozmiarze okna**

- Użyj <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Na przykład:

   [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A> do elementu głównego aplikacji.

   WPF zapewnia wygodny sposób obsługi poziomej, dwukierunkowe i układów w pionie. W ramach prezentacji <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość może służyć do definiowania układu. Wzorce kierunek przepływu są:
   
     - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — układ poziomy łaciński, Azja Wschodnia i tak dalej.
     
     - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — dwukierunkowych dla arabskiego, hebrajskiego i tak dalej.

**Użyj czcionki zamiast fizycznych czcionek**

- W przypadku złożonych czcionek <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości nie musi być lokalizowany.

- Deweloperzy można użyć jednej z następujących czcionek lub utworzyć własne.

   - Globalny interfejs użytkownika
   - Serif globalne sieci San
   - Globalne Serif

**Dodaj XML: lang**

- Dodaj `xml:lang` atrybutu w elemencie głównym interfejsu użytkownika, takie jak `xml:lang="en-US"` dla aplikacji w języku angielskim.

- Ponieważ używają czcionki `xml:lang` Aby ustalić, jakie czcionki do użycia, należy ustawić tę właściwość, do obsługi wielu języków scenariuszy.

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Automatyczny układ i siatki  
 <xref:System.Windows.Controls.Grid> Elementu, jest przydatne w przypadku automatycznego układu, ponieważ umożliwia deweloperom położenie elementów. A <xref:System.Windows.Controls.Grid> kontrolka jest w stanie dystrybucji dostępna ilość miejsca między jego elementów podrzędnych, za pomocą w układzie wierszy i kolumn. Elementy interfejsu użytkownika może obejmować wiele komórek. Ponadto istnieje możliwość mają siatki w obrębie siatki. Siatki są przydatne, ponieważ umożliwiają one tworzenie i umieść złożonego interfejsu użytkownika. Poniższy przykład demonstruje użycie siatki do pozycji niektóre przyciski i tekst. Należy zauważyć, że wysokość i szerokość komórek są ustawione na <xref:System.Windows.GridUnitType.Auto>; dlatego komórkę, która zawiera przycisk za pomocą obrazu jest dopasowywany obrazu.  

 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Na poniższym rysunku przedstawiono siatki produkowane przez poprzedniego kodu.  
  
 ![Przykład Grid](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Siatka  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatyczny układ i siatki, przy użyciu właściwości IsSharedSizeScope  
 A <xref:System.Windows.Controls.Grid> element jest przydatne w zlokalizowanych aplikacjach w celu tworzenia formantów, które Dopasuj do zawartości. Jednak czasami chcesz służy do obsługi określonego rozmiaru, niezależnie od zawartości. Na przykład jeśli masz "OK", "Anuluj" i "Przeglądaj" przyciski, prawdopodobnie nie ma przyciski dopasowana zawartości. W tym przypadku <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> dołączoną właściwość przydaje się do udostępniania tego samego rozmiaru między wiele elementów siatki. W poniższym przykładzie pokazano sposób udostępniania danych między wieloma rozmiaru wierszy i kolumn <xref:System.Windows.Controls.Grid> elementów.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Uwaga** cały przykładowy kod, można zobaczyć [udziału właściwości ustalania rozmiaru między siatkami](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Zobacz także
- [Globalizacja dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
- [Używanie automatycznego układu do utworzenia przycisku](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
- [Używanie siatki do automatycznego układu](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
