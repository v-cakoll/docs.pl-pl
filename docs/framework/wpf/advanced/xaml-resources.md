---
title: Zasoby XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: c43505497b947004ffb282346459967579d52375
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066805"
---
# <a name="xaml-resources"></a>Zasoby XAML
Zasób jest obiektem, który może być ponownie używane w różnych miejscach w aplikacji. Przykładami zasobów pędzle i stylów. W tym omówieniu opisano, jak użyć zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Można również tworzyć i uzyskiwać dostęp do zasobów przy użyciu kodu lub zamiennie między kodem i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Pliki zasobów, opisane w tym temacie są inne niż pliki zasobów opisano w [zasoby aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) i różni się od zasobów osadzony lub połączony opisanych w [ Zarządzanie zasobami aplikacji (.NET)](https://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Korzystanie z zasobów w XAML  
 W poniższym przykładzie zdefiniowano <xref:System.Windows.Media.SolidColorBrush> jako zasób w elemencie głównym strony. Przykład następnie odwołuje się do zasobu i używa go do ustawiania właściwości kilka elementów podrzędnych, w tym <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Każdy element w poziomie struktury (<xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>) ma <xref:System.Windows.FrameworkElement.Resources%2A> właściwość, która jest właściwością, która zawiera zasoby (jako <xref:System.Windows.ResourceDictionary>) definiujący zasobu. Zasoby można zdefiniować w dowolnym elemencie. Jednak zasoby w większości przypadków są definiowane w elemencie głównym, który jest <xref:System.Windows.Controls.Page> w przykładzie.  
  
 Każdy zasób w słowniku zasobów musi mieć unikatowy klucz. Po zdefiniowaniu zasoby w znacznikach przypisać unikatowy klucz za pośrednictwem [x: Key — dyrektywa](../../../../docs/framework/xaml-services/x-key-directive.md). Zazwyczaj klucz jest ciąg. jednak można również ustawić go do innych obiektów przy użyciu rozszerzenia znaczników odpowiednie. Kluczy typu nonstring dla zasobów używanych przez niektórych obszarów funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zwłaszcza w celu style, składnika zasobów i danych stylów.  
  
 Po zdefiniowaniu zasobu, można odwoływać się do zasobu, do użytku z wartością właściwości za pomocą składni rozszerzenia znaczników zasobu, który określa nazwę klucza, na przykład:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 W powyższym przykładzie po [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego przetwarza wartość `{StaticResource MyBrush}` dla <xref:System.Windows.Controls.Control.Background%2A> właściwość <xref:System.Windows.Controls.Button>, logika wyszukiwania zasobów najpierw sprawdza ją pod słownik zasobów <xref:System.Windows.Controls.Button> elementu. Jeśli <xref:System.Windows.Controls.Button> nie ma definicję klucza zasobu `MyBrush` (nie; jego kolekcja zasobów jest pusta) wyszukiwanie następnym razem element nadrzędny <xref:System.Windows.Controls.Button>, czyli <xref:System.Windows.Controls.Page>. W związku z tym, kiedy zdefiniujesz zasób na <xref:System.Windows.Controls.Page> element główny, wszystkie elementy w drzewie logicznym z <xref:System.Windows.Controls.Page> do niego dostęp, i możesz ponownie użyć tego samego zasobu dla ustawienie wartości wszystkich właściwości, który akceptuje <xref:System.Type> , zasobu reprezentuje. W poprzednim przykładzie, taka sama `MyBrush` zasobów ustawia dwóch różnych właściwości: <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>i <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Zasoby statyczne i dynamiczne  
 Zasób może znajdować się jako zasób statyczny lub dynamiczny zasobów. Odbywa się przy użyciu [staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) lub [dynamicresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Rozszerzenie znaczników jest funkcją [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zgodnie z którą można określić odwołanie do obiektu przez rozszerzenie znaczników przetwarzania ciągu atrybutu i zwraca obiekt do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego. Aby uzyskać więcej informacji dotyczących zachowania rozszerzeń znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Korzystając z rozszerzeniem znacznika, zazwyczaj podaje się co najmniej jeden parametr w postaci ciągu, które są przetwarzane przez to rozszerzenie znaczników w szczególności, a nie są oceniane w kontekście właściwością. [Staticresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) przetwarza klucza, sprawdzając wartość tego klucza w wszystkich słownikach zasobów dostępne. Dzieje się to podczas ładowania, który jest punktem w czasie, gdy proces ładowania musi przypisać wartość właściwości, która przyjmuje odwołanie do zasobu statyczne. [Dynamicresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast tego procesy klucza, tworząc wyrażenie, a to wyrażenie pozostaje w nieznanym do momentu aplikacja faktycznie jest uruchomiona, co wyrażenie jest obliczane i podaje wartość.  
  
 Gdy odwołujesz się zasób następujące zagadnienia dotyczące mogą mieć wpływ, niezależnie od użycia odwołania zasób statyczny lub odwołanie do zasobu dynamicznego:  
  
-   Ogólny projekt tworzenia zasobów dla aplikacji (na stronę w aplikacji, w luźno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], w zestawie tylko zasobów).  
  
-   Funkcjonalność aplikacji: Trwa aktualizowanie zasobów w czasie rzeczywistym część wymagań aplikacji?  
  
-   Zachowanie wyszukiwania odpowiednich tego typu odwołanie do zasobu.  
  
-   Przez określoną właściwość lub typ zasobu i natywnych zachowanie tych typów.  
  
### <a name="static-resources"></a>Zasoby statyczne  
 Zasób statyczny odwołuje się do pracy najlepiej w następujących sytuacjach:  
  
-   Projekt aplikacji koncentruje się przede wszystkim jej zasobów na stronie lub zasobów na poziomie aplikacji słowników. Odwołania do zasobów statycznych nie są ponownie oceniane oparte na środowisko uruchomieniowe zachowań, takich jak ponowne załadowanie strony i dlatego może być pewne korzyści wydajności do uniknięcia dużej liczby odwołań zasób dynamiczny, gdy nie są niezbędne dla zasobu i Projekt aplikacji.  
  
-   Ustawiono wartość właściwości, który nie jest włączony <xref:System.Windows.DependencyObject> lub <xref:System.Windows.Freezable>.  
  
-   Tworzysz słownika zasobów, który będzie kompilowana do biblioteki DLL i spakowany jako część aplikacji lub udostępniane między aplikacjami.  
  
-   Tworzysz motywu dla formantu niestandardowego i są definiowane zasoby, które są używane w ramach tematów. Dla tego przypadku zwykle nie chcesz zachowania wyszukiwania odwołanie do zasobu dynamicznego, zamiast tego chcesz, aby zachowanie odwołań statycznych zasobów, aby wyszukiwanie jest przewidywalne, niezależna do motywu. Zasób dynamiczny odwołania, nawet pozostanie odwołania w motywie nieznanym aż do czasu, a istnieje ryzyko, że po motyw zastosowane, niektóre lokalny element będzie ponownie zdefiniować, Twój wybrany motyw chcesz odwołać klucz i elementu lokalnego spadną wcześniejsze do motywu sam w wyszukiwania. Jeśli tak się stanie, Twój wybrany motyw nie będzie działać w oczekiwany sposób.  
  
-   Używasz zasobów można ustawić dużą liczbę właściwości zależności. Właściwości zależności mają wartość efektywna buforowania obsługiwanej przez system właściwości, więc jeśli podasz wartość dla właściwości zależności, które mogą być obliczane w czasie ładowania właściwości zależności nie ma pod kątem reevaluated wyrażenia i może zwrócić Ostatnia wartość skuteczne. Ta technika może być korzyści wydajności.  
  
-   Aby zmienić bazowego zasobu dla wszystkich użytkowników lub chcesz utrzymywać osobnych wystąpień do zapisu dla każdego użytkownika przy użyciu [x: atrybut udostępnione](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Zachowanie Wyszukaj zasób statyczny  
  
1.  Proces wyszukiwania sprawdza, czy żądany klucz w słowniku zasobów, zdefiniowany przez element, który ustawia właściwość.  
  
2.  Proces wyszukiwania jest przesyłany w górę, drzewo logiczne do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany aż do osiągnięcia elementu głównego.  
  
3.  Następnie sprawdzane są zasobów aplikacji. Zasoby aplikacji to zasoby, które w słowniku zasobów, który jest definiowany przez <xref:System.Windows.Application> dla obiektu usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
 Zasób statyczny odwołań z w ramach słownika zasobów musi odwoływać się z zasobem, który został już zdefiniowany leksykalnie przed odwołanie do zasobu. Nie można rozpoznać odwołania w przód przez odwołanie zasób statyczny. Z tego powodu Jeśli używasz odwołania do zasobów statycznych, należy zaprojektować strukturę słownika zasobów taki sposób, że zasoby przeznaczone do użytku przez zasobów są zdefiniowane w lub na początku każdego słownik odpowiednich zasobów.  
  
 Zasób statyczny wyszukiwania można rozszerzyć do motywy, lub zasobów systemowych, ale ta funkcja jest obsługiwana tylko w przypadku, ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] modułu ładującego odracza żądania. Odroczenie jest niezbędne, aby motyw środowiska uruchomieniowego w momencie strona ładuje się poprawnie stosuje się do aplikacji. Jednak zasób statyczny odwołuje się do kluczy, które są znane tylko tam, motywy lub jako system, które nie są zalecane zasoby. Jest to spowodowane odwołania te nie są ponownie oceniane po zmianie motywu przez użytkownika w czasie rzeczywistym. Odwołanie do zasobu dynamicznego jest bardziej niezawodna w przypadku żądania motywu albo zasobów systemowych. Wyjątkiem jest, gdy sam element motyw żąda inny zasób. Te odwołania powinna być odwołań statycznych zasobów z powodów wymienionych wcześniej.  
  
 Zachowanie wyjątek, jeśli odwołanie do statycznych zasobów nie zostanie znaleziony zależy. Jeśli zasób został wstrzymany, wyjątek występuje w czasie wykonywania. Jeśli zasób nie został wstrzymany, wyjątek występuje w czasie ładowania.  
  
### <a name="dynamic-resources"></a>Dynamiczne zasobów  
 Zasoby dynamicznej najlepiej działać dla następujących okolicznościach:  
  
-   Wartości zasobu zależy od warunków, które nie są znane aż do czasu. Obejmuje to zasobów systemowych lub zasobów, które są w przeciwnym razie użytkownik do ustawienia. Na przykład można utworzyć wartości metody ustawiającej, które odwołują się do właściwości systemu, zgodnie z udostępnianych przez <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, lub <xref:System.Windows.SystemParameters>. Te wartości są naprawdę dynamiczne, ponieważ ostatecznie pochodzą one z środowisko uruchomieniowe, użytkownika i systemu operacyjnego. Można również zainstalować motywów dodatku poziomu aplikacji, które mogą ulec zmianie, gdy dostęp do zasobów na poziomie strony musi również przechwytywania zmiany.  
  
-   Tworzysz lub odwołuje się do stylów motywu dla formantu niestandardowego.  
  
-   Zamierzasz dostosować zawartość <xref:System.Windows.ResourceDictionary> w okresie istnienia aplikacji.  
  
-   Masz strukturę skomplikowane zasobów, która ma współzależności, gdzie mogą być wymagane odwołanie do przodu. Odwołania do zasobów statycznych nie obsługują odwołania w przód, ale odwołania do zasobów dynamicznej obsługuje je, ponieważ zasób nie musi przyjąć aż do czasu, a odwołania w przód w związku z tym nie są istotne pojęcia.  
  
-   Utworzono odwołanie do zasobu, który jest szczególnie duże z punktu widzenia kompilacji lub zestaw roboczy i zasobu nie mogą być używane, natychmiast, gdy strona ładuje się. Odwołania do zasobów statycznych zawsze Ładuj z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] po załadowaniu strony; jednak odwołanie do zasobu dynamicznego nie ładuje się dopóki nie będzie faktycznie używana.  
  
-   Tworzysz styl, w którym wartości metody ustawiającej mogą pochodzić od innych wartości, które mają wpływ, motywy lub inne ustawienia użytkownika.  
  
-   Zasoby są stosowane do elementów, które mogą być pokrewnym w drzewie logicznym okresie istnienia aplikacji. Zmiana nadrzędnej również potencjalnie zmienia zakres wyszukiwania zasobów, a więc chcąc zasobów dla elementu reparented go obliczyć ponownie na podstawie nowego zakresu, zawsze odwołanie do zasobu dynamicznego.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Zachowanie Wyszukaj zasób dynamiczny  
 Zachowanie wyszukiwania zasobów dla odwołania do zasobu dynamicznego równoleżnikami zachowania wyszukiwania w kodzie, jeśli wywołasz <xref:System.Windows.FrameworkElement.FindResource%2A> lub <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Proces wyszukiwania sprawdza, czy żądany klucz w słowniku zasobów, zdefiniowany przez element, który ustawia właściwość.  
  
    -   Jeśli element definiuje <xref:System.Windows.FrameworkElement.Style%2A> właściwości <xref:System.Windows.Style.Resources%2A> słownika w ramach <xref:System.Windows.Style> jest zaznaczone.  
  
    -   Jeśli element definiuje <xref:System.Windows.Controls.Control.Template%2A> właściwości <xref:System.Windows.FrameworkTemplate.Resources%2A> słownika w ramach <xref:System.Windows.FrameworkTemplate> jest zaznaczone.  
  
2.  Proces wyszukiwania jest przesyłany w górę, drzewo logiczne do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany aż do osiągnięcia elementu głównego.  
  
3.  Następnie sprawdzane są zasobów aplikacji. Zasoby aplikacji to zasoby, które w słowniku zasobów, który jest definiowany przez <xref:System.Windows.Application> dla obiektu usługi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.  
  
4.  Słownik zasobów motywu jest sprawdzane pod kątem aktualnie aktywnego tematu. Jeśli motyw zmieni się w czasie wykonywania, wartość jest ponownie oceniane.  
  
5.  Zasoby systemu są sprawdzane.  
  
 Zachowanie wyjątku (jeśli istnieje) różni się od:  
  
-   Jeśli zasób żądanej <xref:System.Windows.FrameworkElement.FindResource%2A> wywołać, a nie został znaleziony, zgłaszany jest wyjątek.  
  
-   Jeśli zasób żądanej <xref:System.Windows.FrameworkElement.TryFindResource%2A> wywołać, a nie został znaleziony, jest zgłaszany żaden wyjątek, ale jest zwracana wartość `null`. Jeśli właściwością nie akceptuje `null`, a następnie jest nadal możliwe, zostanie wygenerowany wyjątek bardziej (jest zależna od poszczególnych właściwości ustawiany).  
  
-   Jeśli zasób zażądano przez odwołanie zasób dynamiczny w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]i nie został znaleziony, a następnie zachowanie zależy od systemu ogólne właściwości, ale ogólne działanie tak, jakby żadna operacja ustawienie właściwości wystąpił na poziomie, w której istnieje zasób. Na przykład Jeśli spróbujesz ustawić tła dla elementu poszczególnych przycisk za pomocą zasobu, którego nie można obliczyć, następnie ustawiona żadna wartość wyników, ale wartość efektywna nadal mogą pochodzić z innych uczestników pierwszeństwo systemu i wartości właściwości. Na przykład wartość tła nadal mogą pochodzić z styl przycisku zdefiniowane lokalnie lub stylów kompozycji. Dla właściwości, które nie są zdefiniowane przez style motyw efektywną wartość po ocenie zasobu nie powiodło się mogą pochodzić z wartością domyślną w metadanych właściwości modelu.  
  
#### <a name="restrictions"></a>Ograniczenia  
 Zasób dynamiczny odwołania mają pewne ograniczenia istotne. Wymaga spełnienia co najmniej jedną z następujących warunków:  
  
-   Ustawienia właściwości musi być właściwością na <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>. Czy właściwości muszą być chronione przez <xref:System.Windows.DependencyProperty>.  
  
-   Odwołanie jest podanie wartości w ramach <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
-   Ustawienia właściwości musi być właściwością na <xref:System.Windows.Freezable> dostarczanym w wartości <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> właściwości lub <xref:System.Windows.Setter> wartość.  
  
 Ponieważ musi być właściwością <xref:System.Windows.DependencyProperty> lub <xref:System.Windows.Freezable> właściwości większość zmian właściwości możesz propagować do interfejsu użytkownika, ponieważ zmiana właściwości (wartość zmienione zasób dynamiczny) zostało potwierdzone przez system właściwości. Większość formantów obejmują logikę, która wymusi inny układ formantu, jeśli <xref:System.Windows.DependencyProperty> zmiany i czy właściwość może mieć wpływ na układ. Jednak nie wszystkie właściwości, ma [dynamicresource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) jako ich wartość jest gwarantowane Podaj wartość w taki sposób, że one aktualizowane w czasie rzeczywistym w interfejsie użytkownika. Te funkcje wciąż mogą się różnić w zależności od właściwości, a także w zależności od typu, który jest właścicielem właściwości lub nawet logicznej struktury aplikacji.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Style, DataTemplates i niejawne kluczy  
 Wcześniej stwierdzono, że wszystkie elementy w <xref:System.Windows.ResourceDictionary> musi mieć klucz. Jednakże, oznacza, że wszystkie zasoby muszą mieć jawne `x:Key`. Kilka typów obiektów obsługuje niejawny klucz, gdy zdefiniowane jako zasób, w którym wartość klucza jest powiązany z wartością innej właściwości. Jest to nazywane niejawny klucz, natomiast `x:Key` atrybut jest jawne klucza. Aby zastąpić dowolny klawisz, niejawne, określenie klucza jawne.  
  
 Jednym bardzo ważne dla zasobów jest podczas definiowania <xref:System.Windows.Style>. W rzeczywistości <xref:System.Windows.Style> prawie zawsze jest definiowany jako wpis w słowniku zasobów, ponieważ style natury są przeznaczone do ponownego wykorzystania. Aby uzyskać więcej informacji na temat style zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Style formantów mogą być utworzone za pomocą i do którego odwołuje się niejawny klucz. Style motywów, które definiują domyślny wygląd kontrolki zależą od tego klucza niejawnego. Niejawny klucz z punktu widzenia żądanie jest <xref:System.Type> samego formantu. Niejawny klucz z punktu widzenia Definiowanie zasobu jest <xref:System.Windows.Style.TargetType%2A> stylu. W związku z tym, jeśli tworzysz kompozycje dla kontrolek niestandardowych, tworzenie style, które współdziałają z istniejących stylów motywu, nie należy określić [x: Key — dyrektywa](../../../../docs/framework/xaml-services/x-key-directive.md) tego <xref:System.Windows.Style>. A jeśli chcesz stosować style motywów, nie trzeba określić dowolny styl w ogóle. Na przykład następująca definicja stylu działania, nawet jeśli <xref:System.Windows.Style> zasobów nie ma klucza:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Czy styl tak naprawdę mieć klucz: niejawny klucz `typeof(` <xref:System.Windows.Controls.Button> `)`. W znaczniku, można określić <xref:System.Windows.Style.TargetType%2A> bezpośrednio jako typ nazwy (możesz też opcjonalnie [{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) Aby zwrócić <xref:System.Type>.  
  
 Za pomocą mechanizmów style motyw domyślny używany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], że stylów jest stosowana jako styl środowiska uruchomieniowego <xref:System.Windows.Controls.Button> na stronie mimo że <xref:System.Windows.Controls.Button> sam nie jest podejmowana próba określenia jego <xref:System.Windows.FrameworkElement.Style%2A> właściwości lub określonego zasobu Odwołanie do stylu. Własnego stylu zdefiniowana na stronie znajduje się we wcześniejszej części sekwencji wyszukiwania starszych niż motyw stylu słownika przy użyciu tego samego klucza, zawierającej styl słownika motywu. Można określić `<Button>Hello</Button>` w dowolnym miejscu strony i style zdefiniowane za pomocą <xref:System.Windows.Style.TargetType%2A> z `Button` zastosowanie do tego przycisku. Jeśli chcesz, możesz nadal jawnie klucza styl z taką samą wartość typu, jak <xref:System.Windows.Style.TargetType%2A>dla jasności znaczników, ale jest opcjonalny.  
  
 Style niejawne klucze nie mają zastosowania w kontrolce, jeśli <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> jest `true` (należy również zauważyć, że <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> może być ustawiony jako część natywnych zachowanie dla klasy kontrolki, a nie jawnie na wystąpienie kontrolki). Ponadto w celu obsługi niejawne kluczy dla scenariuszy w klasie pochodnej, formant przesłonięcie <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (wszystkich istniejących kontrolek w ramach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to). Aby uzyskać więcej informacji na temat style, motywy i projektu kontroli zobacz [wytyczne dotyczące projektowania kontrolek w określonych stylach](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> ma również niejawny klucz. Niejawny klucz do <xref:System.Windows.DataTemplate> jest <xref:System.Windows.DataTemplate.DataType%2A> wartości właściwości. <xref:System.Windows.DataTemplate.DataType%2A> można również określić nazwę typu, a nie jawnie za pomocą [{x: Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Aby uzyskać więcej informacji, zobacz [Przegląd Szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.ResourceDictionary>  
 [Zasoby aplikacji](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Definiowanie zasobu i odwoływanie się do niego](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)  
 [Zarządzanie aplikacjami — omówienie](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [x:Type, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [StaticResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [DynamicResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
