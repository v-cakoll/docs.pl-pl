---
title: 'Instrukcje: Przerzucanie element interfejsu użytkownika w poziomie lub w pionie'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767071"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Instrukcje: Przerzucanie element interfejsu użytkownika w poziomie lub w pionie
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ScaleTransform> przerzucić <xref:System.Windows.UIElement> poziomo czy pionowo. W tym przykładzie <xref:System.Windows.Controls.Button> kontroli (typ <xref:System.Windows.UIElement>) jest odwrócony, stosując <xref:System.Windows.Media.ScaleTransform> do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższa ilustracja przedstawia przycisk do przerzucenia.  
  
 ![Przycisk bez przekształcenia](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
Element interfejsu użytkownika do przerzucenia  
  
 Poniżej przedstawiono kod, który tworzy przycisku.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Przykład  
 Aby przerzucić przycisku w poziomie, należy utworzyć <xref:System.Windows.Media.ScaleTransform> i ustaw jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości na wartość -1. Zastosuj <xref:System.Windows.Media.ScaleTransform> na przycisk <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Przycisk poziomo przerzucane o &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
Przycisk po zastosowaniu ScaleTransform —  
  
## <a name="example"></a>Przykład  
 Jak widać na poprzedniej ilustracji, przycisk został przerzucać, ale również została przeniesiona. Wynika to z przycisku został przerzucać z jego lewym górnym rogu. Aby przerzucić przycisku w miejscu, chcesz zastosować <xref:System.Windows.Media.ScaleTransform> do jego center, a nie jego rogu. Prosty sposób zastosowania <xref:System.Windows.Media.ScaleTransform> do przycisków Centrum jest ustawienie przycisku <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość 0,5 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Przycisk poziomo przerzucane o jej środka](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Przycisk z RenderTransformOrigin cosinus 0,5 0,5  
  
## <a name="example"></a>Przykład  
 Aby przerzucić przycisku w pionie, należy ustawić <xref:System.Windows.Media.ScaleTransform> obiektu <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości zamiast jego <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Przycisk w pionie przerzucane o jej środka](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
W pionie odwrócony przycisku  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia — przegląd](../graphics-multimedia/transforms-overview.md)
