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
ms.openlocfilehash: 87b626e575d889447ef061d1ed62ef28efe5dfeb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947345"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Instrukcje: Przeprowadzanie testu trafienia geometrii w wizualizacji
W tym przykładzie pokazano, jak przeprowadzić test trafień na obiekt wizualny, który składa się z co najmniej jeden <xref:System.Windows.Media.Geometry> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać <xref:System.Windows.Media.DrawingGroup> z visual obiektu, który używa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metody. Hit test jest przeprowadzane na renderowanej zawartości każdego rysunku w <xref:System.Windows.Media.DrawingGroup> do określenia, które geometrii został trafiony.  
  
> [!NOTE]
>  W większości przypadków należy użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę pozwala ustalić, czy punkt przecina dowolne renderowanej zawartości wizualizacji.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> Metodą jest przeciążona metoda, która pozwala na przeprowadzanie testu trafienia przy użyciu określonego <xref:System.Windows.Point> lub <xref:System.Windows.Media.Geometry>. Geometria jest malowania, obrysu można rozszerzyć poza granicami wypełnienia. W takim przypadku można wywołać <xref:System.Windows.Media.Geometry.StrokeContains%2A> oprócz <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 Możesz też podać <xref:System.Windows.Media.ToleranceType> używany na potrzeby spłaszczanie Beziera.  
  
> [!NOTE]
>  W tym przykładzie nie bierze pod uwagę jakichkolwiek plików transformacji lub przycinania, które można stosować do geometrii. Ponadto w tym przykładzie nie będzie działać z kontrolkę ze stylem, ponieważ nie ma rysunki bezpośrednio związane z nią.  
  
## <a name="see-also"></a>Zobacz także

- [Test trafienia w warstwie wizualizacji](hit-testing-in-the-visual-layer.md)
- [Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru](how-to-hit-test-using-geometry-as-a-parameter.md)
