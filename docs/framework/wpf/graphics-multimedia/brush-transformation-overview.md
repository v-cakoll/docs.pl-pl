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
ms.openlocfilehash: 1d3a56014e0975f3616b7f90021b4290ced5daab
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453133"
---
# <a name="brush-transformation-overview"></a>Przegląd Przekształcanie pędzla
Klasa pędzla udostępnia dwie właściwości transformacji: <xref:System.Windows.Media.Brush.Transform%2A> i <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Właściwości umożliwiają obracanie, skalowanie, pochylanie i tłumaczenie zawartości pędzla. W tym temacie opisano różnice między tymi dwiema właściwościami i przedstawiono przykłady ich użycia.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z funkcjami danego pędzla. Aby uzyskać <xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>, zobacz [malowanie przy użyciu pełnych kolorów i gradientów — Omówienie](painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>lub <xref:System.Windows.Media.VisualBrush>, zobacz [malowanie przy użyciu obrazów, rysunków i wizualizacji](painting-with-images-drawings-and-visuals.md). Należy również zapoznać się z transformacjemi 2D opisanymi w [Przegląd przekształceń](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Różnice między właściwościami Transform i RelativeTransform  
 Po zastosowaniu przekształcenia do właściwości <xref:System.Windows.Media.Brush.Transform%2A> pędzla musisz znać rozmiar pomalowanego obszaru, jeśli chcesz przekształcić zawartość pędzla na centrum. Załóżmy, że obszar malowany to 200 urządzenia niezależne od szerokości i 150.  Jeśli użyto <xref:System.Windows.Media.RotateTransform>, aby obrócić dane wyjściowe pędzla 45 stopni o centrum, należy dać <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Po zastosowaniu transformacji do właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> pędzla, transformacja zostanie zastosowana do pędzla, zanim jego wyjście zostanie zamapowane na obszar malowany. Poniższa lista zawiera opis kolejności przetwarzania i przekształcania zawartości pędzla.  
  
1. Przetwórz zawartość pędzla. W przypadku <xref:System.Windows.Media.GradientBrush>oznacza to określenie obszaru gradientu. W przypadku <xref:System.Windows.Media.TileBrush><xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowany na <xref:System.Windows.Media.TileBrush.Viewport%2A>. To będzie wynik pędzla.  
  
2. Zaprojektuj dane wyjściowe pędzla na prostokąt przekształcenia 1 x 1.  
  
3. Zastosuj <xref:System.Windows.Media.Brush.RelativeTransform%2A>pędzla, jeśli go zawiera.  
  
4. Zaprojektuj przekształcone dane wyjściowe w obszarze do malowania.  
  
5. Zastosuj <xref:System.Windows.Media.Transform>pędzla, jeśli go zawiera.  
  
 Ponieważ <xref:System.Windows.Media.Brush.RelativeTransform%2A> jest stosowany, podczas gdy dane wyjściowe pędzla są mapowane do prostokąta 1 x 1, przekształcenie i przesunięcia są widoczne jako względne. Na przykład, jeśli użyto <xref:System.Windows.Media.RotateTransform>, aby obrócić dane wyjściowe pędzla 45 stopni o centrum, należy dać <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe kilku pędzli obróconych o 45 stopni przy użyciu właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Właściwości RelativeTransform i Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Używanie RelativeTransform z obiektem TileBrush  
 Ponieważ pędzle kafelków są bardziej złożone niż inne pędzle, zastosowanie <xref:System.Windows.Media.Brush.RelativeTransform%2A> do jednego może dać nieoczekiwane wyniki. Na przykład wykonaj poniższą ilustrację.  
  
 ![Obraz źródła](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 Poniższy przykład używa <xref:System.Windows.Media.ImageBrush>, aby malować prostokątny obszar z powyższym obrazem. Stosuje <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> obiektu <xref:System.Windows.Media.ImageBrush> i ustawia jej Właściwość <xref:System.Windows.Media.TileBrush.Stretch%2A> na <xref:System.Windows.Media.Stretch.UniformToFill>, która powinna zachować współczynnik proporcji obrazu, gdy zostanie on rozciągnięty w celu całkowitego wypełnienia prostokąta.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Ten przykład generuje następujące wyniki:  
  
 ![Przekształcone dane wyjściowe](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Zauważ, że obraz jest zniekształcony, mimo że <xref:System.Windows.Media.TileBrush.Stretch%2A> pędzla został ustawiony na <xref:System.Windows.Media.Stretch.UniformToFill>. Dzieje się tak, ponieważ Przekształć względne jest stosowane po zamapowaniu <xref:System.Windows.Media.TileBrush.Viewbox%2A> pędzla do jego <xref:System.Windows.Media.TileBrush.Viewport%2A>. Poniższa lista zawiera opis poszczególnych etapów procesu:  
  
1. Zaprojektuj zawartość pędzla (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na kafelku podstawowym (<xref:System.Windows.Media.TileBrush.Viewport%2A>) przy użyciu ustawienia <xref:System.Windows.Media.TileBrush.Stretch%2A> pędzla.  
  
     ![Rozciągnij Viewbox w celu dopasowania do okienka ekranu](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2. Utwórz projekt kafelka podstawowego na 1 x 1.  
  
     ![Mapuj okienko ekranu na prostokąt przekształcenia](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3. Zastosuj <xref:System.Windows.Media.RotateTransform>.  
  
     ![Zastosuj przekształcenie względne](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4. Zaprojektuj przekształcony kafelek podstawowy na obszar do malowania.  
  
     ![Zaprojektuj przekształcony pędzel na obszar wyjściowy](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Przykład: obracanie ImageBrush 45 stopni  
 Poniższy przykład stosuje <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.ImageBrush>. Właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> obiektu <xref:System.Windows.Media.RotateTransform> są ustawiane na 0,5, względnych współrzędnych punktu centralnego zawartości. W efekcie zawartość pędzla zostanie obrócona na centrum.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 W następnym przykładzie zastosowano również <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, ale zamiast właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> zostanie użyta Właściwość <xref:System.Windows.Media.Brush.Transform%2A>. Aby obrócić pędzel o centrum, <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> obiektu <xref:System.Windows.Media.RotateTransform> muszą być ustawione na współrzędne bezwzględne. Ponieważ prostokąt malowany przez pędzel jest 175 o 90 pikseli, jego punkt środkowy to (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Na poniższej ilustracji przedstawiono pędzel bez przekształcenia, z przekształceniem stosowanym do właściwości <xref:System.Windows.Media.Brush.RelativeTransform%2A> i przekształceniem stosowanym do właściwości <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 ![Ustawienia RelativeTransform i przekształcenia pędzla](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Ten przykład jest częścią większego przykładu. Pełny przykład można znaleźć w [przykładzie pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji na temat pędzli, zobacz [Omówienie pędzli WPF](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Malowanie jednolitymi kolorami i gradientami — przegląd](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
- [Przekształcenia — przegląd](transforms-overview.md)
