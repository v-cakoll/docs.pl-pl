---
title: Omówienie renderowania grafiki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: c82b2c4599f14f55b51587407a7d96b3e2be9d5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186605"
---
# <a name="wpf-graphics-rendering-overview"></a>Przegląd Renderowanie grafiki WPF
Ten temat zawiera omówienie warstwy wizualnej. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Koncentruje się na roli <xref:System.Windows.Media.Visual> klasy do renderowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługi w modelu.  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Rola obiektu wizualnego  
 Klasa <xref:System.Windows.Media.Visual> jest podstawową abstrakcją, z której wywodzi się każdy <xref:System.Windows.FrameworkElement> obiekt. Służy również jako punkt wejścia do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pisania nowych formantów w , i pod wieloma względami można traktować jako uchwyt okna (HWND) w modelu aplikacji Win32.  
  
 Obiekt <xref:System.Windows.Media.Visual> jest obiektem podstawowym, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] którego podstawową rolą jest zapewnienie obsługi renderowania. Formanty interfejsu <xref:System.Windows.Controls.Button> użytkownika, takie jak i <xref:System.Windows.Controls.TextBox>, pochodzą z <xref:System.Windows.Media.Visual> klasy i używać go do utrwalania ich danych renderowania. Obiekt <xref:System.Windows.Media.Visual> zapewnia obsługę:  
  
- Wyświetlanie danych wyjściowych: Renderowanie utrwalonej, serializowanej zawartości rysunku wizualizacji.  
  
- Przekształcenia: wykonywanie przekształceń w wizualizacji.  
  
- Przycinanie: Zapewnienie obsługi regionu przycinania dla wizualizacji.  
  
- Testowanie trafień: Określanie, czy współrzędna lub geometria znajduje się w granicach wizualizacji.  
  
- Obliczenia obwiedni: Określanie prostokąta ograniczającego wizualizacji.  
  
 Jednak <xref:System.Windows.Media.Visual> obiekt nie obejmuje obsługi funkcji niewyrenderujących, takich jak:  
  
- Obsługa zdarzeń  
  
- Układ  
  
- Style  
  
- Powiązanie danych  
  
- Globalizacja  
  
 <xref:System.Windows.Media.Visual>jest narażony jako publiczna klasa abstrakcyjna, z której muszą pochodzić klasy podrzędne. Na poniższej ilustracji przedstawiono hierarchię obiektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wizualnych, które są widoczne w programie .  
  
 ![Diagram klas pochodzących z obiektu Visual](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>RysunekKlasa wizualna  
 Jest <xref:System.Windows.Media.DrawingVisual> to lekka klasa rysunku używana do renderowania kształtów, obrazów lub tekstu. Ta klasa jest uważana za lekką, ponieważ nie zapewnia obsługi układu lub zdarzeń, co zwiększa jej wydajność środowiska uruchomieniowego. Z tego powodu rysunki są idealne dla tła i obiektów clipart. Może <xref:System.Windows.Media.DrawingVisual> służyć do tworzenia niestandardowego obiektu wizualnego. Aby uzyskać więcej informacji, zobacz [Korzystanie z drawingvisual Objects](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Viewport3DKlasa wizualna  
 Zapewnia <xref:System.Windows.Media.Media3D.Viewport3DVisual> most między <xref:System.Windows.Media.Visual> 2D <xref:System.Windows.Media.Media3D.Visual3D> i obiektów. Klasa <xref:System.Windows.Media.Media3D.Visual3D> jest klasą podstawową dla wszystkich elementów wizualnych 3D. Wymaga <xref:System.Windows.Media.Media3D.Viewport3DVisual> zdefiniowania <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> wartości i <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> wartości. Kamera umożliwia wyświetlanie sceny. Rzutnia określa, gdzie rzutowanie jest mapowana na powierzchnię 2D. Aby uzyskać więcej informacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]na temat 3D in , zobacz [Przegląd grafiki 3-W](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Klasa ContainerVisual  
 Klasa <xref:System.Windows.Media.ContainerVisual> jest używana jako kontener dla <xref:System.Windows.Media.Visual> kolekcji obiektów. Klasa <xref:System.Windows.Media.DrawingVisual> pochodzi od <xref:System.Windows.Media.ContainerVisual> klasy, dzięki czemu zawiera kolekcję obiektów wizualnych.  
  
### <a name="drawing-content-in-visual-objects"></a>Rysowanie zawartości w obiektach wizualnych  
 Obiekt <xref:System.Windows.Media.Visual> przechowuje swoje dane renderowania jako **listę instrukcji grafiki wektorowej**. Każdy element na liście instrukcji reprezentuje niskiego poziomu zestaw danych graficznych i skojarzonych zasobów w formacie serializowanym. Istnieją cztery różne typy danych renderowania, które mogą zawierać zawartość rysunku.  
  
|Typ zawartości rysunku|Opis|  
|--------------------------|-----------------|  
|Grafika wektorowa|Reprezentuje wektorowe dane graficzne <xref:System.Windows.Media.Brush> oraz <xref:System.Windows.Media.Pen> wszelkie skojarzone i informacje.|  
|Image (Obraz)|Reprezentuje obraz w obrębie regionu zdefiniowanego przez plik <xref:System.Windows.Rect>.|  
|Glifów|Reprezentuje rysunek, który <xref:System.Windows.Media.GlyphRun>renderuje , który jest sekwencją glifów z określonego zasobu czcionki. W ten sposób tekst jest reprezentowany.|  
|Film wideo|Reprezentuje rysunek, który renderuje wideo.|  
  
 Umożliwia <xref:System.Windows.Media.DrawingContext> wypełnianie zawartości wizualnej. <xref:System.Windows.Media.Visual> Korzystając z <xref:System.Windows.Media.DrawingContext> poleceń rysowania obiektu, w rzeczywistości przechowujesz zestaw danych renderowania, które będą później używane przez system graficzny; nie rysujesz na ekranie w czasie rzeczywistym.  
  
 Podczas tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formantu, <xref:System.Windows.Controls.Button>takich jak , formant niejawnie generuje dane renderowania dla samego rysunku. Na przykład ustawienie <xref:System.Windows.Controls.ContentControl.Content%2A> właściwości <xref:System.Windows.Controls.Button> powoduje, że formant do przechowywania reprezentacji renderowania glifów.  
  
 A <xref:System.Windows.Media.Visual> opisuje jego zawartość <xref:System.Windows.Media.Drawing> jako jeden lub <xref:System.Windows.Media.DrawingGroup>więcej obiektów zawartych w pliku . A <xref:System.Windows.Media.DrawingGroup> opisuje również maski krycia, przekształcenia, efekty bitmapy i inne operacje, które są stosowane do jego zawartości. <xref:System.Windows.Media.DrawingGroup>operacje są stosowane w następującej kolejności podczas <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A> <xref:System.Windows.Media.DrawingGroup.Opacity%2A>renderowania <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>zawartości: <xref:System.Windows.Media.DrawingGroup.Transform%2A>, , <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, , a następnie .  
  
 Na poniższej ilustracji <xref:System.Windows.Media.DrawingGroup> przedstawiono kolejność, w jakiej operacje są stosowane podczas sekwencji renderowania.  
  
 ![Kolejność operacji grupy rysunkowej](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Kolejność operacji grupy rysunkowej  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie obiektów rysunkowych](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Rysowanie zawartości w warstwie wizualnej  
 Nigdy nie bezpośrednio utworzyć <xref:System.Windows.Media.DrawingContext>wystąpienia; można jednak uzyskać kontekst rysunkowy z niektórych <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>metod, takich jak i . Poniższy przykład pobiera <xref:System.Windows.Media.DrawingContext> z <xref:System.Windows.Media.DrawingVisual> a i używa go do rysowania prostokąta.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Wyliczanie zawartości rysunku w warstwie wizualnej  
 Oprócz innych zastosowań obiekty <xref:System.Windows.Media.Drawing> zapewniają również model obiektów do wyliczania <xref:System.Windows.Media.Visual>zawartości programu .  
  
> [!NOTE]
> Podczas wyliczania zawartości wizualizacji pobierasz <xref:System.Windows.Media.Drawing> obiekty, a nie podstawową reprezentację danych renderowania jako listy instrukcji grafiki wektorowej.  
  
 W poniższym przykładzie <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> użyto <xref:System.Windows.Media.DrawingGroup> metody do <xref:System.Windows.Media.Visual> pobrania wartości a i wyliczyć go.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Jak obiekty wizualne są używane do tworzenia formantów  
 Wiele obiektów w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] składają się z innych obiektów wizualnych, co oznacza, że mogą one zawierać różne hierarchie obiektów podrzędnych. Wiele elementów interfejsu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]użytkownika w , takich jak formanty, składa się z wielu obiektów wizualnych, reprezentujących różne typy elementów renderowania. Na przykład <xref:System.Windows.Controls.Button> formant może zawierać wiele innych <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter>obiektów, <xref:System.Windows.Controls.TextBlock>w tym , i .  
  
 Poniższy kod <xref:System.Windows.Controls.Button> przedstawia formant zdefiniowany w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Jeśli wyliczyć obiekty wizualne, które <xref:System.Windows.Controls.Button> składają się na formant domyślny, można znaleźć hierarchii obiektów wizualnych pokazano poniżej:  
  
 ![Diagram wizualnej hierarchii drzew](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 Formant <xref:System.Windows.Controls.Button> zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z <xref:System.Windows.Controls.ContentPresenter> kolei zawiera element. Element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> jest odpowiedzialny za rysowanie obramowania i tła dla pliku <xref:System.Windows.Controls.Button>. Element <xref:System.Windows.Controls.ContentPresenter> jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>pliku . W takim przypadku, ponieważ są wyświetlane <xref:System.Windows.Controls.ContentPresenter> tekst, <xref:System.Windows.Controls.TextBlock> element zawiera element. Fakt, że <xref:System.Windows.Controls.Button> formant <xref:System.Windows.Controls.ContentPresenter> używa oznacza, że zawartość może być reprezentowana <xref:System.Windows.Controls.Image> przez inne elementy, <xref:System.Windows.Media.EllipseGeometry>takie jak lub geometrii, takich jak .  
  
### <a name="control-templates"></a>Szablony kontrolek  
 Kluczem do rozszerzenia formantu do hierarchii <xref:System.Windows.Controls.ControlTemplate>formantów jest . Szablon formantu określa domyślną hierarchię wizualną formantu. Podczas jawnego odwoływania się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej. Można zastąpić wartości domyślne dla szablonu formantu, aby utworzyć dostosowany wygląd formantu. Na przykład można zmodyfikować wartość koloru <xref:System.Windows.Controls.Button> tła formantu, tak aby używała liniowej wartości koloru gradientu zamiast wartości koloru stałego. Aby uzyskać więcej informacji, zobacz [Style przycisków i szablony](../controls/button-styles-and-templates.md).  
  
 Element interfejsu użytkownika, takich <xref:System.Windows.Controls.Button> jak formant, zawiera kilka list instrukcji grafiki wektorowej, które opisują całą definicję renderowania formantu. Poniższy kod <xref:System.Windows.Controls.Button> przedstawia formant zdefiniowany w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Jeśli wyliczyć obiekty wizualne i listy instrukcji grafiki wektorowej, które składają się na <xref:System.Windows.Controls.Button> formant, można znaleźć hierarchię obiektów zilustrowanych poniżej:  
  
 ![Diagram drzewa wizualnego i danych renderowania](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Formant <xref:System.Windows.Controls.Button> zawiera <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> element, który z <xref:System.Windows.Controls.ContentPresenter> kolei zawiera element. Element <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> jest odpowiedzialny za rysowanie wszystkich dyskretnych elementów graficznych, które tworzą obramowanie i tło przycisku. Element <xref:System.Windows.Controls.ContentPresenter> jest odpowiedzialny za wyświetlanie zawartości <xref:System.Windows.Controls.Button>pliku . W takim przypadku, ponieważ są wyświetlane <xref:System.Windows.Controls.ContentPresenter> obrazu, <xref:System.Windows.Controls.Image> element zawiera element.  
  
 Istnieje wiele punktów, na które należy zwrócić uwagę na hierarchię obiektów wizualnych i listy instrukcji grafiki wektorowej:  
  
- Kolejność w hierarchii reprezentuje kolejność renderowania informacji rysunku. Z głównego elementu wizualnego elementy podrzędne są przesuwane, od lewej do prawej, od góry do dołu. Jeśli element ma wizualne elementy podrzędne, są one przesunięty przed elementem równoramiany.  
  
- Elementy węzłów innych niż liść <xref:System.Windows.Controls.ContentPresenter>w hierarchii, takie jak , które zawierają elementy podrzędne — nie zawierają list instrukcji.  
  
- Jeśli element wizualny zawiera zarówno listę instrukcji grafiki wektorowej, jak i elementy podrzędne wizualne, lista instrukcji w nadrzędnym elemencie wizualnym jest renderowana przed rysunkami w dowolnym wizualnym objects podrzędnym.  
  
- Elementy na liście instrukcji grafiki wektorowej są renderowane od lewej do prawej.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Drzewo wizualne  
 Drzewo wizualne zawiera wszystkie elementy wizualne używane w interfejsie użytkownika aplikacji. Ponieważ element wizualny zawiera utrwalone informacje o rysunku, można myśleć o drzewie wizualnym jako wykresie sceny, zawierającym wszystkie informacje renderowania potrzebne do skomponowania danych wyjściowych do urządzenia wyświetlającego. To drzewo jest akumulacja wszystkich elementów wizualnych utworzonych bezpośrednio przez aplikację, czy w kodzie lub w znacznikach. Drzewo wizualne zawiera również wszystkie elementy wizualne utworzone przez rozszerzenie szablonu elementów, takich jak formanty i obiekty danych.  
  
 Poniższy kod <xref:System.Windows.Controls.StackPanel> przedstawia element zdefiniowany w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Jeśli wyliczyć obiekty wizualne, które <xref:System.Windows.Controls.StackPanel> składają się na element w przykładzie znaczników, można znaleźć hierarchii obiektów wizualnych zilustrowane poniżej:  
  
 ![Diagram wizualnej hierarchii drzew](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Kolejność renderowania  
 Drzewo wizualne określa kolejność renderowania obiektów wizualnych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i rysunkowych. Kolejność przechodzenia rozpoczyna się od wizualizacji głównej, która jest najbardziej najwyższym węzłem w drzewie wizualnym. Elementy podrzędne wizualizacji głównej są następnie przenoszone, od lewej do prawej. Jeśli wizualizacja ma elementy podrzędne, jego elementy podrzędne są przemierzane przed rodzeństwem wizualizacji. Oznacza to, że zawartość wizualizacji podrzędnej jest renderowana przed własną zawartością wizualizacji.  
  
 ![Diagram kolejności renderowania drzewa wizualnego](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Główny wizualizacja  
 Wizualizacja **główna** jest najważniejszym elementem w hierarchii drzewa wizualnego. W większości aplikacji klasa podstawowa wizualizacji <xref:System.Windows.Window> głównej <xref:System.Windows.Navigation.NavigationWindow>jest albo lub . Jednak jeśli hostujesz obiekty wizualne w aplikacji Win32, główna wizualizacja będzie najbardziej wizualną, którą hostujesz w oknie Win32. Aby uzyskać więcej informacji, zobacz [Samouczek: Hostowanie obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relacja z drzewem logicznym  
 Drzewo logiczne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w reprezentuje elementy aplikacji w czasie wykonywania. Chociaż nie można manipulować tego drzewa bezpośrednio, ten widok aplikacji jest przydatne do zrozumienia dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego drzewo logiczne może <xref:System.Windows.Documents.ListItem>reprezentować obiekty danych niewizualnych, takie jak . W wielu przypadkach drzewo logiczne mapuje bardzo ściśle do definicji znaczników aplikacji. Poniższy kod <xref:System.Windows.Controls.DockPanel> przedstawia element zdefiniowany w znacznikach.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Jeśli wyliczyć obiekty logiczne, które <xref:System.Windows.Controls.DockPanel> składają się na element w przykładzie znaczników, można znaleźć hierarchię obiektów logicznych zilustrowane poniżej:  
  
 ![Diagram drzewa](./media/tree1-wcp.gif "Tree1_wcp")  
Diagram drzewa logicznego  
  
 Zarówno drzewo wizualne, jak i drzewo logiczne są synchronizowane z bieżącym zestawem elementów aplikacji, odzwierciedlając wszelkie dodawanie, usuwanie lub modyfikację elementów. Jednak drzewa przedstawiają różne poglądy aplikacji. W przeciwieństwie do drzewa wizualnego drzewa logicznego <xref:System.Windows.Controls.ContentPresenter> nie rozwija elementu formantu. Oznacza to, że nie ma bezpośredniej korespondencji jeden do jednego między drzewem logicznym a drzewem wizualnym dla tego samego zestawu obiektów. W rzeczywistości wywoływanie **LogicalTreeHelper** <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> metody obiektu i **VisualTreeHelper** <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> metody obiektu przy użyciu tego samego elementu jako parametr daje różne wyniki.  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [Drzewa w WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Wyświetlanie drzewa wizualnego za pomocą XamlPad  
 Narzędzie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XamlPad udostępnia opcję wyświetlania i eksplorowania drzewa wizualnego odpowiadającego aktualnie zdefiniowanej zawartości XAML. Kliknij przycisk **Pokaż drzewo wizualne** na pasku menu, aby wyświetlić drzewo wizualne. Poniżej przedstawiono rozszerzenie zawartości XAML do węzłów drzewa wizualnego w panelu **Visual Tree Explorer** xamlPad:  
  
 ![Panel Visual Tree Explorer w XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 <xref:System.Windows.Controls.Label>Zwróć uwagę, <xref:System.Windows.Controls.TextBox>jak <xref:System.Windows.Controls.Button> program , i steruje każdym wyświetlać oddzielną hierarchię obiektów wizualnych w panelu **Visual Tree Explorer** xamlPad. Jest to [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spowodowane <xref:System.Windows.Controls.ControlTemplate> formanty mają, który zawiera drzewa wizualnego tego formantu. Podczas jawnego odwoływania się do formantu, niejawnie odwołujesz się do jego hierarchii wizualnej.  
  
### <a name="profiling-visual-performance"></a>Profilowanie wydajności wizualnej  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera zestaw narzędzi do profilowania wydajności, które umożliwiają analizowanie zachowania w czasie wykonywania aplikacji i określanie typów optymalizacji wydajności, które można zastosować. Narzędzie Visual Profiler zapewnia bogaty, graficzny widok danych o wydajności, mapując bezpośrednio do drzewa wizualnego aplikacji. Na tym zrzucie ekranu sekcja **Użycie procesora CPU** w programie Visual [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Profiler zawiera dokładny podział użycia obiektu usług, takich jak renderowanie i układ.  
  
 ![Wyjście wyświetlania profilera wizualnego](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Wyjście wyświetlania profilera wizualnego  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Zachowanie renderowania wizualnego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wprowadza kilka funkcji, które wpływają na zachowanie renderowania obiektów wizualnych: grafikę w trybie zachowanym, grafikę wektorową i grafikę niezależną od urządzenia.  
  
### <a name="retained-mode-graphics"></a>Grafika w trybie zachowanym  
 Jednym z kluczy do zrozumienia roli Visual obiektu jest zrozumienie różnicy między **tryb natychmiastowy** i **zachowanych systemów** graficznych trybu. Standardowa aplikacja Win32 oparta na GDI lub GDI+ wykorzystuje system graficzny trybu natychmiastowego. Oznacza to, że aplikacja jest odpowiedzialna za ponowne malowanie części obszaru klienta, który jest unieważniony, ze względu na akcję, taką jak zmiana rozmiar okna lub obiekt zmieniający jego wygląd.  
  
 ![Diagram sekwencji renderowania Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Natomiast [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa systemu trybu zachowanego. Oznacza to, że obiekty aplikacji, które mają wygląd definiują zestaw szeregowanych danych rysunku. Po zdefiniowaniu danych rysunku system jest odpowiedzialny za odpowiadanie na wszystkie ponowne malowanie żądań renderowania obiektów aplikacji. Nawet w czasie wykonywania można modyfikować lub tworzyć obiekty aplikacji i nadal polegać na systemie odpowiadania na żądania malowania. Moc w systemie graficznym trybu zachowanego jest to, że informacje o rysunku jest zawsze utrwalane w stanie serializacji przez aplikację, ale renderowanie odpowiedzialność pozostawiona do systemu. Na poniższym diagramie przedstawiono, jak aplikacja opiera się na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odpowiadanie na żądania malowania.  
  
 ![Diagram sekwencji renderowania WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Inteligentne przerysowywanie  
 Jedną z największych zalet korzystania z grafiki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w trybie zachowanym jest to, że można skutecznie zoptymalizować to, co musi być przerysowane w aplikacji. Nawet jeśli masz złożoną scenę o różnym poziomie krycia, zazwyczaj nie trzeba pisać kodu specjalnego przeznaczenia, aby zoptymalizować przerysowywanie. Porównaj to z programowaniem Win32, w którym można poświęcić dużo wysiłku na optymalizację aplikacji, minimalizując ilość ponownego rysowania w regionie aktualizacji. Zobacz [Ponowne rysowanie w regionie aktualizacji](/windows/desktop/gdi/redrawing-in-the-update-region) na przykład typu złożoności związanej z optymalizacją ponownego rysowania w aplikacjach Win32.  
  
### <a name="vector-graphics"></a>Grafika wektorowa  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa **grafiki wektorowej** jako formatu danych renderowania. Grafika wektorowa , w tym skalowalna grafika wektorowa (SVG), metaplik systemu Windows (wmf) i czcionki TrueType, przechowuje dane renderowania i przesyła je jako listę instrukcji opisujących sposób odtworzenia obrazu przy użyciu ćwitryzmów graficznych. Na przykład czcionki TrueType to czcionki konspektu opisujące zestaw linii, krzywych i poleceń, a nie tablica pikseli. Jedną z kluczowych zalet grafiki wektorowej jest możliwość skalowania do dowolnego rozmiaru i rozdzielczości.  
  
 W przeciwieństwie do grafiki wektorowej grafika bitmapowa przechowuje dane renderowania jako reprezentację obrazu w pikselach po pikselu, wstępnie renderowane dla określonej rozdzielczości. Jedną z kluczowych różnic między formatami bitmapowymi a wektorowymi jest wierność oryginalnemu obrazowi źródłowego. Na przykład, gdy rozmiar obrazu źródłowego jest modyfikowany, systemy grafiki bitmapowej rozciągają obraz, podczas gdy systemy grafiki wektorowej skalują obraz, zachowując wierność obrazu.  
  
 Na poniższej ilustracji przedstawiono obraz źródłowy, który został przesułowiony o 300%. Zwróć uwagę na zniekształcenia, które pojawiają się, gdy obraz źródłowy jest rozciągnięty jako obraz graficzny bitmapy, a nie skalowany jako obraz grafiki wektorowej.  
  
 ![Różnice między grafiką rastrową i wektorową](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 Poniższy znacznik pokazuje <xref:System.Windows.Shapes.Path> dwa zdefiniowane elementy. Drugi element używa <xref:System.Windows.Media.ScaleTransform> a, aby zmienić rozmiar instrukcji rysowania pierwszego elementu o 300%. Należy zauważyć, że instrukcje rysowania w <xref:System.Windows.Shapes.Path> elementach pozostają niezmienione.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>Informacje o rozdzielczości i grafiki niezależne od urządzenia  
 Istnieją dwa czynniki systemowe, które określają rozmiar tekstu i grafiki na ekranie: rozdzielczość i DPI. Rozdzielczość opisuje liczbę pikseli wyświetlanych na ekranie. Wraz z wyższą rozdzielczością piksele stają się mniejsze, co powoduje, że grafika i tekst stają się mniejsze. Grafika wyświetlana na monitorze ustawionym na 1024 x 768 będzie znacznie mniejsza po zmianie rozdzielczości na 1600 x 1200.  
  
 Inne ustawienie systemowe, DPI, opisuje rozmiar cala ekranu w pikselach. Większość systemów Windows ma DPI 96, co oznacza, że cal ekranu wynosi 96 pikseli. Zwiększenie ustawienia DPI sprawia, że cal ekranu jest większy; zmniejszenie dpi sprawia, że cal ekranu jest mniejszy. Oznacza to, że cal ekranu nie jest taki sam rozmiar jak cala w świecie rzeczywistym; w większości systemów, to chyba nie. Wraz z zwiększeniem dpi, dpi obsługujących grafiki i tekst stają się większe, ponieważ masz zwiększony rozmiar cala ekranu. Zwiększenie dpi może ułatwić odczytywanie tekstu, szczególnie w wysokiej rozdzielczości.  
  
 Nie wszystkie aplikacje są obsługujące dpi: niektóre używają pikseli sprzętowych jako podstawowej jednostki miary; zmiana dpi systemu nie ma wpływu na te aplikacje. Wiele innych aplikacji używa jednostek obsługujących dpi do opisywania rozmiarów czcionek, ale używa pikseli do opisywania wszystkiego innego. Uczynienie DPI zbyt małym lub zbyt dużym może powodować problemy z układem dla tych aplikacji, ponieważ tekst aplikacji jest skalowany z ustawieniem DPI systemu, ale interfejs użytkownika aplikacji nie. Ten problem został wyeliminowany dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacji opracowanych przy użyciu .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsługuje automatyczne skalowanie przy użyciu piksela niezależnego od urządzenia jako podstawowej jednostki miary, zamiast pikseli sprzętowych; grafika i tekst skalują się prawidłowo bez dodatkowej pracy ze strony dewelopera aplikacji. Na poniższej ilustracji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przedstawiono przykład sposobu, w jaki tekst i grafika są wyświetlane w różnych ustawieniach DPI.  
  
 ![Grafika i tekst w różnych ustawieniach DPI](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Grafika i tekst w różnych ustawieniach DPI  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>Klasa VisualTreeHelper  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> jest statyczną klasą pomocnika, która zapewnia funkcje niskiego poziomu programowania na poziomie obiektu wizualnego, co jest przydatne w bardzo konkretnych scenariuszach, takich jak tworzenie formantów niestandardowych o wysokiej wydajności. W większości przypadków obiekty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] struktury wyższego poziomu, takie jak <xref:System.Windows.Controls.Canvas> i <xref:System.Windows.Controls.TextBlock>, oferują większą elastyczność i łatwość użycia.  
  
### <a name="hit-testing"></a>Testowanie trafień  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> zawiera metody testowania trafień na obiektach wizualnych, gdy domyślna obsługa testu trafień nie spełnia Twoich potrzeb. Metody klasy <xref:System.Windows.Media.VisualTreeHelper> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> można użyć do określenia, czy wartość geometrii lub współrzędnych punktu mieści się w granicach danego obiektu, takiego jak formant lub element graficzny. Na przykład można użyć testowania trafień, aby ustalić, czy kliknięcie myszą w obrębie prostokąta ograniczającego obiektu mieści się w geometrii okręgu Można również zastąpić domyślną implementację testowania trafień w celu wykonania własnego niestandardowego testu trafień. Obliczenia.  
  
 Aby uzyskać więcej informacji na temat testowania trafień, zobacz [Testowanie trafień w warstwie wizualnej](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Wyliczanie drzewa wizualnego  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> zapewnia funkcje wyliczania członków drzewa wizualnego. Aby pobrać element nadrzędny, należy wywołać <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> metodę. Aby pobrać element podrzędny lub bezpośredni element podrzędny <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> obiektu wizualnego, należy wywołać metodę. Ta metoda zwraca <xref:System.Windows.Media.Visual> element podrzędny nadrzędnego w określonym indeksie.  
  
 W poniższym przykładzie pokazano, jak wyliczyć wszystkie elementy podrzędne obiektu wizualnego, który jest techniką, której warto użyć, jeśli chcesz serializować wszystkie informacje renderowania hierarchii obiektów wizualnych.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 W większości przypadków drzewo logiczne jest bardziej użyteczną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] reprezentacją elementów w aplikacji. Chociaż nie modyfikujesz drzewa logicznego bezpośrednio, ten widok aplikacji jest przydatny do zrozumienia dziedziczenia właściwości i routingu zdarzeń. W przeciwieństwie do drzewa wizualnego drzewo logiczne może <xref:System.Windows.Documents.ListItem>reprezentować obiekty danych niewizualnych, takie jak . Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [Drzewa w WPF](../advanced/trees-in-wpf.md).  
  
 Klasa <xref:System.Windows.Media.VisualTreeHelper> zawiera metody zwracania prostokąta ograniczającego obiektów wizualnych. Prostokąt ograniczający obiektu wizualnego można zwrócić, <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>wywołując program . Prostokąt ograniczający wszystkich elementów podrzędnych obiektu wizualnego, w tym samego obiektu <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>wizualnego, można zwrócić, wywołując program . Poniższy kod pokazuje, jak można obliczyć prostokąt ograniczający obiektu wizualnego i wszystkie jego elementy podrzędne.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Test trafienia w warstwie Visual](hit-testing-in-the-visual-layer.md)
- [Użycie obiektów DrawingVisual](using-drawingvisual-objects.md)
- [Samouczek: hosting obiektów wizualnych w aplikacji Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optymalizacja wydajności aplikacji WPF](../advanced/optimizing-wpf-application-performance.md)
