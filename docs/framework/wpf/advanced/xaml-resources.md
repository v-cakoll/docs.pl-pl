---
title: Zasoby XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958821"
---
# <a name="xaml-resources"></a>Zasoby XAML
Zasób jest obiektem, którego można użyć w różnych miejscach w aplikacji. Przykłady zasobów obejmują pędzle i style. W tym omówieniu opisano sposób używania zasobów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie. Możesz również tworzyć zasoby i uzyskiwać do nich dostęp za pomocą kodu lub zamiennie między kodem i [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [zasobów i kodu](resources-and-code.md).  
  
> [!NOTE]
> Pliki zasobów opisane w tym temacie są inne niż pliki zasobów opisane w artykule zasoby [aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md) oraz inne niż osadzone lub połączone zasoby opisane w temacie [Zarządzanie zasobami aplikacji (.NET). ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Używanie zasobów w języku XAML  
 Poniższy przykład definiuje <xref:System.Windows.Media.SolidColorBrush> jako zasób elementu głównego strony. Przykład odwołuje się do zasobu i używa go do ustawiania właściwości kilku elementów podrzędnych, takich jak <xref:System.Windows.Shapes.Ellipse>, a <xref:System.Windows.Controls.TextBlock>i <xref:System.Windows.Controls.Button>a.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Każdy element poziomu platformy<xref:System.Windows.FrameworkElement> (lub <xref:System.Windows.FrameworkContentElement>) ma <xref:System.Windows.FrameworkElement.Resources%2A> właściwość, która jest <xref:System.Windows.ResourceDictionary>właściwością zawierającą zasoby (jako), które definiuje zasób. Możesz definiować zasoby na dowolnym elemencie. Jednak zasoby są najczęściej definiowane w elemencie głównym, który jest <xref:System.Windows.Controls.Page> w przykładzie.  
  
 Każdy zasób w słowniku zasobów musi mieć unikatowy klucz. Podczas definiowania zasobów w znacznikach, należy przypisać unikatowy klucz za pomocą [dyrektywy x:Key](../../xaml-services/x-key-directive.md). Zazwyczaj klucz jest ciągiem; można jednak również ustawić inne typy obiektów przy użyciu odpowiednich rozszerzeń znaczników. Klucze niebędące ciągami dla zasobów są używane przez niektóre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obszary funkcji w, szczególnie w przypadku stylów, zasobów składników i stylów danych.  
  
 Po zdefiniowaniu zasobu można odwoływać się do zasobu, który ma być używany dla wartości właściwości przy użyciu składni rozszerzenia znacznika zasobu, która określa nazwę klucza, na przykład:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 W poprzednim przykładzie, gdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] moduł ładujący przetwarza wartość `{StaticResource MyBrush}` <xref:System.Windows.Controls.Control.Background%2A> właściwości na <xref:System.Windows.Controls.Button>, funkcja logiki wyszukiwania zasobów najpierw sprawdza słownik zasobów dla <xref:System.Windows.Controls.Button> elementu. Jeśli <xref:System.Windows.Controls.Button> nie ma definicji klucza `MyBrush` zasobu (nie jest to możliwe, kolekcja zasobów jest pusta), wyszukiwanie następnie <xref:System.Windows.Controls.Button>sprawdza <xref:System.Windows.Controls.Page>element nadrzędny, czyli. W takim przypadku podczas definiowania zasobu w <xref:System.Windows.Controls.Page> elemencie głównym wszystkie elementy w drzewie <xref:System.Windows.Controls.Page> logicznym mogą uzyskać do niego dostęp i można użyć tego samego zasobu do ustawienia wartości <xref:System.Type> każdej właściwości, która akceptuje ten zasób praw. W `MyBrush` poprzednim przykładzie ten sam zasób ustawia dwie różne właściwości <xref:System.Windows.Controls.Control.Background%2A> : <xref:System.Windows.Controls.Button>a i <xref:System.Windows.Shapes.Shape.Fill%2A>. <xref:System.Windows.Shapes.Rectangle>  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Zasoby statyczne i dynamiczne  
 Zasób może być przywoływany jako zasób statyczny lub zasób dynamiczny. Jest to realizowane przy użyciu [rozszerzenia znacznika StaticResource](staticresource-markup-extension.md) lub [rozszerzenia znacznika DynamicResource —](dynamicresource-markup-extension.md). Rozszerzenie znaczników jest funkcją, w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] której można określić odwołanie do obiektu przez rozszerzenie znacznika przetwarza ciąg atrybutu i zwraca obiekt [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do modułu ładującego. Aby uzyskać więcej informacji o zachowaniu rozszerzenia znaczników, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
 W przypadku korzystania z rozszerzenia znacznika zazwyczaj w postaci ciągu można określić jeden lub więcej parametrów, które są przetwarzane przez określone rozszerzenie znacznika, zamiast oceniać w kontekście ustawianej właściwości. [Rozszerzenie znacznika StaticResource](staticresource-markup-extension.md) przetwarza klucz, wyszukując wartość tego klucza we wszystkich dostępnych słownikach zasobów. Dzieje się tak podczas ładowania, który jest punktem w czasie, kiedy proces ładowania musi przypisać wartość właściwości, która pobiera odwołanie do zasobu statycznego. [Rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md) zamiast tego przetwarza klucz przez utworzenie wyrażenia, a wyrażenie pozostaje nieoceniane do momentu rzeczywistego uruchomienia aplikacji, podczas gdy wyrażenie jest oceniane i zawiera wartość.  
  
 W przypadku odwoływania się do zasobu następujące zagadnienia mogą mieć wpływ na to, czy jest używane odwołanie do zasobu statycznego, czy odwołanie do zasobu dynamicznego:  
  
- Ogólny projekt sposobu tworzenia zasobów dla aplikacji (na stronie w aplikacji, luźno [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]w zestawie danych samego zasobu).  
  
- Funkcja aplikacji: aktualizuje zasoby w czasie rzeczywistym w wymaganiach aplikacji?  
  
- Odpowiednie zachowanie wyszukiwania tego typu odwołania do zasobu.  
  
- Określona właściwość lub typ zasobu oraz natywne zachowanie tych typów.  
  
### <a name="static-resources"></a>Zasoby statyczne  
 Odwołania do zasobów statycznych działają najlepiej w następujących okolicznościach:  
  
- Projekt aplikacji koncentruje się na większości wszystkich zasobów do słowników zasobów na poziomie strony lub aplikacji. Odwołania do zasobów statycznych nie są ponownie oceniane na podstawie zachowań środowiska uruchomieniowego, takich jak ponowne ładowanie strony i w związku z tym może mieć pewne korzyści wynikające z wydajności, aby uniknąć dużej liczby dynamicznych odwołań do zasobów, gdy nie są one niezbędne dla danego zasobu i projekt aplikacji.  
  
- Ustawiasz wartość właściwości, która nie znajduje się w <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable>lub.  
  
- Tworzysz słownik zasobów, który zostanie skompilowany do biblioteki DLL, i spakowany jako część aplikacji lub udostępnione przez aplikacje.  
  
- Tworzysz motyw dla kontrolki niestandardowej i definiujesz zasoby, które są używane w motywach. W takim przypadku zazwyczaj nie ma potrzeby dynamicznego wyszukiwania odwołań do zasobów, zamiast tego należy użyć zachowania odwołania do zasobów statycznych, aby wyszukiwanie było przewidywalne i załączane do motywu. Odwołanie do zasobu dynamicznego, nawet odwołanie w ramach motywu, pozostaje nieoceniane do czasu wykonania i istnieje prawdopodobieństwo, że gdy motyw zostanie zastosowany, jakiś element lokalny spowoduje przedefiniowanie klucza, do którego motyw próbuje się odwołać, a element lokalny będzie się znajdować przed do samego motywu w odnośniku. Jeśli tak się stanie, kompozycja nie będzie zachowywać się w oczekiwany sposób.  
  
- Używasz zasobów do ustawiania dużej liczby właściwości zależności. Właściwości zależności mają efektywne buforowanie wartości, które są włączone przez system właściwości, więc w przypadku podania wartości właściwości zależności, która może być oceniona w czasie ładowania, właściwość dependency nie musi sprawdzać, czy wyrażenie zostało obliczone ponownie i może zwracać Ostatnia efektywna wartość. Ta technika może być korzyścią dla wydajności.  
  
- Aby zmienić podstawowy zasób dla wszystkich odbiorców, lub chcesz zachować oddzielne zapisywalne wystąpienia dla każdego konsumenta przy użyciu [atrybutu x:Shared —](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Zachowanie wyszukiwania zasobów statycznych  
  
1. Proces wyszukiwania sprawdza, czy żądany klucz znajduje się w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość.  
  
2. Następnie proces wyszukiwania przechodzi Drzewo logiczne w górę do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.  
  
3. Następnie sprawdzane są zasoby aplikacji. Zasoby aplikacji to zasoby znajdujące się w słowniku zasobów, które są <xref:System.Windows.Application> zdefiniowane przez obiekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla aplikacji.  
  
 Odwołania do zasobów statycznych z poziomu słownika zasobów muszą odwoływać się do zasobu, który został już zdefiniowany leksykalnie przed odwołaniem do zasobu. Odwołania do przodu nie mogą być rozwiązane przez odwołanie do zasobu statycznego. Z tego powodu w przypadku używania odwołań do zasobów statycznych należy zaprojektować strukturę słownika zasobów, aby zasoby przeznaczone do użycia przez zasób zostały zdefiniowane na początku każdego odpowiedniego słownika zasobów lub w jego bliskim czasie.  
  
 Statyczne Wyszukiwanie zasobów może przekroczyć motywy lub zasoby systemowe, ale jest to obsługiwane tylko w przypadku, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gdy moduł ładujący rozszerzy żądanie. Odroczenie jest niezbędne, aby kompozycja środowiska uruchomieniowego w momencie załadowania strony była poprawnie stosowana do aplikacji. Jednak statyczne odwołania do kluczy, które są znane tylko w motywach lub jako zasoby systemowe, nie są zalecane. Wynika to z faktu, że takie odwołania nie są oceniane, jeśli motyw został zmieniony przez użytkownika w czasie rzeczywistym. Dynamiczne odwołanie do zasobów jest bardziej niezawodne w przypadku żądania motywu lub zasobów systemowych. Wyjątek polega na tym, że element motywu żąda innego zasobu. Odwołania te powinny być odwołaniami do zasobów statycznych z przyczyn wymienionych wcześniej.  
  
 Zachowanie wyjątku w przypadku, gdy odwołanie do zasobu statycznego nie zostanie odnalezione. Jeśli zasób został odroczony, wyjątek występuje w czasie wykonywania. Jeśli zasób nie został odroczony, wyjątek występuje w czasie ładowania.  
  
### <a name="dynamic-resources"></a>Zasoby dynamiczne  
 Zasoby dynamiczne działają najlepiej w następujących okolicznościach:  
  
- Wartość zasobu zależy od warunków, które nie są znane do czasu wykonania. Obejmuje to zasoby systemowe lub zasoby, które w przeciwnym razie użytkownika nie są gotowe do użycia. Na przykład można utworzyć wartości ustawiające odwołujące się do właściwości systemu, które są <xref:System.Windows.SystemColors>udostępniane <xref:System.Windows.SystemFonts>przez, <xref:System.Windows.SystemParameters>lub. Te wartości są naprawdę dynamiczne, ponieważ ostatecznie pochodzą ze środowiska uruchomieniowego użytkownika i systemu operacyjnego. Możesz również mieć motywy na poziomie aplikacji, które mogą ulec zmianie, w przypadku których dostęp do zasobów na poziomie strony musi również zostać przechwycony.  
  
- Tworzysz lub przywołująsz style motywu dla kontrolki niestandardowej.  
  
- W trakcie okresu istnienia aplikacji zamierzasz <xref:System.Windows.ResourceDictionary> dostosować zawartość a.  
  
- Masz skomplikowaną strukturę zasobów, która ma wzajemne zależności, gdzie może być wymagane odwołanie do przodu. Odwołania do zasobów statycznych nie obsługują odwołań do przodu, ale dynamiczne odwołania do zasobów obsługują je, ponieważ zasób nie musi być oceniany do czasu wykonania, a odwołania do przodu nie są odpowiednim pojęciem.  
  
- Odwołuje się do zasobu, który jest szczególnie duży od perspektywy kompilacji lub zestawu roboczego, a zasób może nie być używany natychmiast po załadowaniu strony. Odwołania do zasobów statycznych są zawsze [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ładowane po załadowaniu strony, jednak odwołanie do zasobu dynamicznego nie jest ładowane, dopóki nie zostanie faktycznie użyte.  
  
- Tworzysz styl, w którym wartości setter mogą pochodzić z innych wartości, na które mają wpływ motywy lub inne ustawienia użytkownika.  
  
- Zasoby są stosowane do elementów, które mogą być w drzewie logicznym w czasie trwania aplikacji. Zmiana elementu nadrzędnego również może spowodować zmianę zakresu wyszukiwania zasobów, dlatego jeśli chcesz, aby zasób z elementem nadrzędnym był obliczany na podstawie nowego zakresu, zawsze używaj dynamicznego odwołania do zasobów.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Dynamiczne zachowanie wyszukiwania zasobów  
 Zachowanie wyszukiwania zasobów dla odwołania do zasobu dynamicznego równolegle z zachowaniem wyszukiwania w kodzie w przypadku wywołania <xref:System.Windows.FrameworkElement.FindResource%2A> lub. <xref:System.Windows.FrameworkElement.SetResourceReference%2A>  
  
1. Proces wyszukiwania sprawdza, czy żądany klucz znajduje się w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość.  
  
    - Jeśli element definiuje <xref:System.Windows.FrameworkElement.Style%2A> Właściwość <xref:System.Windows.Style.Resources%2A> , słownik w obrębie <xref:System.Windows.Style> jest zaznaczone.  
  
    - Jeśli element definiuje <xref:System.Windows.Controls.Control.Template%2A> Właściwość <xref:System.Windows.FrameworkTemplate.Resources%2A> , słownik w obrębie <xref:System.Windows.FrameworkTemplate> jest zaznaczone.  
  
2. Następnie proces wyszukiwania przechodzi Drzewo logiczne w górę do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.  
  
3. Następnie sprawdzane są zasoby aplikacji. Zasoby aplikacji to zasoby znajdujące się w słowniku zasobów, które są <xref:System.Windows.Application> zdefiniowane przez obiekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla aplikacji.  
  
4. Słownik zasobów motywu jest sprawdzany dla aktualnie aktywnego motywu. Jeśli kompozycja ulegnie zmianie w czasie wykonywania, wartość zostanie przeszacowana.  
  
5. Zasoby systemu są sprawdzane.  
  
 Zachowanie wyjątków (jeśli istnieje) jest różne:  
  
- Jeśli zasób zażądał <xref:System.Windows.FrameworkElement.FindResource%2A> wywołania i nie został odnaleziony, zostanie zgłoszony wyjątek.  
  
- Jeśli zasób zażądał <xref:System.Windows.FrameworkElement.TryFindResource%2A> wywołania i nie został znaleziony, żaden wyjątek nie jest wywoływany, ale zwrócona wartość to `null`. Jeśli ustawiona właściwość nie akceptuje `null`, nadal jest możliwe, że zostanie podniesiony bardziej szczegółowy wyjątek (zależy to od ustawionej właściwości indywidualnej).  
  
- Jeśli zażądano zasobu przez odwołanie do zasobu dynamicznego w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]programie i nie został on znaleziony, zachowanie jest zależne od ogólnego systemu właściwości, ale ogólne zachowanie jest tak, jakby żadna operacja ustawienia właściwości nie miała na poziomie, na którym zasób istnieje. Na przykład, jeśli spróbujesz ustawić tło dla pojedynczego elementu Button przy użyciu zasobu, którego nie można oszacować, nie ma ustawionej wartości, ale efektywna wartość może nadal pochodzić od innych uczestników w systemie właściwości i priorytecie wartości. Na przykład wartość tła może nadal pochodzić ze zdefiniowanego lokalnie stylu przycisku lub z stylu motywu. Dla właściwości, które nie są zdefiniowane przez style motywu, wartość efektywna po nieudanej ocenie zasobu może pochodzić z wartości domyślnej w metadanych właściwości.  
  
#### <a name="restrictions"></a>Ograniczenia  
 Odwołania do zasobów dynamicznych mają pewne istotne ograniczenia. Należy mieć co najmniej jedną z następujących wartości:  
  
- Ustawiona właściwość musi być właściwością w <xref:System.Windows.FrameworkElement> lub. <xref:System.Windows.FrameworkContentElement> Ta właściwość musi być obsługiwana przez <xref:System.Windows.DependencyProperty>.  
  
- Odwołanie dotyczy wartości w <xref:System.Windows.Style>. <xref:System.Windows.Setter>  
  
- Ustawiana właściwość musi być właściwością <xref:System.Windows.Freezable> , która jest podana jako wartość <xref:System.Windows.FrameworkElement> właściwości <xref:System.Windows.Setter> lub lub <xref:System.Windows.FrameworkContentElement> wartość.  
  
 Ponieważ właściwość ustawiana musi być właściwością <xref:System.Windows.DependencyProperty> lub <xref:System.Windows.Freezable> , większość zmian właściwości może być propagowana do interfejsu użytkownika, ponieważ zmiana właściwości (zmieniona dynamiczna wartość zasobu) jest potwierdzana przez system właściwości. Większość formantów obejmuje logikę, która wymusić inny układ kontrolki <xref:System.Windows.DependencyProperty> , jeśli zmiany i właściwości mogą mieć wpływ na układ. Jednak nie wszystkie właściwości, które mają [rozszerzenie znacznika DynamicResource —](dynamicresource-markup-extension.md) jako ich wartość, są gwarantowane w celu zapewnienia wartości w taki sposób, aby były aktualizowane w czasie rzeczywistym w interfejsie użytkownika. Ta funkcja nadal może różnić się w zależności od właściwości, a także w zależności od typu będącego właścicielem właściwości, a nawet logicznej struktury aplikacji.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Style, datatemplates i klucze niejawne  
 Wcześniej stwierdzono, że wszystkie elementy w <xref:System.Windows.ResourceDictionary> elemencie muszą mieć klucz. Nie oznacza to jednak, że wszystkie zasoby muszą mieć jawną `x:Key`. Kilka typów obiektów obsługuje klucz niejawny, gdy jest zdefiniowany jako zasób, gdzie wartość klucza jest związana z wartością innej właściwości. Jest to tzw. klucz niejawny, natomiast `x:Key` atrybut jest jawnym kluczem. Można zastąpić klucz niejawny, określając klucz jawny.  
  
 Jednym z <xref:System.Windows.Style>najważniejszych scenariuszy dotyczących zasobów jest zdefiniowanie. W rzeczywistości <xref:System.Windows.Style> jest prawie zawsze zdefiniowane jako wpis w słowniku zasobów, ponieważ style są z założenia przeznaczone do ponownego użycia. Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
 Style formantów mogą być tworzone razem z niejawnym kluczem i z odwołaniem. Style motywu definiujące domyślny wygląd formantu polegają na tym niejawnym kluczu. Klucz niejawny z punktu widzenia żądania jest <xref:System.Type> sam formantu. Klucz niejawny z punktu widzenia definiowania zasobu jest <xref:System.Windows.Style.TargetType%2A> stylem. W związku z tym, jeśli tworzysz motywy dla kontrolek niestandardowych, Tworzenie stylów, które współdziałają z istniejącymi stylami motywu, nie musisz określać [dyrektywy x:Key](../../xaml-services/x-key-directive.md) dla tego <xref:System.Windows.Style>elementu. A jeśli chcesz użyć stylów z motywem, nie musisz określać żadnego stylu. Na przykład następująca definicja stylu działa, mimo że <xref:System.Windows.Style> zasób nie ma klucza:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Ten styl naprawdę ma klucz: klucz `typeof(` <xref:System.Windows.Controls.Button> `)`niejawny. W znaczniku można określić <xref:System.Windows.Style.TargetType%2A> bezpośrednio jako nazwę typu (lub opcjonalnie użyć [{x:Type...}](../../xaml-services/x-type-markup-extension.md) do zwrócenia <xref:System.Type>.  
  
 Zgodnie z domyślnymi mechanizmami stylu motywu używanym [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]przez, ten styl jest stosowany jako styl <xref:System.Windows.Controls.Button> środowiska uruchomieniowego na <xref:System.Windows.Controls.Button> stronie, nawet jeśli sam nie próbuje określić swojej <xref:System.Windows.FrameworkElement.Style%2A> właściwości lub określonego zasobu odwołanie do stylu. Styl zdefiniowany na stronie znajduje się wcześniej w sekwencji wyszukiwania niż styl słownika motywu, przy użyciu tego samego klucza, który ma styl słownika motywu. Można tylko określić `<Button>Hello</Button>` dowolne miejsce na stronie, a styl zdefiniowany za pomocą <xref:System.Windows.Style.TargetType%2A> elementu `Button` zostałby zastosowany do tego przycisku. Jeśli chcesz, możesz w dalszym ciągu jawnie użyć stylu z tą samą wartością typu co <xref:System.Windows.Style.TargetType%2A>dla jasności w znaczniku, ale jest to opcjonalne.  
  
 Niejawne klucze dla stylów nie mają zastosowania w przypadku <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> kontrolki, jeśli jest <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> (to `true` również, że może być ustawiony jako część zachowania natywnego dla klasy kontrolki, a nie jawnie w wystąpieniu kontrolki). Ponadto, aby zapewnić obsługę kluczy niejawnych dla scenariuszy klas pochodnych, formant musi przesłonić <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (wszystkie istniejące kontrolki podane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tym celu). Aby uzyskać więcej informacji na temat stylów, motywów i projektu kontrolki, zobacz [wytyczne dotyczące projektowania formantów określonych stylach](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>ma także klucz niejawny. Klucz niejawny elementu <xref:System.Windows.DataTemplate> a <xref:System.Windows.DataTemplate.DataType%2A> jest wartością właściwości. <xref:System.Windows.DataTemplate.DataType%2A>można również określić jako nazwę typu, zamiast jawnie używać [{x:Type...}](../../xaml-services/x-type-markup-extension.md). Aby uzyskać szczegółowe informacje, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby aplikacji](optimizing-performance-application-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [Definiowanie zasobu i odwoływanie się do niego](how-to-define-and-reference-a-resource.md)
- [Zarządzanie aplikacjami — omówienie](../app-development/application-management-overview.md)
- [x:Type, rozszerzenie znaczników](../../xaml-services/x-type-markup-extension.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [DynamicResource, rozszerzenie znaczników](dynamicresource-markup-extension.md)
