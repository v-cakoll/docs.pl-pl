---
title: 'Optymalizacja wydajności: inne zalecenia'
ms.date: 03/30/2017
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
ms.openlocfilehash: cf621ab5f423e2465999b26f32489af1132bece0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582452"
---
# <a name="optimizing-performance-other-recommendations"></a>Optymalizacja wydajności: inne zalecenia
<a name="introduction"></a>Ten temat zawiera zalecenia dotyczące wydajności, a także te, które zostały omówione w sekcji [Optymalizacja wydajności aplikacji WPF](optimizing-wpf-application-performance.md) .  
  
 Ten temat zawiera następujące sekcje:  
  
- [Nieprzezroczystość pędzli i nieprzezroczystość elementów](#Opacity)  
  
- [Nawigacja do obiektu](#Navigation_Objects)  
  
- [Testowanie trafień na dużych powierzchniach 3W](#Hit_Testing)  
  
- [Zdarzenie CompositionTarget. renderingu](#CompositionTarget_Rendering_Event)  
  
- [Unikaj używania ScrollBarVisibility =](#Avoid_Using_ScrollBarVisibility)  
  
- [Konfigurowanie Cache Service czcionki w celu skrócenia czasu uruchamiania](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Nieprzezroczystość pędzli i nieprzezroczystość elementów  
 W przypadku używania <xref:System.Windows.Media.Brush> do ustawiania <xref:System.Windows.Shapes.Shape.Fill%2A> lub <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, lepiej jest ustawić wartość <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType>, a nie ustawienie właściwości <xref:System.Windows.UIElement.Opacity%2A> elementu. Modyfikacja właściwości <xref:System.Windows.UIElement.Opacity%2A> elementu może spowodować, że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzyć tymczasową powierzchnię.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nawigacja do obiektu  
 Obiekt <xref:System.Windows.Navigation.NavigationWindow> pochodzi od <xref:System.Windows.Window> i rozszerza go o obsługę nawigacji zawartości, głównie poprzez agregowanie <xref:System.Windows.Navigation.NavigationService> i dziennika. Obszar klienta <xref:System.Windows.Navigation.NavigationWindow> można zaktualizować, określając identyfikator URI (Uniform Resource Identifier) lub obiekt. Poniższy przykład pokazuje obie metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Każdy obiekt <xref:System.Windows.Navigation.NavigationWindow> ma arkusz, który rejestruje historię przeglądania użytkownika w tym oknie. Jednym z celów tego dziennika jest umożliwienie użytkownikom śledzenia ich kroków.  
  
 W przypadku nawigowania przy użyciu identyfikatora URI (Uniform Resource Identifier) w dzienniku jest przechowywany tylko odwołanie Uniform Resource Identifier (URI). Oznacza to, że za każdym razem, gdy ponownie odwiedzasz stronę, jest ona dynamicznie ponownie skonstruowana, co może być czasochłonne w zależności od złożoności strony. W takim przypadku koszt magazynu dziennika jest niski, ale czas na odtworzenia strony jest potencjalnie wysoki.  
  
 Podczas nawigowania przy użyciu obiektu, w dzienniku jest przechowywane całe drzewo wizualne obiektu. Oznacza to, że za każdym razem, gdy ponownie zostanie wyświetlona strona, jest ona renderowana natychmiast bez konieczności ponownego konstruowania. W takim przypadku koszt magazynu dziennika jest wysoki, ale czas na odtworzenia strony jest niski.  
  
 W przypadku korzystania z obiektu <xref:System.Windows.Navigation.NavigationWindow> należy pamiętać, że obsługa rejestrowania wpływa na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Testowanie trafień na dużych powierzchniach 3W  
 Testowanie trafień na dużych powierzchniach 3W jest bardzo intensywną operacją w zakresie użycia procesora CPU. Jest to szczególnie prawdziwe, gdy powierzchnia 3W jest animowana. Jeśli na tych powierzchni nie jest wymagane testowanie trafień, wyłącz testowanie trafień. Obiekty pochodzące z <xref:System.Windows.UIElement> mogą wyłączyć testowanie trafień, ustawiając właściwość <xref:System.Windows.UIElement.IsHitTestVisible%2A> na `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Zdarzenie CompositionTarget. renderingu  
 Zdarzenie <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> powoduje ciągłą animację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jeśli używasz tego zdarzenia, odłączaj je w każdej okazji.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Unikaj używania ScrollBarVisibility =  
 Jeśli to możliwe, Unikaj używania wartości <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> dla właściwości `HorizontalScrollBarVisibility` i `VerticalScrollBarVisibility`. Te właściwości są zdefiniowane dla obiektów <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer> i <xref:System.Windows.Controls.TextBox> oraz jako właściwość dołączona do obiektu <xref:System.Windows.Controls.ListBox>. Zamiast tego należy ustawić <xref:System.Windows.Controls.ScrollBarVisibility> na <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden> lub <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 Wartość <xref:System.Windows.Controls.ScrollBarVisibility.Auto> jest przeznaczona dla przypadków, gdy ilość miejsca jest ograniczona, a paski przewijania powinny być wyświetlane tylko w razie potrzeby. Na przykład przydatne może być użycie tej <xref:System.Windows.Controls.ScrollBarVisibility> wartości z <xref:System.Windows.Controls.ListBox> 30 elementów, a nie <xref:System.Windows.Controls.TextBox> z setkami wierszy tekstu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurowanie Cache Service czcionki w celu skrócenia czasu uruchamiania  
 Usługa [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] buforowania czcionek udostępnia dane czcionki między aplikacjami [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Pierwsza uruchomiona aplikacja [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uruchamia tę usługę, jeśli usługa nie jest już uruchomiona. Jeśli używasz [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], możesz ustawić opcję "Windows Presentation Foundation (WPF) 3.0.0.0 pamięci podręcznej czcionek" z "ręczne" (domyślnie) na "Automatyczne (opóźnione uruchomienie)", aby skrócić początkowy czas uruchamiania aplikacji [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
## <a name="see-also"></a>Zobacz także

- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Animacja — porady i wskazówki](../graphics-multimedia/animation-tips-and-tricks.md)
