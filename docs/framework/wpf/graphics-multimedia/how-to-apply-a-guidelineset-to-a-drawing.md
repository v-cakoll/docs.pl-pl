---
title: 'Instrukcje: Stosowanie elementu GuidelineSet do rysowania'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699064"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Instrukcje: Stosowanie elementu GuidelineSet do rysowania
Ten przykład przedstawia sposób zastosowania <xref:System.Windows.Media.GuidelineSet> do <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Klasa jest jedynym typem <xref:System.Windows.Media.Drawing> zawierający <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> właściwości. Aby zastosować <xref:System.Windows.Media.GuidelineSet> do innego typu <xref:System.Windows.Media.Drawing>, dodaj go do <xref:System.Windows.Media.DrawingGroup> , a następnie zastosować <xref:System.Windows.Media.GuidelineSet> do Twojej <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.Windows.Media.DrawingGroup> obiekty, które są niemal identyczne; jedyna różnica polega na: drugi <xref:System.Windows.Media.DrawingGroup> ma <xref:System.Windows.Media.GuidelineSet> i nie jest pierwszy.  
  
 Poniższa ilustracja przedstawia dane wyjściowe z przykładu. Ponieważ renderowania różnica między dwoma <xref:System.Windows.Media.DrawingGroup> obiektów jest więc subtelne, części rysunki są powiększone.  
  
 ![DrawingGroup z lub bez GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
