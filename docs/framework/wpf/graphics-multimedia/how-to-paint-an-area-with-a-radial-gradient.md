---
title: Jak malować obszar gradientem promieniowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 75c28cd19ec0423589b6485884842468b89b5e8c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526794"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Jak malować obszar gradientem promieniowym
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.RadialGradientBrush> klasy Maluj obszar gradientem promieniowym.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> prostokąt gradientem promieniowym, które przechodzi z żółty czerwony na niebieski do Limonowozielony malowania.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Poniższa ilustracja przedstawia gradientu z poprzedniego przykładu. Podkreślono zatrzymuje gradientu.  
  
 ![Ograniczniki gradientu w gradient promieniowy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Przykłady w tym temacie na użytek w układzie współrzędnych domyślne ustawienie punktów kontrolnych. System współrzędnych domyślne są określane względem obwiedni: 0 oznacza wartość 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>. Bezwzględnych współrzędnych jest względem obwiedni. Wartości są interpretowane bezpośrednio w przestrzeni lokalnej.  
  
 Dla dodatkowych <xref:System.Windows.Media.RadialGradientBrush> przykłady, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat gradientów oraz inne rodzaje pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
