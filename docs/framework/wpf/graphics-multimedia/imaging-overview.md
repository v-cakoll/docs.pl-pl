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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186694"
---
# <a name="imaging-overview"></a>Przegląd Obrazowanie
Ten temat zawiera wprowadzenie do składnika microsoft Windows Presentation Foundation Imaging Component. WPF Imaging umożliwia deweloperom wyświetlanie, przekształcanie i formatowanie obrazów.  

## <a name="wpf-imaging-component"></a>Składnik obrazowania WPF  
 Program WPF Imaging zapewnia znaczące ulepszenia w zakresie możliwości przetwarzania obrazu w systemie Microsoft Windows. Funkcje obrazowania, takie jak wyświetlanie mapy bitowej lub używanie obrazu na wspólnej formancie, były wcześniej zależne od bibliotek interfejsu GDI (Microsoft Windows Graphics Device Interface) lub Microsoft Windows GDI+. Te interfejsy API zapewniają podstawowe funkcje obrazowania, ale brakuje funkcji, takich jak obsługa rozszerzalności kodeka i obsługa obrazu wysokiej wierności. WPF Imaging został zaprojektowany, aby przezwyciężyć niedociągnięcia GDI i GDI + i zapewnić nowy zestaw interfejsu API do wyświetlania i używania obrazów w aplikacjach.  
  
 Istnieją dwa sposoby dostępu do interfejsu API przetwarzania obrazu WPF, składnik zarządzany i składnik niezarządzane. Składnik niezarządzane zawiera następujące funkcje.  
  
- Model rozszerzalności dla nowych lub zastrzeżonych formatów obrazu.  
  
- Zwiększona wydajność i bezpieczeństwo w natywnych formatach obrazu, w tym bitmapowych (BMP), Joint Photographics Experts Group (JPEG), Portable Network Graphics (PNG), Tagged Image File Format (TIFF), Microsoft Windows Media Photo, Graphics Interchange Format (GIF), i ikona (.ico).  
  
- Zachowanie danych obrazu o wysokiej głębi bitowej do 8 bitów na kanał (32 bity na piksel).  
  
- Nieniszczące skalowanie obrazu, przycinanie i obroty.  
  
- Uproszczone zarządzanie kolorami.  
  
- Obsługa metadanych w pliku, zastrzeżonych.  
  
- Składnik zarządzany wykorzystuje niezarządzaną infrastrukturę, aby zapewnić bezproblemową integrację obrazów z innymi funkcjami WPF, takimi jak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]animacja i grafika. Zarządzany składnik korzysta również z modelu rozszerzalności kodeka obrazu Windows Presentation Foundation (WPF), który umożliwia automatyczne rozpoznawanie nowych formatów obrazów w aplikacjach WPF.  
  
 Większość zarządzanego interfejsu API przetwarzania obrazu <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> WPF znajduje się w obszarze <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageDrawing> nazw, chociaż <xref:System.Windows.Media?displayProperty=nameWithType> kilka <xref:System.Windows.Controls.Image> ważnych typów, <xref:System.Windows.Controls?displayProperty=nameWithType> takich jak i znajdują się w obszarze nazw i znajduje się w obszarze nazw.  
  
 Ten temat zawiera dodatkowe informacje na temat składnika zarządzanego. Aby uzyskać więcej informacji na temat niezarządzanego interfejsu API, zobacz dokumentację [składnika unmanaged WPF Imaging Component.](/windows/desktop/wic/-wic-lh)  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>Formaty obrazów WPF  

 Koder-dekoder służy do dekodowania lub kodowania określonego formatu nośnika. Program WPF Imaging zawiera kodek dla formatów obrazów BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF i ICON. Każdy z tych kodeków umożliwia aplikacjom dekodowanie i, z wyjątkiem ICON, kodowanie ich odpowiednich formatów obrazu.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>jest ważną klasą używaną w dekodowaniu i kodowaniu obrazów. Jest podstawowym budulcem potoku WPF Imaging i reprezentuje pojedynczy, stały zestaw pikseli w określonym rozmiarze i rozdzielczości. A <xref:System.Windows.Media.Imaging.BitmapSource> może być pojedynczą ramką obrazu z wieloma ramkami lub może <xref:System.Windows.Media.Imaging.BitmapSource>być wynikiem przekształcenia wykonywanego na pliku . Jest to element nadrzędny wielu klas podstawowych używanych w obrazowaniu WPF, takich jak <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> służy do przechowywania rzeczywistych danych bitmapowych formatu obrazu. Wiele formatów obrazów obsługuje <xref:System.Windows.Media.Imaging.BitmapFrame>tylko jeden , chociaż formaty takie jak GIF i TIFF obsługują wiele klatek na obraz. Ramki są używane przez dekodery jako dane wejściowe i są przekazywane do koderów do tworzenia plików obrazów.  
  
 W poniższym <xref:System.Windows.Media.Imaging.BitmapFrame> przykładzie pokazano, <xref:System.Windows.Media.Imaging.BitmapSource> jak jest tworzony z a, a następnie dodaje się do obrazu TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Dekodowanie formatu obrazu  
 Dekodowanie obrazu to tłumaczenie formatu obrazu na dane obrazu, które mogą być używane przez system. Dane obrazu mogą być następnie używane do wyświetlania, przetwarzania lub kodowania w innym formacie. Wybór dekodera jest oparty na formacie obrazu. Wybór kodeka jest automatyczny, chyba że określono określony dekoder. Przykłady w [wyświetlania obrazów w WPF](#_displayingimages) sekcji zademonstrują automatyczne dekodowanie. Dekodery formatów niestandardowych opracowane przy użyciu niezarządzanych interfejsów WPF Imaging i zarejestrowane w systemie automatycznie uczestniczą w wyborze dekodera. Dzięki temu formaty niestandardowe mają być wyświetlane automatycznie w aplikacjach WPF.  
  
 W poniższym przykładzie pokazano użycie dekodera bitmapowego do dekodowania obrazu formatu BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Kodowanie formatu obrazu  
 Kodowanie obrazu to translacja danych obrazu do określonego formatu obrazu. Zakodowane dane obrazu mogą być następnie używane do tworzenia nowych plików obrazów. WPF Imaging zapewnia kodery dla każdego z formatów obrazu opisanych powyżej.  
  
 W poniższym przykładzie pokazano użycie kodera do zapisania nowo utworzonego obrazu mapy bitowej.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>Wyświetlanie obrazów w wyw.  
 Istnieje kilka sposobów wyświetlania obrazu w aplikacji Windows Presentation Foundation (WPF). Obrazy mogą być wyświetlane <xref:System.Windows.Controls.Image> za pomocą formantu, <xref:System.Windows.Media.ImageBrush>malowane na <xref:System.Windows.Media.ImageDrawing>wizualizacji za pomocą , lub rysowane za pomocą .  
  
### <a name="using-the-image-control"></a>Korzystanie z kontrolki obrazu  
 <xref:System.Windows.Controls.Image>jest elementem framework i podstawowym sposobem wyświetlania obrazów w aplikacjach. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Image> , mogą być stosowane na dwa sposoby; składni atrybutu lub składni właściwości. W poniższym przykładzie pokazano, jak renderować obraz o szerokości 200 pikseli przy użyciu składni atrybutów i składni tagu właściwości. Aby uzyskać więcej informacji na temat składni atrybutów i składni właściwości, zobacz [Omówienie właściwości zależności](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Wiele przykładów używa <xref:System.Windows.Media.Imaging.BitmapImage> obiektu do odwoływania się do pliku obrazu. <xref:System.Windows.Media.Imaging.BitmapImage>jest <xref:System.Windows.Media.Imaging.BitmapSource> wyspecjalizowanym, który [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jest zoptymalizowany do ładowania i <xref:System.Windows.Controls.Image.Source%2A> jest <xref:System.Windows.Controls.Image> łatwym sposobem wyświetlania obrazów jako formantu.  
  
 W poniższym przykładzie pokazano, jak renderować obraz o szerokości 200 pikseli przy użyciu kodu.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>implementuje <xref:System.ComponentModel.ISupportInitialize> interfejs w celu optymalizacji inicjowania na wielu właściwościach. Zmiany właściwości mogą wystąpić tylko podczas inicjowania obiektu. Zadzwoń, <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> aby zasygnalizować, że rozpoczęła się inicjalizacja i <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> zasygnalizować, że inicjowanie zostało zakończone. Po zainicjowaniu zmiany właściwości są ignorowane.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Obracanie, konwertowanie i przycinanie obrazów  
 WPF WPF umożliwia użytkownikom przekształcanie <xref:System.Windows.Media.Imaging.BitmapImage> obrazów przy <xref:System.Windows.Media.Imaging.BitmapSource> użyciu <xref:System.Windows.Media.Imaging.CroppedBitmap> właściwości <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>lub przy użyciu dodatkowych obiektów, takich jak lub . Te przekształcenia obrazu mogą skalować lub obracać obraz, zmieniać format pikseli obrazu lub przycinać obraz.  
  
 Obroty obrazu są <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> wykonywane <xref:System.Windows.Media.Imaging.BitmapImage>przy użyciu właściwości programu . Obroty mogą być wykonywane tylko w krokach co 90 stopni. W poniższym przykładzie obraz jest obrócony o 90 stopni.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Konwertowanie obrazu na inny format pikseli, <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>taki jak skala szarości, odbywa się za pomocą programu . W poniższych przykładach obraz jest <xref:System.Windows.Media.PixelFormats.Gray4%2A>konwertowany na .  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Aby przyciąć obraz, <xref:System.Windows.UIElement.Clip%2A> właściwość <xref:System.Windows.Controls.Image> <xref:System.Windows.Media.Imaging.CroppedBitmap> lub może być używana. Zazwyczaj, jeśli chcesz tylko wyświetlić część obrazu, <xref:System.Windows.UIElement.Clip%2A> powinny być używane. Jeśli chcesz zakodować i zapisać przycięty <xref:System.Windows.Media.Imaging.CroppedBitmap> obraz, należy go użyć. W poniższym przykładzie obraz jest przycinany <xref:System.Windows.Media.EllipseGeometry>przy użyciu Clip właściwości przy użyciu .  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Rozciąganie obrazów  
 Właściwość <xref:System.Windows.Controls.Image.Stretch%2A> określa, jak obraz jest rozciągnięty, aby wypełnić jego kontener. Właściwość <xref:System.Windows.Controls.Image.Stretch%2A> akceptuje następujące wartości, zdefiniowane przez wyliczenie: <xref:System.Windows.Media.Stretch>  
  
- <xref:System.Windows.Media.Stretch.None>: Obraz nie jest rozciągnięty, aby wypełnić obszar wyjściowy. Jeśli obraz jest większy niż obszar wyjściowy, obraz jest rysowany do obszaru wyjściowego, przycinając to, co nie pasuje.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Obraz jest skalowany w celu dopasowania do obszaru wyjściowego. Ponieważ wysokość i szerokość obrazu są skalowane niezależnie, oryginalny współczynnik proporcji obrazu może nie zostać zachowany. Oznacza to, że obraz może być wypaczony w celu całkowitego wypełnienia kontenera wyjściowego.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Obraz jest skalowany w taki sposób, aby całkowicie mieścił się w obszarze wyjściowym. Współczynnik proporcji obrazu zostanie zachowany.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Obraz jest skalowany w taki sposób, aby całkowicie wypełnił obszar wyjściowy przy zachowaniu oryginalnego współczynnika proporcji obrazu.  
  
 Poniższy przykład stosuje każdy <xref:System.Windows.Media.Stretch> z dostępnych wyliczenia do . <xref:System.Windows.Controls.Image>  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe <xref:System.Windows.Controls.Image.Stretch%2A> z przykładu i pokazuje wpływ różnych ustawień, które zostały zastosowane do obrazu.  
  
 ![Różne ustawienia rozciągania pędzla płytki](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Różne ustawienia rozciągania  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Malowanie obrazami  
 Obrazy mogą być również wyświetlane w aplikacji <xref:System.Windows.Media.Brush>przez malowanie za pomocą pliku . Pędzle umożliwiają malowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] obiektów wszystkim, od prostych, jednolitych kolorów po złożone zestawy wzorów i obrazów. Aby malować obrazami, użyj pliku <xref:System.Windows.Media.ImageBrush>. Jest <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.TileBrush> typem, który definiuje jego zawartość jako obraz bitmapowy. Wyświetla <xref:System.Windows.Media.ImageBrush> pojedynczy obraz, który jest <xref:System.Windows.Media.ImageBrush.ImageSource%2A> określony przez jego właściwości. Można kontrolować sposób rozciągania, wyrównania i sąsiadowania obrazu, co pozwala zapobiegać zniekształceniom i tworzyć wzory i inne efekty. Na poniższej ilustracji przedstawiono pewne <xref:System.Windows.Media.ImageBrush>efekty, które można osiągnąć za pomocą pliku .  
  
 ![Przykłady danych wyjściowych imageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Pędzle obrazów mogą wypełniać kształty, formanty, tekst i inne  
  
 W poniższym przykładzie pokazano, jak malować tło <xref:System.Windows.Media.ImageBrush>przycisku obrazem za pomocą pliku .  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Aby uzyskać <xref:System.Windows.Media.ImageBrush> dodatkowe informacje na temat obrazów i malowania, zobacz [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>Metadane obrazu  
 Niektóre pliki obrazów zawierają metadane opisujące zawartość lub charakterystykę pliku. Na przykład większość aparatów cyfrowych tworzy obrazy zawierające metadane dotyczące formy i modelu aparatu używanego do przechwytywania obrazu. Każdy format obrazu obsługuje metadane inaczej, ale WPF Imaging zapewnia jednolity sposób przechowywania i pobierania metadanych dla każdego obsługiwanego formatu obrazu.  
  
 Dostęp do metadanych <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> jest dostarczany <xref:System.Windows.Media.Imaging.BitmapSource> za pośrednictwem właściwości obiektu. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>zwraca <xref:System.Windows.Media.Imaging.BitmapMetadata> obiekt, który zawiera wszystkie metadane zawarte w obrazie. Te dane mogą znajdować się w jednym schemacie metadanych lub kombinacji różnych schematów. WPF Imaging obsługuje następujące schematy metadanych obrazu: Wymienne pliki obrazów (Exif), tEXt (PNG Textual Data), katalog plików obrazu (IFD), International Press Telecommunications Council (IPTC) i Extensible Metadata Platform (XMP).  
  
 Aby uprościć proces odczytywania metadanych, udostępnia kilka nazwanych <xref:System.Windows.Media.Imaging.BitmapMetadata> właściwości, do których można łatwo uzyskać dostęp, takich jak <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>i <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Wiele z tych właściwości o nazwie może również służyć do pisania metadanych. Dodatkowa obsługa odczytywania metadanych jest dostarczana przez czytnik zapytań metadanych. Metoda <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> służy do pobierania czytnika zapytań metadanych przez dostarczenie zapytania ciągu, takiego jak *"/app1/exif/"*. W poniższym <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> przykładzie jest używany do uzyskania tekstu przechowywanego w lokalizacji *"/Tekst/Opis".*  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Aby napisać metadane, jest używany moduł zapisujący kwerendy metadanych. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>uzyskuje moduł zapisujący kwerendę i ustawia żądaną wartość. W poniższym <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> przykładzie służy do zapisu tekstu przechowywanego w lokalizacji *"/Tekst/Opis".*  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>Rozszerzalność kodeka  
 Podstawową cechą WPF Imaging jest model rozszerzalności dla nowych kodeków obrazu. Te interfejsy niezarządzane umożliwiają deweloperom koderów-dekodów do integracji kodeków z WPF, dzięki czemu nowe formaty obrazów mogą być automatycznie używane przez aplikacje WPF.  
  
 Aby uzyskać przykład interfejsu API rozszerzalności, zobacz [przykładowy kodek Win32](https://go.microsoft.com/fwlink/?LinkID=160052). W tym przykładzie pokazano, jak utworzyć dekoder i koder dla niestandardowego formatu obrazu.  
  
> [!NOTE]
> Koder-dekodu musi być podpisany cyfrowo, aby system go rozpoznał.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Grafika 2D i obrazowanie](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Kodek przykładowy Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
