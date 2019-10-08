---
title: 'Optymalizacja wydajności: zasoby aplikacji'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 759d02afe1934d2ace4ed226d5d911db2d676d98
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005039"
---
# <a name="optimizing-performance-application-resources"></a>Optymalizacja wydajności: zasoby aplikacji
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia udostępnianie zasobów aplikacji, co pozwala na obsługę spójnego wyglądu lub zachowań w różnych typach. Ten temat zawiera kilka zaleceń w tym obszarze, które mogą pomóc w ulepszaniu wydajności aplikacji.  
  
 Aby uzyskać więcej informacji o zasobach, zobacz [zasoby XAML](xaml-resources.md).  
  
## <a name="sharing-resources"></a>Udostępnianie zasobów  
 Jeśli aplikacja używa niestandardowych kontrolek i definiuje zasoby w <xref:System.Windows.ResourceDictionary> (lub węźle zasobów XAML), zaleca się zdefiniowanie zasobów na poziomie <xref:System.Windows.Application> lub <xref:System.Windows.Window> lub zdefiniowanie ich w motywie domyślnym dla kontrolek niestandardowych. Definiowanie zasobów w @no__t formantu niestandardowego — 0 nakłada wpływ na wydajność dla każdego wystąpienia tej kontrolki. Na przykład, jeśli istnieją operacje pędzla intensywnie korzystające z wydajności zdefiniowane jako część definicji zasobu kontrolki niestandardowej i wiele wystąpień kontrolki niestandardowej, zestaw roboczy aplikacji ulegnie znacznemu zwiększeniu.  
  
 Aby zilustrować ten punkt, należy wziąć pod uwagę następujące kwestie. Załóżmy, że tworzysz grę karcianą przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. W przypadku większości gier kart potrzebne są 52 kart z 52 różnymi twarzami. Użytkownik chce zaimplementować kontrolkę niestandardową karty i definiować 52 pędzli (z których każda reprezentuje kartę) w zasobach niestandardowej kontrolki karta. W aplikacji głównej początkowo utworzysz wystąpienia 52 tej karty niestandardowej. Każde wystąpienie kontrolki niestandardowej karty generuje wystąpienia 52 obiektów <xref:System.Windows.Media.Brush>, co daje w wyniku łączną 52 52 liczbę obiektów <xref:System.Windows.Media.Brush> w aplikacji. Przenosząc pędzle z zasobów kontrolki niestandardowej karty do poziomu obiektu <xref:System.Windows.Application> lub <xref:System.Windows.Window> lub definiują je w motywie domyślnym dla kontrolki niestandardowej, zmniejszasz zestaw roboczy aplikacji, ponieważ teraz udostępniamy pędzle 52 między 52 wystąpienia kontrolki karta.  
  
## <a name="sharing-a-brush-without-copying"></a>Udostępnianie pędzla bez kopiowania  
 Jeśli masz wiele elementów korzystających z tego samego obiektu <xref:System.Windows.Media.Brush>, zdefiniuj pędzel jako zasób i odwołuje się do niego, zamiast definiować pędzle w języku XAML. Ta metoda utworzy jedno wystąpienie i użyje go ponownie, a Definiowanie pędzli w tekście w języku XAML tworzy nowe wystąpienie dla każdego elementu.  
  
 Poniższy przykład znaczników ilustruje ten punkt:  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Używaj zasobów statycznych, gdy jest to możliwe  
 Zasób statyczny udostępnia wartość dowolnego atrybutu właściwości XAML przez wyszukanie odwołania do już zdefiniowanego zasobu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie kompilacji.  
  
 Zasób dynamiczny, z drugiej strony, utworzy tymczasowe wyrażenie podczas początkowej kompilacji i w ten sposób opóźnia Wyszukiwanie zasobów do momentu, gdy żądana wartość zasobu jest rzeczywiście wymagana w celu skonstruowania obiektu. Zachowanie wyszukiwania dla tego zasobu jest analogiczne do wyszukiwania w czasie wykonywania, które nakłada wpływ na wydajność. Używaj zasobów statycznych wszędzie tam, gdzie jest to możliwe w aplikacji, używając zasobów dynamicznych tylko w razie potrzeby.  
  
 Poniższy przykład znaczników pokazuje użycie obu typów zasobów:  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md)
- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Inne zalecenia dotyczące wydajności](optimizing-performance-other-recommendations.md)
