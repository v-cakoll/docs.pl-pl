---
title: Przegląd Ekspander
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: ddf6ee550e0eb6af5af44d032e85ecd5b735b951
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130406"
---
# <a name="expander-overview"></a>Przegląd Ekspander
<xref:System.Windows.Controls.Expander> Kontroli umożliwia dostarczanie zawartości w obszarze rozwijania przypomina okna, która zawiera nagłówek.  

<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Tworzenie prostego ekspandera  
 Poniższy przykład pokazuje, jak utworzyć prostą <xref:System.Windows.Controls.Expander> kontroli. Ten przykład tworzy <xref:System.Windows.Controls.Expander> który wygląda podobnie do ilustracji powyżej.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> i <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> z <xref:System.Windows.Controls.Expander> może również zawierać złożonych zawartości, takich jak <xref:System.Windows.Controls.RadioButton> i <xref:System.Windows.Controls.Image> obiektów.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Ustawienie kierunku powiększających obszar zawartości  
 Możesz ustawić obszaru zawartości <xref:System.Windows.Controls.Expander> formantu, aby rozwinąć w jednej z czterech kierunków (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, lub <xref:System.Windows.Controls.ExpandDirection.Right>) przy użyciu <xref:System.Windows.Controls.ExpandDirection> właściwości. Kiedy obszar zawartości jest zwinięte, tylko <xref:System.Windows.Controls.Expander><xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i pojawiają się jego przycisku przełączania. A <xref:System.Windows.Controls.Button> kontrolkę wyświetlającą strzałkę kierunkową służy jako przycisk przełącznika, aby rozwinąć lub zwinąć obszar zawartości. Po rozwinięciu <xref:System.Windows.Controls.Expander> próbuje wyświetlić całej zawartości w obszarze podobne okno.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Kontrolowanie rozmiaru ekspander w panelu  
 Jeśli <xref:System.Windows.Controls.Expander> formant znajduje się wewnątrz kontrolkę układu, który dziedziczy z <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.StackPanel>, nie należy określać <xref:System.Windows.FrameworkElement.Height%2A> na <xref:System.Windows.Controls.Expander> podczas <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.ExpandDirection.Down> lub <xref:System.Windows.Controls.ExpandDirection.Up>. Podobnie, nie określaj <xref:System.Windows.FrameworkElement.Width%2A> na <xref:System.Windows.Controls.Expander> podczas <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.ExpandDirection.Left> lub <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Gdy ustawiasz wymiar rozmiaru <xref:System.Windows.Controls.Expander> kontroli w kierunku, rozwinięty zawartość jest wyświetlana, <xref:System.Windows.Controls.Expander> przejmuje kontrolę nad obszar, który jest używany przez zawartość i wyświetla obramowanie wokół niej. Pokazuje obramowania, nawet wtedy, gdy zawartość jest zwinięta. Rozmiar rozwinięty obszar zawartości ustawia wymiary rozmiaru zawartości <xref:System.Windows.Controls.Expander>, lub jeśli chcesz, aby przewijanie możliwości, na <xref:System.Windows.Controls.ScrollViewer> który otacza zawartości.  
  
 Gdy <xref:System.Windows.Controls.Expander> formant jest ostatnim elementem w <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] automatycznie ustawia <xref:System.Windows.Controls.Expander> wymiary wartość pozostałych obszaru <xref:System.Windows.Controls.DockPanel>. Aby zapobiec to domyślne zachowanie, ustaw <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> właściwość <xref:System.Windows.Controls.DockPanel> obiekt `false`, lub upewnij się, że <xref:System.Windows.Controls.Expander> nie jest ostatnim elementem w <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Tworzenie zawartości przewijany  
 Jeśli zawartość jest zbyt duży rozmiar obszaru zawartości, zawartość można opakować <xref:System.Windows.Controls.Expander> w <xref:System.Windows.Controls.ScrollViewer> zapewnić przewijanej treści. <xref:System.Windows.Controls.Expander> Kontroli automatycznie nie zapewnia funkcji przewijania. Poniższa ilustracja przedstawia <xref:System.Windows.Controls.Expander> kontrolkę zawierającą <xref:System.Windows.Controls.ScrollViewer> kontroli.  
  
 **Ekspander w ScrollViewer**  
  
 ![Zrzut ekranu pokazujący ekspander za pomocą paska przewijania.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Po umieszczeniu <xref:System.Windows.Controls.Expander> w kontrolce <xref:System.Windows.Controls.ScrollViewer>ustaw <xref:System.Windows.Controls.ScrollViewer> wymiaru właściwość, która odpowiada kierunek, w którym <xref:System.Windows.Controls.Expander> otwiera zawartość do rozmiaru <xref:System.Windows.Controls.Expander> obszar zawartości. Na przykład jeśli ustawisz <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość <xref:System.Windows.Controls.Expander> do <xref:System.Windows.Controls.ExpandDirection.Down> (obszar zawartości jest otwierany w dół), ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość <xref:System.Windows.Controls.ScrollViewer> kontrolki wymagane wysokość obszaru zawartości. Jeśli zamiast tego wartość wysokości zawartości, <xref:System.Windows.Controls.ScrollViewer> to ustawienie nie jest rozpoznawane i dlatego nie zapewnia przewijanej treści.  
  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Windows.Controls.Expander> formant, który ma zawartość złożoną i zawiera <xref:System.Windows.Controls.ScrollViewer> kontroli. Ten przykład tworzy <xref:System.Windows.Controls.Expander> to podobnie do ilustracji na początku tej sekcji.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Za pomocą właściwości wyrównania  
 Wyrównaj do zawartości, ustawiając <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.Expander> kontroli. Po ustawieniu tych właściwości, wyrównanie ma zastosowanie do nagłówka, a także do rozwiniętego zawartości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [— Tematy porad](expander-how-to-topics.md)
