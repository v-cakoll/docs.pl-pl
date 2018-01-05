---
title: "Jak implementować moduły definiowania układu"
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
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76bceae5b69fad4c217127617309484edcf18108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-adorner"></a>Jak implementować moduły definiowania układu
Ten przykład przedstawia implementację minimalnego modułu definiowania układu kodu.  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Należy pamiętać, że modułu definiowania układu kodu nie zawierają żadnych zachowania związanego z używaniem renderowania; zapewnienie, że moduł definiowania układu renderuje jest odpowiedzialny za implementujący modułu definiowania układu kodu.   Jest to często stosowana metoda wdrażania sposób renderowania do przesłonięcia <xref:System.Windows.UIElement.OnRender%2A> — metoda i użyj co najmniej jeden <xref:System.Windows.Media.DrawingContext> obiekty do renderowania elementów wizualnych moduł definiowania układu, zgodnie z potrzebami (jak pokazano w tym przykładzie).  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Niestandardowy moduł definiowania układu kodu jest tworzony przez implementującej klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.  Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> z okręgi przez zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)
