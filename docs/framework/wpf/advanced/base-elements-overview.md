---
title: Przegląd Elementy bazy
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 0cd69a4d2d6087c1ebf93bb5931511f32a4c9c5f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110061"
---
# <a name="base-elements-overview"></a>Przegląd Elementy bazy
Wysoki procent klas w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] są uzyskiwane z czterech klas, które są często określane w [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] przesłać dokumenty będące klasy bazowej elementów. Te klasy są <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, i <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Klasa również odnosi się, ponieważ jest wspólna klasa bazowa obu <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Base Element API klas WPF  
 Zarówno <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> są uzyskiwane z <xref:System.Windows.DependencyObject>, za pośrednictwem nieco różne sposoby uzyskiwania dostępu. Podziel na tym poziomie zajmuje się jak <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> są używane w interfejsie użytkownika i co przeznaczenia służą one w aplikacji. <xref:System.Windows.UIElement> ma również <xref:System.Windows.Media.Visual> w jego hierarchii klas, który jest klasa, która udostępnia podstawowe grafiki niższego poziomu pomocy technicznej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> zapewnia ramy renderowania, definiując regiony ekranu prostokątny niezależne. W praktyce <xref:System.Windows.UIElement> jest dla elementów, które będzie obsługiwać większe modelu obiektów przeznaczonych do renderowania i układu w regionach, może być opisany jako regiony ekranu prostokątny i gdzie model zawartości jest celowo bardziej otwarte, aby zezwolić na inny kombinacje elementów. <xref:System.Windows.ContentElement> nie pochodzi od <xref:System.Windows.Media.Visual>; swój model jest fakt, że <xref:System.Windows.ContentElement> może być używane przez coś innego, np. czytnik lub przeglądarkę, która będzie następnie interpretacji elementy i tworzyć pełne <xref:System.Windows.Media.Visual> dla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] korzystać. Niektóre <xref:System.Windows.UIElement> klasy mają być zawartości hostów: zapewniają hostingu i renderowania dla jednego lub więcej <xref:System.Windows.ContentElement> klasy (<xref:System.Windows.Controls.DocumentViewer> jest przykładem takich klasy). <xref:System.Windows.ContentElement> jest używany jako klasa bazowa dla elementów z nieco mniejsze modele obiektów i więcej adresów tekst informacji, lub zawartości dokumentu, który może zostać umieszczony w elemencie <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Framework Core poziomie i  
 <xref:System.Windows.UIElement> Służy jako klasa bazowa dla <xref:System.Windows.FrameworkElement>, i <xref:System.Windows.ContentElement> służy jako klasa bazowa dla <xref:System.Windows.FrameworkContentElement>. Przyczyna tego następnego poziomu klasy jest poziom core WPF, który jest oddzielony od poziomu framework WPF za pomocą tego działu również istniejące w sposób, w jaki [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] są podzielone między zestawami PresentationCore i PresentationFramework. Poziom framework WPF przedstawia bardziej kompleksowe rozwiązanie do potrzeb aplikacji w warstwie podstawowa, łącznie z wdrożeniem menedżera układu, aby obejrzeć prezentację. Poziom core WPF zapewnia sposób użycia większość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez konieczności dodatkowego zestawu. Różnica między tymi poziomy bardzo rzadko jest ważna dla najbardziej typowych scenariuszy projektowania aplikacji i ogólnie rzecz biorąc należy myśleć o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jako całość i nie dotyczą samodzielnie różnicę między poziomie struktury WPF i poziom core WPF. Czasami trzeba wiedzieć o poziomie różnice, jeśli projektu aplikacji zdecydował się zastąpić znacznej ilości WPF framework poziomu funkcjonalności, na przykład jeśli całe rozwiązanie zawiera już własne implementacje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] skład i układ.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Wybieranie który Element ma być z  
 Najbardziej praktycznym sposobem tworzenia niestandardowej klasy, która rozszerza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] polega na elementu pochodnego dla jednego z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas, skąd jak najszerzej usługi żądanej funkcji za pośrednictwem istniejących klas hierarchii. W tej sekcji przedstawiono funkcje, które pochodzą z trzema pomóc zdecydować, która klasa dziedziczy po najważniejszych klasy elementu.  
  
 Przed zaimplementowaniem kontrolki, naprawdę czyli typowe przyczyny pochodząca od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, prawdopodobnie chcesz pochodzi od klasy, która jest formantem praktyczne kontroli rodziny klasę bazową, lub na co najmniej z <xref:System.Windows.Controls.Control> klasy bazowej. Niektóre wskazówki i praktyczne przykłady, zobacz [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
 Jeśli są nietworzenie kontrolki i muszą pochodzić od klasy, który znajduje się wyżej w hierarchii, następujące sekcje są przeznaczone jako przewodnika cechy, które są zdefiniowane w każdej klasie elementu podstawowego.  
  
 Jeśli tworzysz klasę, która pochodzi od klasy <xref:System.Windows.DependencyObject>, dziedziczą następujące funkcje:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> obsługę i ogólne właściwości systemu.  
  
-   Możliwość używania właściwości zależności i dołączone właściwości, które są implementowane jako właściwości zależności.  
  
 Jeśli tworzysz klasę, która pochodzi od klasy <xref:System.Windows.UIElement>, dziedziczą następujące funkcje oprócz tego są udostępniane przez <xref:System.Windows.DependencyObject>:  
  
-   Podstawowa pomoc techniczna dla wartości właściwości animowany. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
-   Podstawowe dane wejściowe zdarzenia pomocy technicznej i sterująca pomocy technicznej. Aby uzyskać więcej informacji, zobacz [przegląd danych wejściowych](input-overview.md) i [polecenia Przegląd](commanding-overview.md).  
  
-   Metody wirtualne, które może zostać zastąpiona w celu zawierają informacje, które system układu.  
  
 Jeśli tworzysz klasę, która pochodzi od klasy <xref:System.Windows.FrameworkElement>, dziedziczą następujące funkcje oprócz tego są udostępniane przez <xref:System.Windows.UIElement>:  
  
-   Wsparcie dla scenorysów i stylów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style> i [Przegląd Scenorysy](../graphics-multimedia/storyboards-overview.md).  
  
-   Obsługa powiązań danych. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](../data/data-binding-overview.md).  
  
-   Pomoc techniczna dla odwołania do zasobów dynamicznej. Aby uzyskać więcej informacji, zobacz [zasoby XAML](xaml-resources.md).  
  
-   Obsługa dziedziczenia wartości właściwości, a inne flagi w metadanych, które pomagają warunki raport o właściwościach framework usług, takich jak powiązania danych, stylów lub implementacji środowiska układu. Aby uzyskać więcej informacji, zobacz [metadane właściwości szablonu](framework-property-metadata.md).  
  
-   Pojęcie drzewo logiczne. Aby uzyskać więcej informacji, zobacz [drzewa w WPF](trees-in-wpf.md).  
  
-   Obsługa praktyczne wykonania poziomie struktury system układu WPF tym <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> przesłonięcie może wykryć, zmiany właściwości układu tego wpływu.  
  
 Jeśli tworzysz klasę, która pochodzi od klasy <xref:System.Windows.ContentElement>, dziedziczą następujące funkcje oprócz tego są udostępniane przez <xref:System.Windows.DependencyObject>:  
  
-   Pomoc techniczna dla animacji. Aby uzyskać więcej informacji, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
-   Podstawowe dane wejściowe zdarzenia pomocy technicznej i sterująca pomocy technicznej. Aby uzyskać więcej informacji, zobacz [przegląd danych wejściowych](input-overview.md) i [polecenia Przegląd](commanding-overview.md).  
  
 Jeśli tworzysz klasę, która pochodzi od klasy <xref:System.Windows.FrameworkContentElement>, pobierz następujące funkcje oprócz tego są udostępniane przez <xref:System.Windows.ContentElement>:  
  
-   Wsparcie dla scenorysów i stylów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style> i [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
-   Obsługa powiązań danych. Aby uzyskać więcej informacji, zobacz [Przegląd wiązanie danych](../data/data-binding-overview.md).  
  
-   Pomoc techniczna dla odwołania do zasobów dynamicznej. Aby uzyskać więcej informacji, zobacz [zasoby XAML](xaml-resources.md).  
  
-   Obsługa dziedziczenia wartości właściwości, a inne flagi w metadanych, które pomagają warunki raport o właściwościach framework usług, takich jak powiązania danych, stylów lub implementacji środowiska układu. Aby uzyskać więcej informacji, zobacz [metadane właściwości szablonu](framework-property-metadata.md).  
  
-   Nie dziedziczą, dostęp do modyfikacji systemu układu (takie jak <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Układ systemu implementacje są dostępne tylko na <xref:System.Windows.FrameworkElement>. Jednak dziedziczy <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> przesłonięcie może wykryć zmiany właściwości, które mają wpływ na układ i zgłoś je do dowolnej zawartości hostów.  
  
 Modele zawartości są opisane dla różnych klas. Model zawartości dla klasy jest jeden składnik to możliwe, należy rozważyć, jeśli chcesz znaleźć odpowiedniej klasy, aby dziedziczyć. Aby uzyskać więcej informacji, zobacz [Model zawartości WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Innych klas bazowych  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> zapewnia obsługę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wątkowości, model i włącza wszystkie obiekty stworzone dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje do skojarzenia z <xref:System.Windows.Threading.Dispatcher>. Nawet jeśli pochodzi od <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, lub <xref:System.Windows.Media.Visual>, należy rozważyć, wynikające z <xref:System.Windows.Threading.DispatcherObject> Aby uzyskać temu modelu wątkowości. Aby uzyskać więcej informacji, zobacz [Model wątkowy](threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual> implementuje koncepcji 2D obiektu, który zwykle wymaga wizualnej prezentacji w przybliżeniu prostokątny obszar. Rzeczywiste renderowanie <xref:System.Windows.Media.Visual> odbywa się w innych klas (nie jest ona niezależna), ale <xref:System.Windows.Media.Visual> klasy zawiera znany typ, który jest używany przez procesy renderowania na różnych poziomach. <xref:System.Windows.Media.Visual> Test trafienia implementuje, ale nie uwidacznia zdarzenia, które zgłaszanie testowania trafień alarmów (zostały one <xref:System.Windows.UIElement>). Aby uzyskać więcej informacji, zobacz [programowanie warstwy Visual](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> symuluje niezmienności w obiektu modyfikowalnego przez nowe możliwości generowania kopii obiektu, gdy niezmienne obiektu jest wymagane lub konieczne ze względu na wydajność. <xref:System.Windows.Freezable> Typ zapewnia wspólnej podstawy dla niektórych elementów graficznych, takich jak geometrii i pędzle, a także animacji. Należy zwrócić uwagę <xref:System.Windows.Freezable> nie jest <xref:System.Windows.Media.Visual>; może on przechowywać właściwości, które stają się właściwości podrzędnych podczas <xref:System.Windows.Freezable> jest stosowany do wypełnienia wartości właściwości innego obiektu, i te właściwości mogą mieć wpływ na renderowania. Aby uzyskać więcej informacji, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> jest <xref:System.Windows.Freezable> pochodne klasy, która specjalnie przy użyciu właściwości nonanimated dodaje warstwę kontroli animacji i niektóre elementy członkowskie narzędzia, dzięki czemu można odróżnić obecnie animowany właściwości.  
  
### <a name="control"></a>formant  
 <xref:System.Windows.Controls.Control> jest zamierzony klasę bazową dla typu obiektu, który różnorodnie jest określane jako kontrola lub składników, w zależności od technologii. Ogólnie rzecz biorąc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy kontrolki są klas, które reprezentują kontrolkę interfejsu użytkownika albo bezpośrednio ściśle uczestniczyć w kompozycji formantu. Funkcje podstawowe, <xref:System.Windows.Controls.Control> umożliwia jest szablonów kontrolki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Control>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
