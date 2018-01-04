---
title: "Optymalizacja wydajności: zasoby aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0a7c9920b321f15f3f01a64fbfc80693042a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-application-resources"></a>Optymalizacja wydajności: zasoby aplikacji
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]pozwala na udostępnianie zasobów aplikacji tak, aby między wpisane podobne elementy można obsługiwać spójny wygląd i zachowanie. Ten temat zawiera kilka zaleceń w tym obszarze, to może pomóc zwiększyć wydajność aplikacji.  
  
 Aby uzyskać więcej informacji dotyczących zasobów, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Udostępnianie zasobów  
 Jeśli aplikacja korzysta z Kontrolki niestandardowe i definiuje zasobów w <xref:System.Windows.ResourceDictionary> (lub węzeł zasoby XAML), zaleca się albo zdefiniowania zasobów w <xref:System.Windows.Application> lub <xref:System.Windows.Window> obiekt poziom lub je zdefiniować w motyw domyślny dla Formanty niestandardowe. Definiowanie zasobów w kontrolkę niestandardową <xref:System.Windows.ResourceDictionary> nakłada negatywny wpływ na wydajność dla każdego wystąpienia tego formantu. Na przykład jeśli masz pędzla intensywnie wydajności operacji zdefiniowane jako część definicji zasobu kontrolkę niestandardową oraz wiele wystąpień formantu niestandardowego zestawu roboczego aplikacji znacznie wzrośnie.  
  
 Aby zilustrować ten punkt, należy rozważyć następujące kwestie. Załóżmy, że tworzysz karty gier using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Dla większości gier trzeba 52 kart o różnych powierzchni 52. Decyzję o implementacji niestandardowego formantu karty i zdefiniuj 52 pędzle (każdy reprezentuje krój karty) w zasobach formantu niestandardowego karty. W głównej aplikacji początkowo utworzyć 52 wystąpień tej kontrolki niestandardowej karty. Każde wystąpienie kontrolki niestandardowej karty generuje 52 wystąpienia <xref:System.Windows.Media.Brush> obiektów, które daje łączną liczbę 52 * 52 <xref:System.Windows.Media.Brush> obiektów w aplikacji. Przenosząc pędzle poza karty zasobów formantu niestandardowego do <xref:System.Windows.Application> lub <xref:System.Windows.Window> poziomie obiektu lub Definiowanie motyw domyślny dla kontrolki niestandardowej, można zmniejszyć zestaw roboczy aplikacji, ponieważ są teraz udostępnianie 52 pędzle wśród 52 wystąpienia formantu karty.  
  
## <a name="sharing-a-brush-without-copying"></a>Udostępnianie pędzla bez kopiowania  
 Jeśli masz wiele elementów korzystającej z tego samego <xref:System.Windows.Media.Brush> obiektu, Zdefiniuj pędzel jako zasób i odwołać, a nie definiowanie w tekście pędzla w [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Ta metoda będzie utworzyć jedno wystąpienie i ponownego wykorzystania, natomiast definiowanie w tekście pędzle w [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] tworzy nowe wystąpienie dla każdego elementu.  
  
 Poniższy przykładowy kod znaczników ilustruje tę sytuację:  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Korzystanie z zasobów statycznych, gdy jest to możliwe  
 Zasób statycznej zapewnia wartość dla każdego atrybutu właściwości XAML wyszukując odwołanie do zasobu już zdefiniowane. Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem wyszukiwania kompilacji.  
  
 Zasób dynamicznej z drugiej strony, utworzy wyrażenia tymczasowego podczas początkowej kompilacji i w związku z tym odroczenie wyszukiwania zasobów, dopóki wartość żądany zasób nie zostanie faktycznie wymagane do utworzenia obiektu. Zachowanie wyszukiwania dla tego zasobu jest odpowiednikiem odnośników czasu wykonywania, która nakłada negatywny wpływ na wydajność. Użyj zasoby statyczne, jeśli to możliwe w aplikacji, korzystając z zasobów dynamicznej tylko wtedy, gdy jest to konieczne.  
  
 Poniższy przykładowy kod znaczników pokazano sposób użycia obu typów zasobów:  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Inne zalecenia dotyczące wydajności](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
