---
title: Grafika i multimedia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 150b742c2195c07abf2b2823871627b0ba827580
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919995"
---
# <a name="graphics-and-multimedia"></a>Grafika i multimedia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, ułatwiając deweloperom tworzenie interesujących interfejsów użytkownika i zawartości. Za pomocą programu Visual Studio można tworzyć grafiki wektorowe lub złożone animacje oraz integrować multimedia z aplikacjami.

W tym temacie przedstawiono funkcje grafiki, animacji i multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.

> [!NOTE]
> Korzystanie z typów WPF w usłudze systemu Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie zadziałała zgodnie z oczekiwaniami.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Nowości dotyczące grafiki i multimediów w WPF 4

Wprowadzono kilka zmian dotyczących grafiki i animacji.

- Zaokrąglenie układu

  Gdy brzeg obiektu znajduje się w środku urządzenia pikselowego, niezależny od DPI system grafiki może tworzyć artefakty renderowania, takie jak rozmyte lub częściowo przezroczyste krawędzie. Poprzednie wersje WPF obejmowały przyciąganie pikseli do obsługi tego przypadku. Program Silverlight 2 wprowadził zaokrąglenie układu, który jest innym sposobem przenoszenia elementów tak, aby krawędzie mieściły się w całej krawędzi pikseli. Funkcja WPF obsługuje teraz zaokrąglanie układu z właściwością dołączone <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> w <xref:System.Windows.FrameworkElement>.

- Buforowana kompozycja

  Korzystając z nowych klas <xref:System.Windows.Media.BitmapCache> i <xref:System.Windows.Media.BitmapCacheBrush>, można buforować złożoną część drzewa wizualnego jako mapę bitową i znacznie poprawić czas renderowania. Mapa bitowa pozostaje niezależna od danych wejściowych użytkownika, takich jak kliknięcia myszą i można ją malować na innych elementach, podobnie jak w przypadku dowolnego pędzla.

- Obsługa programów do cieniowania pikseli 3

  Program WPF 4 jest oparty na <xref:System.Windows.Media.Effects.ShaderEffect> pomocy technicznej wprowadzonej w programie WPF 3,5 z dodatkiem SP1, umożliwiając aplikacjom pisanie efektów przy użyciu programu Pixel Shader (PS) w wersji 3,0. Model cieniowania PS 3,0 jest bardziej zaawansowany niż PS 2,0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.

- Zwalnianie funkcji

  Możesz wzbogacić animacje za pomocą funkcji, które zapewniają dodatkową kontrolę nad zachowaniem animacji. Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji zachowanie sprężynowe. Aby uzyskać więcej informacji, zobacz Typy krzywych napięcia w przestrzeni nazw <xref:System.Windows.Media.Animation>.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafika i renderowanie

WPF obejmuje obsługę grafiki 2-D o wysokiej jakości. Funkcje obejmują pędzle, geometrie, obrazy, kształty i przekształcenia. Aby uzyskać więcej informacji, zobacz [grafika](graphics.md). Renderowanie elementów graficznych opiera się na klasie <xref:System.Windows.Media.Visual>. Struktura obiektów wizualizacji na ekranie jest opisana przez drzewo wizualne. Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).

### <a name="2-d-shapes"></a>Kształty 2-D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia bibliotekę często używanych, rysowanych w wektorach kształtów 2-D, takich jak prostokąty i wielokropek, które przedstawiono na poniższej ilustracji.

![Diagram przedstawiający wielokropek i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Te wewnętrzne [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kształty nie są tylko kształtami: są to elementy programowalne, które implementują wiele funkcji, których oczekujesz od najbardziej typowych kontrolek, które obejmują wprowadzanie klawiatury i myszy. Poniższy przykład pokazuje, jak obsłużyć zdarzenie <xref:System.Windows.UIElement.MouseUp> wywoływane przez kliknięcie elementu <xref:System.Windows.Shapes.Ellipse>.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

Na poniższej ilustracji przedstawiono dane wyjściowe dla poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] znaczników i kodu.

![Okno komunikatu z informacją "kliknięto elipsę!"](./media/index/messagebox-text-output.png)

Aby uzyskać więcej informacji, zobacz temat [kształty i podstawowe Rysowanie w programie WPF — Omówienie](shapes-and-basic-drawing-in-wpf-overview.md). Aby zapoznać się z przykładem wstępnym, zobacz [element Shape Samples](https://go.microsoft.com/fwlink/?LinkID=160037).

### <a name="2-d-geometries"></a>Geometrie 2-D

Gdy kształty 2-D, które [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zapewniają, nie są wystarczające, można użyć obsługi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dla geometrie i ścieżek, aby utworzyć własne. Na poniższej ilustracji przedstawiono, jak można użyć geometrie do tworzenia kształtów, jako pędzla rysowania i obcinania innych [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementów.

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrie.](./media/index/use-geometries-create-shapes.png)

Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md). Aby zapoznać się z przykładem wstępnym, zobacz [przykład geometrie](https://go.microsoft.com/fwlink/?LinkID=159989).

### <a name="2-d-effects"></a>Efekty 2-D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia bibliotekę klas 2-D, których można użyć do tworzenia rozmaitych efektów. Możliwość renderowania 2-D [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów, które mają gradienty, mapy bitowe, rysunki i wideo. i do manipulowania nimi przy użyciu rotacji, skalowania i skośności. Na poniższej ilustracji przedstawiono przykład wielu efektów, które można osiągnąć przy użyciu pędzli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].

![Ilustracja przedstawiająca różne pędzle WPF i elementy programu Paint.](./media/index/brushes-paint-elements.png)

Aby uzyskać więcej informacji, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md). Aby zapoznać się z przykładem wstępnym, zobacz [przykłady pędzli](https://go.microsoft.com/fwlink/?LinkID=159973).

<a name="rendering"></a>

## <a name="3-d-rendering"></a>Renderowanie 3-D

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] udostępnia zestaw funkcji renderowania trójwymiarowych, które integrują się z obsługą grafiki 2-D w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], aby można było tworzyć bardziej atrakcyjne wizualizacje układu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]i danych. Na jednym końcu spektrum [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umożliwia renderowanie obrazów 2-D na powierzchni trójwymiarowych kształtów, które przedstawiono na poniższej ilustracji.

![Zrzut ekranu przedstawiający przykład pokazujący kształty trójwymiarowe z różnymi teksturami.](./media/index/visual-three-dimensional-shape.png)

Aby uzyskać więcej informacji, zobacz temat [Omówienie grafiki trójwymiarowej](3-d-graphics-overview.md). Aby zapoznać się z przykładem wstępnym, zobacz [3-D pełne próbki](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animacja

Używaj animacji, aby tworzyć, wstrząsać, obracać i przerastać elementy. i aby tworzyć interesujące przejścia stron i nie tylko. Ponieważ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pozwala animować większość właściwości, nie tylko można animować większość obiektów [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], można także użyć [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do animowania tworzonych obiektów niestandardowych.

![Zrzut ekranu animowanego modułu.](./media/index/animate-custom-objects.png)

Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md). Aby zapoznać się z przykładem wstępnym, zobacz [Galeria przykładów animacji](https://go.microsoft.com/fwlink/?LinkID=159969).

<a name="media"></a>

## <a name="media"></a>Nośnik

Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i środowiska użytkownika.

### <a name="images"></a>Obrazy

Obrazy, takie jak ikony, tła i nawet części animacji, są podstawową częścią większości aplikacji. Ze względu na to, że często trzeba używać obrazów, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uwidacznia możliwość pracy z nimi na różne sposoby. Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.

![Przykładowy zrzut ekranu z stylem](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia obrazu](imaging-overview.md).

### <a name="video-and-audio"></a>Wideo i audio

Podstawową funkcją możliwości grafiki [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jest zapewnienie natywnej obsługi pracy z multimediami, w tym wideo i audio. Poniższy przykład pokazuje, jak wstawić odtwarzacz multimedialny do aplikacji.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement> jest w stanie odtwarzać wideo i audio, i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.

Aby uzyskać więcej informacji, zobacz [Omówienie multimediów](multimedia-overview.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Animacja i chronometraż — Tematy porad](animation-and-timing-how-to-topics.md)
- [Grafika 3D — przegląd](3-d-graphics-overview.md)
- [Multimedia — przegląd](multimedia-overview.md)
