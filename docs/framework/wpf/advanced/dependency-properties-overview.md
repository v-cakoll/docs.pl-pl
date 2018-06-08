---
title: Przegląd właściwości zależności
description: Właściwość, która nie jest obsługiwana przez system właściwości WPF jest określany jako właściwość zależności. Ten przegląd zawiera opis systemu właściwość WPF i możliwości właściwości zależności.
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
ms.openlocfilehash: 36370eb54e75df9bf2bf8eb9e073bbbee995e287
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827010"
---
# <a name="dependency-properties-overview"></a>Przegląd właściwości zależności

Windows Presentation Foundation (WPF) zawiera zestaw usług, których można użyć, aby rozszerzyć funkcjonalność typu [właściwości](../../../standard/base-types/common-type-system.md#Properties). Zbiorczo te usługi są zwykle nazywane systemu właściwość WPF. Właściwość, która nie jest obsługiwana przez system właściwości WPF jest określany jako właściwość zależności. Ten przegląd zawiera opis systemu właściwość WPF i możliwości właściwości zależności. Dotyczy to również sposób użycia istniejącej właściwości zależności w kodzie XAML i w kodzie. To omówienie wprowadza również specjalne aspektów właściwości zależności, takich jak metadanych właściwości zależności oraz sposobu tworzenia własnych właściwości zależności w niestandardowej klasy.

## <a name="prerequisites"></a>Wymagania wstępne
W tym temacie założono, że niektóre podstawową wiedzę na temat system typów .NET i programowanie zorientowane obiektowo. Przed wykonaniem przykłady w tym temacie, należy również poznać XAML i umieć pisać aplikacje WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Właściwości zależności i CLR
 Na platformie WPF, właściwości są zwykle widoczne jako standardowa .NET [właściwości](../../../standard/base-types/common-type-system.md#Properties). Na poziomie podstawowym można bezpośredniej interakcji z tymi właściwościami i nigdy nie wiadomo, że są one zaimplementowane jako właściwości zależności. Jednak należy się zapoznać z niektórych lub wszystkich funkcji w systemie właściwości WPF, dzięki czemu można korzystać z tych funkcji.

Celem właściwości zależności jest zapewnienie sposobem obliczenia wartości właściwości, na podstawie wartości innych danych wejściowych. Te dane wejściowe może zawierać właściwości systemu, takie jak kompozycje i preferencji użytkownika, mechanizmów określenie właściwości just in time, takich jak powiązania danych i animacje/scenorys, szablonów wielokrotnego użytku, takich jak zasoby i style lub znane wartości przy użyciu relacji nadrzędny podrzędny z innymi elementami w drzewie elementu. Ponadto można zaimplementować właściwości zależności niezależne sprawdzania poprawności, wartości domyślne, wywołania zwrotne, które monitorują zmian do innych właściwości oraz systemu, który można przekształcić wartości właściwości na podstawie potencjalnie środowiska uruchomieniowego informacji. Klasy pochodne można również zmienić niektóre określonych właściwości istniejącej właściwości Zastępowanie metadanych właściwości zależności, zamiast zastępowanie rzeczywistego wykonania istniejącej właściwości lub tworzenia nowych właściwości.

Odwołanie do zestawu SDK można określić, która właściwość jest właściwością zależności w obecności sekcji informacje dotyczące właściwości zależności na stronie zarządzane odniesienia dla tej właściwości. Sekcja informacje dotyczące właściwości zależności zawiera łącze do <xref:System.Windows.DependencyProperty> identyfikatora pola dla danej właściwości zależności i zawiera także listę opcji metadanych, które są ustawione dla tej właściwości, według klasy zastąpienie informacji i inne szczegóły.

## <a name="dependency-properties-back-clr-properties"></a>Właściwości zależności kopii CLR właściwości
Właściwości zależności i systemu właściwość WPF rozszerzyć funkcjonalność właściwości, zapewniając typu, aby utworzyć kopię zapasową właściwość, jako alternatywnej implementacji standardowego wzorca zapisywania kopii właściwość z polem prywatnych. Nazwa tego typu jest <xref:System.Windows.DependencyProperty>. Inne ważne Typ definiujący systemu właściwość WPF jest <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> definiuje klasę podstawową, która można rejestrować i własnej właściwości zależności.

Poniższa lista zawiera terminologii, który jest używany z właściwości zależności:

- **Właściwości zależności:** właściwości, która nie jest obsługiwana przez <xref:System.Windows.DependencyProperty>.

- **Identyfikator właściwości zależności:** A <xref:System.Windows.DependencyProperty> wystąpienia, który jest uzyskany jako wartość zwracaną podczas rejestrowania właściwości zależności, a następnie przechowywane jako statyczny element członkowski klasy. Ten identyfikator jest używany jako parametr dla wielu interfejsów API, które interakcji z systemu właściwości WPF.

- **CLR "otoki":** rzeczywiste get i set implementacji dla właściwości. Tych implementacji zastosować identyfikatora właściwości zależności za pomocą w <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> wywołań, zapewniając zapasowy właściwości przy użyciu systemu właściwość WPF.

W poniższym przykładzie zdefiniowano `IsSpinning` właściwości zależności i przedstawia relacje między <xref:System.Windows.DependencyProperty> identyfikator właściwości, aby utworzyć jego kopię zapasową.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Z konwencją nazewnictwa właściwość i jej zapasowy <xref:System.Windows.DependencyProperty> pole jest ważne. Nazwa pola jest zawsze nazwę właściwości, wraz z sufiksem `Property` dołączane. Aby uzyskać więcej informacji na temat tę Konwencję i przyczyny, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Ustawienie wartości właściwości
Można ustawić właściwości, albo w kodzie XAML.

### <a name="setting-property-values-in-xaml"></a>Ustawienie wartości właściwości w języku XAML 
W poniższym przykładzie XAML Określa kolor tła przycisku kolorem czerwonym. W tym przykładzie przedstawiono sytuacji, gdy wartości prostego ciągu atrybutu XAML są, przekonwertować typu przez parser WPF XAML w WPF typu ( <xref:System.Windows.Media.Color>, poprzez <xref:System.Windows.Media.SolidColorBrush>) w wygenerowanym kodzie.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML obsługuje wiele form składni do ustawiania właściwości. Składnia dla określonej właściwości zależy od typu wartości, który używa właściwości, oraz innych czynników, takich jak obecności konwertera typów. Aby uzyskać więcej informacji na ustawienie właściwości składnię języka XAML, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) i [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

Na przykład składni z systemem innym niż atrybut w poniższym przykładzie XAML przedstawiono inne tło przycisku. Teraz, a nie ustawienia prostego pełnego koloru, tło ma ustawioną obrazu z elementem reprezentujący obrazu i źródło obrazu określony jako atrybut elementu zagnieżdżonych. Jest to przykład składni elementu właściwości.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Ustawianie właściwości w kodzie
 Ustawianie wartości właściwości zależności w kodzie jest zwykle tylko wywołania implementacji zestaw udostępnianych przez [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "otoki".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Pobieranie wartości właściwości jest również zasadniczo wywołanie implementacji "otoki" get:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Możesz także wywołać system właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Nie jest to zazwyczaj konieczne, jeśli są przy użyciu istniejącej właściwości (otoki są bardziej wygodne i zapewnienia lepszej narażenia właściwości narzędzia dla deweloperów), ale wywołanie [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] bezpośrednio jest odpowiednie dla pewnych scenariuszy.

Właściwości można także ustawić w języku XAML i następnie dostępne w dalszej części kodu za pomocą kodu powiązanego. Aby uzyskać więcej informacji, zobacz [CodeBehind i języka XAML w WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Właściwość funkcje udostępniane przez właściwości zależności
Właściwości zależności zawiera funkcje, które rozszerza funkcjonalność właściwości, a nie właściwością, która nie jest obsługiwana przez pole. Często takie funkcje reprezentuje lub obsługuje jeden z następujących funkcji:

- [Zasoby](#resources)

- [Powiązanie danych](#data-binding)

- [Style](#styles)

- [Animacje](#animations)

- [Zastępuje metadane](#metadata-overrides)

- [Dziedziczenie wartości właściwości](#property-value-inheritance)

- [Integracja projektanta WPF](#wpf-designer-integration)

### <a name="resources"></a>Resources
Za pomocą odwołań do zasobu można ustawić wartości właściwości zależności. Zasoby są zazwyczaj określana jako `Resources` wartości właściwości elementu głównego strony lub aplikacji (jak najdogodniejszy dostęp do zasobu włączyć te lokalizacje). Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Media.SolidColorBrush> zasobów.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Po zdefiniowaniu jest zasobu, można odwoływać się do zasobu i użyj go, aby podać wartość właściwości:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Konkretnego zasobu jest określany jako [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (w języku XAML w WPF, możesz użyć odwołanie statyczne lub dynamiczne zasobów). Można użyć odwołania do zasobu dynamicznego, na musi być ustawienie do właściwości zależności, więc w szczególności użycie odwołania dynamicznych zasobów obsługujący przez system właściwości WPF. Aby uzyskać więcej informacji, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Zasoby są traktowane jako wartości lokalnej, co oznacza, że jeśli ustawisz wartość innego lokalnego zostanie wyeliminować odwołanie do zasobu. Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Powiązanie danych
Właściwości zależności można odwołać się do wartości za pośrednictwem powiązania danych. Wiązanie danych działa za pośrednictwem składni rozszerzenia znaczników określonych w języku XAML, lub <xref:System.Windows.Data.Binding> obiektu w kodzie. Z powiązaniem danych określenie wartości końcowej właściwość została odroczona do czasu wykonywania, które wartości są uzyskiwane ze źródła danych.

W poniższym przykładzie <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button>, za pomocą powiązania zadeklarowany w języku XAML. Powiązanie używa kontekstu danych dziedziczone i <xref:System.Windows.Data.XmlDataProvider> źródła danych (tego nie pokazano). Powiązanie, sam określa właściwości source żądany przez <xref:System.Windows.Data.Binding.XPath%2A> w źródle danych.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Powiązania są traktowane jako wartości lokalnej, co oznacza, że jeśli ustawisz wartość innego lokalnego zostanie wyeliminować powiązania. Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Właściwości zależności lub <xref:System.Windows.DependencyObject> klasy, czy nie natywną obsługę <xref:System.ComponentModel.INotifyPropertyChanged> do wytwarzania powiadomienia o zmianach w <xref:System.Windows.DependencyObject> źródła wartości właściwości dla operacji wiązania danych. Aby uzyskać więcej informacji na temat tworzenia właściwości do użycia w danych powiązanie może raportować zmiany do cel wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Style
Style i szablony są dwa dyrektora motywujące scenariusze przy użyciu właściwości zależności. Style są szczególnie przydatne do ustawiania właściwości, które definiują aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Style są zazwyczaj definiowane jako zasoby w języku XAML. Style interakcji z systemu właściwości, ponieważ zawierają one zazwyczaj "ustawiające" dla konkretnej właściwości, a także "Wyzwalacze", które Zmień wartość właściwości na podstawie wartości w czasie rzeczywistym dla innej właściwości.

Poniższy przykład tworzy stylu bardzo proste (może zostać zdefiniowany w <xref:System.Windows.FrameworkElement.Resources%2A> słownika nie pokazano), następnie stosuje bezpośrednio do tego stylu <xref:System.Windows.FrameworkElement.Style%2A> właściwość <xref:System.Windows.Controls.Button>. Metoda setter w ustawia styl <xref:System.Windows.Controls.Control.Background%2A> właściwość styl <xref:System.Windows.Controls.Button> zielony.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Aby uzyskać więcej informacji, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animacje
Można animować właściwości zależności. Gdy animacji są stosowane i jest uruchomiona, wartość animowany działa z wyższym priorytetem niż wartość (na przykład wartości lokalnego), który ma właściwość, w przeciwnym razie.

Animuje w poniższym przykładzie <xref:System.Windows.Controls.Control.Background%2A> na <xref:System.Windows.Controls.Button> właściwości (technicznie, <xref:System.Windows.Controls.Control.Background%2A> jest animowany przy użyciu składni elementu właściwości, aby określić puste <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, a następnie <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwości tego <xref:System.Windows.Media.SolidColorBrush> jest właściwość, która jest bezpośrednio animowany).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Aby uzyskać więcej informacji na animowania właściwości, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) i [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Zastępuje metadane
Aby zmienić pewnymi rodzajami zachowań tych właściwości zależności, zastępowanie metadanych dla tej właściwości, gdy pochodzi z klasy, która pierwotnie rejestruje właściwości zależności. Zastępowanie metadanych zależy od <xref:System.Windows.DependencyProperty> identyfikator. Zastępowanie metadanych nie jest wymagane ponowne wdrażanie właściwości. Zmiana metadanych jest obsługiwany natywnie przez system właściwości; Każda klasa przechowuje potencjalnie poszczególnych metadanych dla wszystkich właściwości, które są dziedziczone z klasy podstawowej, na podstawie-type.

Poniższy przykład zastępuje metadane dla właściwości zależności <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Zastępowanie metadanych właściwości tej konkretnej zależności jest częścią implementacji wzorca, który tworzy kontrolki, których można użyć domyślne style kompozycji.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Aby uzyskać więcej informacji na temat zastępowanie i uzyskiwanie metadanych właściwości, zobacz [metadanych właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dziedziczenie wartości właściwości
Element może dziedziczyć wartość właściwości zależności od jego elementu nadrzędnego w drzewie obiektów.

> [!NOTE]
> Zachowanie dziedziczenia wartość właściwości nie globalnie włączono dla wszystkich właściwości zależności, ponieważ podczas obliczania dziedziczenia ma wpływ na wydajność. Dziedziczenie wartości właściwości zwykle jest włączona tylko dla właściwości, w którym danego scenariusza sugeruje, że dziedziczenie wartość właściwości jest odpowiedni. Można określić, czy właściwości zależności dziedziczy analizując **informacje dotyczące właściwości zależności** sekcji danej właściwości zależności w odwołaniu do zestawu SDK.

Poniższy przykład pokazuje powiązania i ustawia <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość, która określa źródło powiązania, który nie był wyświetlany w wcześniejszego przykładu powiązania. Wszystkie kolejne powiązania obiektów podrzędnych nie trzeba określić źródło, dziedziczonej wartości z użyciem <xref:System.Windows.FrameworkElement.DataContext%2A> w obiekcie nadrzędnym <xref:System.Windows.Controls.StackPanel> obiektu. (Można również obiektu podrzędnego zamiast tego można wybrać bezpośrednio określić własne <xref:System.Windows.FrameworkElement.DataContext%2A> lub <xref:System.Windows.Data.Binding.Source%2A> w <xref:System.Windows.Data.Binding>, aby celowo dziedziczonej wartości dla kontekstu danych elementu powiązania.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integracja projektanta WPF
Formant niestandardowy z właściwościami, które są zaimplementowane jako właściwości zależności będą otrzymywać właściwe [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] obsługuje. Przykładem jest możliwość edytowania właściwości zależności bezpośrednich i dołączone z **właściwości** okna. Aby uzyskać więcej informacji, zobacz [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Pierwszeństwo wartość właściwości zależności
Gdy pojawi się wartość właściwości zależności, są potencjalnie uzyskiwania wartość, która została ustawiona dla tej właściwości, za pomocą jednego z innych na podstawie właściwości wejść, które uczestniczą w systemie właściwości WPF. Pierwszeństwo wartość właściwości zależności istnieje, aby różne scenariusze dotyczące sposobu właściwości pobierania ich wartości można posługiwać się w sposób przewidywalne.

Rozważmy następujący przykład. Przykład zawiera styl, który ma zastosowanie do wszystkich przycisków i ich <xref:System.Windows.Controls.Control.Background%2A> właściwości, ale następnie również określa jeden z przycisków lokalnie ustawionej <xref:System.Windows.Controls.Control.Background%2A> wartość.

> [!NOTE]
> Używa dokumentacji zestawu SDK warunki "wartości lokalnych" lub "lokalnie ustaw wartość" od czasu do czasu Omawiając właściwości zależności. Lokalnie ustaw wartość jest wartością właściwości ustawionej bezpośrednio na wystąpienie obiektu w kodzie, lub jako atrybut elementu w języku XAML.  
  
Zasadniczo dla przycisku pierwszej właściwość jest ustawiona dwa razy, ale ma zastosowanie tylko jedna wartość: wartość o najwyższym priorytecie. Lokalnie ustaw wartość ma najwyższy priorytet (z wyjątkiem uruchomionej animacji, ale żadna animacja nie stosuje się w tym przykładzie) i w związku z tym lokalnie ustaw wartość jest używana zamiast wartości metody ustawiającej styl tła na przycisku pierwszej. Drugi przycisk ma nie wartości lokalnego (i inne wartości o wyższy priorytet niż element style setter) i w związku z tym tło przycisku pochodzi z metody ustawiającej stylu.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Dlaczego istnieje zależność właściwości pierwszeństwa
Zazwyczaj nie trzeba będzie style Zawsze stosuj i przesłaniać nawet lokalnie ustaw wartość pojedynczego elementu (w przeciwnym wypadku byłoby bardzo trudne do użycia na ogół style lub elementów). W związku z tym wartości, które pochodzą ze stylów działania na niższa część niż lokalnie ustawione wartości. Bardziej szczegółowego listę właściwości zależności i skąd pochodzą może efektywną wartość właściwości zależności, zobacz [pierwszeństwo wartość właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Istnieje wiele właściwości, zdefiniowaną dla elementów WPF, które nie są właściwościami zależności. Zasadniczo właściwości zostały zaimplementowane jako właściwości zależności, tylko wtedy, gdy było musi obsługiwać co najmniej jednego ze scenariuszy włączane przez system właściwości: powiązanie, style, animacji, obsługi wartość domyślną, dziedziczenia, danych dołączone do właściwości, lub unieważnienie.

## <a name="learning-more-about-dependency-properties"></a>Więcej informacji na temat właściwości zależności  

- Dołączona właściwość jest typu właściwości, która obsługuje specjalne składni w języku XAML. Dołączona właściwość często nie ma korespondencji 1:1, z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości, oraz nie jest właściwością zależności. Typowy celem dołączona właściwość jest umożliwienie podrzędne elementy do wartości właściwości raportu, aby element nadrzędny, nawet wtedy, gdy element nadrzędny i element podrzędny nie oba posiadają tej właściwości jako część listy elementów członkowskich klasy. Scenariusz podstawowy jest umożliwienie powiadamia element nadrzędny jak powinny być przedstawiane na liście elementów podrzędnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; na przykład, zobacz <xref:System.Windows.Controls.DockPanel.Dock%2A> lub <xref:System.Windows.Controls.Canvas.Left%2A>. Aby uzyskać więcej informacji, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Deweloperzy składnika lub deweloperzy aplikacji może być wymagane utworzenie własnych właściwości zależności, aby włączyć możliwości, takie jak powiązania danych lub style pomocy technicznej lub koercja unieważnianie i wartość działu pomocy technicznej. Aby uzyskać więcej informacji, zobacz [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Ogólnie należy traktować właściwości zależności jako właściwości publiczne, dostępny lub co najmniej wykrywalny przez dowolnego obiekt wywołujący, który ma dostęp do wystąpienia. Aby uzyskać więcej informacji, zobacz [zabezpieczeń właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Zobacz także
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Właściwości zależności tylko do odczytu](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
