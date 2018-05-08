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
ms.openlocfilehash: abcc7c48c602aee742959b39bb5244563eaf4d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expander-overview"></a>Przegląd Ekspander
<xref:System.Windows.Controls.Expander> Kontrola zapewnia narzędzia do udostępniania zawartości w obszarze rozwijania podobny okna, który zawiera nagłówek.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Tworzenie prostego Expander  
 Poniższy przykład przedstawia sposób tworzenia prostej <xref:System.Windows.Controls.Expander> formantu. Ten przykład tworzy <xref:System.Windows.Controls.Expander> prawdopodobnie poprzedniej ilustracji.  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> i <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> z <xref:System.Windows.Controls.Expander> może również zawierać złożonych zawartości, takich jak <xref:System.Windows.Controls.RadioButton> i <xref:System.Windows.Controls.Image> obiektów.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Ustawienie kierunku powiększające obszaru zawartości  
 Możesz ustawić obszar zawartości <xref:System.Windows.Controls.Expander> formant do rozszerzenia w jednym z czterech kierunków (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, lub <xref:System.Windows.Controls.ExpandDirection.Right>) przy użyciu <xref:System.Windows.Controls.ExpandDirection> właściwości. Gdy obszar zawartości jest zwinięte, tylko <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> i jego przycisk przełącznika są wyświetlane. A <xref:System.Windows.Controls.Button> kontrolkę wyświetlającą strzałkę kierunkową jest używany jako przycisk przełącznika aby rozwinąć lub zwinąć obszar zawartości. Po rozwinięciu <xref:System.Windows.Controls.Expander> próbuje wyświetlić całej jego zawartości w obszarze przypominającej okna.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Rozmiar element Expander w Panelu sterowania  
 Jeśli <xref:System.Windows.Controls.Expander> formant znajduje się wewnątrz kontrolkę układu, która dziedziczy <xref:System.Windows.Controls.Panel>, takich jak <xref:System.Windows.Controls.StackPanel>, nie należy określać <xref:System.Windows.FrameworkElement.Height%2A> na <xref:System.Windows.Controls.Expander> podczas <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.ExpandDirection.Down> lub <xref:System.Windows.Controls.ExpandDirection.Up>. Podobnie, nie należy określać <xref:System.Windows.FrameworkElement.Width%2A> na <xref:System.Windows.Controls.Expander> podczas <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość jest ustawiona na <xref:System.Windows.Controls.ExpandDirection.Left> lub <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Podczas ustawiania rozmiaru wymiaru na <xref:System.Windows.Controls.Expander> kontroli w kierunku, czy jest wyświetlana zawartość rozwinięte, <xref:System.Windows.Controls.Expander> przejmuje kontrolę nad obszarem jest używany przez zawartość i wyświetla obramowanie. Pokazuje obramowania, nawet wtedy, gdy zawartość jest zwinięty. Rozmiar obszaru zawartości rozwinięte ustawia wymiary rozmiaru zawartości <xref:System.Windows.Controls.Expander>, lub jeśli użytkownik chce przewijanie możliwości, na <xref:System.Windows.Controls.ScrollViewer> który umieszcza zawartości.  
  
 Gdy <xref:System.Windows.Controls.Expander> formant jest ostatnim elementem w <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] automatycznie ustawia <xref:System.Windows.Controls.Expander> wymiarów równą pozostałej części <xref:System.Windows.Controls.DockPanel>. Aby zapobiec to domyślne zachowanie, ustaw <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> właściwość <xref:System.Windows.Controls.DockPanel> do obiektu `false`, lub upewnij się, że <xref:System.Windows.Controls.Expander> nie jest ostatnim elementem w <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Tworzenie przewijanej treści  
 Jeśli zawartość jest zbyt duży rozmiar obszaru zawartości, może zawijać się zawartość <xref:System.Windows.Controls.Expander> w <xref:System.Windows.Controls.ScrollViewer> zapewnić przewijanej treści. <xref:System.Windows.Controls.Expander> Formant automatycznie nie zapewnia funkcji przewijania. Na poniższej ilustracji pokazano <xref:System.Windows.Controls.Expander> formant, który zawiera <xref:System.Windows.Controls.ScrollViewer> formantu.  
  
 **Expander w ScrollViewer**  
  
 ![Expander z paska przewijania](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Po umieszczeniu <xref:System.Windows.Controls.Expander> kontroli w <xref:System.Windows.Controls.ScrollViewer>ustaw <xref:System.Windows.Controls.ScrollViewer> wymiaru właściwość, która odpowiada kierunek, w którym <xref:System.Windows.Controls.Expander> zawartości otwiera rozmiar <xref:System.Windows.Controls.Expander> obszar zawartości. Na przykład jeśli ustawisz <xref:System.Windows.Controls.Expander.ExpandDirection%2A> właściwość <xref:System.Windows.Controls.Expander> do <xref:System.Windows.Controls.ExpandDirection.Down> (otwiera obszar zawartości w dół), ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość <xref:System.Windows.Controls.ScrollViewer> formantu wymagane wysokość obszaru zawartości. Jeśli zamiast tego wartość wysokości zawartości, <xref:System.Windows.Controls.ScrollViewer> to ustawienie nie jest rozpoznawane i dlatego nie zapewnia przewijanej treści.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Expander> kontroli mający złożonych zawartości i zawiera <xref:System.Windows.Controls.ScrollViewer> formantu. Ten przykład tworzy <xref:System.Windows.Controls.Expander> to jak na ilustracji na początku tej sekcji.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Przy użyciu właściwości wyrównania  
 Zawartość można wyrównać przez ustawienie <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> i <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> właściwości <xref:System.Windows.Controls.Expander> formantu. Wyrównanie ustaw te właściwości, zastosowanie do nagłówka, a także do rozwiniętego zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
