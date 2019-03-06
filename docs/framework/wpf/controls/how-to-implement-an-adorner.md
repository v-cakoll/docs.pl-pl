---
title: 'Instrukcje: Implementuj moduł definiowania układu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: 53a25396ba5d8a5c78e850e636b7c882c03d5152
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362646"
---
# <a name="how-to-implement-an-adorner"></a>Instrukcje: Implementuj moduł definiowania układu
Ten przykład pokazuje implementację minimalny moduł definiowania układu kodu.  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ważne jest, aby należy pamiętać, moduły definiowania układu nie ma żadnych zachowań nieprzerwaną pracę renderowania; zapewnienie, że moduł definiowania układu renderuje spoczywa implementujący moduł definiowania układu kodu.   Często stosowaną metodą wdrażania zachowanie renderowania jest zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody i używać co najmniej jednej <xref:System.Windows.Media.DrawingContext> obiekty do renderowania moduł definiowania układu wizualizacji, zgodnie z potrzebami (jak pokazano w tym przykładzie).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Niestandardowy moduł definiowania układu, w której jest tworzona poprzez implementację klasy, która dziedziczy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.  Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> przy użyciu kółka przez zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Zobacz także
- [Moduły indeksowania układu — omówienie](adorners-overview.md)
