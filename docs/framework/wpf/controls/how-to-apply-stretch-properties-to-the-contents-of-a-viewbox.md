---
title: Jak zastosować właściwości rozciągania dla zawartości okna widoku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 3e81ec9fd045bb3fcf359943e455d2cce94aec55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552808"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Jak zastosować właściwości rozciągania dla zawartości okna widoku
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak zmienić wartość <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> i <xref:System.Windows.Controls.Viewbox.Stretch%2A> właściwości <xref:System.Windows.Controls.Viewbox>.  
  
 W pierwszym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do definiowania <xref:System.Windows.Controls.Viewbox> elementu. Przypisuje <xref:System.Windows.FrameworkElement.MaxWidth%2A> i <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400. Przykład zagnieżdża <xref:System.Windows.Controls.Image> w elemencie <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button> elementy odpowiadające wartości właściwości <xref:System.Windows.Controls.Viewbox.Stretch%2A> i <xref:System.Windows.Controls.StretchDirection> wyliczenia manipulowania stretching zachowanie zagnieżdżone <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Następujące dojść do pliku CodeBehind <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia który poprzedniej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykładzie zdefiniowano.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>
