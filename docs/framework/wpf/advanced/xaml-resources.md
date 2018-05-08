---
title: Zasoby XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 7b917b13909c463cd9d518d79bf8ce2683591dda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-resources"></a>Zasoby XAML
Zasób jest obiekt, który mogą być ponownie używane w różnych miejscach w aplikacji. Przykładami zasobów pędzle i style. Ten przegląd zawiera opis sposobu korzystania z zasobów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Można również tworzyć i uzyskiwać dostęp do zasobów przy użyciu kodu lub zamiennie między kodu i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [zasobów i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Pliki zasobów, w tym temacie opisano są inne niż pliki zasobów opisanego w [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) i inne niż opisane w zasoby osadzone lub połączone [ Zarządzanie zasobami aplikacji (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Korzystanie z zasobów w języku XAML  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Media.SolidColorBrush> jako zasób dla elementu głównego strony. W przykładzie następnie odwołuje się do zasobu i używa jej do ustawienia właściwości kilka elementów podrzędnych, w tym <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Każdy element na poziomie struktury (<xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma <xref:System.Windows.FrameworkElement.Resources%2A> właściwość, która jest właściwość, która zawiera zasoby (jako <xref:System.Windows.ResourceDictionary>) definiujący zasobu. Zasoby można zdefiniować w dowolnym elemencie. Jednak zasoby najczęściej są zdefiniowane w elemencie głównym, który jest <xref:System.Windows.Controls.Page> w przykładzie.  
  
 Każdy zasób w słowniku zasobów musi mieć unikatowy klucz. Po zdefiniowaniu zasobów w znaczniku przypisać unikatowy klucz za pośrednictwem [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md). Zazwyczaj klucz jest ciąg. jednak można również ustawić go do innych obiektów przy użyciu rozszerzenia znaczników odpowiednie. Klucze typu zasobów są używane przez obszarów niektórych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], szczególnie dla style, składnik zasobów i style danych.  
  
 Po zdefiniowaniu zasobu można odwoływać się do zasobu używanego dla wartości właściwości przy użyciu składni rozszerzenie znacznika zasobu, który określa nazwę klucza, na przykład:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 W poprzednim przykładzie gdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego przetwarza wartość `{StaticResource MyBrush}` dla <xref:System.Windows.Controls.Control.Background%2A> właściwości na <xref:System.Windows.Controls.Button>, logika wyszukiwania zasobów najpierw sprawdza słownik zasobów <xref:System.Windows.Controls.Button> elementu. Jeśli <xref:System.Windows.Controls.Button> nie ma definicji klucza zasobu `MyBrush` (nie; jego kolekcja zasobów jest pusta), wyszukiwania następnym razem element nadrzędny <xref:System.Windows.Controls.Button>, która jest <xref:System.Windows.Controls.Page>. W związku z tym, kiedy należy zdefiniować zasobu na <xref:System.Windows.Controls.Page> elementu głównego, wszystkie elementy w drzewa logicznego <xref:System.Windows.Controls.Page> do niego dostęp, a dla ustawienia wartości dowolnej właściwości, która akceptuje można ponownie użyć tego samego zasobu <xref:System.Type> który zasobu reprezentuje. W poprzednim przykładzie, takie same `MyBrush` zasobów ustawia dwa różne właściwości: <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>i <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statycznych i dynamicznych zasobów  
 Zasób można odwoływać się jako zasób statyczne lub dynamiczne zasobów. Odbywa się za pomocą [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) lub [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Rozszerzenie znaczników jest funkcją [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zgodnie z którą można określić odwołania do obiektu z rozszerzeniem znacznika ciąg atrybutu przetwarzać i zwraca obiekt do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego. Aby uzyskać więcej informacji dotyczących zachowania rozszerzeń znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Korzystając z rozszerzeniem znacznika, zwykle zapewnia co najmniej jeden parametr w postaci ciągu przetwarzanych przez to rozszerzenie znaczników w szczególności, a nie oceniane w kontekście ustawienia właściwości. [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) przetwarza klucza, sprawdzając wartość tego klucza w słownikach zasobów dostępne wszystkie. Dzieje się tak podczas ładowania, który jest punktem w czasie, gdy proces ładowania musi przypisać wartość właściwości, która przyjmuje odwołanie do zasobu statycznych. [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast procesów klucza przez utworzenie wyrażenia oraz że wyrażenie pozostaje nieznanym do momentu rzeczywistości uruchomieniu aplikacji, po tym czasie wyrażenie jest obliczane i dostarcza wartość.  
  
 Podając odniesienie zasobu przedstawione poniżej zagadnienia mogą mieć wpływ czy używać odwołanie statyczne zasobów lub odwołanie do zasobu dynamicznego:  
  
-   Ogólnego projektu tworzenia zasobów dla aplikacji (na stronie w aplikacji w luźno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], w zestawie tylko zasobów).  
  
-   Funkcjonalność aplikacji: aktualizuje zasobów w czasie rzeczywistym część wymagań aplikacji?  
  
-   Wyszukiwanie odpowiednich zachowanie tego typu odwołanie do zasobu.  
  
-   Określoną właściwość lub typ zasobu i natywnego zachowanie tych typów.  
  
### <a name="static-resources"></a>Zasoby statyczne  
 Statyczne zasobów odwołuje się do pracy najlepiej w następujących sytuacjach:  
  
-   Projekt aplikacji skupia się najbardziej wszystkich jej zasobów na stronie lub zasobów na poziomie aplikacji słowników. Odwołania do zasobów statyczne nie są ponownie oceniane w oparciu zachowania środowiska uruchomieniowego, takie jak ponowne ładowanie strony i dlatego może być niektóre korzyści wydajności do uniknięcia dużej liczby odwołania do zasobów dynamicznej, gdy nie są niezbędne dla zasobu i Projekt aplikacji.  
  
-   To ustawienie wartości właściwości, która nie jest włączony <xref:System.Windows.DependencyObject> lub <xref:System.Windows.Freezable>.  
  
-   Tworzysz słownik zasobów, które zostaną skompilowane w bibliotekę DLL i spakowane jako część aplikacji lub współużytkowany przez różne aplikacje.  
  
-   Tworzenia motywów kontrolki niestandardowej, a definiowania zasobów, które są używane w ramach tematów. Dla tego przypadku zwykle nie ma zasobu dynamicznego odwołanie wyszukiwania zachowanie, zamiast tego chcesz zachowanie odwołanie statyczne zasobów, aby wyszukiwanie jest przewidywalne, niezależna do motywu. Dynamiczne zasobów nieznanym odwołanie, nawet pozostanie w obrębie motywu odwołanie do środowiska wykonawczego i jest stosowany po motywu zastosowane, niektóre lokalny element będzie ponownie zdefiniować klucz motywu próbuje odwołać się, czy elementu lokalnego spadną uprzedniego Aby motyw sam w wyszukiwania. W takim przypadku kompozycji nie będzie działać w oczekiwany sposób.  
  
-   Używasz zasobów można ustawić dużej liczby właściwości zależności. Właściwości zależności ma wartość efektywna Buforowanie włączone przez system właściwości, więc jeśli Podaj wartość dla właściwości zależności, które może przyjąć w czasie ładowania, właściwości zależności nie ma, sprawdź, czy wyrażenie reevaluated i przywrócić Ostatnia wartość skuteczne. Ta technika może być poprawiać wydajność.  
  
-   Chcesz zmienić podstawowy zasobów dla wszystkich użytkowników lub chcesz zachować osobnych wystąpień do zapisu dla każdego klienta za pomocą [x: atrybut udostępnionych](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Zachowanie wyszukiwania zasobów statyczne  
  
1.  Proces wyszukiwania sprawdza, czy żądany klucz w słowniku zasobów określone przez element, który ustawia właściwość.  
  
2.  Proces wyszukiwania jest przesyłany w górę, drzewa logicznego do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.  
  
3.  Następnie zasoby aplikacji są sprawdzane. Zasoby aplikacji są tych zasobów w ramach słownik zasobów, która jest zdefiniowana przez <xref:System.Windows.Application> obiektów dla sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
 Odwołania do zasobów statyczne z wewnątrz słownik zasobów musi odwoływać się z zasobem, który został już zdefiniowany lexically przed odwołanie do zasobu. Nie można rozpoznać odwołania w przód przez odwołanie statyczne zasobów. Z tego powodu użycie odwołania do zasobu statycznych, należy zaprojektować strukturę słownika zasobów tak, aby zasobów przeznaczonych do użycia przez zasobów są zdefiniowane w lub na początku każdego słownik odpowiednich zasobów.  
  
 Wyszukiwania zasobów statyczne można rozszerzyć do kompozycji, lub zasoby systemowe, ale ta funkcja jest obsługiwana tylko w przypadku, ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego różni się żądanie. Odroczenia jest niezbędne, aby motyw środowiska uruchomieniowego w czasie ładowania strony prawidłowo stosuje się do aplikacji. Jednak statycznych zasobów odwołuje się do kluczy, które nie są tylko istnieje w kompozycji lub jako system zasobów nie są zalecane. Jest to spowodowane takie odwołania nie są ponownie oceniane po zmianie motywu użytkownika w czasie rzeczywistym. Odwołanie do zasobu dynamicznego jest bardziej niezawodne, w przypadku żądania motywu lub zasobów systemowych. Wyjątkiem jest sam element motywu żądanie innego zasobu. Te odwołania powinna być odwołania do zasobu statycznych, z powodów wymienionych poniżej.  
  
 Zachowanie wyjątek, jeśli odwołaniem zasobu statycznych nie zostanie znaleziony zależy. Jeśli zasób został wstrzymany, wyjątek występuje w czasie wykonywania. Jeśli zasób nie został wstrzymany, wyjątek występuje w czasie ładowania.  
  
### <a name="dynamic-resources"></a>Dynamiczne zasobów  
 Zasoby dynamicznej najlepiej w następujących sytuacjach:  
  
-   Wartość zasobu zależy od warunków, które nie są znane do środowiska wykonawczego. W tym zasobów systemowych lub zasobów, które są w inny sposób użytkownika można ustawić. Na przykład można utworzyć wartości metody ustawiającej, które odwołują się do właściwości systemu, jak udostępniany przez <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, lub <xref:System.Windows.SystemParameters>. Te wartości są naprawdę dynamicznej, ponieważ pochodzą one ostatecznie ze środowiska użytkownika i systemu operacyjnego. Można również zainstalować motywów na poziomie aplikacji, które można zmienić, gdy dostęp do zasobów na poziomie strony musi również przechwytywania zmian.  
  
-   Tworzysz lub odwołuje się do stylów motywu kontrolki niestandardowej.  
  
-   Zamierzasz dostosować zawartość <xref:System.Windows.ResourceDictionary> okres istnienia aplikacji.  
  
-   Masz struktura skomplikowane zasobu, która ma zależnościami, gdzie mogą być wymagane odwołanie do przodu. Odwołania do zasobu statycznych nie obsługują odwołania w przód odwołania do zasobów dynamicznej je obsługuje, ponieważ zasób nie musi przyjąć do środowiska wykonawczego, a odwołania w przód w związku z tym nie są istotne pojęcia.  
  
-   Odwołanie do zasobu, który jest szczególnie duże z perspektywy kompilacji lub zestaw roboczy i zasobu nie mogą być używane, natychmiast po załadowaniu strony. Odwołania do zasobów statycznych zawsze załadować z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] załadowanie strony; jednak odwołaniem zasobu dynamicznego nie zostanie załadowany do momentu rzeczywistości jest używany.  
  
-   Tworzysz stylu, których wartości metody ustawiającej może pochodzić z inne wartości, które wpływało motywy lub inne ustawienia użytkownika.  
  
-   Zasoby są stosowanie do elementów, które mogą być pokrewnym w drzewie logicznym okres istnienia aplikacji. Element nadrzędny również potencjalnie zmiana zakresu wyszukiwania zasobów, więc zasobu dla elementu reparented go obliczyć ponownie na podstawie zakresu z nowej, zawsze należy użyć odwołaniem zasobu dynamicznego.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Zachowanie wyszukiwania zasobów dynamicznych  
 Zachowanie wyszukiwania zasobów dla odwołania do zasobu dynamicznego równoleżnikami zachowanie wyszukiwania w kodzie, jeśli wywołujesz <xref:System.Windows.FrameworkElement.FindResource%2A> lub <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Proces wyszukiwania sprawdza, czy żądany klucz w słowniku zasobów określone przez element, który ustawia właściwość.  
  
    -   Jeśli element definiuje <xref:System.Windows.FrameworkElement.Style%2A> właściwości, <xref:System.Windows.Style.Resources%2A> słownika w <xref:System.Windows.Style> jest zaznaczony.  
  
    -   Jeśli element definiuje <xref:System.Windows.Controls.Control.Template%2A> właściwości, <xref:System.Windows.FrameworkTemplate.Resources%2A> słownika w <xref:System.Windows.FrameworkTemplate> jest zaznaczony.  
  
2.  Proces wyszukiwania jest przesyłany w górę, drzewa logicznego do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.  
  
3.  Następnie zasoby aplikacji są sprawdzane. Zasoby aplikacji są tych zasobów w ramach słownik zasobów, która jest zdefiniowana przez <xref:System.Windows.Application> obiektów dla sieci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
4.  Słownik zasobów motywu jest sprawdzany pod kątem motyw obecnie aktywne. Jeśli motyw zmieni się w czasie wykonywania, wartość jest ponownie oceniane.  
  
5.  Zasoby systemowe są sprawdzane.  
  
 Zachowanie wyjątek (jeśli istnieją) różni się od:  
  
-   Jeśli żądanie zostało zgłoszone przez zasób <xref:System.Windows.FrameworkElement.FindResource%2A> połączenia i nie został znaleziony, jest wyjątek.  
  
-   Jeśli żądanie zostało zgłoszone przez zasób <xref:System.Windows.FrameworkElement.TryFindResource%2A> połączenia i nie można odnaleźć nie wyjątek, ale jest zwracana wartość `null`. Jeśli ustawienia właściwości nie akceptuje `null`, jest nadal możliwe, zostanie wygenerowany wyjątek głębiej, a następnie (zależy to od poszczególnych właściwości).  
  
-   Jeśli żądanie zostało zgłoszone przez odwołanie zasobu dynamicznego w zasobu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i nie został znaleziony, a następnie zachowanie zależy od systemu ogólne właściwości ogólne działanie jest jednak tak, jakby żadna operacja ustawienia właściwości wystąpił na poziomie której istnieje zasób. Na przykład Jeśli spróbujesz ustawić w tle elementu poszczególnych przycisk za pomocą zasobu, którego nie można obliczyć, następnie żadna wartość ustawiona wyników, ale wartość efektywna nadal mogą pochodzić z innych uczestników pierwszeństwo systemu i wartości właściwości. Na przykład wartość tła nadal mogą pochodzić z styl przycisku zdefiniowane lokalnie lub stylów motywu. Dla właściwości, które nie są zdefiniowane przez style kompozycji efektywną wartość po dokonaniu oceny zasób może pochodzić z wartością domyślną w metadanych właściwości.  
  
#### <a name="restrictions"></a>Ograniczenia  
 Odwołania do zasobu dynamicznego mają pewne ważne ograniczenia. Co najmniej jedną z następujących muszą być spełnione:  
  
-   Ustawienia właściwości musi być właściwością na <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Czy właściwości muszą być chronione przez <xref:System.Windows.DependencyProperty>.  
  
-   Odwołanie jest dla wartości w <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
-   Ustawienia właściwości musi być właściwością na <xref:System.Windows.Freezable> dostarczanym jako wartości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> właściwości, lub <xref:System.Windows.Setter> wartość.  
  
 Ponieważ właściwość do ustawiania musi być <xref:System.Windows.DependencyProperty> lub <xref:System.Windows.Freezable> właściwości, większość zmian właściwości można propagować do interfejsu użytkownika, ponieważ zmiany właściwości (wartość zmienione zasobu dynamicznego) zostaje potwierdzony przez system właściwości. Większość formantów obejmują logikę, która wymusi inny układ formantu, jeśli <xref:System.Windows.DependencyProperty> zmiany i że właściwości mogą mieć wpływ na układ. Jednak nie wszystkie właściwości zawierających [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) jako ich wartość dotrą do Podaj wartość w taki sposób, aby zaktualizować w czasie rzeczywistym w interfejsie użytkownika. Ta funkcjonalność nadal mogą się różnić w zależności od właściwości, a także w zależności od typu posiada właściwość lub nawet struktury logicznej aplikacji.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Style, DataTemplates i niejawne kluczy  
 Wcześniej, stwierdzono, że wszystkie elementy w <xref:System.Windows.ResourceDictionary> musi mieć klucz. Jednak nie oznacza że wszystkie zasoby muszą mieć jawnego `x:Key`. Kilka typów obiektów obsługuje niejawne klucza, gdy definiowany jako zasób, gdzie wartość klucza jest związany z wartości właściwości innego. Jest to nazywane klucz niejawne, podczas gdy `x:Key` atrybut jest jawne klucza. Dowolny klawisz, niejawne można zastąpić, określając jawne klucza.  
  
 Jest jednym ze scenariuszy bardzo ważne dla zasobów podczas definiowania <xref:System.Windows.Style>. W rzeczywistości <xref:System.Windows.Style> prawie zawsze jest definiowany jako wpis w słowniku zasobów, ponieważ style z założenia są przeznaczone do ponownego użycia. Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Style formantów można zarówno utworzony z i odwołuje się do niejawnego kluczem. Style kompozycji, definiujące domyślny wygląd formantu korzystają z tego klucza niejawne. Niejawne klucz z punktu widzenia ją jest <xref:System.Type> samego formantu. Niejawne klucz z punktu widzenia Definiowanie zasobu jest <xref:System.Windows.Style.TargetType%2A> stylu. Dlatego w przypadku tworzenia motywów w przypadku kontrolek niestandardowych, tworzenie stylów współpracujące z istniejących stylów motywu, nie należy określić [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) tego <xref:System.Windows.Style>. A jeśli chcesz użyć style motywów, nie należy określić każdy styl w ogóle. Na przykład następujący definicji stylu działa, mimo że <xref:System.Windows.Style> zasobów nie ma klucza:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Czy styl naprawdę mieć klucz: niejawna klucza `typeof(` <xref:System.Windows.Controls.Button> `)`. W znaczniku, można określić <xref:System.Windows.Style.TargetType%2A> bezpośrednio jako typ nazwę (lub opcjonalnie można użyć [{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) Aby przywrócić <xref:System.Type>.  
  
 Za pomocą mechanizmów styl motyw domyślny używany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zastosowano styl jako styl środowiska uruchomieniowego <xref:System.Windows.Controls.Button> na stronie, nawet jeśli <xref:System.Windows.Controls.Button> sam nie próbuje określić jego <xref:System.Windows.FrameworkElement.Style%2A> właściwości lub określonych zasobów Odwołanie do stylu. Własnego stylu zdefiniowana na stronie znajduje się wcześniej w kolejności wyszukiwania starszych niż styl słownika motywu, przy użyciu tego samego klucza, zawierający styl słownika motywu. Można określić `<Button>Hello</Button>` w dowolnym miejscu strony i style zdefiniowane z <xref:System.Windows.Style.TargetType%2A> z `Button` powinna zostać zastosowana do tego przycisku. Jeśli chcesz, możesz nadal jawnie klucza styl o tej samej wartości typu jako <xref:System.Windows.Style.TargetType%2A>jasności w Twojej znaczników, ale jest opcjonalny.  
  
 Niejawne klucze style są stosowane w formancie, gdy <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> jest `true` (również należy pamiętać, że <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> może być ustawiony jako część natywnego zachowanie klasy formantu zamiast jawnie na wystąpienie kontrolki). Również, aby zapewnić obsługę niejawne kluczy dla scenariuszy klasy pochodnej, kontrolki musi zastąpić <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (wszystkie istniejące formanty w ramach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to zrobić). Aby uzyskać więcej informacji na temat style, kompozycje i projektu kontroli, zobacz [wskazówki dotyczące projektowania formantów Stylable](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> również ma niejawne klucza. Niejawne klucz dla <xref:System.Windows.DataTemplate> jest <xref:System.Windows.DataTemplate.DataType%2A> wartości właściwości. <xref:System.Windows.DataTemplate.DataType%2A> można również określić jako nazwa typu zamiast jawnie [{x: Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Aby uzyskać więcej informacji, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.ResourceDictionary>  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Definiowanie zasobu i odwoływanie się do niego](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)  
 [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [x:Type, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [StaticResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [DynamicResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
