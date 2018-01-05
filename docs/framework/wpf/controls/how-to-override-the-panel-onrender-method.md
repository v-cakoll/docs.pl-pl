---
title: "Jak zastąpić metodę panela OnRender"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 958595cdfa521b372270d6283c7134ef0ba0ef79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
