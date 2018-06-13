---
title: Jak dostosować rozmiar miniatury na ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 689b73eb58cdfceb2ce5d4e76cbbc3d6c5af8967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551807"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Jak dostosować rozmiar miniatury na ScrollBar
W tym temacie wyjaśniono, jak ustawić <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> o stałym rozmiarze i sposobu określania minimalny rozmiar <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> mający <xref:System.Windows.Controls.Primitives.Thumb> o stałym rozmiarze. Ustawia przykład <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> właściwość <xref:System.Windows.Controls.Primitives.Thumb> do <xref:System.Double.NaN> i Ustawia wysokość <xref:System.Windows.Controls.Primitives.Thumb>.  Aby utworzyć poziomym <xref:System.Windows.Controls.Primitives.ScrollBar> z <xref:System.Windows.Controls.Primitives.Thumb> mający stałą szerokość, Ustaw szerokość <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Opis  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> mający <xref:System.Windows.Controls.Primitives.Thumb> z minimalny rozmiar. W przykładzie wartość <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Aby utworzyć poziomym <xref:System.Windows.Controls.Primitives.ScrollBar> z <xref:System.Windows.Controls.Primitives.Thumb> zawierającego minimalnej szerokości, ustaw <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [ScrollBar — style i szablony](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
