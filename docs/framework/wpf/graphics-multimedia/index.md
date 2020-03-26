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
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112040"
---
# <a name="graphics-and-multimedia"></a>Grafika i multimedia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zapewnia obsługę multimediów, grafiki wektorowej, animacji i kompozycji zawartości, ułatwiając programistom tworzenie interesujących interfejsów użytkownika i treści. Za pomocą programu Visual Studio można tworzyć grafiki wektorowe lub złożone animacje i integrować multimedia z aplikacjami.

W tym temacie przedstawiono funkcje grafiki, animacji i multimediów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]które umożliwiają dodawanie grafiki, efektów przejścia, dźwięku i wideo do aplikacji.

> [!NOTE]
> Za pomocą WPF typów w usłudze systemu Windows jest zdecydowanie odradzane. Jeśli spróbujesz użyć typów WPF w usłudze systemu Windows, usługa może nie działać zgodnie z oczekiwaniami.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Co nowego w grafice i multimediach w WPF 4

Wprowadzono kilka zmian związanych z grafiką i animacjami.

- Zaokrąglanie układu

  Gdy krawędź obiektu spadnie na środku urządzenia pikselowego, niezależny od DPI system graficzny może tworzyć artefakty renderowania, takie jak rozmyte lub półprzezroczyste krawędzie. Poprzednie wersje WPF zawiera przyciąganie pikseli, aby pomóc w obsłudze tej sprawy. Program Silverlight 2 wprowadził zaokrąglanie układu, które jest kolejnym sposobem przenoszenia elementów, tak aby krawędzie spadały na granice całych pikseli. WPF WPF obsługuje teraz <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> zaokrąglanie układu z dołączoną właściwością na <xref:System.Windows.FrameworkElement>.

- Kompozycja buforowana

  Za pomocą <xref:System.Windows.Media.BitmapCache> nowych <xref:System.Windows.Media.BitmapCacheBrush> i klas, można buforować złożoną część drzewa wizualnego jako mapy bitowej i znacznie poprawić czas renderowania. Mapa bitowa pozostaje wrażliwa na dane wejściowe użytkownika, takie jak kliknięcia myszą, i można ją malować na inne elementy, tak jak każdy pędzel.

- Obsługa modułu cieniującego pikseli 3

  WPF 4 opiera się <xref:System.Windows.Media.Effects.ShaderEffect> na podstawie pomocy technicznej wprowadzonej w WPF 3.5 SP1, umożliwiając aplikacjom do zapisu efektów przy użyciu Pixel Shader (PS) w wersji 3.0. Model modułu cieniującego PS 3.0 jest bardziej zaawansowany niż PS 2.0, co pozwala na jeszcze większy wpływ na obsługiwany sprzęt.

- Zwalnianie funkcji

  Animacje można ulepszać za pomocą funkcji dynamiki, które zapewniają dodatkową kontrolę nad zachowaniem animacji. Na przykład można zastosować <xref:System.Windows.Media.Animation.ElasticEase> do animacji, aby nadać animacji sprężyste zachowanie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.Animation> typy dynamiki w obszarze nazw.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Grafika i renderowanie

WPF WPF obejmuje obsługę wysokiej jakości grafiki 2D. Funkcja obejmuje pędzle, geometrie, obrazy, kształty i przekształcenia. Aby uzyskać więcej informacji, zobacz [Grafika](graphics.md). Renderowanie elementów graficznych opiera <xref:System.Windows.Media.Visual> się na klasie. Struktura obiektów wizualnych na ekranie jest opisana przez drzewo wizualne. Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>Kształty 2D

WPF WPF udostępnia bibliotekę powszechnie używanych, wektorowych kształtów 2D, takich jak prostokąty i elipsy, które pokazano na poniższej ilustracji.

![Diagram przedstawiający elipsy i prostokąty.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Te wewnętrzne kształty WPF są nie tylko kształty: są one programowalne elementy, które implementują wiele funkcji, których oczekujesz od większości typowych formantów, które obejmują klawiatury i myszy. W poniższym przykładzie <xref:System.Windows.UIElement.MouseUp> pokazano, jak obsługiwać zdarzenie wywoływane przez kliknięcie <xref:System.Windows.Shapes.Ellipse> elementu.

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

Na poniższej ilustracji przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dane wyjściowe dla poprzedniego znaczników i związanych z kodem.

![Okno komunikatu z napisem "Kliknąłeś elipsę!"](./media/index/messagebox-text-output.png)

Aby uzyskać więcej informacji, zobacz [Kształty i rysunek podstawowy w przeglądzie WPF](shapes-and-basic-drawing-in-wpf-overview.md). Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład elementów kształtu](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>Geometrie 2D

Gdy kształty 2D, które zapewnia WPF nie są wystarczające, można użyć WPF obsługi geometrii i ścieżek do tworzenia własnych. Na poniższej ilustracji pokazano, jak można używać geometrii do tworzenia kształtów jako pędzla rysunku i do przycinania innych elementów WPF.

![Zrzut ekranu przedstawiający sposób tworzenia kształtów za pomocą geometrii.](./media/index/use-geometries-create-shapes.png)

Aby uzyskać więcej informacji, zobacz [Omówienie geometrii](geometry-overview.md). Aby zapoznać się z próbką wprowadzającą, zobacz [Przykład geometrii](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>Efekty 2D

WPF WPF udostępnia bibliotekę klas 2D, których można użyć do tworzenia różnych efektów. Funkcja renderowania 2D WPF WPF umożliwia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] malowanie elementów, które mają gradienty, mapy bitowe, rysunki i klipy wideo; i manipulować nimi za pomocą obrotu, skalowania i pochylania. Poniższa ilustracja podaje przykład wielu efektów, które można osiągnąć przy użyciu pędzli WPF.

![Ilustracja przedstawiająca różne pędzle WPF i elementy malowania.](./media/index/brushes-paint-elements.png)

Aby uzyskać więcej informacji, zobacz [WPF Brushes Overview](wpf-brushes-overview.md). Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>Renderowanie 3D

WPF WPF zapewnia zestaw możliwości renderowania 3D, które integrują się z obsługą grafiki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]2D w WPF w celu utworzenia bardziej ekscytującego układu i wizualizacji danych. Na jednym końcu spektrum WPF WPF umożliwia renderowanie obrazów 2D na powierzchniach kształtów 3D, co pokazuje poniższa ilustracja.

![Zrzut ekranu przedstawiający przykład przedstawiający kształty 3D o różnych teksturach.](./media/index/visual-three-dimensional-shape.png)

Aby uzyskać więcej informacji, zobacz [Omówienie grafiki 3D](3-d-graphics-overview.md). Aby zapoznać się z przykładem wprowadzającym, zobacz [Przykład bryły 3D](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animacja

Użyj animacji, aby formanty i elementy rosły, wstrząsały, obracały się i zanikały; i tworzyć ciekawe przejścia stron i nie tylko. Ponieważ WPF umożliwia animowanie większości właściwości, nie tylko można animować większość obiektów WPF, można również użyć WPF do animowania obiektów niestandardowych, które tworzysz.

![Zrzut ekranu animowanego sześcianu.](./media/index/animate-custom-objects.png)

Aby uzyskać więcej informacji, zobacz [Omówienie animacji](animation-overview.md). Aby zapoznać się z przykładem wprowadzającym, zobacz [Galeria przykładów animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Multimedia

Obrazy, wideo i audio to bogate w multimedia sposoby przekazywania informacji i doświadczeń użytkowników.

### <a name="images"></a>Obrazy

Obrazy, które zawierają ikony, tła, a nawet części animacji, są podstawową częścią większości aplikacji. Ponieważ często trzeba używać obrazów, WPF udostępnia możliwość pracy z nimi na różne sposoby. Na poniższej ilustracji przedstawiono tylko jeden z tych sposobów.

![Przykładowy zrzut ekranu przedstawiający styl](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Aby uzyskać więcej informacji, zobacz [Omówienie obrazowania](imaging-overview.md).

### <a name="video-and-audio"></a>Wideo i audio

Podstawową cechą możliwości grafiki WPF jest zapewnienie natywnej obsługi pracy z multimediami, która obejmuje wideo i audio. W poniższym przykładzie pokazano, jak wstawić odtwarzacz multimedialny do aplikacji.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>jest w stanie odtwarzać zarówno wideo, jak i audio i jest wystarczająco rozszerzalny, aby umożliwić łatwe tworzenie niestandardowych interfejsów użytkownika.

Aby uzyskać więcej informacji, zobacz [Przegląd multimediów](multimedia-overview.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Animacja i chronometraż Tematy porad](animation-and-timing-how-to-topics.md)
- [Omówienie grafiki 3D](3-d-graphics-overview.md)
- [Multimedia — przegląd](multimedia-overview.md)
