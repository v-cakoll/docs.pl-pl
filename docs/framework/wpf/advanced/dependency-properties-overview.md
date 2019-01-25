---
title: Przegląd właściwości zależności
description: Właściwość, która jest wspierana przez system właściwości WPF jest określany jako właściwość zależności. W tym omówieniu opisano system właściwości WPF i możliwości właściwość zależności.
ms.date: 06/06/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 7a7a8cc13a48b453b157443039f11c548756b0fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588655"
---
# <a name="dependency-properties-overview"></a>Przegląd właściwości zależności

Windows Presentation Foundation (WPF) zapewnia zestaw usług, które mogą służyć do rozszerzenia funkcji typu [właściwość](../../../standard/base-types/common-type-system.md#Properties). Zbiorczo te usługi są zwykle określane jako system właściwości WPF. Właściwość, która jest wspierana przez system właściwości WPF jest określany jako właściwość zależności. W tym omówieniu opisano system właściwości WPF i możliwości właściwość zależności. W tym dotyczące używania istniejących właściwości zależności w XAML i kodu. W tym omówieniu wprowadza również specjalistyczne aspektów właściwości zależności, takie jak metadane zależności właściwości oraz sposób tworzenia własnych właściwości zależności niestandardowej klasy.

## <a name="prerequisites"></a>Wymagania wstępne
W tym temacie założono, że niektóre podstawową wiedzę na temat systemu typu platformy .NET i programowanie zorientowane obiektowo. Aby można było pracować z przykładami w tym temacie, należy również zrozumieć XAML i wiedzieć, jak pisać aplikacje WPF. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Właściwości zależności i właściwości aparatu CLR
 W środowisku WPF właściwości są zwykle widoczne jako standard .NET [właściwości](../../../standard/base-types/common-type-system.md#Properties). Na poziomie podstawowym możesz wchodzić w interakcje z tymi właściwościami bezpośrednio i nigdy nie wiadomo, że są one wykonywane jako właściwość zależności. Jednak należy zapoznać się z niektórych lub wszystkich funkcji w systemie właściwości WPF, tak aby można było korzystać z tych funkcji.

Celem właściwości zależności jest sposób do obliczenia wartości właściwości, na podstawie wartości pozostałych danych wejściowych. Te dane wejściowe mogą zawierać właściwości systemu, na przykład motywy i preferencje użytkownika, just-in-time właściwość oznaczanie mechanizmów, takich jak powiązanie danych oraz animacji/scenorysów, szablony wielokrotnego użytku, takie jak zasoby i style lub znane wartości przy użyciu relacji nadrzędny podrzędny z innymi elementami w drzewie elementów. Ponadto można zaimplementować właściwości zależności zapewnienie niezależna Weryfikacja, wartości domyślne, wywołania zwrotne, które monitorują zmiany innych właściwości i systemu, w którym można przekształcić wartości właściwości, na podstawie potencjalnie informacji w czasie wykonywania. Klasy pochodne można również zmienić niektóre szczególne cechy istniejącej właściwości Zastępowanie metadanych właściwości zależności, a nie przesłanianie rzeczywistą implementację istniejących właściwości lub tworzenie nowych właściwości.

Dokumentacja zestawu SDK można zidentyfikować, dla którym właściwość jest właściwością zależności w obecności sekcji informacje dotyczące właściwości zależności, na stronie zarządzana dokumentacja dotycząca dla tej właściwości. Sekcja informacji o zależnościach właściwość zawiera łącze do <xref:System.Windows.DependencyProperty> identyfikator pola dla tej właściwości zależności i zawiera także listę opcji metadanych, które są ustawione dla tej właściwości, informacji o przesłonięciu klasy i inne szczegóły.

## <a name="dependency-properties-back-clr-properties"></a>Właściwości zależności kopii właściwości aparatu CLR
Właściwości zależności i system właściwości WPF należy rozszerzyć funkcjonalność właściwości, zapewniając typ, który tworzy kopię właściwość, jako alternatywnej implementacji do standardowego wzorca zapisywania kopii właściwość z polem prywatnych. Nazwa tego typu jest <xref:System.Windows.DependencyProperty>. Inne ważne typ, który definiuje system właściwości WPF jest <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> definiuje klasę bazową, która może rejestrować i własne właściwości zależności.

Poniższa lista zawiera terminologii, który jest używany z właściwości zależności:

- **Właściwości zależności:** Właściwość, która jest wspierana przez <xref:System.Windows.DependencyProperty>.

- **Identyfikator właściwości zależności:** A <xref:System.Windows.DependencyProperty> wystąpienia, które są uzyskiwane jako wartości zwracanej, podczas rejestrowania właściwości zależności, a następnie jest zapisywana jako członka statycznego w klasie. Ten identyfikator jest używany jako parametr do wielu interfejsów API, które interakcji z systemu właściwości WPF.

- **"Opakowanie" CLR:** Rzeczywiste get i set implementacje dla właściwości. Tych implementacji zestawowi identyfikatora właściwości zależności, korzystając z niego w <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> wywołań, zapewniając w ten sposób zapasowy dla właściwości, korzystając z systemu właściwości WPF.

W poniższym przykładzie zdefiniowano `IsSpinning` właściwości zależności i pokazuje relację <xref:System.Windows.DependencyProperty> identyfikator ma właściwość, która tworzy kopię.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Konwencja nazewnictwa właściwości i tworzenia jego kopii <xref:System.Windows.DependencyProperty> pole jest ważne. Nazwa pola jest zawsze nazwę właściwości, wraz z sufiksem `Property` dołączane. Aby dowiedzieć się więcej o tę Konwencję oraz jego przyczyny, zobacz [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Ustawienie wartości właściwości
Można ustawić właściwości, w kodzie lub w XAML.

### <a name="setting-property-values-in-xaml"></a>Ustawianie wartości właściwości w XAML 
W poniższym przykładzie XAML Określa kolor tła przycisku w kolorze czerwonym. Ten przykład ilustruje przypadek, gdzie wartości prostego ciągu atrybutu XAML jest konwertowany na typ przez parser WPF XAML na typ WPF ( <xref:System.Windows.Media.Color>, poprzez <xref:System.Windows.Media.SolidColorBrush>) w wygenerowanym kodzie.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML obsługuje różne formy składni do ustawiania właściwości. Składnia dla określonej właściwości będzie zależeć od typu wartości, używanego właściwości, a także innych czynników, takich jak obecność konwertera typów. Aby uzyskać więcej informacji na temat składni XAML ustawienie właściwości, zobacz [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) i [składnia XAML w szczegółów](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Na przykład składni-atrybut XAML poniższy kod przedstawia inny tło przycisku. Tym razem, zamiast ustawienia prostego, jednolitego koloru, tła ustawiono obrazu, z elementem reprezentujący ten obraz i źródła tego obrazu, określony jako atrybut elementu zagnieżdżonych. Jest to przykład składni elementu właściwości.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Ustawianie właściwości w kodzie
 Ustawianie wartości właściwości zależności w kodzie jest zwykle po prostu wywołanie do implementacji zestawu udostępnianych przez [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "otoki".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Wprowadzenie wartości właściwości jest również zasadniczo wywołanie do implementacji "otoki" get:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Można również wywołać system właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Nie jest to zazwyczaj konieczne, jeśli są przy użyciu istniejących właściwości (otoki są bardziej wygodne i zapewnić lepsze narażenia właściwości dla narzędzi dla deweloperów), ale wywołanie [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bezpośrednio jest odpowiednie w przypadku niektórych scenariuszy.

Właściwości można również ustawić w XAML i następnie uzyskać dostęp później w kodzie za pomocą związanym z kodem. Aby uzyskać więcej informacji, zobacz [związanym z kodem i XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funkcje właściwości udostępniane przez właściwości zależności
Właściwości zależności zawiera funkcje, które rozszerza funkcjonalność właściwości, a nie właściwością, która jest wspierana przez pola. Często takie funkcje reprezentuje lub obsługuje jedną z następujących funkcji:

- [Zasoby](#resources)

- [Powiązanie danych](#data-binding)

- [Style](#styles)

- [Animacje](#animations)

- [Zastępowanie metadanych](#metadata-overrides)

- [Dziedziczenie wartości właściwości](#property-value-inheritance)

- [Integracja WPF Designer](#wpf-designer-integration)

### <a name="resources"></a>Resources
Wartość właściwości zależności można ustawić, odwołując się do zasobu. Zasoby są zwykle określane jako `Resources` wartości właściwości elementu głównego strony lub aplikacji (te lokalizacje Włącz najdogodniejszy dostęp do zasobu). Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Media.SolidColorBrush> zasobów.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Po zdefiniowaniu zasobu można odwoływać się do zasobu i użyj go, aby podać wartość właściwości:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Ten konkretny zasób jest określany jako [dynamicresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (w programie WPF XAML, możesz użyć odwołania statyczne lub dynamiczne zasobów). Można użyć odwołania do zasobu dynamicznego, możesz musi można Ustawianie właściwości zależności, dlatego specjalnie dynamiczne odwołanie użycie zasobów jest włączona w systemie właściwości WPF. Aby uzyskać więcej informacji, zobacz [zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Zasoby są traktowane jako wartości lokalnej, co oznacza, że jeśli ustawisz innej wartości lokalnej, możesz wyeliminuje odwołanie do zasobu. Aby uzyskać więcej informacji, zobacz [następstwo wartości właściwości](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Powiązanie danych
Właściwości zależności można odwołać się do wartości za pomocą powiązania danych. Powiązywanie danych działa za pośrednictwem składni rozszerzenia znaczników w określonych w XAML, lub <xref:System.Windows.Data.Binding> obiektu w kodzie. Przy użyciu powiązania danych określenie wartości końcowej właściwość jest odroczone do czasu wykonywania, które wartości są uzyskiwane ze źródła danych.

Poniższy przykład ustawia <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button>, za pomocą powiązania zadeklarowanych w XAML. Powiązanie korzysta z kontekstu danych dziedziczone i <xref:System.Windows.Data.XmlDataProvider> źródła danych (niewyświetlany). Powiązanie, sama Określa właściwość source żądany przez <xref:System.Windows.Data.Binding.XPath%2A> w źródle danych.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Powiązania są traktowane jako wartości lokalnej, oznacza to, czy Jeśli ustawisz innej wartości lokalnej, możesz wyeliminuje powiązania. Aby uzyskać więcej informacji, zobacz [następstwo wartości właściwości](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Właściwości zależności lub <xref:System.Windows.DependencyObject> klasy, wykonaj zapewniają natywnej obsługi <xref:System.ComponentModel.INotifyPropertyChanged> na potrzeby powiadomień o zmianach w produkcji <xref:System.Windows.DependencyObject> źródła wartości właściwości dla operacji powiązanie danych. Aby uzyskać więcej informacji na temat tworzenia właściwości do użycia w powiązanie danych można zgłosić zmiany do obiektu docelowego powiązania danych, zobacz [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Style
Style i szablony są dwa chief motywującego scenariusze użycia właściwości zależności. Style są szczególnie przydatne do ustawiania właściwości, które definiują aplikację [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Style są zazwyczaj definiowane jako zasoby w XAML. Style interakcji z systemem właściwość, ponieważ zawierają one zazwyczaj "ustawiających" dla określonej właściwości, a także "triggers", które zmieniają wartość właściwości, na podstawie wartości w czasie rzeczywistym dla innej właściwości.

W poniższym przykładzie utworzono bardzo prosty stylu (może zostać zdefiniowany w <xref:System.Windows.FrameworkElement.Resources%2A> słownika, nie wyświetlane), następnie zastosowanie stylu bezpośrednio do <xref:System.Windows.FrameworkElement.Style%2A> właściwość <xref:System.Windows.Controls.Button>. Metoda ustawiająca zestawy styl <xref:System.Windows.Controls.Control.Background%2A> właściwość ze stylem <xref:System.Windows.Controls.Button> na zielony.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animacje
Właściwości zależności mogą być animowane. Gdy animacji są stosowane i jest uruchomiona, wartość animowany działa z wyższym priorytetem niż wartość (na przykład wartości lokalnego), który ma właściwość, w przeciwnym razie.

Animuje poniższy przykład <xref:System.Windows.Controls.Control.Background%2A> na <xref:System.Windows.Controls.Button> właściwości (z technicznego punktu widzenia <xref:System.Windows.Controls.Control.Background%2A> jest animowany przy użyciu składni elementu właściwości, aby określić puste <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, a następnie <xref:System.Windows.Media.SolidColorBrush.Color%2A> własności, <xref:System.Windows.Media.SolidColorBrush> jest właściwość, która jest bezpośrednio animowany).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Aby uzyskać więcej informacji na temat Animowanie właściwości, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Zastępowanie metadanych
Zastępowanie metadanych dla tej właściwości w przypadku klasy wyprowadzonej z klasy, która pierwotnie rejestruje właściwości zależności można zmienić pewnymi rodzajami zachowań tych właściwości zależności. Zastępowanie metadanych opiera się na <xref:System.Windows.DependencyProperty> identyfikatora. Zastępowanie metadanych nie wymaga ponownej implementacji właściwości. Zmiana metadanych jest obsługiwany natywnie przez system właściwości; Każda klasa przechowuje potencjalnie poszczególnych metadane dla wszystkich właściwości, które są dziedziczone z klasy podstawowej, na podstawie typu.

Poniższy przykład zastępuje metadane dla właściwości zależności <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Zastępowanie metadanych właściwości zależności określonego jest część wzorca wdrożenia, który tworzy kontrolki używające domyślnych stylów z motywów.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Aby uzyskać więcej informacji o zastępowanie i uzyskiwanie metadanych właściwości modelu, zobacz [metadane zależności właściwości](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dziedziczenie wartości właściwości
Element może dziedziczyć wartość właściwości zależności od jego elementu nadrzędnego w drzewie obiektów.

> [!NOTE]
> Zachowanie dziedziczenie wartości właściwości nie globalnie włączono dla wszystkich właściwości zależności, ponieważ czas obliczeń do obsługi dziedziczenia ma wpływ na wydajność. Dziedziczenie wartości właściwości zwykle jest włączona tylko dla właściwości, w którym konkretnego scenariusza sugeruje, że dziedziczenie wartości właściwości jest odpowiednie. Można określić, czy właściwość zależności dziedziczy, analizując **informacje dotyczące właściwości zależności** sekcji dla tej właściwości zależności w odwołaniu do zestawu SDK.

Poniższy przykład pokazuje powiązanie i ustawia <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość, która określa źródło powiązania, który nie został wyświetlony we wcześniejszym przykładzie powiązania. Wszystkie kolejne powiązania w obiekty podrzędne nie trzeba określić źródło, im wartości odziedziczone z <xref:System.Windows.FrameworkElement.DataContext%2A> w obiekcie nadrzędnym <xref:System.Windows.Controls.StackPanel> obiektu. (Alternatywnie obiekt podrzędny zamiast tego można wybrać bezpośrednio określić własny <xref:System.Windows.FrameworkElement.DataContext%2A> lub <xref:System.Windows.Data.Binding.Source%2A> w <xref:System.Windows.Data.Binding>, celowo nie dziedziczonej wartości i zgłaszania i kontekstu danych elementu powiązań.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integracja projektanta WPF
Formant niestandardowy z właściwościami, które są implementowane jako właściwości zależności będą otrzymywać właściwe [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pomocy technicznej. Przykładem jest możliwość edytowania właściwości zależności bezpośrednich i dołączonych przy użyciu **właściwości** okna. Aby uzyskać więcej informacji, zobacz [omówienie tworzenia kontrolek](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Następstwo wartości właściwości
Po otrzymaniu wartość właściwości zależności są potencjalnie uzyskiwania wartość, która została ustawiona dla tej właściwości, za pomocą jednej z pozostałych na podstawie właściwości danych wejściowych, które uczestniczą w systemie właściwości WPF. Następstwo wartości właściwości istnieje, tak aby różne scenariusze dotyczące sposobu właściwości uzyskiwania ich wartości mogą wchodzić w interakcje w przewidywalny sposób.

Rozważmy następujący przykład. Przykład zawiera style, która ma zastosowanie do wszystkich przycisków i ich <xref:System.Windows.Controls.Control.Background%2A> właściwości, ale również określa jeden z przycisków z lokalnie ustawiony <xref:System.Windows.Controls.Control.Background%2A> wartość.

> [!NOTE]
> Zastosowań dokumentacji zestawu SDK warunki "lokalna wartość" lub "lokalnie. Ustaw wartość" od czasu do czasu Omawiając właściwości zależności. Lokalnie ustawiony wartość jest wartością właściwości, który jest ustawiony bezpośrednio na wystąpienie obiektu w kodzie lub jako atrybut elementu w XAML.  
  
W zasadzie pierwszego przycisku dla właściwości ustawiono dwa razy, ale ma zastosowanie tylko jedna wartość: wartość o najwyższym priorytecie. Lokalnie ustawiony wartości ma najwyższy priorytet (z wyjątkiem uruchamiania animacji, ale żadna animacja nie stosuje się w tym przykładzie) i dlatego lokalnie ustaw wartość jest używana zamiast wartości metoda ustawiająca styl tła na pierwszy przycisk. Drugi przycisk ma nie wartości lokalnego (i inne wartości o wyższy priorytet niż style setter), a zatem tło tego przycisku pochodzi z metody ustawiającej stylu.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Dlaczego istnieje następstwo właściwości
Zazwyczaj nie trzeba będzie style Zawsze stosuj i zasłaniać nawet lokalnie ustawiony wartości pojedynczego elementu (w przeciwnym razie byłoby bardzo trudne, ogólnie rzecz biorąc używać stylów lub elementów). W związku z tym, wartości, które pochodzą z style działać na niższym anulują niż lokalnie ustawiony wartość. Dla bardziej szczegółowego listę właściwości zależności i skąd pochodzą może być wartością skutecznych właściwości zależności, zobacz [następstwo wartości właściwości](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Istnieje kilka właściwości zdefiniowanych w przypadku elementów WPF, które nie są właściwościami zależności. Zasadniczo właściwości zostały zaimplementowane jako właściwości zależności tylko wtedy, gdy było potrzeby w celu obsługi co najmniej jeden scenariusze obsługiwane przez system właściwości: wiązania danych, style, animacji, obsługi wartości domyślne, dziedziczenie, dołączone właściwości, lub unieważnieniu.

## <a name="learning-more-about-dependency-properties"></a>Więcej informacji na temat właściwości zależności  

- Dołączona właściwość jest typem właściwości, która obsługuje wyspecjalizowane składnia XAML. Dołączona właściwość często nie mają korespondencji 1:1, z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości i niekoniecznie jest właściwość zależności. Typowym celem dołączoną właściwość jest umożliwienie podrzędnych elementów do zgłaszania wartości właściwości do elementu nadrzędnego, nawet wtedy, gdy element nadrzędny i element podrzędny nie korzystać tę właściwość jako część listy elementów członkowskich klasy. Podstawowy scenariusz jest umożliwienie elementów podrzędnych do powiadamia element nadrzędny, jak powinno zostać wyświetlone w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; na przykład zobacz <xref:System.Windows.Controls.DockPanel.Dock%2A> lub <xref:System.Windows.Controls.Canvas.Left%2A>. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Deweloperzy składników lub deweloperzy aplikacji mogą chcieć tworzyć własne właściwości zależności, aby włączyć funkcje, takie jak powiązania danych lub Obsługa stylów lub wymuszenia unieważnianie i wartość działu pomocy technicznej. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Właściwości zależności powinien ogólnie być uważany właściwości publiczne, dostępny lub co najmniej wykrywane przez dowolny obiekt wywołujący, który ma dostęp do wystąpienia. Aby uzyskać więcej informacji, zobacz [zabezpieczenia właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Zobacz także
- [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Właściwości zależności tylko do odczytu](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)
- [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
