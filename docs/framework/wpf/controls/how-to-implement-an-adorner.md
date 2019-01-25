---
title: 'Instrukcje: Implementuj moduł definiowania układu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f34bdeb87d0bf34a998f9b2e2fb6c42aedec5063
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591685"
---
# <a name="how-to-implement-an-adorner"></a>Instrukcje: Implementuj moduł definiowania układu
Ten przykład pokazuje implementację minimalny moduł definiowania układu kodu.  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ważne jest, aby należy pamiętać, moduły definiowania układu nie ma żadnych zachowań nieprzerwaną pracę renderowania; zapewnienie, że moduł definiowania układu renderuje spoczywa implementujący moduł definiowania układu kodu.   Często stosowaną metodą wdrażania zachowanie renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i używać co najmniej jednej <xref:System.Windows.Media.DrawingContext> obiekty do renderowania moduł definiowania układu wizualizacji, zgodnie z potrzebami (jak pokazano w tym przykładzie).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Niestandardowy moduł definiowania układu, w której jest tworzona poprzez implementację klasy, która dziedziczy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.  Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> przy użyciu kółka przez zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Zobacz także
- [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)
