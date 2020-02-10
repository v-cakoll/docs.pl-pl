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
ms.openlocfilehash: f23f54283849ddaa827a98f0f28a39a72305dc1d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095232"
---
# <a name="drawing-formatted-text"></a>Rysowanie formatowanego tekstu
Ten temat zawiera omówienie funkcji obiektu <xref:System.Windows.Media.FormattedText>. Ten obiekt udostępnia formant niskiego poziomu służący do rysowania tekstu w aplikacjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Omówienie technologii  
 Obiekt <xref:System.Windows.Media.FormattedText> umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być osobno sformatowany. Poniższy przykład przedstawia tekst, do którego zastosowano kilka formatów.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Dla tych deweloperów Migrowanie z Win32 API tabela w sekcji [migracji Win32](#win32_migration) zawiera flagi Win32 DrawText i przybliżony odpowiednik w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Przyczyny używania tekstu sformatowanego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek do rysowania tekstu na ekranie. Każdy formant jest przeznaczony dla innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz biorąc, element <xref:System.Windows.Controls.TextBlock> powinien być używany, gdy wymagana jest obsługa tekstu ograniczonego, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> można użyć, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
 Obiekt <xref:System.Windows.Media.FormattedText> zapewnia więcej funkcji formatowania tekstu niż kontrolki tekstu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] i może być przydatny w przypadkach, gdy chcesz użyć tekstu jako elementu dekoracyjnego. Aby uzyskać więcej informacji, zobacz poniższą sekcję [konwertowanie sformatowanego tekstu na geometrię](#converting_formatted_text).  
  
 Ponadto obiekt <xref:System.Windows.Media.FormattedText> jest przydatny do tworzenia obiektów pochodnych <xref:System.Windows.Media.DrawingVisual>zorientowanych na tekst. <xref:System.Windows.Media.DrawingVisual> jest lekkim klasą rysowania, która jest używana do renderowania kształtów, obrazów lub tekstu. Aby uzyskać więcej informacji, zobacz [test trafień za pomocą przykładu DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Korzystanie z obiektu FormattedText  
 Aby utworzyć sformatowany tekst, Wywołaj konstruktora <xref:System.Windows.Media.FormattedText.%23ctor%2A>, aby utworzyć obiekt <xref:System.Windows.Media.FormattedText>. Po utworzeniu początkowego sformatowanego ciągu tekstowego można zastosować zakres stylów formatowania.  
  
 Użyj właściwości <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>, aby ograniczyć tekst do określonej szerokości. Tekst zostanie automatycznie zawinięty, aby uniknąć przekroczenia określonej szerokości. Użyj właściwości <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>, aby ograniczyć tekst do określonej wysokości. Tekst wyświetli wielokropek, "..." dla tekstu, który przekracza określoną wysokość.  
  
 ![Tekst wyświetlany z WordWrap i wielokropkiem.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Można zastosować wiele stylów formatowania do jednego lub większej liczby znaków. Na przykład można wywołać metody <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>, aby zmienić formatowanie pierwszych pięciu znaków w tekście.  
  
 Poniższy przykład kodu tworzy obiekt <xref:System.Windows.Media.FormattedText>, a następnie stosuje kilka stylów formatowania do tekstu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Jednostka miary rozmiaru czcionki  
 Podobnie jak w przypadku innych obiektów tekstowych w aplikacjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], obiekt <xref:System.Windows.Media.FormattedText> używa pikseli niezależnych od urządzenia jako jednostki miary. Jednak większość aplikacji Win32 używa punktów jako jednostki miary. Jeśli chcesz używać tekstu wyświetlanego w jednostkach punktów w aplikacjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], musisz przekonwertować jednostki niezależne od urządzenia (1/1/96 na jednostkę) na punkty. Poniższy przykład kodu pokazuje, jak wykonać tę konwersję.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Konwertowanie sformatowanego tekstu na geometrię  
 Możesz skonwertować sformatowany tekst na obiekty <xref:System.Windows.Media.Geometry>, co pozwala na tworzenie innych typów wizualnie interesujących. Na przykład można utworzyć obiekt <xref:System.Windows.Media.Geometry> na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikację obrysu, wypełnienia i wyróżnienia konwertowanego tekstu.  
  
 ![Tekst z różnymi kolorami dla wypełnienia i pociągnięcia](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowany do pociągnięcia](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowany do obrysu i wyróżnienia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Gdy tekst jest konwertowany na obiekt <xref:System.Windows.Media.Geometry>, nie jest już kolekcją znaków — nie można modyfikować znaków w ciągu tekstowym. Można jednak mieć wpływ na wygląd przekonwertowanego tekstu, modyfikując jego właściwości obrysu i wypełnienia. Naciśnięcie odnosi się do konturu przekonwertowanego tekstu. wypełnienie odnosi się do obszaru wewnątrz konturu przekonwertowanego tekstu. Aby uzyskać więcej informacji, zobacz [Tworzenie konturów tekstu](how-to-create-outlined-text.md).  
  
 Możesz również skonwertować sformatowany tekst do obiektu <xref:System.Windows.Media.PathGeometry>, a następnie użyć obiektu do wyróżnienia tekstu. Na przykład można zastosować animację do obiektu <xref:System.Windows.Media.PathGeometry>, aby animacja była zgodna z konturem sformatowanego tekstu.  
  
 Poniższy przykład pokazuje sformatowany tekst, który został przekonwertowany na obiekt <xref:System.Windows.Media.PathGeometry>. Animowany Elipsa następuje po ścieżce pociągnięć renderowanego tekstu.  
  
 ![Sfera po geometrii ścieżki tekstu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Sfera po geometrii ścieżki tekstu  
  
 Aby uzyskać więcej informacji, zobacz [How to: Create a PathGeometry animacje for text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Można utworzyć inne interesujące zastosowania dla sformatowanego tekstu, gdy zostanie on przekonwertowany na obiekt <xref:System.Windows.Media.PathGeometry>. Można na przykład przyciąć wideo w celu wyświetlenia go wewnątrz.  
  
 ![Wideo wyświetlające w geometrii ścieżki tekstu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migracja Win32  
 Funkcje <xref:System.Windows.Media.FormattedText> rysowania tekstu są podobne do funkcji funkcji Win32 DrawText. W przypadku tych deweloperów Migrowanie z Win32 API w poniższej tabeli wymieniono flagi Win32 DrawText i przybliżony odpowiednik w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Flaga DrawText|Odpowiednik WPF|Uwagi|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Height%2A>, aby obliczyć odpowiednią pozycję "y" DrawText Win32.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Height%2A> i <xref:System.Windows.Media.FormattedText.Width%2A>, aby obliczyć prostokąt wyjściowy.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.TextAlignment%2A> z wartością ustawioną na <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|None|Nie jest wymagane. Szerokość obszaru i renderowanie ostatniego wiersza są takie same, jak w kontrolce Edycja struktury.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Trimming%2A> z <xref:System.Windows.TextTrimming.CharacterEllipsis>wartością.<br /><br /> Użyj <xref:System.Windows.TextTrimming.WordEllipsis>, aby uzyskać DT_END_ELLIPSIS Win32 z wielokropkiem DT_WORD_ELIPSIS. w tym przypadku wielokropek znaków występuje tylko w przypadku wyrazów, które nie mieszczą się w pojedynczym wierszu.|  
|DT_EXPAND_TABS|None|Nie jest wymagane. Karty są automatycznie rozszerzane, aby zatrzymać każde 4 EMS, które ma w przybliżeniu szerokość 8 znaków niezależnych od języka.|  
|DT_EXTERNALLEADING|None|Nie jest wymagane. Interlinia zewnętrzna zawsze jest uwzględniana w odstępach między wierszami. Użyj właściwości <xref:System.Windows.Media.FormattedText.LineHeight%2A>, aby utworzyć zdefiniowane przez użytkownika interlinię.|  
|DT_HIDEPREFIX|None|Nieobsługiwane. Przed konstruowaniem obiektu <xref:System.Windows.Media.FormattedText> Usuń "&" z ciągu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Jest to domyślne wyrównanie tekstu. Użyj właściwości <xref:System.Windows.Media.FormattedText.TextAlignment%2A> z wartością ustawioną na <xref:System.Windows.TextAlignment.Left>. (Tylko WPF)|  
|DT_MODIFYSTRING|None|Nieobsługiwane.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Przycinanie nie odbywa się automatycznie. Jeśli chcesz wyciąć tekst, użyj właściwości <xref:System.Windows.Media.Visual.VisualClip%2A>.|  
|DT_NOFULLWIDTHCHARBREAK|None|Nieobsługiwane.|  
|DT_NOPREFIX|None|Nie jest wymagane. Znak "&" w ciągach jest zawsze traktowany jako zwykły znak.|  
|DT_PATHELLIPSIS|None|Użyj właściwości <xref:System.Windows.Media.FormattedText.Trimming%2A> z <xref:System.Windows.TextTrimming.WordEllipsis>wartością.|  
|DT_PREFIX|None|Nieobsługiwane. Jeśli chcesz używać podkreśleń dla tekstu, takich jak klawisz akceleratora lub łącze, użyj metody <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>.|  
|DT_PREFIXONLY|None|Nieobsługiwane.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.TextAlignment%2A> z wartością ustawioną na <xref:System.Windows.TextAlignment.Right>. (Tylko WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ustaw właściwość <xref:System.Windows.Media.FormattedText.FlowDirection%2A> na <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|None|Nie jest wymagane. obiekty <xref:System.Windows.Media.FormattedText> zachowują się jako jednowierszowe kontrolki, chyba że jest ustawiona właściwość <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> lub tekst zawiera znak powrotu karetki/wysuwu wiersza (CR/LF).|  
|DT_TABSTOP|None|Brak obsługi dla pozycji tabulatora zdefiniowanego przez użytkownika.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Nie jest wymagane. Najważniejszym uzasadnieniem jest wartość domyślna. Inne wartości pozycjonowania pionowego można zdefiniować za pomocą właściwości <xref:System.Windows.Media.FormattedText.Height%2A> do obliczenia odpowiedniej pozycji "y" DrawText Win32.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Height%2A>, aby obliczyć odpowiednią pozycję "y" DrawText Win32.|  
|DT_WORDBREAK|None|Nie jest wymagane. Dzielenie wyrazów odbywa się automatycznie z <xref:System.Windows.Media.FormattedText> obiektami. Nie można go wyłączyć.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj właściwości <xref:System.Windows.Media.FormattedText.Trimming%2A> z <xref:System.Windows.TextTrimming.WordEllipsis>wartością.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Typografia w WPF](typography-in-wpf.md)
- [Tworzenie tekstu z konturem](how-to-create-outlined-text.md)
- [Instrukcje: Tworzenie animacji PathGeometry dla tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
