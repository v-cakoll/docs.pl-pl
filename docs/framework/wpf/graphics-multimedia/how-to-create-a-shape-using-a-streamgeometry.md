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
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Instrukcje: Tworzenie kształtu przy użyciu elementu StreamGeometry
<xref:System.Windows.Media.StreamGeometry> jest uproszczone alternatywa dla <xref:System.Windows.Media.PathGeometry> do tworzenia kształtów geometrycznych. Użyj <xref:System.Windows.Media.StreamGeometry> niezbędne, aby opisać złożone typy geometryczne, ale nie chcesz koszty obsługi powiązań danych, animacji lub modyfikacji. Na przykład ze względu na jego wydajność <xref:System.Windows.Media.StreamGeometry> klasy jest dobrym wyborem dla opisu moduły definiowania układu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto składni atrybutów, aby utworzyć trójkątna <xref:System.Windows.Media.StreamGeometry> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.StreamGeometry> składni atrybutów, zobacz [składni znacznikowania ścieżki](path-markup-syntax.md) strony.  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie użyto <xref:System.Windows.Media.StreamGeometry> do definiowania trójkąta w kodzie. Po pierwsze w przykładzie jest tworzony <xref:System.Windows.Media.StreamGeometry>, następnie uzyskuje <xref:System.Windows.Media.StreamGeometryContext> i używa go do opisania trójkąt.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Przykład  
 Następny przykład tworzy metodę, która używa <xref:System.Windows.Media.StreamGeometry> i <xref:System.Windows.Media.StreamGeometryContext> do definiowania kształtu geometrycznego, w oparciu o określonych parametrów.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [Tworzenie kształtu przy użyciu elementu PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [Geometria — przegląd](geometry-overview.md)
