---
title: 'Instrukcje: Obsłuż załadowane zdarzenie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 187d75c436913140855f4d860eb3b6ad4656f309
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682946"
---
# <a name="how-to-handle-a-loaded-event"></a>Instrukcje: Obsłuż załadowane zdarzenie
W tym przykładzie pokazano, jak obsługiwać <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> zdarzeń i odpowiedni scenariusz obsługi tego zdarzenia. Tworzy program obsługi <xref:System.Windows.Controls.Button> po załadowaniu strony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wraz z pliku CodeBehind.  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.FrameworkElement>
- [Zdarzenia okresu istnienia obiektu](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)
- [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
