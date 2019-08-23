---
title: Rysowanie formatowanego tekstu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: eeba54ebd63b26a50c8c01a2478e847b3e660a3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937691"
---
# <a name="drawing-formatted-text"></a>Rysowanie formatowanego tekstu
Ten temat zawiera omówienie funkcji <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt zawiera formant niskiego poziomu służący do rysowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tekstu w aplikacjach.  

## <a name="technology-overview"></a>Omówienie technologii  
 <xref:System.Windows.Media.FormattedText> Obiekt umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być sformatowany osobno. Poniższy przykład przedstawia tekst, do którego zastosowano kilka formatów.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> W przypadku tych deweloperów Migrowanie [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] z interfejsu API tabela w sekcji [migracji Win32](#win32_migration) zawiera listę [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] flag DrawText i przybliżony odpowiednik w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Przyczyny używania tekstu sformatowanego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz biorąc, <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]w. <xref:System.Windows.Controls.Label>może być używany, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
 Obiekt zawiera więcej funkcji formatowania tekstu niż [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontrolki tekstu i może być przydatny w przypadkach, gdy chcesz używać tekstu jako ozdobnego elementu. <xref:System.Windows.Media.FormattedText> Aby uzyskać więcej informacji, zobacz poniższą sekcję [konwertowanie sformatowanego tekstu na geometrię](#converting_formatted_text).  
  
 Ponadto <xref:System.Windows.Media.FormattedText> obiekt jest przydatny do tworzenia obiektów pochodnych tekstu <xref:System.Windows.Media.DrawingVisual>. <xref:System.Windows.Media.DrawingVisual>jest lekkim klasą rysowania, która jest używana do renderowania kształtów, obrazów lub tekstu. Aby uzyskać więcej informacji, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Korzystanie z obiektu FormattedText  
 Aby utworzyć sformatowany tekst, wywołaj <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktora, aby <xref:System.Windows.Media.FormattedText> utworzyć obiekt. Po utworzeniu początkowego sformatowanego ciągu tekstowego można zastosować zakres stylów formatowania.  
  
 Użyj właściwości <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> , aby ograniczyć tekst do określonej szerokości. Tekst zostanie automatycznie zawinięty, aby uniknąć przekroczenia określonej szerokości. Użyj właściwości <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> , aby ograniczyć tekst do określonej wysokości. Tekst wyświetli wielokropek, "..." dla tekstu, który przekracza określoną wysokość.  
  
 ![Tekst wyświetlany z WordWrap i wielokropkiem.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Można zastosować wiele stylów formatowania do jednego lub większej liczby znaków. Na przykład można wywołać <xref:System.Windows.Media.FormattedText.SetFontSize%2A> metody i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> , aby zmienić formatowanie pierwszych pięciu znaków w tekście.  
  
 Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiekt, a następnie stosuje kilka stylów formatowania do tekstu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Jednostka miary rozmiaru czcionki  
 Podobnie jak w przypadku innych obiektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] tekstowych w aplikacjach <xref:System.Windows.Media.FormattedText> , obiekt używa niezależnych od urządzenia pikseli jako jednostki miary. Jednak większość [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji używa punktów jako jednostki miary. Jeśli chcesz używać tekstu wyświetlanego w jednostkach punktów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjach, musisz skonwertować jednostki niezależne od urządzenia (1/1/96 cala na jednostkę) do punktów. Poniższy przykład kodu pokazuje, jak wykonać tę konwersję.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Konwertowanie sformatowanego tekstu na geometrię  
 Możesz skonwertować sformatowany tekst na <xref:System.Windows.Media.Geometry> obiekty, co pozwala na tworzenie innych typów wizualnie interesujących. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikację obrysu, wypełnienia i wyróżnienia konwertowanego tekstu.  
  
 ![Tekst z różnymi kolorami dla wypełnienia i pociągnięcia](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowany do pociągnięcia](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowany do obrysu i wyróżnienia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Gdy tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiekt, nie jest już kolekcją znaków — nie można modyfikować znaków w ciągu tekstowym. Można jednak mieć wpływ na wygląd przekonwertowanego tekstu, modyfikując jego właściwości obrysu i wypełnienia. Naciśnięcie odnosi się do konturu przekonwertowanego tekstu. wypełnienie odnosi się do obszaru wewnątrz konturu przekonwertowanego tekstu. Aby uzyskać więcej informacji, zobacz [Tworzenie konturów tekstu](how-to-create-outlined-text.md).  
  
 Możesz również skonwertować sformatowany tekst do <xref:System.Windows.Media.PathGeometry> obiektu, a następnie użyć obiektu do wyróżnienia tekstu. Na przykład można zastosować animację do <xref:System.Windows.Media.PathGeometry> obiektu, aby animacja była zgodna z konturem sformatowanego tekstu.  
  
 Poniższy przykład pokazuje sformatowany tekst, który został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiekt. Animowany Elipsa następuje po ścieżce pociągnięć renderowanego tekstu.  
  
 ![Sfera po geometrii ścieżki tekstu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Sfera po geometrii ścieżki tekstu  
  
 Aby uzyskać więcej informacji, zobacz [jak: Utwórz animację PathGeometry dla tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Można utworzyć inne interesujące zastosowania dla sformatowanego tekstu, gdy zostanie on przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiekt. Można na przykład przyciąć wideo w celu wyświetlenia go wewnątrz.  
  
 ![Wideo wyświetlające w geometrii ścieżki tekstu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migracja Win32  
 Funkcje <xref:System.Windows.Media.FormattedText> programu do rysowania tekstu są podobne do funkcji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] funkcji DrawText. W przypadku tych deweloperów Migrowanie [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] z interfejsu API w poniższej tabeli [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] wymieniono flagi DrawText i przybliżony odpowiednik [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]w.  
  
|Flaga DrawText|Odpowiednik WPF|Uwagi|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Height%2A> , aby obliczyć odpowiednią [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycję DrawText "y".|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Width%2A> i, aby obliczyć prostokąt wyjściowy. <xref:System.Windows.Media.FormattedText.Height%2A>|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj właściwości z wartością ustawioną na <xref:System.Windows.TextAlignment.Center>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A>|  
|DT_EDITCONTROL|Brak|Nie jest wymagane. Szerokość obszaru i renderowanie ostatniego wiersza są takie same, jak w kontrolce Edycja struktury.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj właściwości z wartością <xref:System.Windows.TextTrimming.CharacterEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A><br /><br /> Użyj <xref:System.Windows.TextTrimming.WordEllipsis> , aby [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uzyskać DT_END_ELLIPSIS z wielokropkiem końcowym DT_WORD_ELIPSIS — w tym przypadku wielokropek znaków występuje tylko w przypadku wyrazów, które nie mieszczą się w pojedynczym wierszu.|  
|DT_EXPAND_TABS|Brak|Nie jest wymagane. Karty są automatycznie rozszerzane, aby zatrzymać każde 4 EMS, które ma w przybliżeniu szerokość 8 znaków niezależnych od języka.|  
|DT_EXTERNALLEADING|Brak|Nie jest wymagane. Interlinia zewnętrzna zawsze jest uwzględniana w odstępach między wierszami. Użyj właściwości <xref:System.Windows.Media.FormattedText.LineHeight%2A> , aby utworzyć zdefiniowane przez użytkownika interlinię.|  
|DT_HIDEPREFIX|Brak|Nieobsługiwane. Usuń element "&" z ciągu przed konstruowaniem <xref:System.Windows.Media.FormattedText> obiektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Jest to domyślne wyrównanie tekstu. Użyj właściwości z wartością ustawioną na <xref:System.Windows.TextAlignment.Left>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> (Tylko WPF)|  
|DT_MODIFYSTRING|Brak|Nieobsługiwane.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Przycinanie nie odbywa się automatycznie. Jeśli chcesz wyciąć tekst, użyj <xref:System.Windows.Media.Visual.VisualClip%2A> właściwości.|  
|DT_NOFULLWIDTHCHARBREAK|Brak|Nieobsługiwane.|  
|DT_NOPREFIX|Brak|Nie jest wymagane. Znak "&" w ciągach jest zawsze traktowany jako zwykły znak.|  
|DT_PATHELLIPSIS|Brak|Użyj właściwości z wartością <xref:System.Windows.TextTrimming.WordEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A>|  
|DT_PREFIX|Brak|Nieobsługiwane. Jeśli chcesz używać podkreśleń dla tekstu, takich jak klawisz akceleratora lub łącze, użyj <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metody.|  
|DT_PREFIXONLY|Brak|Nieobsługiwane.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj właściwości z wartością ustawioną na <xref:System.Windows.TextAlignment.Right>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> (Tylko WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ustaw <xref:System.Windows.Media.FormattedText.FlowDirection%2A> właściwość <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Brak|Nie jest wymagane. <xref:System.Windows.Media.FormattedText>obiekty zachowują się jako kontrolki pojedynczej linii, <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> chyba że właściwość jest ustawiona lub tekst zawiera znak powrotu karetki/wysuwu wiersza (CR/LF).|  
|DT_TABSTOP|Brak|Brak obsługi dla pozycji tabulatora zdefiniowanego przez użytkownika.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Nie jest wymagane. Najważniejszym uzasadnieniem jest wartość domyślna. Inne wartości pozycjonowania pionowego można zdefiniować za pomocą <xref:System.Windows.Media.FormattedText.Height%2A> właściwości do obliczenia odpowiedniej [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Height%2A> , aby obliczyć odpowiednią [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycję DrawText "y".|  
|DT_WORDBREAK|Brak|Nie jest wymagane. Dzielenie wyrazów odbywa się <xref:System.Windows.Media.FormattedText> automatycznie z obiektami. Nie można go wyłączyć.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj właściwości z wartością <xref:System.Windows.TextTrimming.WordEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Typografia w WPF](typography-in-wpf.md)
- [Tworzenie tekstu z konturem](how-to-create-outlined-text.md)
- [Instrukcje: Utwórz animację PathGeometry dla tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
