---
title: "Przegląd Obrazowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7d0a880dd30fe737a1bd4d1368dde16ed0df1e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imaging-overview"></a>Przegląd Obrazowanie
Ten temat zawiera wprowadzenie do [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]Umożliwia deweloperom wyświetlania, przekształcanie i sformatować obrazów.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Składnik obrazowania WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]zawiera znaczące ulepszenia w zakresie możliwości w ramach imaging [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Imaging możliwości, takie jak wyświetlanie mapy bitowej lub przy użyciu obrazu na formantu wspólnego zostały wcześniej zależne od [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] lub [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] biblioteki. Te [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] określenie bazowej funkcje obsługi obrazów, ale brak funkcje, takie jak obsługa rozszerzalność kodera-dekodera i o wysokiej wierności obsługi obrazów. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]zaprojektowano w celu rozwiązać niedociągnięć [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] i [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] i podaj nowy zestaw [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] do wyświetlanie i używanie obrazów w aplikacjach.  
  
 Istnieją dwa sposoby [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], zarządzane i niezarządzane składnik. Niezarządzane składnik zapewnia następujące funkcje.  
  
-   Modelu rozszerzeń formaty obrazu nowych lub zastrzeżonych.  
  
-   Zwiększona wydajność i zabezpieczenia w formatach obrazu macierzystego w tym [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)], a ikona (.ico).  
  
-   Zachowania danych wysokiej obrazu głębią bitową maksymalnie 8 bitów na kanał (32 bity na piksel).  
  
-   Skalowanie obrazu bezpieczna, przycinanie i obrotów.  
  
-   Uproszczone zarządzanie kolorami.  
  
-   Obsługa metadanych w pliku, zastrzeżonych.  
  
-   Niezarządzane infrastruktury, aby zapewnić bezproblemową integrację obrazów z innymi korzysta z zarządzanego składnika [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] funkcje, takie jak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animacji i grafiki. Zarządzanego składnika również korzysta z [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] obrazowania modelu rozszerzalności koder-dekoder, co umożliwia automatyczne rozpoznawanie nowy obraz formaty w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 Większość zarządzanej [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] znajdują się w <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> przestrzeni nazw, chociaż niektóre ważne typy, takich jak <xref:System.Windows.Media.ImageBrush> i <xref:System.Windows.Media.ImageDrawing> znajdują się w <xref:System.Windows.Media?displayProperty=nameWithType> przestrzeni nazw i <xref:System.Windows.Controls.Image> znajduje się w <xref:System.Windows.Controls?displayProperty=nameWithType> przestrzeni nazw.  
  
 Ten temat zawiera dodatkowe informacje na temat zarządzanego składnika. Aby uzyskać więcej informacji na temat niezarządzanej [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] zobacz [niezarządzane WPF Imaging Component](https://msdn.microsoft.com/library/ee719902.aspx) dokumentacji.  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formaty obrazu WPF  
 Koder-dekoder służy do zdekodowania lub format nośników kodowania. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]obejmuje kodera-dekodera dla [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)], a IKONA formaty obrazów. Każdy z tych koderów-dekoderów umożliwiają aplikacjom dekodowania i, z wyjątkiem IKONY, kodowanie ich formaty odpowiedniego obrazu.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>Klasa ważne jest używany podczas dekodowania i kodowanie obrazów. Jest podstawowym blokiem konstrukcyjnym [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] potoku i reprezentuje zestaw jednej, stałej pikseli w niektórych rozmiarze i rozdzielczości. A <xref:System.Windows.Media.Imaging.BitmapSource> może być pojedynczej ramki wielu obrazu ramki lub może być wynik transformacji wykonywane na <xref:System.Windows.Media.Imaging.BitmapSource>. Jest on nadrzędny wielu z klasy podstawowej, stosowane w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] imaging, takich jak <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> służy do przechowywania danych rzeczywistych mapy bitowej format obrazu. Wiele formatów obrazów obsługuje tylko jeden <xref:System.Windows.Media.Imaging.BitmapFrame>, mimo że takich jak formaty [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] i [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obsługuje wiele ramek na obrazie. Ramki są używane przez dekodery jako dane wejściowe i są przekazywane do koderów, aby utworzyć pliki obrazów.  
  
 W poniższym przykładzie pokazano sposób <xref:System.Windows.Media.Imaging.BitmapFrame> jest tworzona na podstawie <xref:System.Windows.Media.Imaging.BitmapSource> , a następnie dodać do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] obrazu.  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekodowanie Format obrazu  
 Dekodowanie obrazu jest translacja format obrazu, aby dane obrazu, które mogą być używane przez system. Następnie można dane obrazu do wyświetlania, proces, lub zakodować w innym formacie. Wybór dekodera jest oparty na format obrazu. Koder-dekoder wybór odbywa się automatycznie, chyba że określono określonych dekodera. Przykłady w [wyświetlanie obrazów na platformie WPF](#_displayingimages) sekcji prezentacja dekodowania automatycznego. Dekodery formatu niestandardowego utworzony przy użyciu niezarządzanych [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] automatycznie zarejestrowany w systemie i interfejsy uczestniczyć w zaznaczeniu dekodera. Dzięki temu niestandardowe formaty mają być wyświetlane automatycznie w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 W poniższym przykładzie pokazano użycie dekodera mapy bitowej zdekodować [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] format obrazu.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kodowanie Format obrazu  
 Kodowanie obrazu jest translacja dane obrazu do formatu określonego obrazu. Dane zakodowane obrazu można następnie służyć do tworzenia nowych plików obrazu. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]udostępnia koderów dla każdego z formatów obrazów opisane powyżej.  
  
 W poniższym przykładzie pokazano użycie kodera, aby zapisać nowo utworzony bitmapy.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Wyświetlanie obrazów na platformie WPF  
 Istnieje kilka sposobów, aby wyświetlić obraz w [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji. Obrazy mogą być wyświetlane przy użyciu <xref:System.Windows.Controls.Image> kontroli rysowane przy użyciu visual <xref:System.Windows.Media.ImageBrush>, lub rysowane przy użyciu <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Używanie formantu obrazu  
 <xref:System.Windows.Controls.Image>jest elementem framework i głównej sposób wyświetlania obrazów w aplikacjach. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> mogą być używane w dwa sposoby; Składnia atrybutu lub składni właściwości. Poniższy przykład pokazuje, jak by renderować obraz 200 pikseli szerokości, używając składni atrybutu i składni tagów właściwości. Aby uzyskać więcej informacji o składni atrybutu i składni właściwości, zobacz [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Większość przykładów użycia <xref:System.Windows.Media.Imaging.BitmapImage> obiekt, aby odwołać plik obrazu. <xref:System.Windows.Media.Imaging.BitmapImage>jest specjalistycznej <xref:System.Windows.Media.Imaging.BitmapSource> który jest zoptymalizowana pod kątem [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ładowanie i łatwy sposób na wyświetlanie obrazów jako <xref:System.Windows.Controls.Image.Source%2A> z <xref:System.Windows.Controls.Image> formantu.  
  
 Poniższy przykład przedstawia sposób renderowania obrazu 200 pikseli szerokości, przy użyciu kodu.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>implementuje <xref:System.ComponentModel.ISupportInitialize> interfejsu w celu zoptymalizowania inicjowania na wiele właściwości. Zmiany właściwości mogą występować tylko podczas inicjowania obiektu. Wywołanie <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> sygnalizują, że Inicjowanie zostało uruchomione i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> sygnalizują, że Inicjowanie zostało zakończone. Po zainicjowany, zmiany właściwości są ignorowane.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Obracanie, konwersja i przycinanie obrazów  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Umożliwia użytkownikom Przekształcanie obrazów za pomocą właściwości <xref:System.Windows.Media.Imaging.BitmapImage> lub za pomocą dodatkowych <xref:System.Windows.Media.Imaging.BitmapSource> obiekty, takie jak <xref:System.Windows.Media.Imaging.CroppedBitmap> lub <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Przekształcenia te obrazu można skalować obracanie obrazów, Zmień format piksela obrazu lub Przytnij obraz.  
  
 Obraz obrotów są wykonywane przy użyciu <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapImage>. Obrotów jest możliwe tylko o 90 stopni. W poniższym przykładzie obraz jest obracany o 90 stopni.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Konwertowanie obrazu do formatu piksela różnych, takie jak skali szarości jest wykonywane przy użyciu <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. W poniższych przykładach, obraz jest konwertowana na <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Aby przyciąć obraz, albo <xref:System.Windows.UIElement.Clip%2A> właściwość <xref:System.Windows.Controls.Image> lub <xref:System.Windows.Media.Imaging.CroppedBitmap> mogą być używane. Zwykle, jeśli właśnie mają być wyświetlane część obrazu <xref:System.Windows.UIElement.Clip%2A> powinien być używany. Jeśli potrzebujesz do zakodowania i zapisania przycięty obraz, <xref:System.Windows.Media.Imaging.CroppedBitmap> powinien być używany. W poniższym przykładzie, obraz jest przycięty przy użyciu właściwości Clip <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Rozciąganie obrazów  
 <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość określa, jak obraz jest rozciągany tak, aby wypełnić jego kontenera. <xref:System.Windows.Controls.Image.Stretch%2A> Właściwość przyjmuje następujące wartości zdefiniowane przez <xref:System.Windows.Media.Stretch> wyliczenie:  
  
-   <xref:System.Windows.Media.Stretch.None>: Obraz nie jest rozciągany tak, aby wypełnił obszar danych wyjściowych. Jeśli obraz jest większy niż obszar wyjściowy, obraz jest rysowane do obszaru wyjściowego wycinka, co nie pasuje.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: Obraz jest skalowane w celu dopasowania do obszaru wyjściowego. Ponieważ szerokość i wysokość obrazu są skalowane niezależnie, jego oryginalny współczynnik proporcji obrazu mogą nie zostać zachowane. Oznacza to, że obraz może wypaczenia aby wypełnić kontenera danych wyjściowych.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>Obraz skalowania, aby całkowicie mieści się w obszarze danych wyjściowych. Współczynnik proporcji obrazu są zachowywane.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: Obraz jest skalowana, tak aby całkowicie wypełnia obszaru wyjściowego przy zachowaniu oryginalny współczynnik proporcji obrazu.  
  
 Poniższy przykład dotyczy każdego z dostępnych <xref:System.Windows.Media.Stretch> wyliczenia do <xref:System.Windows.Controls.Image>.  
  
 Poniższa ilustracja przedstawia dane wyjściowe z przykładu i prezentuje działanie wpływ różne <xref:System.Windows.Controls.Image.Stretch%2A> ustawienia mają podczas zastosowany do obrazu.  
  
 ![Różne ustawienia TileBrush Stretch](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Różne ustawienia stretch  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malowanie obrazów  
 Obrazy mogą być także wyświetlane w aplikacji przez malowanie <xref:System.Windows.Media.Brush>. Pędzle umożliwiają malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiekty o nic proste, pełne kolory do złożonych zestawów wzorców i obrazów. Aby malować obrazów, należy użyć <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.ImageBrush> Jest typem <xref:System.Windows.Media.TileBrush> definiuje zawartość jako obraz mapy bitowej. <xref:System.Windows.Media.ImageBrush> Wyświetla pojedynczego obrazu, który jest określony przez jego <xref:System.Windows.Media.ImageBrush.ImageSource%2A> właściwości. Można kontrolować sposób obraz jest rozciągany tak, wyrównany i sąsiadującym, dzięki któremu można zapobiec zakłócenia i wzorce i innych skutków. Na poniższej ilustracji przedstawiono niektóre efekty, które mogą zostać osiągnięty przy <xref:System.Windows.Media.ImageBrush>.  
  
 ![Przykładowe dane wyjściowe ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Kształty, kontrolek, tekst i wpisać pędzle obrazu  
  
 W poniższym przykładzie pokazano, jak namalować tła przycisku przy użyciu obrazu <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Aby uzyskać dodatkowe informacje o <xref:System.Windows.Media.ImageBrush> i malowanie obrazów, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Metadanych obrazu  
 Niektóre pliki obrazów zawierać metadane opisujące zawartość i właściwości pliku. Na przykład większość cyfrowe aparaty fotograficzne tworzenia obrazów, które zawierają metadane dotyczące producenta i modelu aparatu służące do przechwytywania obrazu. Każdy format obrazu obsługuje metadanych w inny sposób, ale [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] zapewnia jednolity sposób przechowywania i pobierania metadanych dla każdego obsługiwanym formacie obrazu.  
  
 Dostęp do metadanych jest zapewniana za pomocą <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> właściwość <xref:System.Windows.Media.Imaging.BitmapSource> obiektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>Zwraca <xref:System.Windows.Media.Imaging.BitmapMetadata> obiekt, który zawiera wszystkie metadane zawarty w obrazie. Dane te mogą się w jeden schemat metadanych lub kombinację różnych systemów. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]obsługuje następujących schematów metadanych obrazu: [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tekst (danych tekstowych PNG), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], i [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Aby uprościć proces odczytu metadanych, <xref:System.Windows.Media.Imaging.BitmapMetadata> udostępnia kilka nazwane właściwości, które są łatwo dostępne takie jak <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, i <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Wiele z tych nazwane właściwości mogą służyć do zapisywania metadanych. Dodatkowe Obsługa odczytu metadanych jest zapewniana przez czytnik zapytania metadanych. <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> — Metoda służy do pobierania metadanych czytnik zapytania podając ciąg zapytania, takich jak *"/ app1/exif /"*. W poniższym przykładzie <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> służy do uzyskiwania tekstu przechowywanego w *"/ tekstu/opis"* lokalizacji.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Aby napisać metadanych, Edytor zapytań metadanych jest używany. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Pobiera moduł zapisujący zapytania i ustawia żądaną wartość. W poniższym przykładzie <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> służy do pisania tekstu w *"/ tekstu/opis"* lokalizacji.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Rozszerzalność kodera-dekodera  
 Funkcja core [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] jest modelu rozszerzalności dla nowego kodeki obrazów. Te interfejsy niezarządzane umożliwiają deweloperom koder-dekoder integracji koderów-dekoderów z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dzięki nowej formatów obrazów automatycznie mogą być używane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
 Przykładowe rozszerzalności [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], zobacz [Win32 próbki koder-dekoder](http://go.microsoft.com/fwlink/?LinkID=160052). W tym przykładzie pokazano, jak utworzyć dekodera i koder formatu niestandardowego obrazu.  
  
> [!NOTE]
>  Koder-dekoder muszą być podpisane cyfrowo na jego zidentyfikowanie przez system.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Imaging.BitmapSource>  
 <xref:System.Windows.Media.Imaging.BitmapImage>  
 <xref:System.Windows.Controls.Image>  
 <xref:System.Windows.Media.Imaging.BitmapMetadata>  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Koder-dekoder Win32 próbki](http://go.microsoft.com/fwlink/?LinkID=160052)
