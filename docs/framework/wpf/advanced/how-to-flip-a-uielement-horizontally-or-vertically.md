---
title: Jak przerzucić element interfejsu użytkownika w poziomie lub w pionie
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 89dcf668f1fe361480dabdab227a35ea40c344a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Jak przerzucić element interfejsu użytkownika w poziomie lub w pionie
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ScaleTransform> do przerzucenia <xref:System.Windows.UIElement> poziomo czy pionowo. W tym przykładzie <xref:System.Windows.Controls.Button> formantu (typu <xref:System.Windows.UIElement>) jest odwrócony, stosując <xref:System.Windows.Media.ScaleTransform> do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Na poniższej ilustracji przedstawiono przycisku do przerzucenia.  
  
 ![Przycisk bez przekształcenia](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
UIElement do przerzucenia  
  
 Poniżej przedstawiono kod, który tworzy przycisku.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Przykład  
 Przerzuć przycisku w poziomie, należy utworzyć <xref:System.Windows.Media.ScaleTransform> i ustawić jej <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości na wartość -1. Zastosuj <xref:System.Windows.Media.ScaleTransform> na przycisk <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Przycisk poziomie przerzucane o &#40;0,0&#41;](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
Przycisk po zastosowaniu ScaleTransform  
  
## <a name="example"></a>Przykład  
 Jak widać na poprzedniej ilustracji, przycisk został odwrócony, ale również została przeniesiona. Wynika to z przycisku został odwrócony z jego lewym górnym rogu. Aby odwrócić przycisku w miejscu, które chcesz zastosować <xref:System.Windows.Media.ScaleTransform> jego Centrum, a nie jej rogu. Łatwo zastosować <xref:System.Windows.Media.ScaleTransform> do przycisków Centrum jest skonfigurowanie przycisku <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Przycisk poziomie przerzucane o jego center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Przycisk RenderTransformOrigin 0,5, 0,5  
  
## <a name="example"></a>Przykład  
 Aby przerzucić przycisku w pionie, ustaw <xref:System.Windows.Media.ScaleTransform> obiektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości zamiast jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Przycisk pionowo przerzucane o jego center](../../../../docs/framework/wpf/advanced/media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
Przycisk pionowo odwrócony  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
