---
title: 'Instrukcje: Dostosuj rozmiar miniatury na ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 30fc72e3f0631b01777bf058c7a7470cc376a547
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354326"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Instrukcje: Dostosuj rozmiar miniatury na ScrollBar
W tym temacie wyjaśniono, jak ustawić <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> o stałym rozmiarze i jak określić minimalny rozmiar <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Przykład  
  
## <a name="description"></a>Opis  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> zawierający <xref:System.Windows.Controls.Primitives.Thumb> o stałym rozmiarze. Przykład ustawia <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> właściwość <xref:System.Windows.Controls.Primitives.Thumb> do <xref:System.Double.NaN> i Ustawia wysokość <xref:System.Windows.Controls.Primitives.Thumb>.  Aby utworzyć poziomej <xref:System.Windows.Controls.Primitives.ScrollBar> za pomocą <xref:System.Windows.Controls.Primitives.Thumb> zawierającego stałej szerokości, Ustaw szerokość <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Opis  
 Poniższy przykład tworzy <xref:System.Windows.Controls.Primitives.ScrollBar> zawierający <xref:System.Windows.Controls.Primitives.Thumb> przy użyciu minimalnego rozmiaru. W przykładzie ustawiono wartość <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Aby utworzyć poziomej <xref:System.Windows.Controls.Primitives.ScrollBar> z <xref:System.Windows.Controls.Primitives.Thumb> zawierający minimalnej szerokości, ustaw <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kod  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Zobacz także
- [ScrollBar — style i szablony](scrollbar-styles-and-templates.md)
