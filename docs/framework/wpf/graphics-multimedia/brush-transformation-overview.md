---
title: "Przegląd Przekształcanie pędzla"
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
helpviewer_keywords:
- brushes [WPF], transformation properties
- properties [WPF], transformation
- transformation properties of brushes [WPF]
ms.assetid: 8b9bfc09-12fd-4cd5-b445-99949f27bc39
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa4a533594c1e89942406e7df0a49215e3885418
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="brush-transformation-overview"></a>Przegląd Przekształcanie pędzla
Klasa pędzla oferuje dwie właściwości przekształcenia: <xref:System.Windows.Media.Brush.Transform%2A> i <xref:System.Windows.Media.Brush.RelativeTransform%2A>. Właściwości umożliwiają obracanie, skalowanie pochylanie i tłumaczenie zawartość pędzla. W tym temacie opisano różnice między te dwie właściwości i przykłady ich użycia.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy zrozumieć funkcje pędzel przekształcany. Dla <xref:System.Windows.Media.LinearGradientBrush> i <xref:System.Windows.Media.RadialGradientBrush>, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Aby uzyskać <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush>, lub <xref:System.Windows.Media.VisualBrush>, zobacz [malowanie obrazów, rysunki i elementy wizualne](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md). Należy także zapoznać się z przekształceń 2W, opisanego w [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
<a name="transformversusrelativetransform"></a>   
## <a name="differences-between-the-transform-and-relativetransform-properties"></a>Różnice między właściwości RelativeTransform i przekształcenia  
 Po zastosowaniu transformacji do pędzla <xref:System.Windows.Media.Brush.Transform%2A> właściwość, należy znać rozmiar malowanego obszaru, aby przekształcić zawartość pędzla o jego Centrum. Załóżmy, że malowanego obszaru jest 200 szeroki pikselach niezależnych od urządzenia i 150 wysoka.  Jeśli używasz <xref:System.Windows.Media.RotateTransform> obracania pędzla wyjściowy 45 stopni, o jego Centrum, można udzielić <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 100 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 75.  
  
 Po zastosowaniu transformacji do pędzla <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości, że stosowana jest transformacja pędzla przed jego dane wyjściowe jest mapowany na malowanego obszaru. Poniższa lista zawiera opis kolejności, w którym zawartość pędzla są przetwarzane i przekształcenia.  
  
1.  Przetwarzanie zawartości pędzla. Aby uzyskać <xref:System.Windows.Media.GradientBrush>, oznacza to, że określenie obszaru gradientu. Aby uzyskać <xref:System.Windows.Media.TileBrush>, <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowany na <xref:System.Windows.Media.TileBrush.Viewport%2A>. Staje się on dane wyjściowe pędzla.  
  
2.  Na prostokąt 1 x 1 przekształcenia danych wyjściowych projektu pędzla.  
  
3.  Zastosuj pędzla <xref:System.Windows.Media.Brush.RelativeTransform%2A>, jeśli istnieje.  
  
4.  Projekt przekształcone dane wyjściowe na powierzchni do rysowania.  
  
5.  Zastosuj pędzla <xref:System.Windows.Media.Transform>, jeśli istnieje.  
  
 Ponieważ <xref:System.Windows.Media.Brush.RelativeTransform%2A> jest stosowana, a dane wyjściowe pędzla jest zamapowany na prostokąt 1 x 1, przekształcanie Centrum i wartości przesunięcia wydają się być względny. Na przykład jeśli użyto <xref:System.Windows.Media.RotateTransform> obracania pędzla wyjściowy 45 stopni, o jego Centrum, można udzielić <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.CenterX%2A> 0,5 i <xref:System.Windows.Media.RotateTransform.CenterY%2A> 0,5.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe kilka pędzle, które zostały obrócone o 45 stopni przy użyciu <xref:System.Windows.Media.Brush.RelativeTransform%2A> i <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Właściwości RelativeTransform i Transform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-brushrelativetransform-transform-small.png "graphicsmm_brushrelativetransform_transform_small")  
  
<a name="relativetransformandtilebrush"></a>   
## <a name="using-relativetransform-with-a-tilebrush"></a>Przy użyciu właściwości RelativeTransform z element TileBrush  
 Ponieważ pędzle kafelka są bardziej skomplikowane niż inne pędzle, stosowanie <xref:System.Windows.Media.Brush.RelativeTransform%2A> do jednego może je spowodować nieoczekiwane wyniki. Na przykład należy wykonać poniższy obraz.  
  
 ![Obraz źródłowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-1-original-image.jpg "graphicsmm_reltransform_1_original_image")  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.ImageBrush> namalować prostokątny obszar z poprzednim obrazu. Ma to zastosowanie <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush> obiektu <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości i ustawia jej <xref:System.Windows.Media.TileBrush.Stretch%2A> właściwości <xref:System.Windows.Media.Stretch.UniformToFill>, który zachować współczynnik proporcji obrazu, gdy jest on rozciągany tak, aby wypełnić prostokąt.  
  
 [!code-xaml[BrushOverviewExamples_snip#GraphicsMMRelativeTransformExample2Inline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/RelativeTransformIllustration.xaml#graphicsmmrelativetransformexample2inline)]  
  
 Ten przykład generuje następujące wyniki:  
  
 ![Przekształcone dane wyjściowe](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-6-output.png "graphicsmm_reltransform_6_output")  
  
 Zwróć uwagę, że obraz jest zniekształcony, mimo że pędzla <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawiono <xref:System.Windows.Media.Stretch.UniformToFill>. Wynika to z faktu przekształcenie względne są stosowane po pędzla <xref:System.Windows.Media.TileBrush.Viewbox%2A> jest mapowany na jego <xref:System.Windows.Media.TileBrush.Viewport%2A>. Na poniższej liście opisano każdy etap procesu:  
  
1.  Projekt zawartość pędzla (<xref:System.Windows.Media.TileBrush.Viewbox%2A>) na jego podstawowy Kafelek (<xref:System.Windows.Media.TileBrush.Viewport%2A>) przy użyciu pędzla <xref:System.Windows.Media.TileBrush.Stretch%2A> ustawienie.  
  
     ![Rozciąganie Viewbox do rozmiaru okienka ekranu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-2-viewbox-to-viewport.png "graphicsmm_reltransform_2_viewbox_to_viewport")  
  
2.  Projekt podstawowy Kafelek na prostokąt przekształcenia 1 x 1.  
  
     ![Okienko ekranu mapy na prostokąt przekształcenia](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-3-output-to-transform.png "graphicsmm_reltransform_3_output_to_transform")  
  
3.  Zastosuj <xref:System.Windows.Media.RotateTransform>.  
  
     ![Zastosuj przekształcenie względne](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-4-transform-rotate.png "graphicsmm_reltransform_4_transform_rotate")  
  
4.  Projekt po przekształceniu podstawowy Kafelek na powierzchni do rysowania.  
  
     ![Projekt po przekształceniu pędzla do obszaru wyjściowego](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-reltransform-5-transform-to-output.png "graphicsmm_reltransform_5_transform_to_output")  
  
<a name="rotateexample"></a>   
## <a name="example-rotate-an-imagebrush-45-degrees"></a>Przykład: Obracanie ImageBrush 45 stopni  
 Następujący przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwość <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform> Obiektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości są ustawione na 0,5 punktu współrzędnych względnych Centrum zawartości. W związku z tym zawartość pędzla są obracane o jego center.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Kolejnym przykładzie ma również zastosowanie <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, ale używa <xref:System.Windows.Media.Brush.Transform%2A> właściwości zamiast <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości. Obracanie pędzla o jego center <xref:System.Windows.Media.RotateTransform> obiektu <xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> musi być ustawiona na współrzędne bezwzględne. Ponieważ prostokąt jest malowane przez pędzla 175 90 pikseli, jest jego punktu centralnego (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Na poniższej ilustracji przedstawiono pędzla bez przekształcania, stosowane do przekształcania <xref:System.Windows.Media.Brush.RelativeTransform%2A> właściwości i stosowane do przekształcania <xref:System.Windows.Media.Brush.Transform%2A> właściwości.  
  
 ![Pędzel RelativeTransform i przekształcanie ustawienia](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
 Ten przykład jest częścią większego przykładu. Pełny przykład, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat pędzle, zobacz [omówienie pędzle WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Brush.Transform%2A>  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.Brush>  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
