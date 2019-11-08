---
title: Przegląd Elementy bazy
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 823c81bf6b21b88d719503387a68ce6e7d643d61
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740914"
---
# <a name="base-elements-overview"></a>Przegląd Elementy bazy
Wysoki procent klas w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pochodzą od czterech klas, które są powszechnie określane w dokumentacji zestawu SDK jako klas podstawowych elementów. Te klasy to <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>i <xref:System.Windows.FrameworkContentElement>. Klasa <xref:System.Windows.DependencyObject> jest również związana, ponieważ jest wspólną klasą bazową obu <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Interfejsy API elementu podstawowego w klasach WPF  
 Zarówno <xref:System.Windows.UIElement>, jak i <xref:System.Windows.ContentElement> są otrzymywane od <xref:System.Windows.DependencyObject>, przez nieco różne ścieżki. Podział na ten poziom zajmuje się sposobem, w jaki <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement> są używane w interfejsie użytkownika i jakie znaczenie pełni w aplikacji. <xref:System.Windows.UIElement> ma także <xref:System.Windows.Media.Visual> w hierarchii klas, która jest klasą, która uwidacznia obsługę grafiki niższego poziomu w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> udostępnia strukturę renderowania przez definiowanie niezależnych regionów prostokątnego ekranu. W <xref:System.Windows.UIElement> jest dla elementów, które będą obsługiwały większy model obiektów, są przeznaczone do renderowania i układu w regionach, które mogą być opisane jako prostokątne regiony ekranu, i gdzie model zawartości jest świadomie otwarty, aby umożliwić różne kombinacje elementów. <xref:System.Windows.ContentElement> nie pochodzi od <xref:System.Windows.Media.Visual>; jego modelem jest to, że <xref:System.Windows.ContentElement> będzie używana przez coś innego, takiego jak czytelnik lub przeglądarka, która następnie interpretuje elementy i produkuje kompletne <xref:System.Windows.Media.Visual> do użycia przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Niektóre klasy <xref:System.Windows.UIElement> mają być hostami zawartości: zapewniają hosting i renderowanie dla co najmniej jednej klasy <xref:System.Windows.ContentElement> (<xref:System.Windows.Controls.DocumentViewer> jest przykładem takiej klasy). <xref:System.Windows.ContentElement> jest używana jako klasa bazowa dla elementów mających nieco mniejsze modele obiektów i więcej adresu tekstu, informacji lub zawartości dokumentu, która może być hostowana w <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Poziom platformy i poziom podstawowy  
 <xref:System.Windows.UIElement> służy jako klasa bazowa dla <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.ContentElement> służy jako klasa bazowa dla <xref:System.Windows.FrameworkContentElement>. Powodem tego następnego poziomu klas jest obsługa poziomu WPF Core, który jest oddzielony od poziomu platformy WPF, z tym podziałem istniejącym również w sposobie dzielenia interfejsów API między zestawami 'Presentationcore i platformie docelowej. Poziom platformy WPF zawiera pełniejsze rozwiązanie dla podstawowych potrzeb aplikacji, w tym implementację Menedżera układu dla prezentacji. Poziom WPF Core umożliwia korzystanie z wielu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez konieczności narzutu dodatkowego zestawu. Rozróżnienie między tymi poziomami bardzo rzadko dotyczy większości typowych scenariuszy tworzenia aplikacji, a ogólnie rzecz biorąc, należy traktować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interfejsów API jako całości i nie dotyczy to różnic między poziomem platformy WPF a poziomem WPF. Może być konieczne poznanie różnic poziomu, jeśli projekt aplikacji zdecyduje się na zastępowanie znaczących ilości funkcjonalności poziomu platformy WPF, na przykład jeśli ogólne rozwiązanie ma już własne implementacje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kompozycji i wyglądu.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Wybieranie elementu, z którego pochodzi  
 Najbardziej praktycznym sposobem tworzenia klasy niestandardowej, która rozszerza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jest wynikająca z jednej z klas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], gdzie najprawdopodobniej można korzystać z odpowiedniej funkcjonalności za pośrednictwem istniejącej hierarchii klas. Ta sekcja zawiera listę funkcji, które są dostarczane z trzema najważniejszymi klasami elementów, aby ułatwić podjęcie decyzji o tym, której klasy należy odziedziczyć.  
  
 Jeśli wdrażasz kontrolkę, która jest w rzeczywistości jednym z bardziej typowych przyczyn pochodnych z klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], prawdopodobnie chcesz pochodzić z klasy, która jest praktyczną kontrolą, klasą bazową rodziny formantów lub co najmniej z klasy bazowej <xref:System.Windows.Controls.Control>. Aby uzyskać wskazówki i praktyczne przykłady, zobacz temat [Tworzenie kontroli — Omówienie](../controls/control-authoring-overview.md).  
  
 Jeśli nie tworzysz kontrolki i chcesz utworzyć ją z klasy, która jest wyższa w hierarchii, następujące sekcje są przeznaczone jako przewodnik dla cech, które są zdefiniowane w każdej klasie elementów podstawowych.  
  
 Jeśli utworzysz klasę, która pochodzi od <xref:System.Windows.DependencyObject>, dziedziczą następujące funkcje:  
  
- Obsługa <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> oraz ogólna obsługa systemu właściwości.  
  
- Możliwość używania właściwości zależności i dołączonych właściwości, które są implementowane jako właściwości zależności.  
  
 Jeśli utworzysz klasę pochodzącą z <xref:System.Windows.UIElement>, będziesz dziedziczyć następujące funkcje oprócz tych dostarczonych przez <xref:System.Windows.DependencyObject>:  
  
- Pomoc techniczna Basic dla animowanych wartości właściwości. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
- Podstawowa obsługa zdarzeń wejściowych i obsługa poleceń. Aby uzyskać więcej informacji, zobacz [przegląd danych wejściowych](input-overview.md) i [Omówienie poleceń](commanding-overview.md).  
  
- Metody wirtualne, które mogą zostać zastąpione w celu zapewnienia informacji dla systemu układu.  
  
 Jeśli utworzysz klasę pochodzącą z <xref:System.Windows.FrameworkElement>, będziesz dziedziczyć następujące funkcje oprócz tych dostarczonych przez <xref:System.Windows.UIElement>:  
  
- Obsługa stylów i scenorysów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Style> i [scenorysów — Omówienie](../graphics-multimedia/storyboards-overview.md).  
  
- Obsługa powiązań danych. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
- Obsługa dynamicznych odwołań do zasobów. Aby uzyskać więcej informacji, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Obsługa dziedziczenia wartości właściwości oraz inne flagi w metadanych, które pomagają zgłosić warunki dotyczące właściwości usług ramowych, takich jak powiązanie danych, style lub implementacja struktury układu. Aby uzyskać więcej informacji, zobacz [metadane właściwości struktury](framework-property-metadata.md).  
  
- Koncepcja drzewa logicznego. Aby uzyskać więcej informacji, zobacz [drzewa w WPF](trees-in-wpf.md).  
  
- Obsługa praktycznej implementacji na poziomie platformy WPF w systemie układu, w tym przesłonięcie <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>, które może wykryć zmiany właściwości, które mają wpływ na układ.  
  
 Jeśli utworzysz klasę pochodzącą z <xref:System.Windows.ContentElement>, będziesz dziedziczyć następujące funkcje oprócz tych dostarczonych przez <xref:System.Windows.DependencyObject>:  
  
- Obsługa animacji. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
- Podstawowa obsługa zdarzeń wejściowych i obsługa poleceń. Aby uzyskać więcej informacji, zobacz [przegląd danych wejściowych](input-overview.md) i [Omówienie poleceń](commanding-overview.md).  
  
 Jeśli utworzysz klasę pochodzącą z <xref:System.Windows.FrameworkContentElement>, uzyskasz następujące funkcje oprócz tych udostępnionych przez <xref:System.Windows.ContentElement>:  
  
- Obsługa stylów i scenorysów. Aby uzyskać więcej informacji, zobacz Omówienie <xref:System.Windows.Style> i [animacji](../graphics-multimedia/animation-overview.md).  
  
- Obsługa powiązań danych. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
- Obsługa dynamicznych odwołań do zasobów. Aby uzyskać więcej informacji, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Obsługa dziedziczenia wartości właściwości i innych flag w metadanych, które pomagają zgłosić warunki dotyczące właściwości usług ramowych, takich jak powiązanie danych, style lub implementacja struktury układu. Aby uzyskać więcej informacji, zobacz [metadane właściwości struktury](framework-property-metadata.md).  
  
- Nie dziedziczysz dostępu do modyfikacji systemu układu (takich jak <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Implementacje systemu układów są dostępne tylko na <xref:System.Windows.FrameworkElement>. Można jednak odziedziczyć <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> przesłonięcia, które może wykryć zmiany właściwości, które mają wpływ na układ i zgłosić je do dowolnego hosta zawartości.  
  
 Modele zawartości są udokumentowane dla różnych klas. Model zawartości dla klasy jest jednym z możliwych czynników, które należy wziąć pod uwagę, jeśli chcesz znaleźć odpowiednią klasę, z której pochodzi. Aby uzyskać więcej informacji, zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Inne klasy bazowe  
  
### <a name="dispatcherobject"></a>DispatcherObject —  
 <xref:System.Windows.Threading.DispatcherObject> zapewnia obsługę modelu wątkowego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i umożliwia skojarzenie wszystkich obiektów utworzonych dla aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z <xref:System.Windows.Threading.Dispatcher>. Nawet jeśli nie pochodzą one z <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>lub <xref:System.Windows.Media.Visual>, należy rozważyć wyprowadzanie z <xref:System.Windows.Threading.DispatcherObject>, aby umożliwić obsługę tego modelu wątkowego. Aby uzyskać więcej informacji, zobacz [model wątkowości](threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual> implementuje koncepcję obiektu 2D, który ogólnie wymaga prezentacji wizualnej w rejonie prostokątny. Rzeczywiste renderowanie <xref:System.Windows.Media.Visual> ma miejsce w innych klasach (nie jest samodzielny), ale Klasa <xref:System.Windows.Media.Visual> zapewnia znany typ, który jest używany przez procesy renderowania na różnych poziomach. <xref:System.Windows.Media.Visual> implementuje testowanie trafień, ale nie ujawnia zdarzeń, które zgłaszają pozytywne testy na trafień (znajdują się w <xref:System.Windows.UIElement>). Aby uzyskać więcej informacji, zobacz [programowanie warstw wizualnych](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> symuluje niezmienności w modyfikowalnym obiekcie przez udostępnienie metody do generowania kopii obiektu, gdy wymagany jest obiekt niezmienny lub żądany ze względu na wydajność. Typ <xref:System.Windows.Freezable> zapewnia wspólną podstawę dla niektórych elementów graficznych, takich jak geometrie i pędzle, a także animacji. W szczególności <xref:System.Windows.Freezable> nie jest <xref:System.Windows.Media.Visual>; może przechowywać właściwości, które stają się właściwościami, gdy <xref:System.Windows.Freezable> jest stosowana do wypełnienia wartości właściwości innego obiektu, a te właściwości mogą mieć wpływ na renderowanie. Aby uzyskać więcej informacji, zobacz [Freezable obiektów — Omówienie](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> jest klasą pochodną <xref:System.Windows.Freezable>, która w sposób umożliwia dodanie warstwy formantu animacji i niektórych elementów członkowskich narzędzia, dzięki czemu właściwości animowane mogą być rozróżniane na podstawie nieanimowanych właściwości.  
  
### <a name="control"></a>formant  
 <xref:System.Windows.Controls.Control> jest zamierzoną klasą bazową dla typu obiektu, który jest przez różnego rodzaju formantem lub składnikiem, w zależności od technologii. Ogólnie rzecz biorąc, klasy formantów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są klasami, które bezpośrednio reprezentują kontrolkę interfejsu użytkownika lub ściśle współpracują z kompozycją kontroli. Podstawowe funkcje, które <xref:System.Windows.Controls.Control> włącza, to Control tworzenia szablonów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Control>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
