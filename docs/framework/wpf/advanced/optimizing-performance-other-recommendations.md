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
ms.openlocfilehash: 727331adb41251460209f157d1804ff455bcf473
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186299"
---
# <a name="optimizing-performance-other-recommendations"></a>Optymalizacja wydajności: inne zalecenia
<a name="introduction"></a>Ten temat zawiera zalecenia dotyczące wydajności oprócz tych objętych tematami w optymalizacji [wydajności aplikacji WPF](optimizing-wpf-application-performance.md) sekcji.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Krycie na pędzle versus krycie na elementach](#Opacity)  
  
- [Nawigacja do obiektu](#Navigation_Objects)  
  
- [Testowanie trafień na dużych powierzchniach 3D](#Hit_Testing)  
  
- [Zdarzenie CompositionTarget.Rendering](#CompositionTarget_Rendering_Event)  
  
- [Unikaj używania funkcji ScrollBarVisibility=Auto](#Avoid_Using_ScrollBarVisibility)  
  
- [Konfigurowanie usługi Buforowanie czcionek w celu skrócenia czasu rozruchu](#FontCache)  
  
<a name="Opacity"></a>
## <a name="opacity-on-brushes-versus-opacity-on-elements"></a>Krycie na pędzle versus krycie na elementach  
 W przypadku <xref:System.Windows.Media.Brush> użycia a, aby ustawić <xref:System.Windows.Shapes.Shape.Fill%2A> lub <xref:System.Windows.Shapes.Shape.Stroke%2A> elementu, <xref:System.Windows.Media.Brush.Opacity%2A?displayProperty=nameWithType> lepiej jest ustawić wartość, <xref:System.Windows.UIElement.Opacity%2A> a nie ustawienie właściwości elementu. Modyfikowanie <xref:System.Windows.UIElement.Opacity%2A> właściwości elementu może [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spowodować utworzenie powierzchni tymczasowej.  
  
<a name="Navigation_Objects"></a>
## <a name="navigation-to-object"></a>Nawigacja do obiektu  
 Obiekt <xref:System.Windows.Navigation.NavigationWindow> pochodzi z <xref:System.Windows.Window> i rozszerza go z obsługą nawigacji zawartości, przede wszystkim przez agregowanie <xref:System.Windows.Navigation.NavigationService> i arkusza. Obszar klienta można zaktualizować, <xref:System.Windows.Navigation.NavigationWindow> określając jednolity identyfikator zasobu (URI) lub obiekt. W poniższym przykładzie przedstawiono obie metody:  
  
 [!code-csharp[Performance#PerformanceSnippet14](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/TestNavigation.xaml.cs#performancesnippet14)]
 [!code-vb[Performance#PerformanceSnippet14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/testnavigation.xaml.vb#performancesnippet14)]  
  
 Każdy <xref:System.Windows.Navigation.NavigationWindow> obiekt ma dziennik, który rejestruje historię nawigacji użytkownika w tym oknie. Jednym z celów dziennika jest umożliwienie użytkownikom ponownego prześledzania ich kroków.  
  
 Podczas nawigacji przy użyciu jednolitego identyfikatora zasobu (URI) dziennik przechowuje tylko odwołanie do jednolitego identyfikatora zasobu (URI). Oznacza to, że za każdym razem, gdy ponownie odwiedzasz stronę, jest ona dynamicznie rekonstruowana, co może być czasochłonne w zależności od złożoności strony. W takim przypadku koszt magazynu dziennika jest niski, ale czas odtworzenia strony jest potencjalnie wysoki.  
  
 Podczas nawigacji za pomocą obiektu dziennik przechowuje całe drzewo wizualne obiektu. Oznacza to, że za każdym razem, gdy ponownie odwiedzasz stronę, jest renderowana natychmiast bez konieczności rekonstrukcji. W takim przypadku koszt magazynu dziennika jest wysoki, ale czas odtworzenia strony jest niski.  
  
 Podczas korzystania <xref:System.Windows.Navigation.NavigationWindow> z obiektu, należy pamiętać, jak obsługa rejestrowania wpływa na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).  
  
<a name="Hit_Testing"></a>
## <a name="hit-testing-on-large-3d-surfaces"></a>Testowanie trafień na dużych powierzchniach 3D  
 Testowanie trafień na dużych powierzchniach 3D jest bardzo wydajną operacją pod względem zużycia procesora. Jest to szczególnie ważne, gdy powierzchnia 3D jest animowanie. Jeśli nie potrzebujesz testowania trafień na tych powierzchniach, wyłącz testowanie trafień. Obiekty, które pochodzą <xref:System.Windows.UIElement> z można wyłączyć <xref:System.Windows.UIElement.IsHitTestVisible%2A> testowanie `false`trafień, ustawiając właściwość .  
  
<a name="CompositionTarget_Rendering_Event"></a>
## <a name="compositiontargetrendering-event"></a>Zdarzenie CompositionTarget.Rendering  
 Zdarzenie <xref:System.Windows.Media.CompositionTarget.Rendering?displayProperty=nameWithType> powoduje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ciągłe animowanie. Jeśli używasz tego zdarzenia, odłącz je przy każdej okazji.  
  
<a name="Avoid_Using_ScrollBarVisibility"></a>
## <a name="avoid-using-scrollbarvisibilityauto"></a>Unikaj używania funkcji ScrollBarVisibility=Auto  
 Jeśli to możliwe, <xref:System.Windows.Controls.ScrollBarVisibility.Auto?displayProperty=nameWithType> należy unikać `HorizontalScrollBarVisibility` `VerticalScrollBarVisibility` używania wartości dla i właściwości. Te właściwości są <xref:System.Windows.Controls.RichTextBox>zdefiniowane dla , <xref:System.Windows.Controls.ScrollViewer>i <xref:System.Windows.Controls.TextBox> obiektów oraz <xref:System.Windows.Controls.ListBox> jako dołączona właściwość obiektu. Zamiast tego <xref:System.Windows.Controls.ScrollBarVisibility> ustaw <xref:System.Windows.Controls.ScrollBarVisibility.Disabled> <xref:System.Windows.Controls.ScrollBarVisibility.Hidden>na <xref:System.Windows.Controls.ScrollBarVisibility.Visible>, lub .  
  
 Wartość <xref:System.Windows.Controls.ScrollBarVisibility.Auto> jest przeznaczona dla przypadków, gdy ilość miejsca jest ograniczona, a paski przewijania powinny być wyświetlane tylko wtedy, gdy jest to konieczne. Na przykład może być przydatne <xref:System.Windows.Controls.ScrollBarVisibility> użycie tej <xref:System.Windows.Controls.ListBox> wartości z 30 elementów, w przeciwieństwie do <xref:System.Windows.Controls.TextBox> z setkami wierszy tekstu.  
  
<a name="FontCache"></a>
## <a name="configure-font-cache-service-to-reduce-start-up-time"></a>Konfigurowanie usługi Buforowanie czcionek w celu skrócenia czasu rozruchu  
 Usługa WPF Font Cache udostępnia dane czcionek między aplikacjami WPF. Pierwsza uruchomiona aplikacja WPF uruchamia tę usługę, jeśli usługa nie jest jeszcze uruchomiona. Jeśli używasz systemu Windows Vista, można ustawić "Windows Presentation Foundation (WPF) Font Cache 3.0.0.0" z "Manual" (domyślnie) do "Automatyczne (Opóźnione uruchamianie)", aby skrócić początkowy czas uruchamiania aplikacji WPF.  
  
## <a name="see-also"></a>Zobacz też

- [Planowanie wydajności aplikacji](planning-for-application-performance.md)
- [Wykorzystanie możliwości sprzętu](optimizing-performance-taking-advantage-of-hardware.md)
- [Układ i projekt](optimizing-performance-layout-and-design.md)
- [Grafika 2D i obrazowanie](optimizing-performance-2d-graphics-and-imaging.md)
- [Zachowanie obiektu](optimizing-performance-object-behavior.md)
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Tekst](optimizing-performance-text.md)
- [Powiązanie danych](optimizing-performance-data-binding.md)
- [Animacja — porady i wskazówki](../graphics-multimedia/animation-tips-and-tricks.md)
