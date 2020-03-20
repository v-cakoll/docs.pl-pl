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
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187110"
---
# <a name="expander-overview"></a>Przegląd Ekspander
Formant <xref:System.Windows.Controls.Expander> umożliwia dostarczanie zawartości w obszarze rozwijanym, który przypomina okno i zawiera nagłówek.  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>Tworzenie prostego ekspandera  
 W poniższym przykładzie pokazano, jak utworzyć prosty <xref:System.Windows.Controls.Expander> formant. W tym <xref:System.Windows.Controls.Expander> przykładzie tworzy, który wygląda jak poprzednia ilustracja.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 I <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> może <xref:System.Windows.Controls.Expander> również zawierać złożoną zawartość, takich jak <xref:System.Windows.Controls.RadioButton> i <xref:System.Windows.Controls.Image> obiektów.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Ustawianie kierunku rozwijającego się obszaru zawartości  
 Obszar <xref:System.Windows.Controls.Expander> zawartości formantu można ustawić tak, aby<xref:System.Windows.Controls.ExpandDirection.Down>rozwijał się w jednym z czterech kierunków <xref:System.Windows.Controls.ExpandDirection.Up>( , , <xref:System.Windows.Controls.ExpandDirection.Left>, lub <xref:System.Windows.Controls.ExpandDirection.Right>) za pomocą <xref:System.Windows.Controls.ExpandDirection> właściwości. Gdy obszar zawartości jest zwinięty, wyświetlany jest tylko <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> przycisk przełączania i jego przełącznik. Formant <xref:System.Windows.Controls.Button> wyświetlatyszałka kierunkowa jest używany jako przycisk przełączania, aby rozwinąć lub zwinąć obszar zawartości. Po rozwinięciu <xref:System.Windows.Controls.Expander> próbuje wyświetlić całą jego zawartość w obszarze przypominającym okno.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Kontrolowanie rozmiaru ekspandera w panelu  
 Jeśli <xref:System.Windows.Controls.Expander> formant znajduje się wewnątrz formantu <xref:System.Windows.Controls.StackPanel>układu, który <xref:System.Windows.FrameworkElement.Height%2A> dziedziczy <xref:System.Windows.Controls.Expander> po <xref:System.Windows.Controls.Expander.ExpandDirection%2A> <xref:System.Windows.Controls.Panel>, takich <xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.Controls.ExpandDirection.Up>jak , nie należy określać na kiedy właściwość jest ustawiona na lub . Podobnie <xref:System.Windows.FrameworkElement.Width%2A> nie należy określać <xref:System.Windows.Controls.Expander> na <xref:System.Windows.Controls.Expander.ExpandDirection%2A> kiedy właściwość <xref:System.Windows.Controls.ExpandDirection.Left> <xref:System.Windows.Controls.ExpandDirection.Right>jest ustawiona na lub .  
  
 Po ustawieniu wymiaru rozmiaru <xref:System.Windows.Controls.Expander> na formancie w kierunku, w <xref:System.Windows.Controls.Expander> którym wyświetlana jest rozwinięta zawartość, przejmuje kontrolę nad obszarem używanym przez zawartość i wyświetla obramowanie wokół niej. Obramowanie jest wyświetlane nawet wtedy, gdy zawartość jest zwinięta. Aby ustawić rozmiar rozwiniętego obszaru zawartości, ustaw wymiary <xref:System.Windows.Controls.Expander>rozmiaru zawartości zawartości , lub jeśli <xref:System.Windows.Controls.ScrollViewer> chcesz przewijać, na tym, który otacza zawartość.  
  
 Gdy <xref:System.Windows.Controls.Expander> formant jest ostatnim <xref:System.Windows.Controls.DockPanel>elementem w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Expander> , automatycznie ustawia wymiary <xref:System.Windows.Controls.DockPanel>na równy pozostałemu obszarowi . Aby zapobiec temu domyślnemu <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> <xref:System.Windows.Controls.DockPanel> zachowaniu, `false`ustaw właściwość obiektu <xref:System.Windows.Controls.Expander> na , lub <xref:System.Windows.Controls.DockPanel>upewnij się, że nie jest to ostatni element w pliku .  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>Tworzenie przewijanej zawartości  
 Jeśli zawartość jest zbyt duża dla rozmiaru obszaru zawartości, można <xref:System.Windows.Controls.Expander> zawinąć <xref:System.Windows.Controls.ScrollViewer> zawartość w a, aby zapewnić przewijaną zawartość. Formant <xref:System.Windows.Controls.Expander> nie zapewnia automatycznie możliwości przewijania. Na poniższej <xref:System.Windows.Controls.Expander> ilustracji przedstawiono formant, który zawiera formant. <xref:System.Windows.Controls.ScrollViewer>  
  
 **Expander w scrollviewer**  
  
 ![Zrzut ekranu przedstawiający ekspander z paskiem przewijania.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Po umieszczeniu <xref:System.Windows.Controls.Expander> formantu <xref:System.Windows.Controls.ScrollViewer>w <xref:System.Windows.Controls.ScrollViewer> , ustawić właściwość wymiaru, <xref:System.Windows.Controls.Expander> która odpowiada kierunku, <xref:System.Windows.Controls.Expander> w którym zawartość otwiera się do rozmiaru obszaru zawartości. Na przykład jeśli <xref:System.Windows.Controls.Expander.ExpandDirection%2A> ustawisz <xref:System.Windows.Controls.Expander> właściwość na do <xref:System.Windows.Controls.ExpandDirection.Down> (obszar <xref:System.Windows.FrameworkElement.Height%2A> zawartości otwiera <xref:System.Windows.Controls.ScrollViewer> się w dół), ustaw właściwość na formancie na wymaganą wysokość dla obszaru zawartości. Jeśli zamiast tego ustawisz wymiar wysokości <xref:System.Windows.Controls.ScrollViewer> na samej zawartości, nie rozpoznaje tego ustawienia i w związku z tym nie zapewnia przewijanej zawartości.  
  
 W poniższym przykładzie <xref:System.Windows.Controls.Expander> pokazano, jak utworzyć formant, który ma złożoną <xref:System.Windows.Controls.ScrollViewer> zawartość i który zawiera formant. W tym <xref:System.Windows.Controls.Expander> przykładzie tworzy, który jest jak ilustracja na początku tej sekcji.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>Korzystanie z właściwości wyrównania  
 Zawartość można wyrównać, <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ustawiając właściwości <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> <xref:System.Windows.Controls.Expander> i właściwości formantu. Po ustawieniu tych właściwości wyrównanie dotyczy nagłówka, a także rozwiniętej zawartości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Tematy in jakże](expander-how-to-topics.md)
