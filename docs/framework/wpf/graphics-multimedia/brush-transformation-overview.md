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
ms.openlocfilehash: 0b55d2000b8a70bc42373cb976a84ff54ebc4245
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169575"
---
# <a name="brush-transformation-overview"></a>Przegląd Przekształcanie pędzla
Klasa pędzla udostępnia dwie właściwości transformacji: <xref:System.Windows.Media.Brush.Transform%2A> i <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Właściwości umożliwiają obracanie, skalowanie, pochylanie i tłumaczenie zawartość pędzla. W tym temacie opisano różnice między te dwie właściwości i przykłady ich użycia.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, musisz zrozumieć funkcje pędzla, który jest przekształcany. Aby uzyskać <xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush>, zobacz [malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md). Należy także zapoznać się z przekształceń 2D, opisanego w [przekształca Przegląd](transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Różnice między właściwości RelativeTransform i przekształcenia  
 Jeżeli zastosujesz przekształcenia pędzla <xref:System.Windows.Media.Brush.Transform%2A> właściwość, należy sprawdzić rozmiar malowanego obszaru, czy chcesz przekształcić zawartość pędzla o jej środka. Załóżmy, że malowanego obszaru jest 200 szerokiego pikselach niezależnych od urządzenia i 150 wysoka.  Jeśli użyto <xref:System.Windows.Media.RotateTransform> celu Obróć pędzel danych wyjściowych 45 stopni, o jej środka, można udzielić <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Jeżeli zastosujesz przekształcenia pędzla <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości tej transformacji jest stosowany do pędzla, przed jego danych wyjściowych jest mapowany do malowanego obszaru. Poniższa lista zawiera opis kolejności, w którym przetwarzane i przekształcić pędzel zawartość.  
  
1.  Przetwarzanie zawartości pędzla. Aby uzyskać <xref:System.Windows.Media.GradientBrush>, oznacza to, że określenie obszaru gradientu. Aby uzyskać <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowany na <xref:System.Windows.Media.TileBrush.Viewport%2A>. Ten staje się dane wyjściowe pędzla.  
  
2.  Projekt pędzel danych wyjściowych na prostokąt przekształcenia 1 x 1.  
  
3.  Stosowanie pędzla <xref:System.Windows.Media.Brush.RelativeTransform%2A>, jeśli taki istnieje.  
  
4.  Projekt przekształcone dane wyjściowe do obszaru do malowania.  
  
5.  Stosowanie pędzla <xref:System.Windows.Media.Transform>, jeśli taki istnieje.  
  
 Ponieważ <xref:System.Windows.Media.Brush.RelativeTransform%2A> jest stosowany, natomiast pędzla danych wyjściowych jest mapowany do prostokąta 1 x 1, przekształcenie Centrum wartości przesunięcia wydaje się być względny. Na przykład, jeśli użyto <xref:System.Windows.Media.RotateTransform> celu Obróć pędzel danych wyjściowych 45 stopni, o jej środka, można udzielić <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> wynosi 0,5 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> wynosi 0,5.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe zostaną przesunięte o 45 stopni przy użyciu pędzli kilka <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Właściwości RelativeTransform i Transform](./media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Za pomocą RelativeTransform z użyciem TileBrush  
 Ponieważ pędzle kafelka są bardziej skomplikowane niż inne pędzle, stosując <xref:System.Windows.Media.Brush.RelativeTransform%2A> do jednego może dawać nieoczekiwane wyniki. Za przykład niech posłuży poniższej ilustracji.  
  
 ![Obraz źródłowy](./media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować prostokątny obszar za pomocą wcześniejszej ilustracji. Ma to zastosowanie <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush> obiektu <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwość i zestawach jego <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości <xref:System.Windows.Media.Stretch.UniformToFill>, który powinno zachować współczynnik proporcji obrazu, po jego jest rozciągany tak, aby wypełnić prostokąt.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Ten przykład generuje następujące wyniki:  
  
 ![Przekształcone dane wyjściowe](./media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Należy zauważyć, że obraz jest zniekształcony, nawet jeśli pędzla <xref:System.Windows.Media.TileBrush.Stretch%2A> została ustawiona na <xref:System.Windows.Media.Stretch.UniformToFill>. To dlatego przekształcenie względne są stosowane po pędzla <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowany na jego <xref:System.Windows.Media.TileBrush.Viewport%2A>. Na poniższej liście opisano każdy etap procesu:  
  
1.  Projekt pędzla zawartość (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na jego podstawowy Kafelek (<xref:System.Windows.Media.TileBrush.Viewport%2A>) przy użyciu pędzli <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie.  
  
     ![Rozciąganie Viewbox, aby dopasować okienka ekranu](./media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projekt podstawowy Kafelek na prostokąt przekształcenia 1 x 1.  
  
     ![Okienko ekranu mapy na prostokąt przekształcenia](./media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Zastosuj <xref:System.Windows.Media.RotateTransform>.  
  
     ![Zastosuj przekształcenie względne](./media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projekt po przekształceniu podstawowy Kafelek do obszaru do malowania.  
  
     ![Projekt po przekształceniu pędzla do obszaru wyjściowego](./media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Przykład: Obróć ImageBrush 45 stopni  
 Następujący przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwość <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Obiektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości są ustawione na 0,5 punktu współrzędnych względnych Centrum zawartości. W rezultacie zawartość pędzla są obracane o jej środka.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Dotyczy również w następnym przykładzie <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, ale używa <xref:System.Windows.Media.Brush.Transform%2A> właściwości zamiast <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości. Aby obrócić pędzla o jej środka <xref:System.Windows.Media.RotateTransform> obiektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> musi być ustawione na współrzędne bezwzględne. Ponieważ prostokąta jest malowane przez pędzel 175 pikseli 90, jest jego punktu centralnego (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Na poniższej ilustracji przedstawiono pędzli bez transformacji, z zadaniami transformacji stosowane do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości i przekształcenie zastosowane do <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Pędzel RelativeTransform i przekształcać ustawienia](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 W tym przykładzie jest częścią większego przykładu. Aby uzyskać pełny przykład, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat pędzle, zobacz [pędzle WPF — Przegląd](wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Brush.Transform%2A>
- <xref:System.Windows.Media.Brush.RelativeTransform%2A>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.Brush>
- [Przegląd Malowanie jednolitymi kolorami i gradientami](painting-with-solid-colors-and-gradients-overview.md)
- [Malowanie obrazami, rysowaniem i Visual](painting-with-images-drawings-and-visuals.md)
- [Przegląd Przekształcenia](transforms-overview.md)
