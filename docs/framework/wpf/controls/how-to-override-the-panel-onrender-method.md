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
ms.openlocfilehash: 8f3b65bdfe96efdc57c6b8d30991439d3bdb0bc5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506218"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Jak zastąpić metodę panela OnRender
Ten przykład przedstawia sposób przesłonięcia <xref:System.Windows.Controls.Panel.OnRender%2A> metody <xref:System.Windows.Controls.Panel> celu stosowanie efektów niestandardowych graficznego elementu układu.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Controls.Panel.OnRender%2A> metody, aby można było dodać efekty graficzne do elementu renderowanego panelu. Na przykład służy tej metody można dodać obramowanie niestandardowe lub efekty w tle. A <xref:System.Windows.Media.DrawingContext> obiekt jest przekazywany jako argument, który udostępnia metody do rysowania kształtów, tekstu, obrazów lub wideo. W rezultacie ta metoda jest przydatna do dostosowywania obiektów panel.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Panel>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Przykładowe niestandardowe panelu promieniowego](https://go.microsoft.com/fwlink/?LinkID=159982)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
