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
ms.openlocfilehash: 538cc23a3ee7696a28de43e5724dc450328205ff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372181"
---
# <a name="drawing-formatted-text"></a>Rysowanie formatowanego tekstu
Ten temat zawiera omówienie funkcji <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt zapewnia kontrolę niskiego poziomu dla Rysowanie tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji.  
  
  
## <a name="technology-overview"></a>Omówienie technologii  
 <xref:System.Windows.Media.FormattedText> Obiekt umożliwia rysowanie tekstu wielowierszowego, w którym każdy znak w tekście mogą indywidualnie sformatowane. Poniższy przykład pokazuje tekst, który ma kilka formaty stosowane do niego.  
  
 ![Tekst wyświetlany za pomocą obiektu FormattedText](./media/formattedtext01.jpg "FormattedText01")  
Tekst wyświetlany za pomocą metody FormattedText  
  
> [!NOTE]
>  Dla tych deweloperów migracji z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] interfejsu API tabeli w [migracji Win32](#win32_migration) sekcji list [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText flag i przybliżony odpowiedniej wartości wyrażonej w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Powody do korzystania z tekstu sformatowanego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wiele kontrolek dla Rysowanie tekstu na ekranie. Każdy formant jest przeznaczona do innego scenariusza i ma swój własny listę funkcjami i ograniczeniami. Ogólnie rzecz biorąc <xref:System.Windows.Controls.TextBlock> element powinien być używany, gdy obsługa text ograniczony jest wymagane, na przykład krótkie zdanie w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> może służyć, gdy wymagana jest obsługa minimalnej ilości tekstu. Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Obiekt zapewnia większą tekstu funkcji niż [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontrolek tekstu i może być przydatne w sytuacjach, w której chcesz użyć tekstu jako dekoracyjnych element. Aby uzyskać więcej informacji, zobacz następującą sekcję [Konwertowanie tekstu w formacie geometrii](#converting_formatted_text).  
  
 Ponadto <xref:System.Windows.Media.FormattedText> obiekt jest przydatne do tworzenia, zorientowane na tekst <xref:System.Windows.Media.DrawingVisual>-obiektami wywodzącymi. <xref:System.Windows.Media.DrawingVisual> jest klasą rysowania uproszczone, która jest używany do renderowania kształty, obrazy i tekst. Aby uzyskać więcej informacji, zobacz [trafień za pomocą DrawingVisuals próbkę](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Za pomocą obiektu FormattedText  
 Aby utworzyć sformatowany tekst, wywołaj <xref:System.Windows.Media.FormattedText.%23ctor%2A> Konstruktor do tworzenia <xref:System.Windows.Media.FormattedText> obiektu. Po utworzeniu początkowego tekstu sformatowanego ciągu można zastosować szeroką gamę style formatowania.  
  
 Użyj <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwości, aby ograniczyć tekst, który ma określonej szerokości. Tekst będzie automatycznie zawijany w celu uniknięcia przekroczenia określonej szerokości. Użyj <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> właściwości, aby ograniczyć tekst, który ma określonej wysokości. Tekst zostanie wyświetlona wielokropek "..." na tekst, który przekracza określonej wysokości.  
  
 ![Tekst wyświetlany za pomocą obiektu FormattedText](./media/formattedtext02.png "FormattedText02")  
Wyświetlany tekst zawierający wordwrapping i wielokropek  
  
 Wiele stylów formatowania można zastosować do co najmniej jeden znak. Na przykład można nazwać zarówno <xref:System.Windows.Media.FormattedText.SetFontSize%2A> i <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody, aby zmienić formatowanie pięć pierwszych znaków w tekście.  
  
 Poniższy przykład kodu tworzy <xref:System.Windows.Media.FormattedText> obiektu, a następnie stosuje kilka stylów formatowania do tekstu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Rozmiar czcionki jednostka miary  
 Podobnie jak w przypadku innych obiektów tekstu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji <xref:System.Windows.Media.FormattedText> obiekt używa pikselach niezależnych od urządzenia jako jednostka miary. Jednak większość [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje używają punktów jako jednostka miary. Jeśli chcesz użyć tekstu wyświetlanego w jednostkach punktów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, musisz przekonwertować [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] punktów. Poniższy przykład kodu pokazuje, jak wykonać tę konwersję.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Konwertowanie sformatowany tekst do geometrii  
 Możesz przekonwertować sformatowany tekst do <xref:System.Windows.Media.Geometry> obiektów, co pozwala na tworzenie innych rodzajów wizualnie tekstu. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konspekt ciąg tekstowy.  
  
 ![Kontur tekstu przy użyciu pędzel gradientów liniowych](./media/outlinedtext02.jpg "OutlinedText02")  
Kontur tekstu przy użyciu pędzel gradientów liniowych  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych interesujące, modyfikując obrysu, wypełnij i wyróżnienie tekst skonwertowany.  
  
 ![Tekst w różnych kolorach wypełnienia i pociągnięcia](./media/outlinedtext03.jpg "OutlinedText03")  
Przykład ustawień obrysu i wypełnienia na różne kolory  
  
 ![Tekst z ImageBrush zastosowany do obrysu](./media/outlinedtext04.jpg "OutlinedText04")  
Przykład ImageBrush dotyczą pociągnięcia  
  
 ![Tekst z ImageBrush zastosowany do obrysu](./media/outlinedtext05.jpg "OutlinedText05")  
Przykład ImageBrush stosowane do obrysu i wyróżnienia  
  
 Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu nie jest już zbioru znaków — nie można zmodyfikować znaków w ciągu tekstowym. Jednak może wpłynąć na wygląd tekstu przekonwertowany, modyfikując jej obrysu i wypełnienie właściwości. Stroke odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany. Aby uzyskać więcej informacji, zobacz [Utwórz tekst opisane](how-to-create-outlined-text.md).  
  
 Można także przekonwertować tekst sformatowany <xref:System.Windows.Media.PathGeometry> obiektu, a następnie użyj obiektu wyróżnianie tekstu. Na przykład, można zastosować animacji, aby <xref:System.Windows.Media.PathGeometry> obiekt animacji poniżej zarys tekstu sformatowanego.  
  
 W poniższym przykładzie pokazano tekstu sformatowanego, który został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiektu. Animowany elipsy postępuje zgodnie ze ścieżką pociągnięć renderowanego tekstu.  
  
 ![Kula geometrią ścieżki tekstu](./media/textpathgeometry01.gif "TextPathGeometry01")  
Kula geometrią ścieżki tekstu  
  
 Aby uzyskać więcej informacji, zobacz [jak: Tworzenie animacji PathGeometry tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Możesz utworzyć inne interesujące zastosowania tekstu sformatowanego, po został przekonwertowany na <xref:System.Windows.Media.PathGeometry> obiektu. Można na przykład klipu wideo, aby wyświetlić wewnątrz niego.  
  
 ![Wyświetlanie wideo geometrii ścieżki tekstu](./media/videotextdemo01.png "VideoTextDemo01")  
Wyświetlanie wideo geometrii ścieżki tekstu  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migracja Win32  
 Funkcje <xref:System.Windows.Media.FormattedText> Rysowanie tekstu są podobne do funkcji [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText funkcji. Dla tych deweloperów migrowany [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] interfejsu API, w poniższej tabeli wymieniono [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText flag i przybliżony odpowiedniej wartości wyrażonej w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Flaga DrawText|Odpowiednik w WPF|Uwagi|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości do obliczenia na odpowiedni [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> i <xref:System.Windows.Media.FormattedText.Width%2A> właściwości do obliczenia prostokąt danych wyjściowych.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Brak|Nie jest wymagane. Miejsca szerokość i ostatni wiersz renderowania są takie same jak w ramach formant edycji.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Użyj <xref:System.Windows.TextTrimming.WordEllipsis> można pobrać [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS z DT_WORD_ELIPSIS zakończenia wielokropka — w tym przypadku znak wielokropka występuje tylko w wyrazy, które nie mieszczą się w jednym wierszu.|  
|DT_EXPAND_TABS|Brak|Nie jest wymagane. Karty są automatycznie rozszerza się na zatrzymanie co 4 ems, czyli około szerokość 8 znaków niezależny od języka.|  
|DT_EXTERNALLEADING|Brak|Nie jest wymagane. Wiodących zewnętrznych zawsze znajduje się w wierszami. Użyj <xref:System.Windows.Media.FormattedText.LineHeight%2A> właściwości do utworzenia interlinia zdefiniowanych przez użytkownika.|  
|DT_HIDEPREFIX|Brak|Nieobsługiwane. Usuń "&" z ciągu przed konstruowanie <xref:System.Windows.Media.FormattedText> obiektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Jest to domyślne wyrównanie tekstu. Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Left>. (Tylko WPF)|  
|DT_MODIFYSTRING|Brak|Nieobsługiwane.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Wycinka nie jest realizowane automatycznie. Do klipu tekstu, należy użyć <xref:System.Windows.Media.Visual.VisualClip%2A> właściwości.|  
|DT_NOFULLWIDTHCHARBREAK|Brak|Nieobsługiwane.|  
|DT_NOPREFIX|Brak|Nie jest wymagane. Znaku "&" w ciągach jest zawsze traktowany jako normalne znaki.|  
|DT_PATHELLIPSIS|Brak|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Brak|Nieobsługiwane. Jeśli chcesz używać znaków podkreślenia dla tekstu, na przykład klawisza skrótu lub łącza, użyj <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metody.|  
|DT_PREFIXONLY|Brak|Nieobsługiwane.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Użyj <xref:System.Windows.Media.FormattedText.TextAlignment%2A> właściwość z wartością ustawioną na <xref:System.Windows.TextAlignment.Right>. (Tylko WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Ustaw <xref:System.Windows.Media.FormattedText.FlowDirection%2A> właściwość <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Brak|Nie jest wymagane. <xref:System.Windows.Media.FormattedText> obiekty zachowywać się jak formant jeden wiersz, chyba że albo <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> właściwość ma wartość lub tekst zawiera CR/LF (CR/LF).|  
|DT_TABSTOP|Brak|Brak obsługi położenie tabulatorów zdefiniowanych przez użytkownika.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Nie jest wymagane. Najważniejsze uzasadnienie jest ustawieniem domyślnym. Inne pionowy pozycjonowania wartości można zdefiniować przy użyciu <xref:System.Windows.Media.FormattedText.Height%2A> właściwości do obliczenia na odpowiedni [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Użyj <xref:System.Windows.Media.FormattedText.Height%2A> właściwości do obliczenia na odpowiedni [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozycji DrawText "y".|  
|DT_WORDBREAK|Brak|Nie jest wymagane. Wyrazów odbywa się automatycznie przy użyciu <xref:System.Windows.Media.FormattedText> obiektów. Nie można wyłączyć.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Użyj <xref:System.Windows.Media.FormattedText.Trimming%2A> właściwość z wartością <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.FormattedText>
- [Dokumenty w WPF](documents-in-wpf.md)
- [Typografia w WPF](typography-in-wpf.md)
- [Tworzenie tekstu z konturem](how-to-create-outlined-text.md)
- [Instrukcje: Tworzenie animacji PathGeometry tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
