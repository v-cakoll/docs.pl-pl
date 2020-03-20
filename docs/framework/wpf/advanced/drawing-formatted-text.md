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
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186567"
---
# <a name="drawing-formatted-text"></a>Rysowanie formatowanego tekstu
Ten temat zawiera omówienie funkcji <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt zapewnia niską kontrolę [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rysowania tekstu w aplikacjach.  

## <a name="technology-overview"></a>Przegląd technologii  
 Obiekt <xref:System.Windows.Media.FormattedText> umożliwia rysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być indywidualnie sformatowany. W poniższym przykładzie pokazano tekst, który ma kilka formatów stosowanych do niego.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> W przypadku deweloperów migrujących z interfejsu API Systemu Win32 w tabeli w sekcji [Migracja Win32](#win32_migration) wymieniono flagi Programu Win32 DrawText i przybliżony odpowiednik w pliku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Powody korzystania z sformatowanego tekstu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wiele elementów sterujących rysowania tekstu na ekranie. Każdy formant jest przeznaczony do innego scenariusza i ma własną listę funkcji i ograniczeń. Ogólnie rzecz <xref:System.Windows.Controls.TextBlock> biorąc element powinien być używany, gdy wymagana jest ograniczona [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]obsługa tekstu, na przykład krótkie zdanie w pliku . <xref:System.Windows.Controls.Label>może być używany, gdy wymagana jest minimalna obsługa tekstu. Aby uzyskać więcej informacji, zobacz [Dokumenty w WPF](documents-in-wpf.md).  
  
 Obiekt <xref:System.Windows.Media.FormattedText> zapewnia większe funkcje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] formatowania tekstu niż formanty tekstu i może być przydatny w przypadkach, gdy chcesz użyć tekstu jako elementu dekoracyjnego. Aby uzyskać więcej informacji, zobacz następującą sekcję [Konwertowanie tekstu sformatowanego na geometrię](#converting_formatted_text).  
  
 Ponadto <xref:System.Windows.Media.FormattedText> obiekt jest przydatny do tworzenia obiektów <xref:System.Windows.Media.DrawingVisual>tekstowych. <xref:System.Windows.Media.DrawingVisual>jest klasą rysunku odciążony, która służy do renderowania kształtów, obrazów lub tekstu. Aby uzyskać więcej informacji, zobacz [Hit Test using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Korzystanie z obiektu FormattedText  
 Aby utworzyć sformatowany <xref:System.Windows.Media.FormattedText.%23ctor%2A> tekst, należy <xref:System.Windows.Media.FormattedText> wywołać konstruktora, aby utworzyć obiekt. Po utworzeniu początkowego sformatowanego ciągu tekstowego można zastosować zakres stylów formatowania.  
  
 Użyj <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwości, aby ograniczyć tekst do określonej szerokości. Tekst zostanie automatycznie zawinięty, aby uniknąć przekroczenia określonej szerokości. Użyj <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> właściwości, aby ograniczyć tekst do określonej wysokości. W tekście pojawi się wielokropek "..." dla tekstu, który przekracza określoną wysokość.  
  
 ![Tekst wyświetlany z oświetlenią i wielokropkiem.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 Do jednego lub kilku znaków można zastosować wiele stylów formatowania. Na przykład można wywołać <xref:System.Windows.Media.FormattedText.SetFontSize%2A> <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> zarówno metody, jak i metody, aby zmienić formatowanie pierwszych pięciu znaków w tekście.  
  
 Poniższy przykład kodu <xref:System.Windows.Media.FormattedText> tworzy obiekt, a następnie stosuje kilka stylów formatowania do tekstu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Jednostka miary rozmiaru czcionki  
 Podobnie jak w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przypadku innych <xref:System.Windows.Media.FormattedText> obiektów tekstowych w aplikacjach, obiekt używa pikseli niezależnych od urządzenia jako jednostki miary. Jednak większość aplikacji Win32 używa punktów jako jednostki miary. Jeśli chcesz użyć tekstu wyświetlanego w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jednostkach punktów w aplikacjach, musisz przekonwertować jednostki niezależne od urządzenia (1/96 cala na jednostkę) na punkty. W poniższym przykładzie kodu pokazano, jak wykonać tę konwersję.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>Konwertowanie sformatowanego tekstu na geometrię  
 Sformatowany tekst <xref:System.Windows.Media.Geometry> można konwertować na obiekty, co pozwala na tworzenie innych typów tekstu interesującego wizualnie. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu pędzla gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikowanie obrysu, wypełnienia i wyróżnienia przekonwertowanego tekstu.  
  
 ![Tekst o różnych kolorach wypełnienia i obrysu](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu i podświetlenia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Gdy tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiekt, nie jest już kolekcją znaków — nie można modyfikować znaków w ciągu tekstowym. Można jednak wpłynąć na wygląd przekonwertowanego tekstu, modyfikując jego właściwości obrysu i wypełnienia. Obrys odnosi się do konturu przekonwertowanego tekstu; wypełnienie odnosi się do obszaru wewnątrz konturu przekonwertowanego tekstu. Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu zarysowane](how-to-create-outlined-text.md).  
  
 Można również przekonwertować <xref:System.Windows.Media.PathGeometry> sformatowany tekst na obiekt i użyć go do wyróżniania tekstu. Na przykład można zastosować animację <xref:System.Windows.Media.PathGeometry> do obiektu, tak aby animacja podążała za konturem sformatowanego tekstu.  
  
 W poniższym przykładzie przedstawiono sformatowany tekst, który został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiekt. Animowana elipsa podąża ścieżką obrysów renderowanego tekstu.  
  
 ![Kula podążając za geometrią ścieżki tekstu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Kula podążając za geometrią ścieżki tekstu  
  
 Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie animacji pathgeometry dla tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Po przekonwertowaniu tekstu na <xref:System.Windows.Media.PathGeometry> obiekt można tworzyć inne interesujące zastosowania sformatowanego tekstu. Na przykład można przyciąć wideo, aby wyświetlić je w środku.  
  
 ![Wideo wyświetlane w geometrii ścieżki tekstu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Migracja win32  
 Funkcje <xref:System.Windows.Media.FormattedText> rysowania tekstu są podobne do funkcji funkcji Win32 DrawText. W przypadku deweloperów migrujących z interfejsu API Win32 w poniższej tabeli wymieniono flagi Programu Win32 DrawText i przybliżony odpowiednik w pliku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Flaga DrawText|Odpowiednik WPF|Uwagi|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości, aby obliczyć odpowiednią pozycję "y" programu Win32 DrawText.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości <xref:System.Windows.Media.FormattedText.Width%2A> i, aby obliczyć prostokąt wyjściowy.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwości z ustawioną <xref:System.Windows.TextAlignment.Center>wartością .|  
|DT_EDITCONTROL|Brak|Niewymagane. Szerokość miejsca i renderowanie ostatniego wiersza są takie same jak w formancie edycji struktury.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwości z <xref:System.Windows.TextTrimming.CharacterEllipsis>wartością .<br /><br /> Użyj, <xref:System.Windows.TextTrimming.WordEllipsis> aby uzyskać DT_END_ELLIPSIS Win32 z DT_WORD_ELIPSIS wielokropekem końcowym — w tym przypadku wielokropek znaków występuje tylko w wyrazach, które nie pasują do pojedynczego wiersza.|  
|DT_EXPAND_TABS|Brak|Niewymagane. Karty są automatycznie rozszerzane, aby zatrzymać co 4 ems, co jest w przybliżeniu szerokość 8 znaków niezależnych od języka.|  
|DT_EXTERNALLEADING|Brak|Niewymagane. Interlinii zewnętrznej jest zawsze uwzględniane w odstępach między wierszami. Użyj <xref:System.Windows.Media.FormattedText.LineHeight%2A> tej właściwości, aby utworzyć odstępy między wierszami zdefiniowane przez użytkownika.|  
|DT_HIDEPREFIX|Brak|Bez pomocy technicznej. Usuń "&" z ciągu przed skonstruowaniem <xref:System.Windows.Media.FormattedText> obiektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Jest to domyślne wyrównanie tekstu. Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwości z ustawioną <xref:System.Windows.TextAlignment.Left>wartością . (tylko WPF)|  
|DT_MODIFYSTRING|Brak|Bez pomocy technicznej.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Przycinanie nie odbywa się automatycznie. Jeśli chcesz przyciąć tekst, <xref:System.Windows.Media.Visual.VisualClip%2A> użyj właściwości.|  
|DT_NOFULLWIDTHCHARBREAK|Brak|Bez pomocy technicznej.|  
|DT_NOPREFIX|Brak|Niewymagane. Znak "&" w ciągach jest zawsze traktowany jako normalny znak.|  
|DT_PATHELLIPSIS|Brak|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwości z <xref:System.Windows.TextTrimming.WordEllipsis>wartością .|  
|DT_PREFIX|Brak|Bez pomocy technicznej. Jeśli chcesz użyć podkreśleń dla tekstu, takich jak klucz <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> akceleratora lub łącze, użyj metody.|  
|DT_PREFIXONLY|Brak|Bez pomocy technicznej.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwości z ustawioną <xref:System.Windows.TextAlignment.Right>wartością . (tylko WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ustaw <xref:System.Windows.Media.FormattedText.FlowDirection%2A> właściwość <xref:System.Windows.FlowDirection.RightToLeft>na .|  
|DT_SINGLELINE|Brak|Niewymagane. <xref:System.Windows.Media.FormattedText>obiekty zachowują się jako formant pojedynczego wiersza, chyba że <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwość jest ustawiona lub tekst zawiera powrót karetki/źródło wysuwu wiersza (CR/LF).|  
|DT_TABSTOP|Brak|Brak obsługi zdefiniowanych przez użytkownika pozycji tabulatora.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Niewymagane. Górne uzasadnienie jest ustawieniem domyślnym. Inne wartości pozycjonowania pionowego <xref:System.Windows.Media.FormattedText.Height%2A> można zdefiniować za pomocą właściwości do obliczenia odpowiedniej pozycji "y" programu Win32 DrawText.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości, aby obliczyć odpowiednią pozycję "y" programu Win32 DrawText.|  
|DT_WORDBREAK|Brak|Niewymagane. Rozbicie programu Word <xref:System.Windows.Media.FormattedText> odbywa się automatycznie z obiektami. Nie można go wyłączyć.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwości z <xref:System.Windows.TextTrimming.WordEllipsis>wartością .|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Typografia w WPF](typography-in-wpf.md)
- [Tworzenie tekstu z konturem](how-to-create-outlined-text.md)
- [Jak: Tworzenie animacji pathgeometry dla tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
