---
title: Omówienie właściwości zależności
description: Właściwość, która jest wspierana przez system właściwości WPF jest znany jako właściwość zależności. W tym przeglądzie opisano system właściwości WPF i możliwości właściwości zależności.
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
ms.openlocfilehash: 542e0a84e4c5cfc3750c33fe29cb40d3643e91e3
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80636027"
---
# <a name="dependency-properties-overview"></a>Omówienie właściwości zależności

Windows Presentation Foundation (WPF) udostępnia zestaw usług, które mogą służyć do rozszerzenia funkcjonalności [właściwości](../../../standard/base-types/common-type-system.md#properties)typu . Łącznie te usługi są zazwyczaj określane jako system właściwości WPF. Właściwość, która jest wspierana przez system właściwości WPF jest znany jako właściwość zależności. W tym przeglądzie opisano system właściwości WPF i możliwości właściwości zależności. Obejmuje to, jak używać istniejących właściwości zależności w XAML i w kodzie. W tym przeglądzie przedstawiono również specjalistyczne aspekty właściwości zależności, takie jak metadane właściwości zależności i jak utworzyć własną właściwość zależności w klasie niestandardowej.

## <a name="prerequisites"></a>Wymagania wstępne
W tym temacie założono, że masz podstawową wiedzę na temat systemu typu .NET i programowania obiektowego. Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć XAML i wiedzieć, jak pisać aplikacje WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: Moja pierwsza aplikacja komputerowa WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Właściwości zależności i właściwości CLR
 W WPF WPF właściwości są zazwyczaj udostępniane jako standardowe [właściwości](../../../standard/base-types/common-type-system.md#properties).NET . Na poziomie podstawowym można wchodzić w interakcje z tymi właściwościami bezpośrednio i nigdy nie wiedzieć, że są one implementowane jako właściwość zależności. Jednak należy zapoznać się z niektórych lub wszystkich funkcji systemu właściwości WPF, dzięki czemu można skorzystać z tych funkcji.

Celem właściwości zależności jest zapewnienie sposobu obliczania wartości właściwości na podstawie wartości innych danych wejściowych. Te inne dane wejściowe mogą obejmować właściwości systemu, takie jak motywy i preferencje użytkownika, mechanizmy określania właściwości just-in-time, takie jak powiązanie danych i animacje/scenorysy, szablony wielokrotnego użytku, takie jak zasoby i style, lub wartości znane za pośrednictwem relacji nadrzędny podrzędny z innymi elementami w drzewie elementów. Ponadto właściwość zależności może być zaimplementowana w celu zapewnienia niezależnej weryfikacji, wartości domyślnych, wywołań zwrotnych, które monitorują zmiany w innych właściwościach, oraz systemu, który może wymuszać wartości właściwości na podstawie potencjalnie informacji o czasie wykonywania. Klasy pochodne można również zmienić niektóre specyficzne cechy istniejącej właściwości przez zastąpienie metadanych właściwości zależności, zamiast zastępowania rzeczywistej implementacji istniejących właściwości lub tworzenia nowych właściwości.

W odwołaniu do SDK można zidentyfikować, która właściwość jest właściwością zależności przez obecność sekcji Informacje o właściwości zależności na stronie odwołania do zarządzanego dla tej właściwości. Sekcja Informacje o właściwości zależności zawiera <xref:System.Windows.DependencyProperty> łącze do pola identyfikatora dla tej właściwości zależności, a także zawiera listę opcji metadanych, które są ustawione dla tej właściwości, informacje o zastępowania dla klasy i inne szczegóły.

## <a name="dependency-properties-back-clr-properties"></a>Właściwości zależności z powrotem właściwości CLR
Właściwości zależności i system właściwości WPF rozszerzają funkcjonalność właściwości, udostępniając typ, który tworzy kopię zapasową właściwości, jako alternatywną implementację do standardowego wzorca tworzenia kopii zapasowej właściwości z polem prywatnym. Nazwa tego typu <xref:System.Windows.DependencyProperty>to . Innym ważnym typem, który definiuje system <xref:System.Windows.DependencyObject>właściwości WPF jest . <xref:System.Windows.DependencyObject>definiuje klasę podstawową, która może rejestrować i posiadać właściwość zależności.

Poniżej wymieniono terminologię używaną z właściwościami zależności:

- **Właściwość zależności:** Właściwość, która jest <xref:System.Windows.DependencyProperty>wspierana przez .

- **Identyfikator właściwości zależności:** Wystąpienie, <xref:System.Windows.DependencyProperty> które jest uzyskiwane jako wartość zwracana podczas rejestrowania właściwości zależności, a następnie przechowywane jako statyczny element członkowski klasy. Ten identyfikator jest używany jako parametr dla wielu interfejsów API, które współdziałają z systemem właściwości WPF.

- **CLR "owijka":** Rzeczywiste get i ustawić implementacje dla właściwości. Te implementacje zawierają identyfikator właściwości zależności przy <xref:System.Windows.DependencyObject.GetValue%2A> użyciu <xref:System.Windows.DependencyObject.SetValue%2A> go w i wywołuje, zapewniając w ten sposób kopię zapasowa dla właściwości przy użyciu systemu właściwości WPF.

Poniższy przykład definiuje `IsSpinning` właściwość zależności i pokazuje <xref:System.Windows.DependencyProperty> relację identyfikatora z właściwością, którą wspiera.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Konwencja nazewnictwa właściwości i <xref:System.Windows.DependencyProperty> jej pola zapasowego jest ważna. Nazwa pola jest zawsze nazwą właściwości, z dodatkiem `Property` sufiksu. Aby uzyskać więcej informacji na temat tej konwencji i jej przyczyn, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Ustawianie wartości właściwości
Właściwości można ustawić w kodzie lub w formacie XAML.

### <a name="setting-property-values-in-xaml"></a>Ustawianie wartości właściwości w języku XAML
Poniższy przykład XAML określa kolor tła przycisku jako czerwony. W tym przykładzie ilustruje przypadek, w którym wartość prostego ciągu dla atrybutu XAML jest konwertowany <xref:System.Windows.Media.Color>przez analizator <xref:System.Windows.Media.SolidColorBrush>WPF XAML na typ WPF (a , w drodze a) w wygenerowanym kodzie.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML obsługuje różne formularze składni do ustawiania właściwości. Składnia, która ma być używana dla określonej właściwości, będzie zależeć od typu wartości używanego przez właściwość, a także od innych czynników, takich jak obecność konwertera typu. Aby uzyskać więcej informacji na temat składni XAML dla ustawiania właściwości, zobacz [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) i [Składnia XAML w szczegółach](xaml-syntax-in-detail.md).

Jako przykład składni bez atrybutów, w poniższym przykładzie XAML pokazano inne tło przycisku. Tym razem, zamiast ustawiania prostego koloru jednolitego, tło jest ustawione na obraz, z elementem reprezentującym ten obraz i źródłem tego obrazu określonym jako atrybut elementu zagnieżdżonego. Jest to przykład składni elementu właściwości.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Ustawianie właściwości w kodzie
 Ustawienie wartości właściwości zależności w kodzie jest zazwyczaj tylko wywołanie implementacji zestawu udostępniane przez CLR "otoki".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Uzyskanie wartości właściwości jest również zasadniczo wywołanie get "otoki" implementacji:

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Można również wywołać interfejsy <xref:System.Windows.DependencyObject.GetValue%2A> API <xref:System.Windows.DependencyObject.SetValue%2A> systemu właściwości i bezpośrednio. Nie jest to zazwyczaj konieczne, jeśli używasz istniejących właściwości (otoki są wygodniejsze i zapewniają lepszą ekspozycję właściwości dla narzędzi deweloperskich), ale bezpośrednie wywołanie interfejsów API jest odpowiednie dla niektórych scenariuszy.

Właściwości można również ustawić w XAML, a następnie uzyskać dostęp później w kodzie, za pośrednictwem kodu. Aby uzyskać szczegółowe informacje, zobacz [Code-Behind i XAML w WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funkcjonalność właściwości zapewniana przez właściwość zależności
Właściwość zależności zapewnia funkcjonalność, która rozszerza funkcjonalność właściwości, w przeciwieństwie do właściwości, która jest wspierana przez pole. Często taka funkcja reprezentuje lub obsługuje jedną z następujących funkcji:

- [Zasoby](#resources)

- [Powiązanie danych](#data-binding)

- [Style](#styles)

- [Animacje](#animations)

- [Zastąpienia metadanych](#metadata-overrides)

- [Dziedziczenie wartości właściwości](#property-value-inheritance)

- [Integracja z projektantem WPF](#wpf-designer-integration)

### <a name="resources"></a>Zasoby
Wartość właściwości zależności można ustawić, odwołując się do zasobu. Zasoby są zazwyczaj określone `Resources` jako wartość właściwości elementu głównego strony lub aplikacji (te lokalizacje umożliwiają najwygodniejszy dostęp do zasobu). W poniższym przykładzie <xref:System.Windows.Media.SolidColorBrush> pokazano, jak zdefiniować zasób.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Po zdefiniowaniu zasobu można odwoływać się do zasobu i używać go do zapewnienia wartości właściwości:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Ten konkretny zasób odwołuje się jako [Rozszerzenie znaczników DynamicResource](dynamicresource-markup-extension.md) (w WPF XAML można użyć statycznego lub dynamicznego odwołania do zasobu). Aby użyć odwołania do zasobu dynamicznego, należy ustawienie właściwości zależności, więc jest to w szczególności użycie odwołania do zasobów dynamicznych, które jest włączone przez system właściwości WPF. Aby uzyskać więcej informacji, zobacz [Zasoby XAML](xaml-resources.md).

> [!NOTE]
> Zasoby są traktowane jako wartość lokalna, co oznacza, że jeśli ustawisz inną wartość lokalną, wyeliminujesz odwołanie do zasobu. Aby uzyskać więcej informacji, zobacz [Priorytet wartości właściwości zależności](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Powiązanie danych
Właściwość zależności może odwoływać się do wartości za pośrednictwem powiązania danych. Powiązanie danych działa za pośrednictwem określonej składni rozszerzenia <xref:System.Windows.Data.Binding> znaczników w języku XAML lub obiektu w kodzie. W przypadku powiązania danych określenie wartości właściwości końcowej jest odroczone do czasu wykonywania, w którym to czasie wartość jest uzyskiwana ze źródła danych.

W poniższym <xref:System.Windows.Controls.ContentControl.Content%2A> przykładzie <xref:System.Windows.Controls.Button>ustawia właściwość dla , przy użyciu powiązania zadeklarowane w XAML. Powiązanie używa kontekstu danych dziedziczonych <xref:System.Windows.Data.XmlDataProvider> i źródła danych (nie pokazano). Samo powiązanie określa żądaną <xref:System.Windows.Data.Binding.XPath%2A> właściwość źródłową w źródle danych.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Powiązania są traktowane jako wartość lokalna, co oznacza, że jeśli ustawisz inną wartość lokalną, wyeliminujesz powiązanie. Aby uzyskać szczegółowe informacje, zobacz [Pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).

Właściwości zależności lub <xref:System.Windows.DependencyObject> klasy nie są natywnie obsługiwane <xref:System.ComponentModel.INotifyPropertyChanged> na potrzeby tworzenia <xref:System.Windows.DependencyObject> powiadomień o zmianach wartości właściwości źródłowej dla operacji wiązania danych. Aby uzyskać więcej informacji na temat tworzenia właściwości do użycia w powiązaniu danych, które mogą zgłaszać zmiany w docelowym powiązaniu danych, zobacz [Omówienie powiązania danych](../data/data-binding-overview.md).

### <a name="styles"></a>Style
Style i szablony są dwa główne scenariusze motywujące do korzystania z właściwości zależności. Style są szczególnie przydatne do ustawiania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]właściwości definiujących aplikację . Style są zazwyczaj definiowane jako zasoby w języku XAML. Style współdziałają z systemem właściwości, ponieważ zazwyczaj zawierają "setters" dla określonych właściwości, a także "wyzwalacze", które zmieniają wartość właściwości na podstawie wartości w czasie rzeczywistym dla innej właściwości.

Poniższy przykład tworzy prosty styl (który <xref:System.Windows.FrameworkElement.Resources%2A> byłby zdefiniowany wewnątrz słownika, nie pokazano), <xref:System.Windows.FrameworkElement.Style%2A> a <xref:System.Windows.Controls.Button>następnie stosuje ten styl bezpośrednio do właściwości dla . Ustawiacz w stylu ustawia <xref:System.Windows.Controls.Control.Background%2A> właściwość dla <xref:System.Windows.Controls.Button> stylu na zielony.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Aby uzyskać więcej informacji, zobacz [Stylowanie i tworzenie szablonów](../controls/styling-and-templating.md).

### <a name="animations"></a>Animacje
Właściwości zależności mogą być animowane. Gdy animacja jest stosowana i jest uruchomiona, animowana wartość działa z wyższym priorytetem niż jakakolwiek wartość (na przykład wartość lokalna), która ma właściwość w przeciwnym razie.

Poniższy <xref:System.Windows.Controls.Control.Background%2A> przykład animuje <xref:System.Windows.Controls.Button> na właściwości (technicznie <xref:System.Windows.Controls.Control.Background%2A> jest animowany przy użyciu składni <xref:System.Windows.Media.SolidColorBrush> elementu <xref:System.Windows.Controls.Control.Background%2A>właściwości, <xref:System.Windows.Media.SolidColorBrush.Color%2A> aby określić puste jako , a następnie właściwość, która <xref:System.Windows.Media.SolidColorBrush> jest właściwość, która jest bezpośrednio animowane).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Aby uzyskać więcej informacji na temat animowania właściwości, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md) i [Omówienie scenochorystur](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Zastąpienia metadanych
Można zmienić niektóre zachowania właściwości zależności, zastępując metadane dla tej właściwości, gdy pochodzisz z klasy, która pierwotnie rejestruje właściwość zależności. Zastępowanie metadanych zależy <xref:System.Windows.DependencyProperty> od identyfikatora. Nadrzędne metadane nie wymaga ponownego implementacji właściwości. Zmiana metadanych jest obsługiwana natywnie przez system właściwości; każda klasa potencjalnie przechowuje indywidualne metadane dla wszystkich właściwości, które są dziedziczone z klas podstawowych, na podstawie typu.

Poniższy przykład zastępuje metadane właściwości <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>zależności . Zastępowanie tego metadanych właściwości określonej zależności jest częścią wzorca implementacji, który tworzy formanty, które mogą używać domyślnych stylów z motywów.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Aby uzyskać więcej informacji na temat zastępowania lub uzyskiwania metadanych właściwości, zobacz [Metadane właściwości zależności](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dziedziczenie wartości właściwości
Element może dziedziczyć wartość właściwości zależności z jego elementu nadrzędnego w drzewie obiektów.

> [!NOTE]
> Zachowanie dziedziczenia wartości właściwości nie jest globalnie włączone dla wszystkich właściwości zależności, ponieważ czas obliczania dziedziczenia ma pewien wpływ na wydajność. Dziedziczenie wartości właściwości jest zazwyczaj włączone tylko dla właściwości, w których określony scenariusz sugeruje, że dziedziczenie wartości właściwości jest odpowiednie. Można określić, czy właściwość zależności dziedziczy, patrząc na **informacje o właściwości zależności** sekcji dla tej właściwości zależności w odwołaniu SDK.

Poniższy przykład pokazuje powiązanie <xref:System.Windows.FrameworkElement.DataContext%2A> i ustawia właściwość, która określa źródło powiązania, które nie zostało pokazane we wcześniejszym przykładzie wiązania. Wszelkie kolejne powiązania w obiektach podrzędnych nie trzeba określać źródła, <xref:System.Windows.FrameworkElement.DataContext%2A> mogą <xref:System.Windows.Controls.StackPanel> używać dziedziczonej wartości w obiekcie nadrzędnym. (Alternatywnie obiekt podrzędny może zamiast tego wybrać <xref:System.Windows.FrameworkElement.DataContext%2A> opcję <xref:System.Windows.Data.Binding.Source%2A> bezpośredniego <xref:System.Windows.Data.Binding>określenia własnego lub w , i celowo nie używać dziedziczonej wartości dla kontekstu danych jego powiązań.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Aby uzyskać więcej informacji, zobacz [Dziedziczenie wartości właściwości](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integracja projektanta WPF
Formant niestandardowy z właściwości, które są implementowane jako właściwości zależności otrzyma odpowiednie WPF Designer dla programu Visual Studio pomocy technicznej. Jednym z przykładów jest możliwość edytowania właściwości bezpośredniego i dołączone zależności z **właściwości** okna. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia formantu](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Pierwszeństwo wartości właściwości zależności
Po uzyskaniu wartości właściwości zależności, są potencjalnie uzyskanie wartości, która została ustawiona na tej właściwości za pośrednictwem jednego z innych danych wejściowych opartych na właściwości, które uczestniczą w systemie właściwości WPF. Typy wartości właściwości zależności istnieje tak, że wiele scenariuszy, jak właściwości uzyskać ich wartości mogą współdziałać w przewidywalny sposób.

Rozważmy następujący przykład. Przykład zawiera styl, który ma zastosowanie <xref:System.Windows.Controls.Control.Background%2A> do wszystkich przycisków i ich właściwości, ale <xref:System.Windows.Controls.Control.Background%2A> następnie określa również jeden przycisk z wartością ustawioną lokalnie.

> [!NOTE]
> Dokumentacja zestawu SDK używa terminów "wartość lokalna" lub "wartość ustawiona lokalnie" od czasu do czasu podczas omawiania właściwości zależności. Lokalnie ustawiona wartość jest wartością właściwości, która jest ustawiona bezpośrednio na wystąpienie obiektu w kodzie lub jako atrybut elementu w XAML.  
  
Zasadniczo dla pierwszego przycisku właściwość jest ustawiona dwa razy, ale stosuje się tylko jedną wartość: wartość o najwyższym priorytecie. Lokalnie ustawiona wartość ma najwyższy priorytet (z wyjątkiem uruchomionej animacji, ale w tym przykładzie nie ma zastosowania żadna animacja) i w związku z tym zamiast wartości ustawiającej styl dla tła na pierwszym przycisku. Drugi przycisk nie ma wartości lokalnej (i nie ma innej wartości o wyższym priorytecie niż ustawiacz stylów), a zatem tło w tym przycisku pochodzi z ustawiającego styl.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Dlaczego istnieje pierwszeństwo właściwości zależności?
Zazwyczaj nie chcesz, aby style były zawsze stosowane i zasłaniały nawet lokalnie ustawioną wartość pojedynczego elementu (w przeciwnym razie trudno byłoby użyć stylów lub elementów w ogóle). W związku z tym wartości, które pochodzą ze stylów działają z niższym precedensem niż wartość ustawiona lokalnie. Aby uzyskać dokładniejszą listę właściwości zależności i skąd może pochodzić wartość efektywna właściwości zależności, zobacz [Pierwszeństwo wartości właściwości zależności.](dependency-property-value-precedence.md)

> [!NOTE]
> Istnieje wiele właściwości zdefiniowane na WPF elementów, które nie są właściwości zależności. Ogólnie rzecz biorąc właściwości zostały zaimplementowane jako właściwości zależności tylko wtedy, gdy potrzebne do obsługi co najmniej jeden ze scenariuszy włączonych przez system właściwości: powiązanie danych, stylizacja, animacja, domyślna obsługa wartości, dziedziczenie, dołączone właściwości lub unieważnienie.

## <a name="learning-more-about-dependency-properties"></a>Dowiedz się więcej o właściwościach zależności  

- Dołączona właściwość jest typem właściwości, która obsługuje wyspecjalizowaną składnię w języku XAML. Dołączone właściwość często nie ma korespondencji 1:1 z właściwością środowiska wykonawczego języka wspólnego (CLR) i niekoniecznie jest właściwością zależności. Typowym celem dołączonej właściwości jest umożliwienie elementom podrzędnym raportowania wartości właściwości do elementu nadrzędnego, nawet jeśli element nadrzędny i element podrzędny nie posiadają tej właściwości jako część listy członków klasy. Jednym z podstawowych scenariuszy jest umożliwienie elementom podrzędnym informowania rodzica o tym, w jaki sposób powinny być prezentowane w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; na przykład, <xref:System.Windows.Controls.DockPanel.Dock%2A> zobacz <xref:System.Windows.Controls.Canvas.Left%2A>lub . Aby uzyskać szczegółowe informacje, zobacz [Omówienie załączonych właściwości](attached-properties-overview.md).

- Deweloperzy składników lub deweloperzy aplikacji mogą chcieć utworzyć własną właściwość zależności, aby włączyć możliwości, takie jak powiązanie danych lub obsługa stylów, lub obsługę unieważnienia i przymusu wartości. Aby uzyskać szczegółowe informacje, zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md).

- Należy wziąć pod uwagę właściwości zależności jako właściwości publicznych, dostępne lub przynajmniej wykrywalne przez dowolnego obiektu wywołującego, który ma dostęp do wystąpienia. Aby uzyskać więcej informacji, zobacz [Bezpieczeństwo właściwości zależności](dependency-property-security.md).

## <a name="see-also"></a>Zobacz też

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Właściwości zależności tylko do odczytu](read-only-dependency-properties.md)
- [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Architektura WPF](wpf-architecture.md)
