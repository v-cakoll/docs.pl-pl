---
title: Definiowanie zasobów XAML
description: Dowiedz się więcej o zasobach XAML w WPF dla platformy .NET Core. Informacje o typach zasobów XAML i sposobach definiowania zasobów XAML.
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071284"
---
# <a name="overview-of-xaml-resources"></a>Przegląd zasobów XAML

Zasób jest obiektem, którego można użyć w różnych miejscach w aplikacji. Przykłady zasobów obejmują pędzle i style. W tym omówieniu opisano sposób używania zasobów w programie Extensible Application Markup Language (XAML). Możesz również tworzyć zasoby i uzyskiwać do nich dostęp za pomocą kodu.

> [!NOTE]
> Zasoby XAML opisane w tym artykule różnią się od *zasobów aplikacji* , które zwykle są plikami dodanymi do aplikacji, takich jak zawartość, dane lub osadzone pliki.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Używanie zasobów w języku XAML

Poniższy przykład definiuje <xref:System.Windows.Media.SolidColorBrush> jako zasób elementu głównego strony. Przykład odwołuje się do zasobu i używa go do ustawiania właściwości kilku elementów podrzędnych, takich jak <xref:System.Windows.Shapes.Ellipse>, a <xref:System.Windows.Controls.TextBlock>i a. <xref:System.Windows.Controls.Button>

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Każdy element poziomu platformy<xref:System.Windows.FrameworkElement> (lub <xref:System.Windows.FrameworkContentElement>) ma <xref:System.Windows.FrameworkElement.Resources%2A> właściwość, która jest <xref:System.Windows.ResourceDictionary> typem zawierającym zdefiniowane zasoby. Można zdefiniować zasoby dla dowolnego elementu, na przykład <xref:System.Windows.Controls.Button>. Jednak zasoby są najczęściej definiowane w elemencie głównym, który jest <xref:System.Windows.Controls.Page> w przykładzie.

Każdy zasób w słowniku zasobów musi mieć unikatowy klucz. Podczas definiowania zasobów w znacznikach, należy przypisać unikatowy klucz za pomocą [dyrektywy x:Key](../xaml-services/xkey-directive.md). Zazwyczaj klucz jest ciągiem; można jednak również ustawić inne typy obiektów przy użyciu odpowiednich rozszerzeń znaczników. Klucze niebędące ciągami dla zasobów są używane przez niektóre obszary funkcji w WPF, szczególnie w przypadku stylów, zasobów składników i stylów danych.

Zdefiniowanego zasobu można użyć ze składnią rozszerzenia znacznika zasobu, która określa nazwę klucza zasobu. Na przykład użyj zasobu jako wartości właściwości w innym elemencie.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

W poprzednim przykładzie, gdy moduł ładujący `{StaticResource MyBrush}` XAML przetwarza wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości na <xref:System.Windows.Controls.Button>, funkcja logiki wyszukiwania zasobów najpierw sprawdza słownik zasobów dla <xref:System.Windows.Controls.Button> elementu. Jeśli <xref:System.Windows.Controls.Button> nie ma definicji klucza `MyBrush` zasobu (w tym przykładzie nie jest to możliwe; kolekcja zasobów jest pusta), wyszukiwanie dalej sprawdza element nadrzędny <xref:System.Windows.Controls.Button>, czyli. <xref:System.Windows.Controls.Page> W przypadku zdefiniowania zasobu w elemencie <xref:System.Windows.Controls.Page> głównym wszystkie elementy w drzewie logicznym <xref:System.Windows.Controls.Page> mogą uzyskać do niego dostęp. Można też ponownie użyć tego samego zasobu do ustawiania wartości właściwości, która akceptuje ten sam typ, który reprezentuje zasób. W poprzednim przykładzie `MyBrush` ten sam zasób ustawia dwie różne właściwości: <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button>a i. <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle>

## <a name="static-and-dynamic-resources"></a>Zasoby statyczne i dynamiczne

Zasób może być przywoływany jako statyczny lub dynamiczny. Odwołania są tworzone przy użyciu [rozszerzenia znacznika StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) lub [rozszerzenia znacznika DynamicResource —](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Rozszerzenie znaczników jest funkcją języka XAML, która pozwala określić odwołanie do obiektu przez rozszerzenie znacznika przetwarza ciąg atrybutu i zwraca obiekt do modułu ładującego XAML. Aby uzyskać więcej informacji o zachowaniu rozszerzenia znaczników, zobacz [rozszerzenia znaczników i XAML WPF](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

W przypadku korzystania z rozszerzenia znacznika zazwyczaj w postaci ciągu jest tworzony jeden lub więcej parametrów, które są przetwarzane przez określone rozszerzenie znacznika. [Rozszerzenie znacznika StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) przetwarza klucz, wyszukując wartość tego klucza we wszystkich dostępnych słownikach zasobów. Przetwarzanie odbywa się podczas ładowania, czyli gdy proces ładowania musi przypisać wartość właściwości. [Rozszerzenie znacznika DynamicResource —](../../framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast tego przetwarza klucz przez utworzenie wyrażenia, a to wyrażenie nie jest oceniane do momentu uruchomienia aplikacji, podczas której wyrażenie jest oceniane i zawiera wartość.

W przypadku odwoływania się do zasobu następujące zagadnienia mogą mieć wpływ na to, czy jest używane odwołanie do zasobu statycznego, czy odwołanie do zasobu dynamicznego:

- Podczas określania ogólnego projektu sposobu tworzenia zasobów dla aplikacji (na stronie w aplikacji, w luźnej liczbie XAML lub w zestawie zasobów) należy wziąć pod uwagę następujące kwestie:

- Funkcjonalność aplikacji. Czy aktualizowane są zasoby w ramach wymagań aplikacji w czasie rzeczywistym?
- Odpowiednie zachowanie wyszukiwania tego typu odwołania do zasobu.
- Określona właściwość lub typ zasobu oraz natywne zachowanie tych typów.

## <a name="static-resources"></a>Zasoby statyczne

Odwołania do zasobów statycznych działają najlepiej w następujących okolicznościach:

- Projekt aplikacji koncentruje się na większości zasobów do słowników zasobów na poziomie strony lub aplikacji. Odwołania do zasobów statycznych nie są ponownie oceniane na podstawie zachowań środowiska uruchomieniowego, takich jak ponowne ładowanie strony. W związku z tym może mieć pewne korzyści wynikające z wydajności, aby uniknąć dużej liczby dynamicznych odwołań do zasobów, gdy nie są one potrzebne w oparciu o projekt i aplikację.

- Ustawiasz wartość właściwości, która nie należy do <xref:System.Windows.DependencyObject> ani. <xref:System.Windows.Freezable>

- Tworzysz słownik zasobów, który zostanie skompilowany do biblioteki DLL i spakowany jako część aplikacji lub udostępnione przez aplikacje.

- Tworzysz motyw dla kontrolki niestandardowej i definiujesz zasoby, które są używane w motywach. W takim przypadku zwykle nie ma potrzeby zachowania wyszukiwania odwołań do zasobów dynamicznych; Zamiast tego chcesz użyć zachowania odwołania do zasobów statycznych, aby wyszukiwanie było przewidywalne i samodzielne w motywie. Odwołanie do zasobu dynamicznego, nawet odwołanie w ramach motywu, pozostaje nieoceniane do czasu wykonania. i istnieje prawdopodobieństwo, że po zastosowaniu motywu, jakiś element lokalny spowoduje przedefiniowanie klucza, do którego motyw próbuje się odwołać, a element lokalny będzie się znajdował przed samą kompozycją w wyszukiwaniu. Jeśli tak się stanie, kompozycja nie będzie zachowywać się zgodnie z oczekiwaniami.

- Używasz zasobów do ustawiania dużej liczby właściwości zależności. Właściwości zależności mają efektywne buforowanie wartości, które są włączone przez system właściwości, więc w przypadku podania wartości właściwości zależności, która może być Szacowana w czasie ładowania, właściwość dependency nie musi sprawdzać, czy wyrażenie zostało obliczone i może zwracać ostatnią wartość efektywną. Ta technika może być korzyścią dla wydajności.

- Aby zmienić podstawowy zasób dla wszystkich odbiorców, lub chcesz zachować oddzielne zapisywalne wystąpienia dla każdego konsumenta przy użyciu [atrybutu x:Shared —](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Zachowanie wyszukiwania zasobów statycznych

Poniżej opisano proces wyszukiwania, który automatycznie występuje, gdy odwołanie do zasobu statycznego jest przywoływane przez właściwość lub element:

01. Proces wyszukiwania sprawdza, czy żądany klucz znajduje się w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość.

01. Następnie proces wyszukiwania przechodzi Drzewo logiczne w górę do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.

01. Zasoby aplikacji są sprawdzane. Zasoby aplikacji to zasoby w słowniku zasobów zdefiniowane przez <xref:System.Windows.Application> obiekt dla aplikacji WPF.

Odwołania do zasobów statycznych z poziomu słownika zasobów muszą odwoływać się do zasobu, który został już zdefiniowany leksykalnie przed odwołaniem do zasobu. Odwołania do przodu nie mogą być rozwiązane przez odwołanie do zasobu statycznego. Z tego powodu Zaprojektuj strukturę słownika zasobów w taki sposób, że zasoby są definiowane na początku każdego odpowiedniego słownika zasobów lub wkrótce.

Statyczne Wyszukiwanie zasobów może przekroczyć motywy lub zasoby systemowe, ale ta funkcja wyszukiwania jest obsługiwana tylko w przypadku, gdy moduł ładujący XAML rozszerzy żądanie. Odroczenie jest niezbędne, aby kompozycja środowiska uruchomieniowego w momencie załadowania strony była poprawnie stosowana do aplikacji. Jednak statyczne odwołania do kluczy, które są znane tylko w motywach lub jako zasoby systemowe, nie są zalecane, ponieważ takie odwołania nie są ponownie oceniane, jeśli motyw zostanie zmieniony przez użytkownika w czasie rzeczywistym. Dynamiczne odwołanie do zasobów jest bardziej niezawodne w przypadku żądania motywu lub zasobów systemowych. Wyjątek polega na tym, że element motywu żąda innego zasobu. Odwołania te powinny być odwołaniami do zasobów statycznych z przyczyn wymienionych wcześniej.

Zachowanie wyjątku w przypadku, gdy odwołanie do zasobu statycznego nie zostanie odnalezione. Jeśli zasób został odroczony, wyjątek występuje w czasie wykonywania. Jeśli zasób nie został odroczony, wyjątek występuje w czasie ładowania.

## <a name="dynamic-resources"></a>Zasoby dynamiczne

Zasoby dynamiczne działają najlepiej, gdy:

- Wartość zasobu, w tym zasoby systemowe lub zasoby, które są w przeciwnym razie użytkownik settable, zależy od warunków, które nie są znane do czasu wykonania. Na przykład można utworzyć wartości ustawiające odwołujące się do właściwości systemu, które <xref:System.Windows.SystemColors>są <xref:System.Windows.SystemFonts>udostępniane przez <xref:System.Windows.SystemParameters>, lub. Te wartości są naprawdę dynamiczne, ponieważ ostatecznie pochodzą ze środowiska uruchomieniowego użytkownika i systemu operacyjnego. Możesz również mieć motywy na poziomie aplikacji, które mogą ulec zmianie, w przypadku których dostęp do zasobów na poziomie strony musi również zostać przechwycony.

- Tworzysz lub przywołująsz style motywu dla kontrolki niestandardowej.

- W trakcie okresu istnienia aplikacji zamierzasz <xref:System.Windows.ResourceDictionary> dostosować zawartość elementu.

- Masz skomplikowaną strukturę zasobów, która ma wzajemne zależności, gdzie może być wymagane odwołanie do przodu. Odwołania do zasobów statycznych nie obsługują odwołań do przekazywania, ale dynamiczne odwołania do zasobów obsługują je, ponieważ nie trzeba oceniać zasobu do czasu wykonania, a odwołania do przodu nie są odpowiednim pojęciem.

- Odwołujesz się do zasobu, który jest duży od perspektywy kompilacji lub zestawu roboczego, a zasób może nie być używany natychmiast po załadowaniu strony. Odwołania do zasobów statycznych są zawsze ładowane z XAML podczas ładowania strony. Jednak dynamiczne odwołanie do zasobów nie zostanie załadowane do momentu użycia.

- Tworzysz styl, w którym wartości setter mogą pochodzić z innych wartości, na które mają wpływ motywy lub inne ustawienia użytkownika.

- Są stosowane zasoby do elementów, które mogą zostać odszukane w drzewie logicznym podczas okresu istnienia aplikacji. Zmiana elementu nadrzędnego również może spowodować zmianę zakresu wyszukiwania zasobów, dlatego jeśli chcesz, aby zasób z elementem nadrzędnym był obliczany na podstawie nowego zakresu, zawsze używaj dynamicznego odwołania do zasobów.

### <a name="dynamic-resource-lookup-behavior"></a>Dynamiczne zachowanie wyszukiwania zasobów

Zachowanie wyszukiwania zasobów dla odwołania do zasobu dynamicznego polega na równoległym zachowaniu wyszukiwania w kodzie w przypadku <xref:System.Windows.FrameworkElement.FindResource%2A> wywołania <xref:System.Windows.FrameworkElement.SetResourceReference%2A>lub:

01. Wyszukiwanie wyszukuje żądany klucz w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość:

    - Jeśli element definiuje <xref:System.Windows.FrameworkElement.Style%2A> właściwość, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> element ma zaznaczone jego <xref:System.Windows.Style.Resources> słownik.

    - Jeśli element definiuje <xref:System.Windows.Controls.Control.Template%2A> właściwość, <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> słownik elementu jest sprawdzany.

01. Wyszukiwanie przechodzi przez Drzewo logiczne do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany do momentu osiągnięcia elementu głównego.

01. Zasoby aplikacji są sprawdzane. Zasoby aplikacji to zasoby znajdujące się w słowniku zasobów, które są <xref:System.Windows.Application> zdefiniowane przez obiekt dla aplikacji WPF.

01. Słownik zasobów motywu jest sprawdzany dla aktualnie aktywnego motywu. Jeśli kompozycja ulegnie zmianie w czasie wykonywania, wartość zostanie przeszacowana.

01. Zasoby systemu są sprawdzane.

Zachowanie wyjątków (jeśli istnieje) jest różne:

- Jeśli zasób zażądał <xref:System.Windows.FrameworkElement.FindResource%2A> wywołania i nie został odnaleziony, zgłaszany jest wyjątek.

- Jeśli zasób zażądał <xref:System.Windows.FrameworkElement.TryFindResource%2A> wywołania i nie został znaleziony, żaden wyjątek nie jest zgłaszany, a zwrócona wartość to `null`. Jeśli ustawiona właściwość nie akceptuje `null`, nadal jest możliwe, że zostanie wygenerowany dokładniejszy wyjątek, w zależności od ustawionej właściwości indywidualnej.

- Jeśli zasób otrzymał żądanie odwołania do zasobu dynamicznego w języku XAML i nie został znaleziony, zachowanie zależy od ogólnego systemu właściwości. Ogólnym zachowaniem jest to, że nie ma żadnej operacji ustawienia właściwości na poziomie, na którym znajduje się zasób. Na przykład, jeśli spróbujesz ustawić tło dla pojedynczego elementu Button przy użyciu zasobu, którego nie można oszacować, wówczas żadne wyniki nie zostaną ustawione, ale wartość efektywna nadal może pochodzić od innych uczestników w systemie właściwości i w pierwszeństwie wartości. Na przykład wartość tła może nadal pochodzić ze zdefiniowanego lokalnie stylu przycisku lub z stylu motywu. Dla właściwości, które nie są zdefiniowane przez style motywu, wartość efektywna po nieudanej ocenie zasobu może pochodzić z wartości domyślnej w metadanych właściwości.

### <a name="restrictions"></a>Ograniczenia

Odwołania do zasobów dynamicznych mają pewne istotne ograniczenia. Musi być spełniony co najmniej jeden z następujących warunków:

- Ustawiona właściwość musi być właściwością w <xref:System.Windows.FrameworkElement> lub. <xref:System.Windows.FrameworkContentElement> Ta właściwość musi być obsługiwana przez <xref:System.Windows.DependencyProperty>.

- Odwołanie dotyczy wartości w `StyleSetter`.

- Ustawiana właściwość musi być <xref:System.Windows.Freezable> właściwością, która jest podana jako wartość właściwości <xref:System.Windows.FrameworkElement> lub lub <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Setter> wartość.

Ponieważ właściwość ustawiana musi być właściwością <xref:System.Windows.DependencyProperty> lub <xref:System.Windows.Freezable> , większość zmian właściwości można propagować do interfejsu użytkownika, ponieważ zmiana właściwości (zmieniona dynamiczna wartość zasobu) jest potwierdzana przez system właściwości. Większość formantów obejmuje logikę, która wymusić inny układ kontrolki <xref:System.Windows.DependencyProperty> , jeśli zmiany i właściwości mogą mieć wpływ na układ. Jednak nie wszystkie właściwości, które mają [rozszerzenie znacznika DynamicResource —](../../framework/wpf/advanced/dynamicresource-markup-extension.md) jako ich wartość, są gwarantowane w celu zapewnienia aktualizacji w czasie rzeczywistym w interfejsie użytkownika. Ta funkcja nadal może różnić się w zależności od właściwości, a także w zależności od typu będącego właścicielem właściwości, a nawet logicznej struktury aplikacji.

## <a name="styles-datatemplates-and-implicit-keys"></a>Style, datatemplates i klucze niejawne

Mimo że wszystkie elementy w <xref:System.Windows.ResourceDictionary> a muszą mieć klucz, który nie oznacza, że wszystkie zasoby muszą mieć jawnie `x:Key`. Kilka typów obiektów obsługuje klucz niejawny, gdy jest zdefiniowany jako zasób, gdzie wartość klucza jest związana z wartością innej właściwości. Ten typ klucza jest znany jako klucz niejawny, natomiast `x:Key` atrybut jest kluczem jawnym. Można zastąpić klucz niejawny, określając klucz jawny.

Jednym z <xref:System.Windows.Style>ważnych scenariuszy dotyczących zasobów jest zdefiniowanie. W rzeczywistości <xref:System.Windows.Style> jest prawie zawsze zdefiniowane jako wpis w słowniku zasobów, ponieważ style są z założenia przeznaczone do ponownego użycia. Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](styles-templates-overview.md).

Style formantów mogą być tworzone razem z niejawnym kluczem i z odwołaniem. Style motywu definiujące domyślny wygląd formantu polegają na tym niejawnym kluczu. Z punktu widzenia żądania, klucz niejawny jest <xref:System.Type> samego formantu. Z punktu widzenia definiowania zasobów klucz niejawny jest <xref:System.Windows.Style.TargetType%2A> stylem. W związku z tym, jeśli tworzysz motywy dla kontrolek niestandardowych lub tworzysz style, które współdziałają z istniejącymi stylami motywu, nie musisz określać [dyrektywy x:Key](../xaml-services/xkey-directive.md) dla tego <xref:System.Windows.Style>elementu. A jeśli chcesz użyć stylów z motywem, nie musisz określać żadnego stylu. Na przykład następująca definicja stylu działa, mimo że <xref:System.Windows.Style> zasób nie ma klucza:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Ten styl naprawdę ma klucz: klucz `typeof(System.Windows.Controls.Button)`niejawny. W znaczniku można określić <xref:System.Windows.Style.TargetType%2A> bezpośrednio jako nazwę typu (lub opcjonalnie użyć [{x:Type...}](../xaml-services/xtype-markup-extension.md) do zwrócenia <xref:System.Type>.

Za pomocą domyślnych mechanizmów stylu motywu używanych przez WPF, ten styl jest stosowany jako styl środowiska uruchomieniowego <xref:System.Windows.Controls.Button> na stronie, nawet jeśli <xref:System.Windows.Controls.Button> sam nie próbuje określić jego <xref:System.Windows.FrameworkElement.Style%2A> właściwości lub określonego odwołania do zasobu w stylu. Styl zdefiniowany na stronie znajduje się wcześniej w sekwencji wyszukiwania niż styl słownika motywu, przy użyciu tego samego klucza, który ma styl słownika motywu. Można tylko określić `<Button>Hello</Button>` dowolne miejsce na stronie, a styl zdefiniowany za pomocą <xref:System.Windows.Style.TargetType%2A> elementu `Button` zostałby zastosowany do tego przycisku. Jeśli chcesz, możesz nadal jawnie utworzyć klucz stylu z taką samą wartością typu jak <xref:System.Windows.Style.TargetType%2A> dla jasności w znaczniku, ale jest to opcjonalne.

Niejawne klucze dla stylów nie mają zastosowania w <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> kontrolce `true`if is. (Należy również zauważyć <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> , że może być ustawiony jako część zachowania natywnego dla klasy kontrolki, zamiast jawnie na wystąpieniu kontrolki). Ponadto, aby zapewnić obsługę kluczy niejawnych dla scenariuszy klas pochodnych, formant musi przesłonić <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (wszystkie istniejące kontrolki dostarczane jako część WPF obejmują to zastąpienie). Aby uzyskać więcej informacji na temat stylów, motywów i projektu kontrolki, zobacz [wytyczne dotyczące projektowania formantów określonych stylach](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>ma także klucz niejawny. Klucz niejawny elementu <xref:System.Windows.DataTemplate> a jest <xref:System.Windows.DataTemplate.DataType%2A> wartością właściwości. <xref:System.Windows.DataTemplate.DataType%2A>można również określić jako nazwę typu, zamiast jawnie używać [{x:Type...}](../xaml-services/xtype-markup-extension.md). Aby uzyskać szczegółowe informacje, zobacz [tworzenia szablonów danych — omówienie](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.ResourceDictionary>
- [Zasoby aplikacji](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Zasoby i kod](../../framework/wpf/advanced/resources-and-code.md)
- [Definiowanie zasobu i odwoływanie się do niego](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Omówienie zarządzania aplikacjami](../../framework/wpf/app-development/application-management-overview.md)
- [X:Type — — rozszerzenie znaczników](../xaml-services/xtype-markup-extension.md)
- [StaticResource — Rozszerzenie znaczników](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [DynamicResource — — Rozszerzenie znaczników](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
