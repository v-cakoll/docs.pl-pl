---
title: 'Instrukcje: Zaokrąglanie rogów elementu RectangleGeometry'
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089136"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="c8911-102">Instrukcje: Zaokrąglanie rogów elementu RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="c8911-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="c8911-103">Aby zaokrąglić rogi <xref:System.Windows.Media.RectangleGeometry>, ustaw jego <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> właściwości na wartość większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="c8911-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="c8911-104">Większe wartości, bardziej okrągłe prostokąta.</span><span class="sxs-lookup"><span data-stu-id="c8911-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8911-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8911-105">Example</span></span>  
 <span data-ttu-id="c8911-106">W poniższym przykładzie pokazano kilka <xref:System.Windows.Media.RectangleGeometry> obiektów z różnymi <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> i <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c8911-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="c8911-107"><xref:System.Windows.Media.RectangleGeometry> Obiekty są wyświetlane przy użyciu <xref:System.Windows.Shapes.Path> elementów.</span><span class="sxs-lookup"><span data-stu-id="c8911-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="c8911-108">![Prostokąty za pomocą różnych RadiusX&#47;RadiusY ustawienia](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="c8911-108">![Rectangles with different RadiusX&#47;RadiusY settings](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="c8911-109">Prostokąty z zaokrąglonymi narożnikami</span><span class="sxs-lookup"><span data-stu-id="c8911-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8911-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8911-110">See also</span></span>

- [<span data-ttu-id="c8911-111">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="c8911-111">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="c8911-112">Tworzenie kształtu złożonego</span><span class="sxs-lookup"><span data-stu-id="c8911-112">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="c8911-113">Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="c8911-113">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
