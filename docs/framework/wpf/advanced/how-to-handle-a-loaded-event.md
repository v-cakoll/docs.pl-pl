---
title: "Jak obsłużyć załadowane zdarzenie"
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
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35376d3a759e326ae7de77657529c4bed5e38c37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-loaded-event"></a>Jak obsłużyć załadowane zdarzenie
W tym przykładzie przedstawiono sposób obsługi <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> zdarzeń i odpowiednim scenariuszu obsługi tego zdarzenia. Tworzy program obsługi <xref:System.Windows.Controls.Button> załadowanie strony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wraz z pliku CodeBehind.  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement>  
 [Zdarzenia okresu istnienia obiektu](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
