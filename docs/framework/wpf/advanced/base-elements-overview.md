---
title: Przegląd Elementy bazy
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: bcfcb87d0ddf5181a47d459e821bacd9b9f6b61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="base-elements-overview"></a>Przegląd Elementy bazy
Wysoki procent klas w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są uzyskiwane z czterech klas, które są często określane w [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] dokumentacji jako klasy podstawowej elementu. Te klasy są <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, i <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Klasa również odnosi się, ponieważ jest wspólna klasa podstawowa obu <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>  
 
  
<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Interfejsy API Base Element w klasach WPF  
 Zarówno <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> pochodne <xref:System.Windows.DependencyObject>, za pomocą ścieżek nieco inny. Podziel na tym poziomie zajmuje się jak <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> są używane w interfejsie użytkownika i co cel służą w aplikacji. <xref:System.Windows.UIElement> ma również <xref:System.Windows.Media.Visual> w swojej hierarchii klasy, która jest klasa, która przedstawia podstawowy Obsługa grafiki niższego poziomu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> zapewnia platformę renderowania, definiując regiony ekranu prostokątne niezależne. W praktyce <xref:System.Windows.UIElement> jest dla elementów, które będzie obsługiwać większego modelu obiektu są przeznaczone do renderowania i układu w regionach, który można określić jako regiony ekranu prostokątne i gdzie model zawartości jest celowo więcej otwarty, aby umożliwić różnych kombinacje elementów. <xref:System.Windows.ContentElement> nie pochodzi od <xref:System.Windows.Media.Visual>; jego model jest to, że <xref:System.Windows.ContentElement> może być zużyte przez coś innego, np. czytnik lub przeglądarkę, która będzie następnie interpretacji elementy i tworzy pełną <xref:System.Windows.Media.Visual> dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] korzystać. Niektóre <xref:System.Windows.UIElement> klas powinny być zawartości hostów: zapewniają hosting i renderowania dla jednego lub więcej <xref:System.Windows.ContentElement> klasy (<xref:System.Windows.Controls.DocumentViewer> Przykładem takich klasy). <xref:System.Windows.ContentElement> jest używany jako klasa podstawowa dla elementów z nieco mniejsze modele obiektów i więcej adresów tekst informacji, lub zawartość dokumentu, który może być obsługiwana w <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Framework Core poziomie i  
 <xref:System.Windows.UIElement> Służy jako klasa podstawowa dla <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.ContentElement> służy jako klasa podstawowa dla <xref:System.Windows.FrameworkContentElement>. Przyczyną tego poziomu klas jest do obsługi poziomu core WPF, która jest niezależna od poziomu framework WPF z tego podziału również istniejących w sposób [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] są podzielone między zestawami PresentationCore i PresentationFramework. Poziom framework WPF przedstawia oprogramowanie na potrzeby aplikacji w warstwie podstawowa, łącznie z wdrożeniem menedżera układu do prezentacji. Poziom core WPF umożliwia Użyj większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez konieczności przełączania koszty dodatkowe zestawu. Różnica między tymi bardzo rzadko poziomy kwestie dotyczące najbardziej typowych scenariuszy programowania aplikacji i ogólnie należy traktować z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jako całość i nie dotyczą samodzielnie różnicę między poziom framework WPF i poziom core WPF. Czasami trzeba wiedzieć o poziomu rozróżnienia, jeśli wybierze projektu aplikacji zastąpienie znacznej ilości WPF framework poziomu funkcjonalności, na przykład jeśli ogólnego rozwiązania jest już własne implementacje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] skład i układu.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Wybierania który Element pochodzić z  
 Najbardziej praktycznym sposobem tworzenia niestandardowej klasy, która rozszerza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] za wynikające z jednego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas, skąd pobrać jak to możliwe z wymaganej funkcjonalności przy użyciu istniejącej klasy hierarchii. Ta sekcja zawiera funkcje, które pochodzą z trzema najważniejszych klasy elementów, aby określić, która klasa dziedziczy po.  
  
 W przypadku wdrażania formantu, naprawdę czyli więcej najczęstsze przyczyny wynikających z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, prawdopodobnie chcesz pochodzi z klasy, która jest formantem praktyczne kontroli rodziny klasę podstawową, lub na co najmniej z <xref:System.Windows.Controls.Control> klasy podstawowej. Niektóre wskazówki i przykłady praktyczne, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Jeśli nie są tworzone formantu i muszą pochodzić z klasy, która jest wyżej w hierarchii, sekcje są przeznaczone jako przewodnik dla właściwości, które są zdefiniowane w każdej klasy podstawowej elementu.  
  
 W przypadku utworzenia klasy, która jest pochodną <xref:System.Windows.DependencyObject>, dziedziczą następujące funkcje:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> pomocy i obsługi systemu ogólne właściwości.  
  
-   Możliwość, użyj właściwości zależności i dołączone właściwości, które są wdrażane jako właściwości zależności.  
  
 W przypadku utworzenia klasy, która jest pochodną <xref:System.Windows.UIElement>, dziedziczą następujące funkcje oprócz udostępniane przez <xref:System.Windows.DependencyObject>:  
  
-   Podstawowa pomoc techniczna dla wartości właściwości animacji. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Obsługa zdarzeń w wersji Basic wejściowych i sterująca pomocy technicznej. Aby uzyskać więcej informacji, zobacz [omówienie wprowadzania](../../../../docs/framework/wpf/advanced/input-overview.md) i [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
-   Metody wirtualne, które mogą zostać zastąpione, aby podać informacje do układu systemu.  
  
 W przypadku utworzenia klasy, która jest pochodną <xref:System.Windows.FrameworkElement>, dziedziczą następujące funkcje oprócz udostępniane przez <xref:System.Windows.UIElement>:  
  
-   Obsługa stylów i scenorys. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style> i [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
-   Obsługa wiązania z danymi. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Obsługa odwołania do zasobów dynamicznych. Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Obsługa dziedziczenia wartości właściwości, a inne flagi w metadanych, które pomogą warunki raport o właściwościach framework usług takich jak powiązania danych, style lub framework stosowania układu. Aby uzyskać więcej informacji, zobacz [metadanych właściwości Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Pojęcie drzewa logicznego. Aby uzyskać więcej informacji, zobacz [drzewa WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
-   Obsługę praktyczne implementacji poziomie struktury WPF systemu układu, w tym <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> zastąpienia, która wykrywa zmiany właściwości taki układ wpływ.  
  
 W przypadku utworzenia klasy, która jest pochodną <xref:System.Windows.ContentElement>, dziedziczą następujące funkcje oprócz udostępniane przez <xref:System.Windows.DependencyObject>:  
  
-   Obsługa animacji. Aby uzyskać więcej informacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Obsługa zdarzeń w wersji Basic wejściowych i sterująca pomocy technicznej. Aby uzyskać więcej informacji, zobacz [omówienie wprowadzania](../../../../docs/framework/wpf/advanced/input-overview.md) i [droższe omówienie](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 W przypadku utworzenia klasy, która jest pochodną <xref:System.Windows.FrameworkContentElement>, pobierz następujące funkcje oprócz udostępniane przez <xref:System.Windows.ContentElement>:  
  
-   Obsługa stylów i scenorys. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style> i [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Obsługa wiązania z danymi. Aby uzyskać więcej informacji, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Obsługa odwołania do zasobów dynamicznych. Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Obsługa dziedziczenia wartości właściwości, a inne flagi w metadanych, które pomogą warunki raport o właściwościach framework usług takich jak powiązania danych, style lub framework stosowania układu. Aby uzyskać więcej informacji, zobacz [metadanych właściwości Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Nie dziedziczy dostęp do modyfikacji systemu układu (takich jak <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Układ implementacji systemu są dostępne tylko na <xref:System.Windows.FrameworkElement>. Jednak dziedziczy <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> zastąpienia, która wykrywa zmiany właściwości, które wpływają na układ i je na wszystkich hostach, zawartości raportu.  
  
 Modele zawartości są udokumentowane dla różnych klas. Model zawartości dla klasy jest jeden składnik możliwe, należy rozważyć, jeśli chcesz znaleźć odpowiedniej klasy pochodzić z. Aby uzyskać więcej informacji, zobacz [modelu zawartości WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Inne klasy podstawowe  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> zapewnia obsługę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wątkowość modelu i włącza wszystkie obiekty utworzone dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji ma być skojarzone z <xref:System.Windows.Threading.Dispatcher>. Nawet jeśli pochodzi od <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, lub <xref:System.Windows.Media.Visual>, należy rozważyć pochodny <xref:System.Windows.Threading.DispatcherObject> Aby uzyskać wsparcie to modelu wątkowości. Aby uzyskać więcej informacji, zobacz [Model wątkowy](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
### <a name="visual"></a>Wizualne  
 <xref:System.Windows.Media.Visual> implementuje pojęcie 2D obiekt, który zwykle wymaga wizualną prezentację w przybliżeniu prostokątny obszar. Rzeczywiste renderowanie <xref:System.Windows.Media.Visual> odbywa się w innych klas (nie jest autonomiczną), ale <xref:System.Windows.Media.Visual> klasa udostępnia znanym typem, który jest używany przez procesy renderowania na różnych poziomach. <xref:System.Windows.Media.Visual> Testowanie trafień implementuje, ale nie ujawnia zdarzenia, które zgłosiły testowania trafień alarmów (są to <xref:System.Windows.UIElement>). Aby uzyskać więcej informacji, zobacz [programowania Visual warstwy](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> symuluje immutability w obiekcie modyfikowalną przez nowe możliwości generowania kopii obiektu, gdy niezmienne obiektu jest wymagane lub pożądane ze względu na wydajność. <xref:System.Windows.Freezable> Typ stanowi podstawę typowe dla niektórych elementów graficznych, takich jak mają geometrię i pędzle, a także animacji. Należy zwrócić uwagę <xref:System.Windows.Freezable> nie jest <xref:System.Windows.Media.Visual>; może zawierać właściwości, które stają się podrzędnych podczas <xref:System.Windows.Freezable> jest stosowany do wypełnienia wartości właściwości innego obiektu i te właściwości mogą mieć wpływ na renderowania. Aby uzyskać więcej informacji, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> jest <xref:System.Windows.Freezable> klasy, w szczególności z właściwości nonanimated dodającego warstwy formantu animacji i niektóre elementy członkowskie narzędzia, dzięki czemu można rozróżnić obecnie animowanej właściwości.  
  
### <a name="control"></a>Formant  
 <xref:System.Windows.Controls.Control> jest zamierzone klasę podstawową dla typu obiektu, który różnorodnie jest określane jako formant lub składników, w zależności od technologii. Ogólnie rzecz biorąc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, które reprezentują formantu interfejsu użytkownika albo bezpośrednio ściśle uczestniczyć w kontroli kompozycji występują następujące klasy formantu. Podstawowe funkcje który <xref:System.Windows.Controls.Control> umożliwia jest formant tworzenia szablonów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Control>  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Tworzenie kontrolek — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
