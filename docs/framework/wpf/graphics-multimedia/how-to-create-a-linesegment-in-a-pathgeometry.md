---
title: 'Instrukcje: Tworzenie obiektu LineSegment w elemencie PathGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: a50c98ccc3f6d517e0917cb774af4d49d2bfa7a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054552"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="a5c55-102">Instrukcje: Tworzenie obiektu LineSegment w elemencie PathGeometry</span><span class="sxs-lookup"><span data-stu-id="a5c55-102">How to: Create a LineSegment in a PathGeometry</span></span>

<span data-ttu-id="a5c55-103">Ten przykład przedstawia sposób tworzenia segment linii.</span><span class="sxs-lookup"><span data-stu-id="a5c55-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="a5c55-104">Aby utworzyć segment linii, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.LineSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="a5c55-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>

## <a name="example"></a><span data-ttu-id="a5c55-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5c55-105">Example</span></span>

<span data-ttu-id="a5c55-106">Rysowanie w poniższych przykładach <xref:System.Windows.Media.LineSegment> z (10, 50) do (200, 70).</span><span class="sxs-lookup"><span data-stu-id="a5c55-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="a5c55-107">Na poniższej ilustracji przedstawiono wynikowe <xref:System.Windows.Media.LineSegment>; tło siatki został dodany do wyświetlenia w układzie współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a5c55-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>

<span data-ttu-id="a5c55-108">![Obiekt LineSegment w PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") LineSegment rysowane z (10,50) (200,70)</span><span class="sxs-lookup"><span data-stu-id="a5c55-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment drawn from (10,50) to (200,70)</span></span>

<span data-ttu-id="a5c55-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a5c55-109">[xaml]</span></span>

<span data-ttu-id="a5c55-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], można użyć składni atrybutów do opisania ścieżki.</span><span class="sxs-lookup"><span data-stu-id="a5c55-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

<span data-ttu-id="a5c55-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="a5c55-111">[xaml]</span></span>

<span data-ttu-id="a5c55-112">(Należy pamiętać, że ta składnia atrybutu faktycznie tworzy <xref:System.Windows.Media.StreamGeometry>, lekki wersję <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a5c55-112">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a5c55-113">Aby uzyskać więcej informacji, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.)</span><span class="sxs-lookup"><span data-stu-id="a5c55-113">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>

<span data-ttu-id="a5c55-114">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], może również zwracać segment linii przy użyciu składni elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5c55-114">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="a5c55-115">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="a5c55-115">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1">
  <Path.Data>
    <PathGeometry>
      <PathFigure StartPoint="10,50">
        <LineSegment Point="200,70" />
      </PathFigure>
    </PathGeometry>
  </Path.Data>
</Path>
```

```csharp
PathFigure myPathFigure = new PathFigure();
myPathFigure.StartPoint = new Point(10, 50);

LineSegment myLineSegment = new LineSegment();
myLineSegment.Point = new Point(200, 70);

PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();
myPathSegmentCollection.Add(myLineSegment);

myPathFigure.Segments = myPathSegmentCollection;

PathFigureCollection myPathFigureCollection = new PathFigureCollection();
myPathFigureCollection.Add(myPathFigure);

PathGeometry myPathGeometry = new PathGeometry();
myPathGeometry.Figures = myPathFigureCollection;

Path myPath = new Path();
myPath.Stroke = Brushes.Black;
myPath.StrokeThickness = 1;
myPath.Data = myPathGeometry;
```

```vb
Dim myPathFigure As New PathFigure()
myPathFigure.StartPoint = New Point(10, 50)

Dim myLineSegment As New LineSegment()
myLineSegment.Point = New Point(200, 70)

Dim myPathSegmentCollection As New PathSegmentCollection()
myPathSegmentCollection.Add(myLineSegment)

myPathFigure.Segments = myPathSegmentCollection

Dim myPathFigureCollection As New PathFigureCollection()
myPathFigureCollection.Add(myPathFigure)

Dim myPathGeometry As New PathGeometry()
myPathGeometry.Figures = myPathFigureCollection

Dim myPath As New Path()
myPath.Stroke = Brushes.Black
myPath.StrokeThickness = 1
myPath.Data = myPathGeometry
```

<span data-ttu-id="a5c55-116">W tym przykładzie jest częścią większego przykładu; Aby uzyskać pełny przykład, zobacz [przykładowe geometrii](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="a5c55-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5c55-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5c55-117">See also</span></span>

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="a5c55-118">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="a5c55-118">Geometry Overview</span></span>](geometry-overview.md)
