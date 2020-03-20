---
title: Przegląd Przekształcanie pędzla
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
ms.openlocfilehash: deac1be2fd19703055b76af8173111b4453f0d6b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186529"
---
# <a name="brush-transformation-overview"></a>Przegląd Przekształcanie pędzla
Brush Klasa zawiera dwie właściwości <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A>transformacji: i . Właściwości umożliwiają obracanie, skalowanie, pochylanie i tłumaczenie zawartości pędzla. W tym temacie opisano różnice między tymi dwiema właściwościami i przedstawiono przykłady ich użycia.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zrozumieć funkcje pędzla, który przekształcasz. Dla <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.RadialGradientBrush>i , zobacz [Malowanie z jednolitych kolorów i gradientów Omówienie](painting-with-solid-colors-and-gradients-overview.md). Zobacz też <xref:System.Windows.Media.ImageBrush> [Malowanie obrazami, rysunkami i wizualizacjami](painting-with-images-drawings-and-visuals.md). <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush> Należy również zapoznać się z przekształceniami 2D opisanymi w [przeglądzie przekształceń](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Różnice między właściwościami przekształcania i względnegotransformu  
 Po zastosowaniu przekształcenia do <xref:System.Windows.Media.Brush.Transform%2A> właściwości pędzla, należy znać rozmiar obszaru malowane, jeśli chcesz przekształcić zawartość pędzla o jego środku. Załóżmy, że malowany obszar ma 200 pikseli niezależnych od urządzeń i 150 wysokości.  Jeśli użyto <xref:System.Windows.Media.RotateTransform> a do obracania wyjścia pędzla o 45 stopni <xref:System.Windows.Media.RotateTransform> wokół <xref:System.Windows.Media.RotateTransform.CenterX%2A> jego środka, dałbyś 100 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Po zastosowaniu przekształcenia do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości pędzla, że transformacja jest stosowana do pędzla przed jego dane wyjściowe jest mapowany do obszaru malowane. Na poniższej liście opisano kolejność przetwarzania i przekształcania zawartości pędzla.  
  
1. Przećkaj zawartość pędzla. Dla <xref:System.Windows.Media.GradientBrush>a oznacza to określenie obszaru gradientu. Dla <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowane <xref:System.Windows.Media.TileBrush.Viewport%2A>do . Staje się to wyjście pędzla.  
  
2. Rzut wyjście pędzla na prostokąt transformacji 1 x 1.  
  
3. Zastosuj szczotkę <xref:System.Windows.Media.Brush.RelativeTransform%2A>, jeśli ma.  
  
4. Rzut przekształcone dane wyjściowe na obszarze do malowania.  
  
5. Zastosuj szczotkę <xref:System.Windows.Media.Transform>, jeśli ma.  
  
 Ponieważ <xref:System.Windows.Media.Brush.RelativeTransform%2A> jest stosowany, gdy dane wyjściowe pędzla jest mapowany na prostokąt 1 x 1, przekłęć centrum i wartości odsunięcia wydają się być względne. Na przykład, jeśli <xref:System.Windows.Media.RotateTransform> użyto a do obracania wyjścia pędzla o 45 <xref:System.Windows.Media.RotateTransform> stopni <xref:System.Windows.Media.RotateTransform.CenterX%2A> wokół jego środka, <xref:System.Windows.Media.RotateTransform.CenterY%2A> należy podać a 0,5 i a 0,5.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe kilku pędzli, <xref:System.Windows.Media.Brush.RelativeTransform%2A> które <xref:System.Windows.Media.Brush.Transform%2A> zostały obrócene o 45 stopni przy użyciu właściwości i.  
  
 ![Właściwości RelativeTransform i Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>
## <a name="using-relativetransform-with-a-tilebrush"></a>Korzystanie z relativetransform z tileBrush  
 Ponieważ pędzle kafelków są bardziej złożone niż <xref:System.Windows.Media.Brush.RelativeTransform%2A> inne pędzle, zastosowanie a do jednego może przynieść nieoczekiwane rezultaty. Na przykład należy wziąć następujący obraz.  
  
 ![Obraz źródłowy](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 W poniższym przykładzie <xref:System.Windows.Media.ImageBrush> użyto do malowania prostokątnego obszaru z poprzednim obrazem. Stosuje <xref:System.Windows.Media.RotateTransform> a do <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości obiektu i ustawia <xref:System.Windows.Media.TileBrush.Stretch%2A> jego <xref:System.Windows.Media.Stretch.UniformToFill>właściwość do , który powinien zachować proporcje obrazu, gdy jest rozciągnięty, aby całkowicie wypełnić prostokąt.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Ten przykład generuje następujące wyniki:  
  
 ![Przekształcona produkcja](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Zwróć uwagę, że obraz jest zniekształcony, <xref:System.Windows.Media.TileBrush.Stretch%2A> mimo <xref:System.Windows.Media.Stretch.UniformToFill>że pędzel został ustawiony na . To dlatego, że względne przekształcenie jest <xref:System.Windows.Media.TileBrush.Viewbox%2A> stosowany po <xref:System.Windows.Media.TileBrush.Viewport%2A>pędzla jest mapowany do jego . Na poniższej liście opisano każdy krok procesu:  
  
1. Zaprojektować zawartość pędzla (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na<xref:System.Windows.Media.TileBrush.Viewport%2A>jego płytkę <xref:System.Windows.Media.TileBrush.Stretch%2A> bazową ( ) za pomocą ustawienia pędzla.  
  
     ![Rozciągnij pole widzenia, aby dopasować je do rzutni](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Rzutowanie kafelka bazowego na prostokąt transformacji 1 x 1.  
  
     ![Mapowanie rzutni na prostokąt transformacji](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Zastosuj <xref:System.Windows.Media.RotateTransform>plik .  
  
     ![Stosowanie przekształcenia względnego](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Rzut przekształcony płytki bazowej na obszarze do malowania.  
  
     ![Rzutowanie pędzla przekształconego na obszar wyjściowy](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Przykład: Obróć pędzel obrazu o 45 stopni  
 Poniższy przykład stosuje <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Brush.RelativeTransform%2A> do <xref:System.Windows.Media.ImageBrush>właściwości . Zarówno <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> obiekt, <xref:System.Windows.Media.RotateTransform.CenterY%2A> jak i właściwości są ustawione na 0,5, względne współrzędne punktu środkowego zawartości. W rezultacie zawartość pędzla jest obracana wokół jego środka.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 W następnym przykładzie <xref:System.Windows.Media.RotateTransform> stosuje <xref:System.Windows.Media.ImageBrush>się również do <xref:System.Windows.Media.Brush.Transform%2A> , ale <xref:System.Windows.Media.Brush.RelativeTransform%2A> używa właściwości zamiast właściwości. Aby obrócić pędzel wokół <xref:System.Windows.Media.RotateTransform> jego środka, obiekt <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> musi być ustawiony na współrzędne bezwzględne. Ponieważ prostokąt malowany pędzlem ma rozmiar 175 na 90 pikseli, jego punktem środkowym jest (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Na poniższej ilustracji przedstawiono pędzel bez przekształcenia, z przekształcenia stosowane do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości i z przekształcenia stosowane do <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Ustawienia Brush RelativeTransform i Transform](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 W tym przykładzie jest częścią większej próbki. Aby uzyskać pełną próbkę, zobacz [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji na temat pędzli, zobacz [Przegląd pędzli WPF](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przekształcenia — przegląd](transforms-overview.md)
