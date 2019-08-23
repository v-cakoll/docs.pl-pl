---
title: 'Instrukcje: Przeprowadzanie testu trafienia geometrii w wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923377"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Instrukcje: Przeprowadzanie testu trafienia geometrii w wizualizacji
Ten przykład pokazuje, jak wykonać test trafień na obiekcie wizualizacji, który składa się z co <xref:System.Windows.Media.Geometry> najmniej jednego obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, <xref:System.Windows.Media.DrawingGroup> jak pobrać z obiektu wizualizacji, który <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> używa metody. Test trafień jest następnie wykonywany dla renderowanej zawartości każdego rysunku w programie, <xref:System.Windows.Media.DrawingGroup> aby określić, która geometria została trafiona.  
  
> [!NOTE]
> W większości przypadków można użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, aby określić, czy punkt przecina zawartość wizualizacji.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 Metoda jest przeciążoną metodą, która umożliwia trafienie testu przy użyciu określonego <xref:System.Windows.Point> lub <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.Geometry.FillContains%2A> W przypadku wybrania geometrii, naciśnięcie może wykraczać poza granice wypełnienia. W takim przypadku może być konieczne wywołanie <xref:System.Windows.Media.Geometry.StrokeContains%2A> dodatku do. <xref:System.Windows.Media.Geometry.FillContains%2A>  
  
 Możesz również podać <xref:System.Windows.Media.ToleranceType> , który jest używany do celów spłaszczania Beziera.  
  
> [!NOTE]
> Ten przykład nie uwzględnia żadnych transformacji lub wycinków, które mogą być stosowane do geometrii. Ponadto ten przykład nie będzie działał z kontrolką z stylem, ponieważ nie ma bezpośrednio skojarzonych z nim rysunków.  
  
## <a name="see-also"></a>Zobacz także

- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru](how-to-hit-test-using-geometry-as-a-parameter.md)
