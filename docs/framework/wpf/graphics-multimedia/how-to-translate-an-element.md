---
title: Jak przesunąć element
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111975"
---
# <a name="how-to-translate-an-element"></a>Jak przesunąć element
W tym przykładzie pokazano, jak przetłumaczyć (przenieść) element za pomocą . <xref:System.Windows.Media.TranslateTransform>  
  
 Klasa <xref:System.Windows.Media.TranslateTransform> jest szczególnie przydatna w przypadku ruchomych elementów wewnątrz paneli, które nie obsługują pozycjonowania bezwzględnego. Na przykład, stosując <xref:System.Windows.Media.TranslateTransform> a <xref:System.Windows.UIElement.RenderTransform%2A> do właściwości elementu, można przenieść <xref:System.Windows.Controls.StackPanel> element <xref:System.Windows.Controls.DockPanel>w obrębie lub .  
  
 Użyj <xref:System.Windows.Media.TranslateTransform.X%2A> właściwości, <xref:System.Windows.Media.TranslateTransform> aby określić ilość w pikselach, aby przenieść element wzdłuż osi x. Użyj <xref:System.Windows.Media.TranslateTransform.Y%2A> właściwości, aby określić ilość w pikselach, aby przenieść element wzdłuż osi y. Na koniec zastosuj <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.  
  
 W poniższym przykładzie użyto a, <xref:System.Windows.Media.TranslateTransform> aby przenieść element 50 pikseli w prawo i 50 pikseli w dół.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Zobacz też

- [Przekształcenia — przegląd](transforms-overview.md)
