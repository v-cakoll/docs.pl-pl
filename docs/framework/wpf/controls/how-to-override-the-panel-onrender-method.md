---
title: Jak zastąpić metodę panela OnRender
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: e591bc195d3b0ba58002bda42ddb3e9ed35d312e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554875"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Jak zastąpić metodę panela OnRender
Ten przykład przedstawia sposób przesłonięcia <xref:System.Windows.Controls.Panel.OnRender%2A> metody <xref:System.Windows.Controls.Panel> Aby dodać niestandardowe efektów graficznych do elementu układu.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Controls.Panel.OnRender%2A> metody, aby można było dodać efekty graficzny element renderowany panelu. Na przykład służy tej metody do dodawania niestandardowych obramowanie lub efekty tła. A <xref:System.Windows.Media.DrawingContext> obiekt jest przekazywany jako argument, który udostępnia metody Rysowanie kształtów, tekst, obrazy lub wideo. W związku z tym ta metoda jest przydatna do dostosowania obiektu panelu.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Panel>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Przykład niestandardowych panelu promieniowego](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
