---
title: 'Instrukcje: Tworzenie kształtu przy użyciu elementu StreamGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348032"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="3b7e7-102">Instrukcje: Tworzenie kształtu przy użyciu elementu StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="3b7e7-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="3b7e7-103"><xref:System.Windows.Media.StreamGeometry> jest uproszczone alternatywa dla <xref:System.Windows.Media.PathGeometry> do tworzenia kształtów geometrycznych.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-103"><xref:System.Windows.Media.StreamGeometry> is lightweight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="3b7e7-104">Użyj <xref:System.Windows.Media.StreamGeometry> niezbędne, aby opisać złożone typy geometryczne, ale nie chcesz koszty obsługi powiązań danych, animacji lub modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="3b7e7-105">Na przykład ze względu na jego wydajność <xref:System.Windows.Media.StreamGeometry> klasy jest dobrym wyborem dla opisu moduły definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7e7-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b7e7-106">Example</span></span>  
 <span data-ttu-id="3b7e7-107">W poniższym przykładzie użyto składni atrybutów, aby utworzyć trójkątna <xref:System.Windows.Media.StreamGeometry> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b7e7-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="3b7e7-108">Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.StreamGeometry> składni atrybutów, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7e7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b7e7-109">Example</span></span>  
 <span data-ttu-id="3b7e7-110">W następnym przykładzie użyto <xref:System.Windows.Media.StreamGeometry> do definiowania trójkąta w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="3b7e7-111">Po pierwsze w przykładzie jest tworzony <xref:System.Windows.Media.StreamGeometry>, następnie uzyskuje <xref:System.Windows.Media.StreamGeometryContext> i używa go do opisania trójkąt.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="3b7e7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b7e7-112">Example</span></span>  
 <span data-ttu-id="3b7e7-113">Następny przykład tworzy metodę, która używa <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.StreamGeometryContext> do definiowania kształtu geometrycznego, w oparciu o określonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="3b7e7-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3b7e7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b7e7-114">See also</span></span>

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [<span data-ttu-id="3b7e7-115">Tworzenie kształtu przy użyciu elementu PathGeometry</span><span class="sxs-lookup"><span data-stu-id="3b7e7-115">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [<span data-ttu-id="3b7e7-116">Geometria — przegląd</span><span class="sxs-lookup"><span data-stu-id="3b7e7-116">Geometry Overview</span></span>](geometry-overview.md)
