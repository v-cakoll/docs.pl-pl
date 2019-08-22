---
title: 'Instrukcje: Zastępowanie metody OnRender panelu'
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666714"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Instrukcje: Zastępowanie metody OnRender panelu
Ten przykład pokazuje, <xref:System.Windows.Controls.Panel.OnRender%2A> jak zastąpić <xref:System.Windows.Controls.Panel> metodę w celu dodania niestandardowych efektów graficznych do elementu układu.  
  
## <a name="example"></a>Przykład  
 Użyj metody <xref:System.Windows.Controls.Panel.OnRender%2A> , aby dodać efekty graficzne do renderowanego elementu panelu. Na przykład można użyć tej metody, aby dodać obramowanie niestandardowe lub efekty tła. <xref:System.Windows.Media.DrawingContext> Obiekt jest przekazaniem jako argument, który zapewnia metody rysowania kształtów, tekstu, obrazów lub filmów wideo. W związku z tym ta metoda jest przydatna do dostosowywania obiektu panelu.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Panel>
- [Panele — omówienie](panels-overview.md)
- [Tematy z instrukcjami](panel-how-to-topics.md)
