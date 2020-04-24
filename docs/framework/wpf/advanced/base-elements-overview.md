---
title: Przegląd Elementy bazy
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: f6519675ebf3624152e1077e7582f04e38b1dce9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644040"
---
# <a name="base-elements-overview"></a>Przegląd Elementy bazy
Wysoki procent klas [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w są uzyskiwane z czterech klas, które są powszechnie określane w dokumentacji SDK jako klasy elementów podstawowych. Klasy te <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkElement>są <xref:System.Windows.ContentElement>, <xref:System.Windows.FrameworkContentElement>, i . Klasa <xref:System.Windows.DependencyObject> jest również powiązana, ponieważ jest to <xref:System.Windows.UIElement> wspólna klasa podstawowa zarówno<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>Interfejsy API elementu podstawowego w klasach WPF  
 Oba <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> i pochodzą <xref:System.Windows.DependencyObject>z , poprzez nieco inne ścieżki. Podział na tym poziomie dotyczy <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> sposobu lub są używane w interfejsie użytkownika i w jakim celu służą w aplikacji. <xref:System.Windows.UIElement>również <xref:System.Windows.Media.Visual> ma w swojej hierarchii klas, która jest klasą, która [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]udostępnia obsługę grafiki niższego poziomu leżącego u podstaw . <xref:System.Windows.Media.Visual>zapewnia strukturę renderowania, definiując niezależne prostokątne obszary ekranu. W praktyce jest dla elementów, <xref:System.Windows.UIElement> które będą obsługiwać większy model obiektu, są przeznaczone do renderowania i układu w regionach, które mogą być opisane jako prostokątne obszary ekranu i gdzie model zawartości jest celowo bardziej otwarty, aby umożliwić różne kombinacje elementów. <xref:System.Windows.ContentElement>nie pochodzi z <xref:System.Windows.Media.Visual>; jego model jest <xref:System.Windows.ContentElement> to, że będzie zużywane przez coś innego, takich jak czytnik <xref:System.Windows.Media.Visual> lub [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] widza, który następnie interpretować elementy i produkować kompletne do konsumpcji. Niektóre <xref:System.Windows.UIElement> klasy mają być hostami zawartości: zapewniają hosting i <xref:System.Windows.ContentElement> renderowanie<xref:System.Windows.Controls.DocumentViewer> dla jednej lub więcej klas ( jest przykładem takiej klasy). <xref:System.Windows.ContentElement>jest używana jako klasa podstawowa dla elementów z nieco mniejszymi modelami obiektów i która <xref:System.Windows.UIElement>bardziej odnosi się do tekstu, informacji lub zawartości dokumentu, które mogą być hostowane w programie .  
  
### <a name="framework-level-and-core-level"></a>Poziom ram i poziom rdzenia  
 <xref:System.Windows.UIElement>służy jako klasa <xref:System.Windows.FrameworkElement>podstawowa <xref:System.Windows.ContentElement> dla , i <xref:System.Windows.FrameworkContentElement>służy jako klasa podstawowa dla . Powodem tego następnego poziomu klas jest obsługa poziomu rdzenia WPF, który jest oddzielony od poziomu struktury WPF, z tego podziału również istniejące w jaki sposób interfejsy API są podzielone między PresentationCore i PresentationFramework zestawów. Poziom struktury WPF przedstawia bardziej kompletne rozwiązanie dla podstawowych potrzeb aplikacji, w tym implementacji menedżera układu do prezentacji. Poziom rdzenia WPF zapewnia sposób [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użycia wiele bez podejmowania narzutu dodatkowego zestawu. Rozróżnienie między tymi poziomami bardzo rzadko ma znaczenie dla większości typowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] scenariuszy tworzenia aplikacji i ogólnie należy myśleć o interfejsach API jako całości i nie dotyczą się z różnicy między poziomem struktury WPF I WPF poziom rdzenia. Może być konieczne wiedzieć o różnice poziomu, jeśli projekt aplikacji zdecyduje się zastąpić znaczne ilości funkcji na poziomie struktury WPF, na przykład jeśli ogólne rozwiązanie ma już własne implementacje kompozycji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] i układu.  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>Wybieranie elementu, z którego ma pochodzić  
 Najbardziej praktycznym sposobem utworzenia klasy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niestandardowej, która rozszerza [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się jest przez wyprowadzenie z jednej z klas, gdzie można uzyskać jak najwięcej żądanej funkcjonalności za pośrednictwem istniejącej hierarchii klas. W tej sekcji wymieniono funkcje, które pochodzi z trzech najważniejszych klas elementów, które pomogą Ci zdecydować, które klasy dziedziczyć z.  
  
 Jeśli implementujesz formant, który jest naprawdę jednym z bardziej typowych powodów, dla pochodzących z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasy, prawdopodobnie chcesz pochodzić z klasy, która <xref:System.Windows.Controls.Control> jest praktyczną formantem, klasą podstawową rodziny kontroli lub przynajmniej z klasy podstawowej. Aby uzyskać pewne wskazówki i praktyczne przykłady, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).  
  
 Jeśli nie tworzysz formantu i trzeba wyprowadzić z klasy, która jest wyższa w hierarchii, poniższe sekcje są przeznaczone jako przewodnik dla tego, jakie właściwości są zdefiniowane w każdej klasie elementu podstawowego.  
  
 Jeśli utworzysz klasę, <xref:System.Windows.DependencyObject>która wywodzi się z programu , dziedziczysz następujące funkcje:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>wsparcia <xref:System.Windows.DependencyObject.SetValue%2A> i wsparcia oraz ogólnego wsparcia systemu własności.  
  
- Możliwość używania właściwości zależności i dołączonych właściwości, które są implementowane jako właściwości zależności.  
  
 Jeśli utworzysz klasę, <xref:System.Windows.UIElement>która wywodzi się z , <xref:System.Windows.DependencyObject>dziedziczysz następujące funkcje oprócz funkcji dostarczonych przez:  
  
- Podstawowa obsługa animowanych wartości właściwości. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
- Podstawowa obsługa zdarzeń wejściowych i obsługa polecenia. Aby uzyskać więcej informacji, zobacz [Omówienie wprowadzania i](input-overview.md) [omówienie poleceń](commanding-overview.md).  
  
- Metody wirtualne, które można zastąpić, aby dostarczyć informacji do systemu układu.  
  
 Jeśli utworzysz klasę, <xref:System.Windows.FrameworkElement>która wywodzi się z , <xref:System.Windows.UIElement>dziedziczysz następujące funkcje oprócz funkcji dostarczonych przez:  
  
- Obsługa stylów i scenochłów. Aby uzyskać więcej <xref:System.Windows.Style> informacji, zobacz [omówienie scenochorystur](../graphics-multimedia/storyboards-overview.md).  
  
- Obsługa powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Obsługa dynamicznych odwołań do zasobów. Aby uzyskać więcej informacji, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Obsługa dziedziczenia wartości właściwości i inne flagi w metadanych, które pomagają zgłaszać warunki dotyczące właściwości do usług framework, takich jak powiązanie danych, style lub implementacja struktury układu. Aby uzyskać więcej informacji, zobacz [Metadata właściwości framework](framework-property-metadata.md).  
  
- Koncepcja drzewa logicznego. Aby uzyskać więcej informacji, zobacz [Drzewa w WPF](trees-in-wpf.md).  
  
- Obsługa praktycznej implementacji na poziomie struktury WPF <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> systemu układu, w tym zastąpienia, które można wykryć zmiany właściwości, które wpływają na układ.  
  
 Jeśli utworzysz klasę, <xref:System.Windows.ContentElement>która wywodzi się z , <xref:System.Windows.DependencyObject>dziedziczysz następujące funkcje oprócz funkcji dostarczonych przez:  
  
- Obsługa animacji. Aby uzyskać więcej informacji, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
- Podstawowa obsługa zdarzeń wejściowych i obsługa polecenia. Aby uzyskać więcej informacji, zobacz [Omówienie wprowadzania i](input-overview.md) [omówienie poleceń](commanding-overview.md).  
  
 Jeśli utworzysz klasę, <xref:System.Windows.FrameworkContentElement>która wywodzi się z , <xref:System.Windows.ContentElement>otrzymasz następujące funkcje oprócz tej dostarczonej przez:  
  
- Obsługa stylów i scenochłów. Aby uzyskać więcej <xref:System.Windows.Style> informacji, zobacz [omówienie animacji](../graphics-multimedia/animation-overview.md).  
  
- Obsługa powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Obsługa dynamicznych odwołań do zasobów. Aby uzyskać więcej informacji, zobacz [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Obsługa dziedziczenia wartości właściwości i inne flagi w metadanych, które pomagają zgłaszać warunki dotyczące właściwości do usług framework, takich jak powiązanie danych, style lub implementacja struktury układu. Aby uzyskać więcej informacji, zobacz [Metadata właściwości framework](framework-property-metadata.md).  
  
- Nie dziedziczą dostępu do modyfikacji układu <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>systemu (takich jak ). Implementacje systemu układu <xref:System.Windows.FrameworkElement>są dostępne tylko w programie . Dziedziczysz jednak <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> zastąpienie, które może wykryć zmiany właściwości, które wpływają na układ i zgłosić je do wszystkich hostów zawartości.  
  
 Modele zawartości są dokumentowane dla różnych klas. Model zawartości dla klasy jest jednym z możliwych czynników, które należy wziąć pod uwagę, jeśli chcesz znaleźć odpowiednią klasę, z której można się wyprowadzić. Aby uzyskać więcej informacji, zobacz [Model zawartości WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>Inne klasy podstawowe  
  
### <a name="dispatcherobject"></a>Dispatcherobject  
 <xref:System.Windows.Threading.DispatcherObject>zapewnia obsługę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu wątkowego i umożliwia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] skojarzenie wszystkich obiektów <xref:System.Windows.Threading.Dispatcher>utworzonych dla aplikacji z programem . Nawet jeśli nie pochodzisz <xref:System.Windows.UIElement> <xref:System.Windows.DependencyObject>z <xref:System.Windows.Media.Visual>, lub , należy <xref:System.Windows.Threading.DispatcherObject> rozważyć wyprowadzenie z w celu uzyskania tej obsługi modelu wątków. Aby uzyskać więcej informacji, zobacz [Model wątkowy](threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual>implementuje koncepcję obiektu 2D, który zazwyczaj wymaga prezentacji wizualnej w regionie z grubsza prostokątnym. Rzeczywiste renderowanie odbywa <xref:System.Windows.Media.Visual> się w innych klasach (nie jest <xref:System.Windows.Media.Visual> samodzielny), ale klasa zapewnia znany typ, który jest używany przez procesy renderowania na różnych poziomach. <xref:System.Windows.Media.Visual>implementuje testy trafień, ale nie ujawnia zdarzeń, które zgłaszają <xref:System.Windows.UIElement>pozytywy testów trafień (są w ). Aby uzyskać więcej informacji, zobacz [Programowanie warstw wizualnych](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>symuluje niezmienność w zmiennym obiekcie, udostępniając środki do generowania kopii obiektu, gdy niezmienny obiekt jest wymagany lub pożądany ze względu na wydajność. Typ <xref:System.Windows.Freezable> zapewnia wspólną podstawę dla niektórych elementów graficznych, takich jak geometrie i pędzle, a także animacje. W szczególności, <xref:System.Windows.Freezable> nie <xref:System.Windows.Media.Visual>jest ; może przechowywać właściwości, które stają się <xref:System.Windows.Freezable> właściwościpodwładne, gdy jest stosowany do wypełnienia wartości właściwości innego obiektu, a te właściwości podrzędne mogą mieć wpływ na renderowanie. Aby uzyskać więcej informacji, zobacz [Omówienie obiektów freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>jest <xref:System.Windows.Freezable> klasą pochodną, która w szczególności dodaje warstwę kontrolną animacji i niektóre elementy członkowskie narzędzia, dzięki czemu aktualnie animowane właściwości można odróżnić od właściwości nieanimowanych.  
  
### <a name="control"></a>Kontrola  
 <xref:System.Windows.Controls.Control>jest przeznaczoną klasą podstawową dla typu obiektu, który jest różnie określany jako formant lub składnik, w zależności od technologii. Ogólnie rzecz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biorąc klasy kontroli są klasy, które bezpośrednio reprezentują formant interfejsu użytkownika lub uczestniczyć ściśle w kompozycji kontroli. Podstawową funkcją, która <xref:System.Windows.Controls.Control> umożliwia jest formowanie templating.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.Control>
- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
