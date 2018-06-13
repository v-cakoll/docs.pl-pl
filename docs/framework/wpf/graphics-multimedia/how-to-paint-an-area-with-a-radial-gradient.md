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
ms.openlocfilehash: d794f85ce4968e1cf1759df5358834f3b4cdfb50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560645"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Jak malować obszar gradientem promieniowym
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.RadialGradientBrush> klasy namalować obszar o gradientu promieniowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.RadialGradientBrush> namalować prostokąt z gradientu promieniowego, który przejścia z żółtym na kolor czerwony, niebieski do Limonowy zielony.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono gradientu z poprzedniego przykładu. Zatrzymuje gradientu ma zostały wyróżnione.  
  
 ![Gradientu promieniowego gradientu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Przykłady w tym temacie Korzystanie z systemu współrzędnych domyślne ustawienie punkty kontrolne. System współrzędnych domyślna jest określana względem obwiedni: 0 wskazuje 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute>. Bezwzględny układ współrzędnych nie jest określana względem obwiedni. Wartości są interpretowane bezpośrednio w lokalnej przestrzeni.  
  
 Aby uzyskać dodatkowe <xref:System.Windows.Media.RadialGradientBrush> przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat gradientach i innych typów pędzle zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
