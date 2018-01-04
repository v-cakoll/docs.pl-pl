---
title: "Jak przesunąć element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f9b8363f0c3b9e0a9653dfc9864727c9460f695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-translate-an-element"></a>Jak przesunąć element
W tym przykładzie pokazano, jak tłumaczenia (przenoszenia) elementu przy użyciu <xref:System.Windows.Media.TranslateTransform>.  
  
 <xref:System.Windows.Media.TranslateTransform> Klasa jest szczególnie przydatna do przenoszenia elementów wewnątrz panele, które nie obsługują bezwzględny. Na przykład stosując <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu, można przenieść elementu w obrębie <xref:System.Windows.Controls.StackPanel> lub <xref:System.Windows.Controls.DockPanel>.  
  
 Użyj <xref:System.Windows.Media.TranslateTransform.X%2A> właściwości <xref:System.Windows.Media.TranslateTransform> do określenia ilości, w pikselach, można przenieść elementu na osi x. Użyj <xref:System.Windows.Media.TranslateTransform.Y%2A> właściwości w celu określenia ilości, w pikselach, aby przenieść element wzdłuż osi y. Na koniec zastosować <xref:System.Windows.Media.TranslateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.TranslateTransform> można przenieść elementu 50 pikseli na prawo i 50 pikseli w dół.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
