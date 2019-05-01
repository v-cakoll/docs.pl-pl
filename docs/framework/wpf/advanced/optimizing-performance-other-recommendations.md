---
title: 'Optymalizacja wydajności: Inne zalecenia'
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
ms.openlocfilehash: 56d3e3cad09b46090a11b884f3ac590e8d4ba23a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773103"
---
# <a name="optimizing-performance-other-recommendations"></a>Optymalizacja wydajności: Inne zalecenia
<a name="introduction"></a> Ten temat zawiera zalecenia dotyczące wydajności, oprócz tych objętych tematy w [optymalizowania wydajności aplikacji WPF](optimizing-wpf-application-performance.md) sekcji.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Nieprzezroczystość na pędzle i przezroczystość elementów](#Opacity)  
  
- [Nawigacja do obiektu](#Navigation_Objects)  
  
- [Test na dużych powierzchni 3D trafienia](#Hit_Testing)  
  
- [Zdarzenie CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Unikaj używania scrollbarvisibility — = Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Konfigurowanie usługi pamięci podręcznej czcionki skrócić czas uruchamiania](#FontCache)  
  
<a name="Opacity"></a>   
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Nieprzezroczystość na pędzle i przezroczystość elementów  
 Kiedy używasz <xref:System.Windows.Media.Brush> można ustawić <xref:System.Windows.Shapes.Shape.Fill%2A> lub <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, to lepiej ustawić <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> wartości zamiast ustawienie elementu <xref:System.Windows.UIElement.Opacity%2A> właściwości. Modyfikowanie elementu <xref:System.Windows.UIElement.Opacity%2A> może spowodować, że właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do utworzenia tymczasowego powierzchni.  
  
<a name="Navigation_Objects"></a>   
## <a name="navigation-to-object"></a>Nawigacja do obiektu  
 <xref:System.Windows.Navigation.NavigationWindow> Pochodzi od klasy obiektu <xref:System.Windows.Window> i rozszerza je z obsługą nawigowania po zawartości, przede wszystkim przez agregowanie <xref:System.Windows.Navigation.NavigationService> i dziennika. Możesz zaktualizować obszaru klienckiego <xref:System.Windows.Navigation.NavigationWindow> , określając opcję [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] lub obiektu. Poniższy przykład pokazuje obie metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Każdy <xref:System.Windows.Navigation.NavigationWindow> obiekt ma dziennika, która zawiera rekordy historii nawigacji dla danego użytkownika w tym oknie. Jednym z celów dziennika jest Zezwalaj użytkownikom na odtwarzanie ich kroki.  
  
 Po przejściu przy użyciu [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], dziennika są przechowywane tylko [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] odwołania. Oznacza to, że zawsze ponownie stronę, go jest dynamicznie odtworzone, które mogą być dużo czasu w zależności od złożoności strony. W tym przypadku koszt przechowywania dziennika jest niska, ale czas do odtworzenia strony jest potencjalnie wysoki.  
  
 Po przejściu przy użyciu obiektu, arkusz przechowuje całe drzewo wizualne obiektu. Oznacza to, każdym razem odwiedzisz stronie renderowania bezpośrednio bez konieczności odtworzony. W tym przypadku koszt przechowywania dziennika jest wysoka, ale mało czasu do odtworzenia na stronie.  
  
 Kiedy używasz <xref:System.Windows.Navigation.NavigationWindow> obiektu, należy pamiętać, jak obsługa rejestrowanie ma wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>   
## <a name="hit-testing-on-large-3d-surfaces"></a>Test na dużych powierzchni 3D trafienia  
 Testowanie trafień na dużych powierzchni 3D jest to intensywna operacja bardzo wydajności pod kątem użycia procesora CPU. Jest to szczególnie istotne w przypadku, gdy jest animowanie powierzchni 3D. Jeśli nie potrzebujesz testowania trafień na te powierzchnie, wyłącz, testowanie trafień. Obiekty, które są uzyskiwane z <xref:System.Windows.UIElement> można wyłączyć testowania trafień, ustawiając <xref:System.Windows.UIElement.IsHitTestVisible%2A> właściwość `false`.  
  
<a name="CompositionTarget_Rendering_Event"></a>   
## <a name="compositiontargetrendering-event"></a>Zdarzenie CompositionTarget.Rendering  
 <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> Powoduje, że zdarzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stale animować. Jeśli używasz tego zdarzenia, można go odłączyć przy każdej okazji.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>   
## <a name="avoid-using-scrollbarvisibilityauto"></a>Unikaj używania scrollbarvisibility — = Auto  
 Jeśli to możliwe, należy unikać <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> wartość `HorizontalScrollBarVisibility` i `VerticalScrollBarVisibility` właściwości. Te właściwości są zdefiniowane dla <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.ScrollViewer>, i <xref:System.Windows.Controls.TextBox> obiektów, a jako dołączoną właściwość dla <xref:System.Windows.Controls.ListBox> obiektu. Zamiast tego należy ustawić <xref:System.Windows.Controls.ScrollBarVisibility> do <xref:System.Windows.Controls.ScrollBarVisibility.Disabled>, <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>, lub <xref:System.Windows.Controls.ScrollBarVisibility.Visible>.  
  
 <xref:System.Windows.Controls.ScrollBarVisibility.Auto> Wartość jest przeznaczona dla przypadków, gdy liczba miejsc jest ograniczona i paski przewijania powinien być wyświetlany, gdy jest to konieczne. Na przykład, być może warto użyć tej funkcji <xref:System.Windows.Controls.ScrollBarVisibility> wartością <xref:System.Windows.Controls.ListBox> 30 elementów, w przeciwieństwie do <xref:System.Windows.Controls.TextBox> wraz z setkami wierszy tekstu.  
  
<a name="FontCache"></a>   
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurowanie usługi pamięci podręcznej czcionki skrócić czas uruchamiania  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Czcionki Cache service udostępnia dane czcionki między [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji. Pierwszy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, możesz uruchomić rozpoczyna się tej usługi, jeśli usługa nie jest już uruchomiona. Jeśli używasz [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], można ustawić usługę "Windows Presentation Foundation (WPF) czcionki pamięć podręczną 3.0.0.0" od "Ręczny" (wartość domyślna) "Automatycznie (opóźnione uruchomienie)" w celu skrócenia czasu początkowego rozruchu z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji.  
  
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
