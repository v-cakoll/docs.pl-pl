---
title: Przegląd właściwości zależności
description: Właściwość, która jest obsługiwana przez system właściwości WPF, jest znana jako właściwość zależności. To omówienie zawiera opis systemu właściwości WPF i możliwości właściwości zależności.
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
ms.openlocfilehash: 5803d656d765f3f4fe3039e28b9c06202218fcfc
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973988"
---
# <a name="dependency-properties-overview"></a>Przegląd właściwości zależności

Windows Presentation Foundation (WPF) zawiera zestaw usług, których można użyć do rozszerania funkcjonalności [Właściwości](../../../standard/base-types/common-type-system.md#Properties)typu. Zbiorowo te usługi są zwykle określane jako system właściwości WPF. Właściwość, która jest obsługiwana przez system właściwości WPF, jest znana jako właściwość zależności. To omówienie zawiera opis systemu właściwości WPF i możliwości właściwości zależności. Obejmuje to używanie istniejących właściwości zależności w języku XAML i w kodzie. Ten przegląd zawiera również wyspecjalizowane aspekty właściwości zależności, takie jak metadane właściwości zależności, oraz sposób tworzenia własnej właściwości zależności w klasie niestandardowej.

## <a name="prerequisites"></a>Wymagania wstępne
W tym temacie założono, że masz pewną podstawową wiedzę na temat systemu typu .NET i programowania zorientowanego obiektowo. Aby postępować zgodnie z przykładami w tym temacie, należy również zrozumieć język XAML i wiedzieć, jak pisać aplikacje WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Właściwości zależności i właściwości CLR
 W WPF właściwości są zwykle uwidaczniane jako standardowe [Właściwości](../../../standard/base-types/common-type-system.md#Properties)platformy .NET. Na poziomie podstawowym można bezpośrednio korzystać z tych właściwości i nigdy nie wiedzieć, że są one zaimplementowane jako właściwość zależności. Należy jednak zapoznać się z niektórymi lub wszystkimi funkcjami systemu właściwości WPF, dzięki czemu można korzystać z tych funkcji.

Celem właściwości zależności jest zapewnienie sposobu obliczenia wartości właściwości na podstawie wartości innych danych wejściowych. Te inne dane wejściowe mogą obejmować właściwości systemu, takie jak motywy i preferencje użytkownika, mechanizmy wyznaczania właściwości just-in-Time, takie jak powiązanie danych i animacje/Scenorysy, szablony wielokrotnego użytku, takie jak zasoby i style lub znane wartości za pomocą relacji nadrzędny-podrzędny z innymi elementami w drzewie elementów. Ponadto można zaimplementować właściwość zależności, aby zapewnić samodzielną weryfikację, wartości domyślne, wywołania zwrotne, które monitorują zmiany do innych właściwości, oraz system, który może wymuszać wartości właściwości na podstawie informacji o potencjalnie czasie wykonywania. Klasy pochodne mogą również zmieniać pewne charakterystyki istniejącej właściwości poprzez zastępowanie metadanych właściwości zależności, zamiast przesłaniać rzeczywistą implementację istniejących właściwości lub tworzyć nowe właściwości.

W Kompendium zestawu SDK można określić, która właściwość jest właściwością zależności przez obecność sekcji Informacje o właściwości zależności na zarządzanej stronie odwołania dla tej właściwości. Sekcja informacji o zależnościach zawiera link do pola identyfikatora <xref:System.Windows.DependencyProperty> dla tej właściwości zależności, a także zawiera listę opcji metadanych ustawionych dla tej właściwości, informacje o zastępowaniu dla klasy i inne szczegóły.

## <a name="dependency-properties-back-clr-properties"></a>Właściwości zależności z poprzednimi właściwościami środowiska CLR
Właściwości zależności i funkcja rozszerzająca system właściwości WPF, dostarczając typ, który wykonuje kopię zapasową właściwości, jako alternatywną implementację standardowego wzorca wykonywania kopii zapasowej właściwości z polem prywatnym. Nazwa tego typu jest <xref:System.Windows.DependencyProperty>. Innym ważnym typem, który definiuje system właściwości WPF, jest <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject> definiuje klasę bazową, która może zarejestrować właściwość zależności.

Poniżej wymieniono terminologię używaną z właściwościami zależności:

- **Właściwość zależności:** Właściwość, która jest obsługiwana przez <xref:System.Windows.DependencyProperty>.

- **Identyfikator właściwości zależności:** Wystąpienie <xref:System.Windows.DependencyProperty>, które jest uzyskiwane jako wartość zwracana podczas rejestrowania właściwości zależności, a następnie przechowywane jako statyczny element członkowski klasy. Ten identyfikator jest używany jako parametr dla wielu interfejsów API, które współdziałają z systemem właściwości WPF.

- **Środowisko CLR "otoka":** Rzeczywiste implementacje get i Set dla właściwości. Te implementacje obejmują identyfikator właściwości zależności przy użyciu go w <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> wywołania, co zapewnia tworzenie kopii zapasowych dla właściwości przy użyciu systemu właściwości WPF.

W poniższym przykładzie zdefiniowano właściwość zależności `IsSpinning` i jest wyświetlana relacja identyfikatora <xref:System.Windows.DependencyProperty> do właściwości, z którą się odwraca.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
Konwencja nazewnictwa właściwości i jej <xref:System.Windows.DependencyProperty> pole zapasowe jest ważne. Nazwa pola jest zawsze nazwą właściwości, z sufiksem `Property` dołączonym. Aby uzyskać więcej informacji na temat tej konwencji i przyczyn dla nich, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Ustawianie wartości właściwości
Można ustawić właściwości w kodzie lub w języku XAML.

### <a name="setting-property-values-in-xaml"></a>Ustawianie wartości właściwości w języku XAML 
Poniższy przykład XAML określa kolor tła przycisku w kolorze czerwonym. Ten przykład ilustruje przypadek, w którym prosta wartość ciągu dla atrybutu XAML jest konwertowana na typ w języku WPF XAML do typu WPF (<xref:System.Windows.Media.Color>, w formie <xref:System.Windows.Media.SolidColorBrush>) w wygenerowanym kodzie.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

Język XAML obsługuje różne formy składni do ustawiania właściwości. Składnia, która ma być używana dla określonej właściwości, będzie zależeć od typu wartości, która jest używana przez właściwość, a także innych czynników, takich jak obecność konwertera typów. Aby uzyskać więcej informacji na temat składni języka XAML dla ustawienia właściwości, Zobacz szczegółowe [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) i [składni języka XAML](xaml-syntax-in-detail.md).

Jako przykład składni nie będącej atrybutami, Poniższy przykład XAML pokazuje inne tło przycisku. Tym razem, zamiast ustawiania prostego pełnego koloru, tło jest ustawione na obraz, z elementem reprezentującym ten obraz oraz źródłem tego obrazu określony jako atrybut zagnieżdżonego elementu. Jest to przykład składni elementu właściwości.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Ustawianie właściwości w kodzie
 Ustawianie wartości właściwości zależności w kodzie jest zazwyczaj tylko wywołaniem implementacji zestawu uwidocznionym przez środowisko CLR "otoka".

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Pobieranie wartości właściwości jest również zasadniczo wywołaniem implementacji "otoki":

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Można również wywołać interfejsy API systemu właściwości <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> bezpośrednio. Zwykle nie jest to konieczne, jeśli używasz istniejących właściwości (otoki są wygodniejsze i zapewniają lepszy ekspozycję właściwości dla narzędzi programistycznych), ale wywołania interfejsów API są odpowiednie dla pewnych scenariuszy.

Właściwości można również ustawić w języku XAML, a następnie uzyskać do nich dostęp później w kodzie. Aby uzyskać szczegółowe informacje, zobacz [kod w kodzie i XAML w WPF](code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Funkcje właściwości zapewniane przez właściwość zależności
Właściwość Dependency zawiera funkcje, które rozszerzają funkcjonalność właściwości w przeciwieństwie do właściwości, która jest obsługiwana przez pole. Często takie funkcje reprezentują lub obsługują jedną z następujących funkcji:

- [Zasoby](#resources)

- [Powiązanie danych](#data-binding)

- [Style](#styles)

- [Animacje](#animations)

- [Zastąpienia metadanych](#metadata-overrides)

- [Dziedziczenie wartości właściwości](#property-value-inheritance)

- [Integracja z projektantem WPF](#wpf-designer-integration)

### <a name="resources"></a>Resources
Wartość właściwości zależności można ustawić, odwołując się do zasobu. Zasoby są zwykle określane jako wartość właściwości `Resources` elementu głównego strony lub aplikacji (te lokalizacje umożliwiają najbardziej wygodny dostęp do zasobu). Poniższy przykład pokazuje, jak zdefiniować zasób <xref:System.Windows.Media.SolidColorBrush>.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Po zdefiniowaniu zasobu można odwołać się do zasobu i użyć go, aby podać wartość właściwości:

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Ten konkretny zasób jest przywoływany jako [rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md) (w języku XAML WPF, można użyć odwołania do zasobu statycznego lub dynamicznego). Aby użyć dynamicznego odwołania do zasobów, należy ustawić właściwość zależności, więc jest to dokładnie dynamiczne użycie odwołania do zasobów, które jest włączone w systemie właściwości WPF. Aby uzyskać więcej informacji, zobacz [zasoby XAML](xaml-resources.md).

> [!NOTE]
> Zasoby są traktowane jako wartość lokalna, co oznacza, że jeśli zostanie ustawiona inna wartość lokalna, odwołanie do zasobu zostanie wyeliminowane. Aby uzyskać więcej informacji, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).

### <a name="data-binding"></a>Powiązanie danych
Właściwość zależności może odwoływać się do wartości za pomocą powiązania danych. Powiązanie danych działa przez określoną składnię rozszerzenia znacznika w języku XAML lub obiekt <xref:System.Windows.Data.Binding> w kodzie. W przypadku powiązania danych ostateczne Określanie wartości właściwości jest odroczone do czasu uruchomienia, podczas którego wartość jest uzyskiwana ze źródła danych.

Poniższy przykład ustawia właściwość <xref:System.Windows.Controls.ContentControl.Content%2A> dla <xref:System.Windows.Controls.Button>przy użyciu powiązania zadeklarowanego w języku XAML. Powiązanie używa dziedziczonego kontekstu danych i źródła danych <xref:System.Windows.Data.XmlDataProvider> (niepokazywany). Samo powiązanie określa żądaną Właściwość źródłową przez <xref:System.Windows.Data.Binding.XPath%2A> w ramach źródła danych.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Powiązania są traktowane jako wartość lokalna, co oznacza, że jeśli ustawisz inną wartość lokalną, zostanie wyeliminowane powiązanie. Aby uzyskać szczegółowe informacje, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).

Właściwości zależności lub klasy <xref:System.Windows.DependencyObject> nie obsługują natywnie <xref:System.ComponentModel.INotifyPropertyChanged> do celów tworzenia powiadomień o zmianach w <xref:System.Windows.DependencyObject> wartości właściwości źródłowej dla operacji związanych z wiązaniem danych. Aby uzyskać więcej informacji na temat tworzenia właściwości do użycia w powiązaniu danych, które mogą raportować zmiany w celu powiązania danych, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).

### <a name="styles"></a>Style
Style i szablony są dwa z głównego scenariusza z motywem do korzystania z właściwości zależności. Style są szczególnie przydatne do ustawiania właściwości, które definiują [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]aplikacji. Style są zazwyczaj definiowane jako zasoby w języku XAML. Style współdziałają z systemem właściwości, ponieważ zazwyczaj zawierają "Setters" dla określonych właściwości, a także "wyzwalacze", które zmieniają wartość właściwości na podstawie wartości w czasie rzeczywistym dla innej właściwości.

Poniższy przykład tworzy bardzo prosty styl (który zostanie zdefiniowany w słowniku <xref:System.Windows.FrameworkElement.Resources%2A>, nie jest wyświetlany), a następnie stosuje ten styl bezpośrednio do właściwości <xref:System.Windows.FrameworkElement.Style%2A> <xref:System.Windows.Controls.Button>. Metoda ustawiająca w stylu ustawia właściwość <xref:System.Windows.Controls.Control.Background%2A> dla <xref:System.Windows.Controls.Button> z stylem na zielony.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Aby uzyskać więcej informacji, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).

### <a name="animations"></a>Animacje
Właściwości zależności można animować. Gdy animacja jest stosowana i jest uruchomiona, animowana wartość działa z wyższym priorytetem niż jakakolwiek wartość (na przykład wartość lokalna), która w przeciwnym razie ma.

Poniższy przykład Animuj <xref:System.Windows.Controls.Control.Background%2A> na właściwości <xref:System.Windows.Controls.Button> (technicznie <xref:System.Windows.Controls.Control.Background%2A> jest animowany przy użyciu składni elementu właściwości do określenia pustej <xref:System.Windows.Media.SolidColorBrush> jako <xref:System.Windows.Controls.Control.Background%2A>, a następnie właściwość <xref:System.Windows.Media.SolidColorBrush.Color%2A> tego <xref:System.Windows.Media.SolidColorBrush> jest właściwością, która jest bezpośrednio animowana).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Aby uzyskać więcej informacji na temat animowania właściwości, zobacz [Omówienie animacji](../graphics-multimedia/animation-overview.md) i [Omówienie scenorysów](../graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Zastąpienia metadanych
Niektóre zachowania właściwości zależności można zmienić, zastępując metadane tej właściwości, gdy pochodzą z klasy, która pierwotnie rejestruje właściwość zależności. Zastępowanie metadanych opiera się na identyfikatorze <xref:System.Windows.DependencyProperty>. Zastępowanie metadanych nie wymaga ponownego wdrożenia właściwości. Zmiana metadanych jest obsługiwana natywnie przez system właściwości; Każda Klasa potencjalnie przechowuje pojedyncze metadane dla wszystkich właściwości, które są dziedziczone z klas bazowych, dla poszczególnych typów.

Poniższy przykład zastępuje metadane dla właściwości zależności <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. Zastępowanie tego konkretnej metadanych właściwości zależności jest częścią wzorca implementacji, który tworzy kontrolki, które mogą używać domyślnych stylów z motywów.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Aby uzyskać więcej informacji na temat przesłaniania lub uzyskiwania metadanych właściwości, zobacz [metadane właściwości zależności](dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Dziedziczenie wartości właściwości
Element może dziedziczyć wartość właściwości zależności z jej elementu nadrzędnego w drzewie obiektów.

> [!NOTE]
> Zachowanie dziedziczenia wartości właściwości nie jest globalnie włączone we wszystkich właściwościach zależności, ponieważ czas obliczeń dla dziedziczenia ma wpływ na wydajność. Dziedziczenie wartości właściwości jest zazwyczaj włączone tylko dla właściwości, w których konkretny scenariusz sugeruje, że dziedziczenie wartości właściwości jest odpowiednie. Można określić, czy właściwość zależności dziedziczy przez przejrzenie sekcji **informacji o zależności** dla tej właściwości zależności w odwołaniu do zestawu SDK.

Poniższy przykład przedstawia powiązanie i ustawia właściwość <xref:System.Windows.FrameworkElement.DataContext%2A>, która określa źródło powiązania, które nie zostało pokazane w poprzednim przykładzie powiązania. Wszystkie kolejne powiązania w obiektach podrzędnych nie muszą określać źródła, ale mogą używać dziedziczonej wartości z <xref:System.Windows.FrameworkElement.DataContext%2A> w obiekcie nadrzędnym <xref:System.Windows.Controls.StackPanel>. (Alternatywnie zamiast tego można wybrać, aby bezpośrednio określić własne <xref:System.Windows.FrameworkElement.DataContext%2A> lub <xref:System.Windows.Data.Binding.Source%2A> w <xref:System.Windows.Data.Binding>i w sposób celowy nie używać dziedziczonej wartości dla kontekstu danych ich powiązań).

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Aby uzyskać więcej informacji, zobacz [dziedziczenie wartości właściwości](property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Integracja z projektantem WPF
Kontrolka niestandardowa z właściwościami, które są implementowane jako właściwości zależności, będzie otrzymywać odpowiedni Projektant WPF dla pomocy technicznej programu Visual Studio. Przykładem jest możliwość edycji właściwości zależności bezpośrednie i dołączone przy użyciu okna **Właściwości** . Aby uzyskać więcej informacji, zobacz temat [Tworzenie kontroli — przegląd](../controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Pierwszeństwo wartości właściwości zależności
Po otrzymaniu wartości właściwości zależności można uzyskać wartość ustawioną dla tej właściwości za pomocą dowolnego z innych danych wejściowych opartych na właściwościach, które uczestniczą w systemie właściwości WPF. Pierwszeństwo wartości właściwości zależności istnieje, dzięki czemu różne scenariusze dotyczące sposobu, w jaki właściwości uzyskują swoje wartości, mogą współdziałać w przewidywalny sposób.

Rozważmy następujący przykład. Przykład zawiera styl stosowany do wszystkich przycisków i ich <xref:System.Windows.Controls.Control.Background%2A> właściwości, ale również określa jeden przycisk z lokalną ustawioną <xref:System.Windows.Controls.Control.Background%2A> wartością.

> [!NOTE]
> Dokumentacja zestawu SDK używa warunków "lokalna wartość" lub "lokalnie ustawiona wartość" sporadycznie podczas omawiania właściwości zależności. Wartość ustawiona lokalnie to wartość właściwości, która jest ustawiana bezpośrednio w wystąpieniu obiektu w kodzie lub jako atrybut w elemencie XAML.  
  
W zasadzie dla pierwszego przycisku właściwość jest ustawiana dwa razy, ale stosowana jest tylko jedna wartość: wartość o najwyższym priorytecie. Ustawiona lokalnie wartość ma najwyższy priorytet (z wyjątkiem uruchomionej animacji, ale w tym przykładzie nie ma żadnej animacji), a tym samym wartość ustawiona lokalnie jest używana zamiast wartości style setter dla tła pierwszego przycisku. Drugi przycisk nie ma wartości lokalnej (i nie ma innej wartości o wyższym priorytecie niż Metoda ustawiająca styl) i w ten sposób tło tego przycisku pochodzi z metody ustawiającej style.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Dlaczego ma pierwszeństwo właściwość zależności?
Zwykle nie chcesz, aby style były zawsze stosowane, i aby zasłaniać nawet lokalnie ustawioną wartość pojedynczego elementu (w przeciwnym razie trudno jest użyć w ogóle stylów lub elementów). W związku z tym wartości, które pochodzą ze stylów, działają przy mniejszej poprzedniku niż wartość ustawiona lokalnie. Aby zapoznać się z bardziej dokładną listą właściwości zależności i, w której może występować wartość właściwości zależności, zobacz [pierwszeństwo wartości właściwości zależności](dependency-property-value-precedence.md).

> [!NOTE]
> W elementach WPF są zdefiniowane różne właściwości, które nie są właściwościami zależności. Według i duże, właściwości zostały zaimplementowane jako właściwości zależności tylko wtedy, gdy trzeba obsługiwać co najmniej jeden z scenariuszy włączonych przez system właściwości: powiązanie danych, styl, animacja, obsługa wartości domyślnych, dziedziczenie, dołączone właściwości lub unieważniania.

## <a name="learning-more-about-dependency-properties"></a>Dowiedz się więcej o właściwościach zależności  

- Dołączona właściwość jest typem właściwości, która obsługuje wyspecjalizowaną składnię w języku XAML. Dołączona właściwość często nie ma zgodności 1:1 z właściwością środowiska uruchomieniowego języka wspólnego (CLR) i nie musi być właściwością zależności. Typowym celem dołączonej właściwości jest umożliwienie elementom podrzędnym zgłaszania wartości właściwości do elementu nadrzędnego, nawet jeśli element nadrzędny i element podrzędny nie posiadają tej właściwości jako części list elementów członkowskich klasy. Jednym z głównych scenariuszy jest włączenie elementów podrzędnych w celu informowania o tym, jak powinny być prezentowane w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; Aby zapoznać się z przykładem, zobacz <xref:System.Windows.Controls.DockPanel.Dock%2A> lub <xref:System.Windows.Controls.Canvas.Left%2A>. Aby uzyskać szczegółowe informacje, zobacz [Omówienie funkcji dołączone właściwości](attached-properties-overview.md).

- Deweloperzy składników lub deweloperzy aplikacji mogą chcieć utworzyć własną właściwość zależności, aby umożliwić obsługę takich funkcji jak powiązanie danych lub style, lub na potrzeby obsługi nieprawidłowych i wymuszania wartości. Aby uzyskać szczegółowe informacje, zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md).

- Właściwości zależności powinny być ogólnie uznawane za właściwości publiczne, dostępne lub co najmniej wykrywalne przez dowolnego wywołującego, który ma dostęp do wystąpienia. Aby uzyskać więcej informacji, zobacz temat [Ochrona właściwości zależności](dependency-property-security.md).

## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Właściwości zależności tylko do odczytu](read-only-dependency-properties.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Architektura WPF](wpf-architecture.md)
