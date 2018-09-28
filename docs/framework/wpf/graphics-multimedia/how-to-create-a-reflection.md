---
title: Jak utworzyć odbicie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 716adff5c5c41e6601e384b6669516cb6ba1041d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421258"
---
# <a name="how-to-create-a-reflection"></a>Jak utworzyć odbicie
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.VisualBrush> utworzyć odbicie. Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejącej wizualizacji, ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenie odbicia <xref:System.Windows.Controls.Border> zawiera wiele elementów. Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.  
  
 ![A odzwierciedlone obiekt wizualny](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odbitych obiekt wizualny  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać pełny przykład, który zawiera przykłady pokazujące, jak części ekranu, powiększanie i Tworzenie odbić, zobacz [przykładowe VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.VisualBrush>  
 [Malowanie przy użyciu obrazów, rysowania i wizualizacji](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
