---
title: Jak malować obszar gradientem promieniowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452756"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Jak malować obszar gradientem promieniowym
Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.RadialGradientBrush> do malowania obszaru z gradientem promieniowym.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.RadialGradientBrush>, aby malować prostokąt z gradientem promieniowym, który przechodzi z żółtego do czerwonego do zielonego koloru wapna.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono gradient z poprzedniego przykładu. Ogranicznik gradientu został wyróżniony.  
  
 ![Gradienty zatrzymane w gradiencie promieniowym](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> W przykładach w tym temacie użyto domyślnego układu współrzędnych do ustawiania punktów kontrolnych. Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: 0 wskazuje 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni. Można zmienić ten system współrzędnych, ustawiając właściwość <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na <xref:System.Windows.Media.BrushMappingMode.Absolute>wartość. Bezwzględny układ współrzędnych nie należy do obwiedni. Wartości są interpretowane bezpośrednio w miejscu lokalnym.  
  
 Aby uzyskać dodatkowe przykłady <xref:System.Windows.Media.RadialGradientBrush>, zobacz [Przykładowe pędzle](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).
