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
ms.openlocfilehash: c4539847368c1a5789e99ec92106d17077ed5943
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102534"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Instrukcje: Zastępowanie metody OnRender panelu
Ten przykład przedstawia sposób przesłonięcia <xref:System.Windows.Controls.Panel.OnRender%2A> metody <xref:System.Windows.Controls.Panel> celu stosowanie efektów niestandardowych graficznego elementu układu.  
  
## <a name="example"></a>Przykład  
 Użyj <xref:System.Windows.Controls.Panel.OnRender%2A> metody, aby można było dodać efekty graficzne do elementu renderowanego panelu. Na przykład służy tej metody można dodać obramowanie niestandardowe lub efekty w tle. A <xref:System.Windows.Media.DrawingContext> obiekt jest przekazywany jako argument, który udostępnia metody do rysowania kształtów, tekstu, obrazów lub wideo. W rezultacie ta metoda jest przydatna do dostosowywania obiektów panel.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Panel>
- [Panele — omówienie](panels-overview.md)
- [Przykładowe niestandardowe panelu promieniowego](https://go.microsoft.com/fwlink/?LinkID=159982)
- [Tematy z instrukcjami](panel-how-to-topics.md)
