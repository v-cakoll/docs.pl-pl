---
title: 'Instrukcje: Malowanie obszaru gradientem promieniowym'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916100"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Instrukcje: Malowanie obszaru gradientem promieniowym
Ten przykład pokazuje, <xref:System.Windows.Media.RadialGradientBrush> jak używać klasy do malowania obszaru z gradientem promieniowym.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Windows.Media.RadialGradientBrush> do malowania prostokąta z gradientem promieniowym, który przechodzi z żółtej do czerwonego do zielonego koloru wapna.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono gradient z poprzedniego przykładu. Ogranicznik gradientu został wyróżniony.  
  
 ![Gradienty zatrzymane w gradiencie promieniowym](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> W przykładach w tym temacie użyto domyślnego układu współrzędnych do ustawiania punktów kontrolnych. Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: wartość 0 oznacza 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni. Można zmienić ten system współrzędnych przez ustawienie <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość. <xref:System.Windows.Media.BrushMappingMode.Absolute> Bezwzględny układ współrzędnych nie należy do obwiedni. Wartości są interpretowane bezpośrednio w miejscu lokalnym.  
  
 Aby uzyskać <xref:System.Windows.Media.RadialGradientBrush> więcej przykładów, zobacz [przykład pędzli](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).
