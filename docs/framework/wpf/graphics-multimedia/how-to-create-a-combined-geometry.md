---
title: 'Instrukcje: Tworzenie połączonej geometrii'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910108"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="868fe-102">Instrukcje: Tworzenie połączonej geometrii</span><span class="sxs-lookup"><span data-stu-id="868fe-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="868fe-103">W tym przykładzie pokazano, jak połączyć geometrii.</span><span class="sxs-lookup"><span data-stu-id="868fe-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="868fe-104">Aby połączyć dwa geometrii, należy użyć <xref:System.Windows.Media.CombinedGeometry> obiektu.</span><span class="sxs-lookup"><span data-stu-id="868fe-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="868fe-105">Ustaw jego <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> właściwości za pomocą dwóch geometrii, łączyć, a następnie ustaw <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> właściwość, która określa, jak geometrii będą połączone ze sobą, aby `Union`, `Intersect`, `Exclude`, lub `Xor`.</span><span class="sxs-lookup"><span data-stu-id="868fe-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="868fe-106">Aby utworzyć geometrii złożonego z co najmniej dwóch geometrii, użyj <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="868fe-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="868fe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="868fe-107">Example</span></span>  
 <span data-ttu-id="868fe-108">W poniższym przykładzie <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenie geometrii `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="868fe-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="868fe-109">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.</span><span class="sxs-lookup"><span data-stu-id="868fe-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="868fe-110">![Wyłącz wyniki użycia trybu łączenia](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="868fe-110">![Results of the Exclude combine mode](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="868fe-111">Wyklucz połączone Geometrie</span><span class="sxs-lookup"><span data-stu-id="868fe-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="868fe-112">W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="868fe-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="868fe-113">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.</span><span class="sxs-lookup"><span data-stu-id="868fe-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="868fe-114">![Wyniki INTERSECT połączyć tryb](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="868fe-114">![Results of the Intersect combine mode](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="868fe-115">Intersect połączone Geometrie</span><span class="sxs-lookup"><span data-stu-id="868fe-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="868fe-116">W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Union`.</span><span class="sxs-lookup"><span data-stu-id="868fe-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="868fe-117">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.</span><span class="sxs-lookup"><span data-stu-id="868fe-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="868fe-118">![Wyniki Unii połączyć tryb](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="868fe-118">![Results of the Union combine mode](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="868fe-119">Unia połączone Geometrie</span><span class="sxs-lookup"><span data-stu-id="868fe-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="868fe-120">W niej następujące znaczniki <xref:System.Windows.Media.CombinedGeometry> jest zdefiniowana za pomocą trybu łączenia `Xor`.</span><span class="sxs-lookup"><span data-stu-id="868fe-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="868fe-121">Zarówno <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> są definiowane jako okręgów, tego samego serwera radius, ale z przesunięciem centra o 50.</span><span class="sxs-lookup"><span data-stu-id="868fe-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="868fe-122">![Wyniki Xor użycia trybu łączenia](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="868fe-122">![Results of the Xor combine mode](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="868fe-123">Xor połączone Geometrie</span><span class="sxs-lookup"><span data-stu-id="868fe-123">Combined Geometry Xor</span></span>
