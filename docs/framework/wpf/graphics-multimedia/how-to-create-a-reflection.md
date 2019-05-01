---
title: 'Instrukcje: Tworzenie odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 61b597cd36fcf0d60f215d9b5403f3b42b21dec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904228"
---
# <a name="how-to-create-a-reflection"></a>Instrukcje: Tworzenie odbicia
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.VisualBrush> utworzyć odbicie. Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejącej wizualizacji, ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenie odbicia <xref:System.Windows.Controls.Border> zawiera wiele elementów. Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.  
  
 ![A odzwierciedlone obiekt wizualny](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")  
Odbitych obiekt wizualny  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Aby uzyskać pełny przykład, który zawiera przykłady pokazujące, jak części ekranu, powiększanie i Tworzenie odbić, zobacz [przykładowe VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.VisualBrush>
- [Malowanie przy użyciu obrazów, rysowania i wizualizacji](painting-with-images-drawings-and-visuals.md)
