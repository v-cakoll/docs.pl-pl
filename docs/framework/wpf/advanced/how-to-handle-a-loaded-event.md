---
title: 'Instrukcje: Obsługa załadowanego zdarzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: b8cd2f5e9d848cebb712e7b4930ca39efe48ecc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122554"
---
# <a name="how-to-handle-a-loaded-event"></a>Instrukcje: Obsługa załadowanego zdarzenia
W tym przykładzie pokazano, jak obsługiwać <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> zdarzeń i odpowiedni scenariusz obsługi tego zdarzenia. Tworzy program obsługi <xref:System.Windows.Controls.Button> po załadowaniu strony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wraz z pliku CodeBehind.  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement>
- [Obiekt okresu istnienia zdarzeń](object-lifetime-events.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [— Tematy porad](base-elements-how-to-topics.md)
