---
title: Przegląd Obrazowanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: dba2f8b07134560abd77832293ce2a81e55e4875
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209713"
---
# <a name="imaging-overview"></a>Przegląd Obrazowanie
Ten temat zawiera wprowadzenie do [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] Umożliwia deweloperom do wyświetlenia, przekształcania i formatowanie obrazów.  

<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Składnik obrazowania WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zapewnia znaczące ulepszenia w zakresie możliwości w ramach imaging [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Tworzenie obrazu funkcji, takich jak wyświetlanie mapy bitowej lub za pomocą obrazu na formancie wspólnego zostały wcześniej zależnej od [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] lub [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] bibliotek. Te [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] oferują funkcje obsługi obrazów linii bazowej, ale brak funkcje, takie jak obsługa kodera-dekodera rozszerzalność i obsługę obrazu o dużej wierności. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zaprojektowano w celu pokonania braków [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] i [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] i podaj nowy zestaw [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] wyświetlić obrazy i używać w aplikacjach.  
  
 Istnieją dwa sposoby dostępu do [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], zarządzane i niezarządzane składnik. Niezarządzane składnik udostępnia następujące funkcje.  
  
-   Model rozszerzalności dla formatów obraz nowe lub chronione prawem własności.  
  
-   Zwiększona wydajność i zabezpieczenia formatów obrazów natywnych w tym [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]i ikony (.ico).  
  
-   Zachowywanie danych wysokiej głębokości bitów obrazu maksymalnie 8 bitów na kanał (32 bity na piksel).  
  
-   Skalowanie obrazów bezpieczne, przycinanie i możliwość wymiany.  
  
-   Uproszczone zarządzanie kolorami.  
  
-   Obsługa metadanych w pliku, zastrzeżonych.  
  
-   Niezarządzane infrastruktury, aby zapewnić bezproblemową integrację obrazów z innymi korzysta z zarządzanego składnika [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcje, takie jak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animacji i grafiki. Składnik zarządzany również korzysta z Windows Presentation Foundation (WPF) obrazowania kodera-dekodera rozszerzalności modelu, który umożliwia automatyczne rozpoznawanie nowych formatów obrazów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 W większości zarządzanej [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] znajdują się w <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> przestrzeni nazw, chociaż kilka ważnych typów, takich jak <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.ImageDrawing> znajdują się w <xref:System.Windows.Media?displayProperty=nameWithType> przestrzeni nazw i <xref:System.Windows.Controls.Image> znajduje się w <xref:System.Windows.Controls?displayProperty=nameWithType> przestrzeni nazw.  
  
 Ten temat zawiera dodatkowe informacje na temat zarządzanego składnika. Aby uzyskać więcej informacji na temat niezarządzaną [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zobacz [niezarządzanych WPF Imaging Component](/windows/desktop/wic/-wic-lh) dokumentacji.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formaty obrazu WPF  
 Koder-dekoder służy do zdekodowania lub zakodować format nośników. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] obejmuje kodera-dekodera dla [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]ikona formaty obrazów. Każda z tych kodery-dekodery umożliwiają aplikacjom dekodowania i, z wyjątkiem IKONY, kodowanie ich formaty odpowiedniego obrazu.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> jest klasą ważne jest używany w dekodowanie i kodowanie obrazów. Jest podstawowym budulcem [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] potoku i reprezentuje zestaw pojedynczego, stała pikseli w niektórych rozmiarze i rozdzielczości. A <xref:System.Windows.Media.Imaging.BitmapSource> może być pojedynczej ramki wielu obraz ramki lub może być wynikiem przekształcenie wykonywane na <xref:System.Windows.Media.Imaging.BitmapSource>. Jest to poziom nadrzędny wielu z klasy podstawowej, używane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] imaging takich jak <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> służy do przechowywania danych mapy bitowej rzeczywisty format obrazu. Wiele formatów obrazów obsługują tylko jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, mimo że formatów, takich jak [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] i [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obsługuje większą liczbę ramek na obrazie. Ramki są używane przez dekodery jako dane wejściowe i są przekazywane do koderów, aby utworzyć pliki obrazów.  
  
 Poniższy przykład pokazuje, jak <xref:System.Windows.Media.Imaging.BitmapFrame> jest tworzona na podstawie <xref:System.Windows.Media.Imaging.BitmapSource> i dodanych do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazu.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekodowanie Format obrazu  
 Dekodowanie obrazu jest translacji na format obrazu z danymi obrazu, które mogą być używane przez system. Następnie można danych obrazu do wyświetlenia, procesu lub zakodować w innym formacie. Wybór dekodera opiera się na format obrazu. Wybieranie kodera-dekodera odbywa się automatycznie, chyba że określono określonych dekodera. W przykładach w [wyświetlanie obrazów w WPF](#_displayingimages) sekcji pokazują, automatyczne dekodowania. Format niestandardowy dekodery opracowanych za pomocą niezarządzanych [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] automatycznie zarejestrowany w systemie i interfejsy uczestniczyć w zaznaczeniu dekodera. Dzięki temu formatów niestandardowych, które mają być wyświetlane automatycznie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 W poniższym przykładzie pokazano użycie dekodera mapy bitowej w celu zdekodowania [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] format obrazu.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kodowanie Format obrazu  
 Kodowanie obrazów jest tłumaczenia danych obrazu do formatu określonego obrazu. Dane zakodowane obrazu, następnie może służyć do tworzenia nowych plików obrazu. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] udostępnia koderów dla wszystkich obrazów w formacie opisanych powyżej.  
  
 Poniższy przykład demonstruje użycie kodera, aby zapisać obraz nowo utworzonej mapy bitowej.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Wyświetlanie obrazów w WPF  
 Istnieje kilka sposobów, aby wyświetlić obraz w aplikacji Windows Presentation Foundation (WPF). Obrazy mogą być wyświetlane za pomocą <xref:System.Windows.Controls.Image> kontrolki rysowane na wizualizacji przy użyciu polecenia <xref:System.Windows.Media.ImageBrush>, lub przy użyciu <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Używanie kontrolki obrazu  
 <xref:System.Windows.Controls.Image> jest elementem framework i podstawowym sposobem na wyświetlanie obrazów w aplikacjach. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> mogą być używane w na dwa sposoby; Składnia atrybutu lub składnia właściwości. Poniższy przykład pokazuje, jak by renderować obraz 200 pikseli przy użyciu składni atrybutów i składnia tagu właściwości. Aby uzyskać więcej informacji na temat składni atrybutów i składnia właściwości, zobacz [Przegląd właściwości zależności](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Wiele przykładów użycia <xref:System.Windows.Media.Imaging.BitmapImage> obiekt, aby odwoływać się do pliku obrazu. <xref:System.Windows.Media.Imaging.BitmapImage> jest to wyspecjalizowana <xref:System.Windows.Media.Imaging.BitmapSource> który jest zoptymalizowany pod kątem [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ładowania i łatwy sposób wyświetlania obrazów jako <xref:System.Windows.Controls.Image.Source%2A> z <xref:System.Windows.Controls.Image> kontroli.  
  
 Poniższy przykład pokazuje, jak renderować obraz 200 pikseli przy użyciu kodu.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> implementuje <xref:System.ComponentModel.ISupportInitialize> interfejsu, aby zoptymalizować inicjowania na wiele właściwości. Zmiany właściwości mogą występować tylko podczas inicjowania obiektu. Wywołaj <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> do sygnalizowania, że Inicjowanie zostało uruchomione i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> do sygnalizowania, że Inicjowanie zostało zakończone. Po zainicjowaniu, zmiany właściwości są ignorowane.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Obracanie, konwersja i przycinanie obrazów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umożliwia użytkownikom Przekształcanie obrazów za pomocą właściwości <xref:System.Windows.Media.Imaging.BitmapImage> lub za pomocą dodatkowych <xref:System.Windows.Media.Imaging.BitmapSource> obiekty, takie jak <xref:System.Windows.Media.Imaging.CroppedBitmap> lub <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Transformacjami obrazu można skalować obrócić obraz, Zmień format pikseli, obrazu lub przyciąć obraz.  
  
 Obraz obroty są wykonywane przy użyciu <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapImage>. Możliwość wymiany jest możliwe wyłącznie o 90 stopni. W poniższym przykładzie obraz jest obracany o 90 stopni.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Konwertowanie obrazu na format pikseli różnych, takie jak to zrobić w skali szarości przy użyciu <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. W poniższych przykładach obrazu jest konwertowany na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Aby przyciąć obraz, albo <xref:System.Windows.UIElement.Clip%2A> właściwość <xref:System.Windows.Controls.Image> lub <xref:System.Windows.Media.Imaging.CroppedBitmap> mogą być używane. Zwykle, jeśli chcesz wyświetlić część obrazu, <xref:System.Windows.UIElement.Clip%2A> powinny być używane. Jeśli potrzebujesz do zakodowania i zapisania przycięty obraz <xref:System.Windows.Media.Imaging.CroppedBitmap> powinny być używane. W poniższym przykładzie obraz jest przycięty, przy użyciu właściwości klipu <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Rozciąganie obrazów  
 <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, jak obraz jest rozciągany tak do wypełnienia jego kontenera. <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość akceptuje następujące wartości, zdefiniowane przez <xref:System.Windows.Media.Stretch> wyliczenia:  
  
-   <xref:System.Windows.Media.Stretch.None>: Obraz, który nie jest rozciągany tak, aby wypełnił obszar danych wyjściowych. Jeśli obraz, który jest większy niż obszar wyjściowy, do obszaru wyjściowego przycinania, co nie mieści się rysowania obrazu.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Obraz, który jest skalowany w celu dopasowania do obszaru wyjściowego. Ponieważ szerokość i wysokość obrazu są skalowane osobno, oryginalnym współczynnik proporcji obrazu mogą nie zostać zachowane. Oznacza to obraz, który może być zniekształcenia Aby całkowicie wypełnić kontenera danych wyjściowych.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: Obraz jest skalowana tak, aby całkowicie mieści się w obszarze danych wyjściowych. Współczynnik proporcji obrazu są zachowywane.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Obraz jest skalowana tak, aby całkowicie wypełnia obszar wyjściowy przy jednoczesnym zachowaniu oryginalny współczynnik proporcji obrazu.  
  
 Następujący przykład dotyczy każdego z dostępnych <xref:System.Windows.Media.Stretch> wyliczenia do <xref:System.Windows.Controls.Image>.  
  
 Poniższa ilustracja przedstawia dane wyjściowe z przykładu i demonstruje wpływają na poszczególne <xref:System.Windows.Controls.Image.Stretch%2A> ustawienia mają podczas zastosowane do obrazu.  
  
 ![Different TileBrush Stretch settings](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Różne ustawienia Stretch Database  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malowanie przy użyciu obrazów  
 Obrazy mogą być także wyświetlane w aplikacji przez malowanie <xref:System.Windows.Media.Brush>. Pędzle umożliwia malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiektów ze wszystkim z proste, pełne kolory do złożonych zestawów wzorców i obrazy. Aby rysować przy użyciu obrazów, użyj <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> Jest typem <xref:System.Windows.Media.TileBrush> definiujący swoją zawartość jako obraz mapy bitowej. <xref:System.Windows.Media.ImageBrush> Wyświetla pojedynczy obraz, który jest określony przez jego <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwości. Można kontrolować, jak obraz jest rozciągany tak, wyrównany i fragmentacji, dzięki któremu można będzie zapobiegać zniekształceniom oraz wzorców i innych skutków. Na poniższej ilustracji przedstawiono niektóre efekty, które można osiągnąć za pomocą <xref:System.Windows.Media.ImageBrush>.  
  
 ![ImageBrush output examples](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Pędzle obrazu można wypełnić kształtów, formantów, tekstu i więcej  
  
 W poniższym przykładzie pokazano, jak namalować tła przycisku przy użyciu obrazów przy użyciu <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Aby uzyskać dodatkowe informacje na temat <xref:System.Windows.Media.ImageBrush> zobaczyć malowanie obrazami [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Image Metadata  
 Niektóre pliki obrazów zawiera metadane opisujące zawartość i właściwości pliku. Na przykład większość cyfrowe aparaty fotograficzne tworzenia obrazów, które zawierają metadane dotyczące producenta i modelu aparatu używane do przechwytywania obrazu. Każdy format obrazu obsługuje metadanych w inny sposób, ale [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zapewnia jednolity sposób przechowywania i pobierania metadanych dla każdego obsługiwanym formacie obrazu.  
  
 Dostęp do metadanych jest oferowana w ramach <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapSource> obiektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> Zwraca <xref:System.Windows.Media.Imaging.BitmapMetadata> obiekt, który zawiera wszystkie metadane, które są zawarte w obrazie. Te dane mogą być w jednym schemacie metadanych lub kombinacji różnych systemów. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] obsługuje następujących schematów metadanych obrazu: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tekst (PNG dane tekstowe), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], i [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Aby uprościć proces odczytu metadanych, <xref:System.Windows.Media.Imaging.BitmapMetadata> udostępnia kilka nazwane właściwości, które są łatwo dostępne takie jak <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, i <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Wiele z tych właściwości o nazwie można również zapisać metadane. Dodatkowa obsługa podczas odczytywania metadanych znajduje się przez czytnik zapytania metadanych. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> Metoda służy do pobierania metadanych czytnik zapytania, podając zapytanie ciągu, takich jak *"/ app1/exif /"*. W poniższym przykładzie <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> służy do uzyskiwania tekstu przechowywanego w *"/ Text/opis"* lokalizacji.  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Aby zapisać metadane, Edytor zapytań metadanych jest używany. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> Pobiera moduł zapisujący zapytania i ustawia żądaną wartość. W poniższym przykładzie <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> używany do zapisywania tekstu, przechowywane w *"/ Text/opis"* lokalizacji.  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Rozszerzalność kodera-dekodera  
 Funkcja core [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] modelu rozszerzalności dla nowych kodeki obrazów. Te niezarządzane interfejsy umożliwiają deweloperom kodera-dekodera integracja koderów-dekoderów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dzięki nowej formatów obrazów automatycznie mogą być używane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 Przykładowe możliwości rozszerzania [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], zobacz [kodera-dekodera Win32 przykładowe](https://go.microsoft.com/fwlink/?LinkID=160052). W tym przykładzie pokazano, jak utworzyć dekodera i koder formatu obrazu niestandardowego.  
  
> [!NOTE]
>  Koder-dekoder musi być podpisany cyfrowo dla systemu, aby można było go rozpoznać.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Koder-dekoder Win32 próbki](https://go.microsoft.com/fwlink/?LinkID=160052)
