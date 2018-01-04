---
title: "Optymalizacja wydajności: inne zalecenia"
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
- Terminal Services rendering [WPF]
- opacity [WPF]
- hit-test objects [WPF]
- ScrollBarVisibility enumeration [WPF]
- brushes [WPF], performance
ms.assetid: d028cc65-7e97-4a4f-9859-929734eaf40d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e45296befd51af5e4b03f123241efba030fd3754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-other-recommendations"></a>Optymalizacja wydajności: inne zalecenia
<a name="introduction"></a>W tym temacie przedstawiono zalecenia dotyczące wydajności, oprócz tych objętych tematy w [optymalizacji wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md) sekcji.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Nieprzezroczystość na pędzle i nieprzezroczystości dla elementów](#Opacity)  
  
-   [Nawigacja do obiektu](#Navigation_Objects)  
  
-   [Testowanie na dużych powierzchni 3D trafień](#Hit_Testing)  
  
-   [Zdarzenie CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
-   [Unikaj używania ScrollBarVisibility = Auto](#Avoid_Using_ScrollBarVisibility)  
  
-   [Konfigurowanie usługi pamięć podręczna czcionki, aby skrócić czas uruchamiania](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Nieprzezroczystość na pędzle i nieprzezroczystości dla elementów  
 Jeśli używasz <xref:System.Windows.Media.Brush> można ustawić <xref:System.Windows.Shapes.Shape.Fill%2A> lub <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, zaleca się ustawić <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> wartość zamiast ustawienie elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości. Zmodyfikowanie elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości może spowodować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] można utworzyć tymczasowego powierzchni.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nawigacja do obiektu  
 <xref:System.Windows.Navigation.NavigationWindow> Pochodną obiektu <xref:System.Windows.Window> i rozszerza ją z obsługą nawigację po zawartości, przede wszystkim przez agregowanie <xref:System.Windows.Navigation.NavigationService> i dziennika. Można aktualizować obszaru klienckiego <xref:System.Windows.Navigation.NavigationWindow> , określając albo [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] lub obiektu. Poniższy przykład pokazuje obie metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Każdy <xref:System.Windows.Navigation.NavigationWindow> obiekt ma dziennika, który rejestruje historii nawigacji użytkownika w danym przedziale. Jednym z celów dziennika jest umożliwienie użytkownikom odtworzenie ich czynności.  
  
 Po przejściu przy użyciu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], dziennika są przechowywane tylko [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołania. Oznacza to, że zawsze ponownie strony, jego jest dynamicznie odtworzone, co może być czasochłonne w zależności od złożoności strony. W takim przypadku koszt magazynu dziennika jest niska, ale czas do odtworzenia strony jest potencjalnie wysoki.  
  
 Po przejściu przy użyciu obiektu, arkusz przechowuje całego drzewa wizualnego obiektu. Oznacza to, zawsze ponownie stronie renderowania natychmiast bez konieczności odtworzony. W takim przypadku koszt magazynu dziennika jest wysoka, ale brakuje czas odtworzenia strony.  
  
 Jeśli używasz <xref:System.Windows.Navigation.NavigationWindow> obiektu, należy pamiętać, jak obsługa rejestrowanie ma wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testowanie na dużych powierzchni 3D trafień  
 Testowanie trafień na dużych powierzchni 3D jest bardzo wydajności to intensywna operacja pod względem użycie procesora CPU. Dotyczy to zwłaszcza 3D powierzchni jest animacji. Jeśli nie wymagają testowania trafień na te powierzchnie, Wyłącz testowanie trafień. Obiekty, które są pochodnymi <xref:System.Windows.UIElement> można wyłączyć testowania trafień przez ustawienie <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwości `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Zdarzenie CompositionTarget.Rendering  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Zdarzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stale animacji. Jeśli używasz tego zdarzenia, należy ją odłączyć przy okazji każdego.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Unikaj używania ScrollBarVisibility = Auto  
 Jeśli to możliwe, należy unikać <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> wartość `HorizontalScrollBarVisibility` i `VerticalScrollBarVisibility` właściwości. Te właściwości są definiowane dla <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, i <xref:System.Windows.Controls.TextBox> obiektów, a jako dołączona właściwość dla <xref:System.Windows.Controls.ListBox> obiektu. Zamiast tego należy ustawić <xref:System.Windows.Controls.ScrollBarVisibility> do <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, lub <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Wartość jest przeznaczona dla przypadków, gdy ilość miejsca jest ograniczona, a tylko powinny być wyświetlane paski przewijania, gdy jest to konieczne. Na przykład mogą być użyteczne użyć tego <xref:System.Windows.Controls.ScrollBarVisibility> wartości z <xref:System.Windows.Controls.ListBox> 30 elementów w przeciwieństwie do <xref:System.Windows.Controls.TextBox> setki wierszy tekstu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurowanie usługi pamięć podręczna czcionki, aby skrócić czas uruchamiania  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Usługi pamięć podręczna czcionki udostępnia dane czcionek między [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Pierwszy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uruchomieniu aplikacji uruchamia tej usługi, jeśli usługa nie jest już uruchomiona. Jeśli używasz [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], można ustawić "[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] pamięci podręcznej czcionki 3.0.0.0" usługi "Ręczny" (wartość domyślna) ma wartość "Automatycznie (opóźnione uruchomienie)" w celu skrócenia czasu początkowego rozruchu z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Planowanie wydajności aplikacji](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Wykorzystanie możliwości sprzętu](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Układ i projekt](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Grafika 2D i obrazowanie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Zachowanie obiektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Animacja — porady i wskazówki](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
