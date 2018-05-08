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
ms.openlocfilehash: 978c97b8cae24bff4ebdea8f4e56a940e5907fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-formatted-text"></a>Rysowanie formatowanego tekstu
Ten temat zawiera omówienie funkcji <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt zapewnia kontrolę niskiego poziomu dla Rysowanie tekstu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
## <a name="technology-overview"></a>Omówienie technologii  
 <xref:System.Windows.Media.FormattedText> Obiekt umożliwia rysowanie tekstu w wielu wierszach, w którym każdy znak w tekście można osobno sformatowany. W poniższym przykładzie przedstawiono tekst, który ma kilka formatów zastosować dla niego.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Przy użyciu metody FormattedText wyświetlanego tekstu.  
  
> [!NOTE]
>  Dla tych deweloperów migracji z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] interfejsu API, tabeli w [migracji Win32](#win32_migration) sekcji list [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText flagi i przybliżony odpowiednik w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Przyczyny przy użyciu tekstu sformatowanego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele formantów na rysowanie tekstu na ekranie. Każdej kontrolki jest przeznaczona do innego scenariusza i ma własną listę funkcji i ograniczenia. Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> Jeśli obsługa ograniczona tekstu jest wymagane, na przykład krótki zdanie w, należy użyć elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> można można użyć, gdy wymagana jest obsługa minimalnej ilości tekstu. Aby uzyskać więcej informacji, zobacz [dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Obiekt zapewnia funkcji niż większa tekstu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontrolek tekstu i mogą być przydatne w sytuacjach, w której chcesz używać jako elementu ozdobne tekstu. Aby uzyskać więcej informacji, zobacz sekcję poniżej [konwersji tekstu w formacie geometrii](#converting_formatted_text).  
  
 Ponadto <xref:System.Windows.Media.FormattedText> obiektu jest przydatne w przypadku tworzenia tekstowych <xref:System.Windows.Media.DrawingVisual>-pochodnych obiektów. <xref:System.Windows.Media.DrawingVisual> jest klasą rysowania lekkie używany do renderowania kształty, obrazy i tekst. Aby uzyskać więcej informacji, zobacz [trafień przy użyciu DrawingVisuals próbki](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Przy użyciu obiektu FormattedText  
 Aby utworzyć tekst sformatowany, należy wywołać <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktora w celu utworzenia <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu początkowej tekst sformatowany, można zastosować zakres formatowania style.  
  
 Użyj <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwości, aby ograniczyć tekst, który ma określoną szerokość. W celu uniknięcia przekroczenia określona szerokość automatycznie zawijania tekstu. Użyj <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> właściwości, aby ograniczyć tekst, który ma stałą wysokość. Tekst wyświetli wielokropek "..." na tekst, który przekracza określonej wysokości.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Wyświetlany tekst zawierający wordwrapping i wielokropka  
  
 Wiele stylów formatowania można zastosować do co najmniej jeden znak. Na przykład można wywołać jednocześnie <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody do formatowania pięć pierwszych znaków w tekście.  
  
 Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiekt, a następnie stosuje kilka stylów formatowania tekstu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Rozmiar czcionki jednostki miary  
 Podobnie jak inne obiekty tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, <xref:System.Windows.Media.FormattedText> obiekt używa pikselach niezależnych od urządzenia jako jednostka miary. Jednak większość [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje używają punktów jako jednostka miary. Jeśli chcesz użyć tekst wyświetlany w jednostkach punktów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, należy przekonwertować [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] do punktów. Poniższy przykład kodu pokazuje sposób wykonywania konwersji.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Konwertowanie sformatowanego tekstu do geometrii.  
 Możesz przekształcić tekst sformatowany do <xref:System.Windows.Media.Geometry> obiektów, pozwala na tworzenie innych typów wizualnie tekstu. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konturu ciąg tekstowy.  
  
 ![Używanie pędzla gradientu liniowego konspektu tekstu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Używanie pędzla gradientu liniowego konspektu tekstu  
  
 Poniższe przykłady przedstawiają kilka sposobów tworzenia interesujące efekty wizualne, modyfikując obrysu, wypełnij i wyróżnianie tekstu przekonwertowany.  
  
 ![Tekst z różnymi kolorami wypełnienia i pociągnięcia](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Przykładowa konfiguracja obrysu i wypełnienia do różnych kolorów  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Przykład pędzel obrazu na obrysu  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Przykład pędzel obrazu na obrysu i wyróżnienia  
  
 Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu, nie jest już zbiór znaków — nie można zmodyfikować znaków w ciągu tekstowym. Jednak może wpływać na wygląd tekst skonwertowany zmieniając jej obrysu i wypełnienie właściwości. Obrysu odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany. Aby uzyskać więcej informacji, zobacz [Utwórz tekst opisane](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Można również przeprowadzić konwersję tekst sformatowany do <xref:System.Windows.Media.PathGeometry> obiektu i obiekt używany do wyróżnienia. Na przykład można zastosować animacji <xref:System.Windows.Media.PathGeometry> obiekt, tak aby animacji następuje konturu tekst sformatowany.  
  
 W poniższym przykładzie przedstawiono sformatowanego tekstu, który został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiektu. Animowany elipsy następuje ścieżka naciśnięcia renderowanego tekstu.  
  
 ![Kuli geometrią ścieżki tekstu](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Kuli geometrią ścieżki tekstu  
  
 Aby uzyskać więcej informacji, zobacz [porady: Tworzenie animacji PathGeometry tekstu](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Można utworzyć inne ciekawe sposoby tekst sformatowany, gdy został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiektu. Można na przykład klipu wideo, aby wyświetlić wewnątrz niej.  
  
 ![Wyświetlanie wideo w geometrii ścieżki tekstu](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Wyświetlanie wideo w geometrii ścieżki tekstu  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migracja Win32  
 Funkcje <xref:System.Windows.Media.FormattedText> Rysowanie tekstu są podobne do funkcji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText funkcji. Dla tych deweloperów migrowania [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] interfejsu API, w poniższej tabeli wymieniono [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText flagi i przybliżony odpowiednik w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Flaga DrawText|Odpowiednik WPF|Uwagi|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości można obliczyć odpowiedniego [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> i <xref:System.Windows.Media.FormattedText.Width%2A> właściwości, aby obliczyć prostokąt danych wyjściowych.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Brak|Nie jest wymagane. Szerokość miejsca i ostatniego wiersza renderowania są takie same jak w ramach formantów edycji.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Użyj <xref:System.Windows.TextTrimming.WordEllipsis> uzyskanie [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS z DT_WORD_ELIPSIS kończyć wielokropka — w takim przypadku znak wielokropka występuje tylko w wyrazy, które nie mieszczą się w jednym wierszu.|  
|DT_EXPAND_TABS|Brak|Nie jest wymagane. Karty są automatycznie dodawany do zatrzymuje co 4 ems, czyli około szerokość 8 znaków niezależny od języka.|  
|DT_EXTERNALLEADING|Brak|Nie jest wymagane. Zawsze znajduje wiodące zewnętrzne odstępy. Użyj <xref:System.Windows.Media.FormattedText.LineHeight%2A> właściwość, aby utworzyć odstępy zdefiniowane przez użytkownika.|  
|DT_HIDEPREFIX|Brak|Nieobsługiwane. Usuń 'i' z ciągu przed konstruowania <xref:System.Windows.Media.FormattedText> obiektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Jest to domyślne wyrównanie tekstu. Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Left>. (Tylko WPF)|  
|DT_MODIFYSTRING|Brak|Nieobsługiwane.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Wycinka nie jest wykonywane automatycznie. Na klipie tekst, należy użyć <xref:System.Windows.Media.Visual.VisualClip%2A> właściwości.|  
|DT_NOFULLWIDTHCHARBREAK|Brak|Nieobsługiwane.|  
|DT_NOPREFIX|Brak|Nie jest wymagane. 'I' znaków w ciągach zawsze jest traktowane jako normalne znaki.|  
|DT_PATHELLIPSIS|Brak|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Brak|Nieobsługiwane. Jeśli chcesz używać znaków podkreślenia dla tekstu, na przykład klawisza skrótu lub łącza, użyj <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metody.|  
|DT_PREFIXONLY|Brak|Nieobsługiwane.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Right>. (Tylko WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ustaw <xref:System.Windows.Media.FormattedText.FlowDirection%2A> właściwości <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Brak|Nie jest wymagane. <xref:System.Windows.Media.FormattedText> obiekty zachowują się jako formant jednym wierszu, chyba że albo <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwość ma wartość lub tekst zawiera CR/LF (CR/LF).|  
|DT_TABSTOP|Brak|Brak obsługi położenie tabulatorów zdefiniowane przez użytkownika.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Nie jest wymagane. Justowanie TOP jest ustawieniem domyślnym. Inne pionowy pozycjonowania wartości można zdefiniować za pomocą <xref:System.Windows.Media.FormattedText.Height%2A> właściwości można obliczyć odpowiedniego [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości można obliczyć odpowiedniego [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_WORDBREAK|Brak|Nie jest wymagane. Dzielenie wyrazów odbywa się automatycznie z <xref:System.Windows.Media.FormattedText> obiektów. Nie można wyłączyć.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.FormattedText>  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Tworzenie tekstu z konturem](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Porady: Tworzenie animacji PathGeometry tekstu](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)
