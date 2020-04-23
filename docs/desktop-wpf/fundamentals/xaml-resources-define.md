---
title: Definiowanie zasobów XAML
description: Dowiedz się więcej o zasobach XAML w WPF dla platformy .NET Core. Poznaj typy zasobów XAML i dowiedz się, jak zdefiniować zasoby XAML.
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
# <a name="overview-of-xaml-resources"></a>Omówienie zasobów XAML

Zasób jest obiektem, który można ponownieżyć w różnych miejscach w aplikacji. Przykładami zasobów są pędzle i style. W tym opisie opisano sposób używania zasobów w języku XAML (Extensible Application Markup Language). Można również tworzyć i uzyskiwać dostęp do zasobów przy użyciu kodu.

> [!NOTE]
> Zasoby XAML opisane w tym artykule różnią się od *zasobów aplikacji,* które są zazwyczaj plikami dodawanymi do aplikacji, takimi jak zawartość, dane lub osadzone pliki.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Korzystanie z zasobów w języku XAML

Poniższy przykład definiuje <xref:System.Windows.Media.SolidColorBrush> jako zasób na elemencie głównym strony. W przykładzie odwołuje się do zasobu i używa go do <xref:System.Windows.Shapes.Ellipse>ustawiania <xref:System.Windows.Controls.TextBlock>właściwości <xref:System.Windows.Controls.Button>kilku elementów podrzędnych, w tym , a , i .

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Każdy element na<xref:System.Windows.FrameworkElement> poziomie <xref:System.Windows.FrameworkContentElement>struktury <xref:System.Windows.FrameworkElement.Resources%2A> ( lub ) <xref:System.Windows.ResourceDictionary> ma właściwość, która jest typem, który zawiera zdefiniowane zasoby. Zasoby można zdefiniować na dowolnym <xref:System.Windows.Controls.Button>elemencie, takim jak . Jednak zasoby są najczęściej definiowane w elemencie głównym, który znajduje <xref:System.Windows.Controls.Page> się w przykładzie.

Każdy zasób w słowniku zasobów musi mieć unikatowy klucz. Podczas definiowania zasobów w znacznikach, należy przypisać unikatowy klucz za pośrednictwem [x:Key Dyrektywy](../xaml-services/xkey-directive.md). Zazwyczaj klucz jest ciągiem; jednak można również ustawić go do innych typów obiektów przy użyciu odpowiednich rozszerzeń znaczników. Klucze inne niż ciągi zasobów są używane przez niektóre obszary obiektów w WPF, w szczególności dla stylów, zasobów składników i stylów danych.

Zdefiniowanego zasobu można użyć ze składnią rozszerzenia znaczników zasobów, która określa nazwę klucza zasobu. Na przykład użyj zasobu jako wartości właściwości na inny element.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

W poprzednim przykładzie, gdy moduł ładujący XAML <xref:System.Windows.Controls.Control.Background%2A> przetwarza <xref:System.Windows.Controls.Button>wartość `{StaticResource MyBrush}` właściwości na , logika wyszukiwania <xref:System.Windows.Controls.Button> zasobów najpierw sprawdza słownik zasobów dla elementu. Jeśli <xref:System.Windows.Controls.Button> nie ma definicji klucza `MyBrush` zasobu (w tym przykładzie nie; jego kolekcja zasobów jest pusta), wyszukiwanie następnie sprawdza element nadrzędny <xref:System.Windows.Controls.Button>, który jest <xref:System.Windows.Controls.Page>. Jeśli zdefiniujesz <xref:System.Windows.Controls.Page> zasób na elemencie głównym, wszystkie elementy w drzewie logicznym <xref:System.Windows.Controls.Page> mogą uzyskać do niego dostęp. I można ponownie użyć tego samego zasobu do ustawiania wartości dowolnej właściwości, która akceptuje tego samego typu, który reprezentuje zasób. W poprzednim przykładzie `MyBrush` ten sam zasób <xref:System.Windows.Controls.Control.Background%2A> ustawia <xref:System.Windows.Controls.Button>dwie różne <xref:System.Windows.Shapes.Shape.Fill%2A> właściwości: a i . <xref:System.Windows.Shapes.Rectangle>

## <a name="static-and-dynamic-resources"></a>Zasoby statyczne i dynamiczne

Zasób można odwoływać się jako statyczne lub dynamiczne. Odwołania są tworzone przy użyciu [rozszerzenia znaczników StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) lub [rozszerzenia znaczników DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Rozszerzenie znaczników jest funkcją XAML, która umożliwia określenie odwołania do obiektu przez przetworzenie rozszerzenia znaczników ciągu atrybutu i zwrócenie obiektu do modułu ładującego XAML. Aby uzyskać więcej informacji na temat zachowania rozszerzenia [znaczników, zobacz Rozszerzenia znaczników i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Korzystając z rozszerzenia znaczników, zazwyczaj należy podać jeden lub więcej parametrów w formie ciągu, które są przetwarzane przez to rozszerzenie znaczników. [Rozszerzenie znaczników StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) przetwarza klucz, wyszukując wartość tego klucza we wszystkich dostępnych słownikach zasobów. Przetwarzanie odbywa się podczas ładowania, czyli gdy proces ładowania musi przypisać wartość właściwości. [Rozszerzenie znaczników DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) zamiast przetwarza klucz, tworząc wyrażenie, a wyrażenie to pozostaje nieocenione do momentu uruchomieniu aplikacji, w którym to czasie wyrażenie jest oceniane i zapewnia wartość.

Podczas odwoływania się do zasobu następujące zagadnienia mogą mieć wpływ na to, czy używasz odwołania do zasobu statycznego, czy dynamicznego zasobu:

- Podczas określania ogólnego projektu sposobu tworzenia zasobów dla aplikacji (na stronę, w aplikacji, w luźnym xaml lub w zestawie tylko do zasobów), należy wziąć pod uwagę następujące kwestie:

- Funkcjonalność aplikacji. Czy aktualizowanie zasobów w czasie rzeczywistym jest częścią wymagań aplikacji?
- Odpowiednie zachowanie wyszukiwania tego typu odwołania do zasobu.
- Określona właściwość lub typ zasobu i zachowanie macierzyste tych typów.

## <a name="static-resources"></a>Zasoby statyczne

Odwołania do zasobów statycznych działają najlepiej w następujących okolicznościach:

- Projekt aplikacji koncentruje większość swoich zasobów w słownikach zasobów na poziomie strony lub aplikacji. Odwołania do zasobów statycznych nie są ponownie wycenialne na podstawie zachowań środowiska wykonawczego, takich jak ponowne ładowanie strony. Dlatego może być pewne korzyści wydajności, aby uniknąć dużej liczby odwołań do zasobów dynamicznych, gdy nie są one konieczne na podstawie projektu zasobów i aplikacji.

- Ustawiasz wartość właściwości, która nie znajduje się <xref:System.Windows.DependencyObject> na <xref:System.Windows.Freezable>lub .

- Tworzysz słownik zasobów, który zostanie skompilowany do biblioteki DLL i spakowany jako część aplikacji lub udostępniony między aplikacjami.

- Tworzysz motyw dla formantu niestandardowego i definiujesz zasoby, które są używane w motywach. W tym przypadku zazwyczaj nie chcesz dynamicznego zachowania wyszukiwania odwołania do zasobu; Zamiast tego chcesz zachowanie odwołania do zasobów statycznych, tak aby wyszukiwanie jest przewidywalne i samodzielne dla motywu. W przypadku odwołania do zasobu dynamicznego nawet odwołanie w motywie pozostaje nieocenione do czasu wykonywania. i istnieje szansa, że gdy motyw jest stosowany, jakiś element lokalny będzie przedefiniować klucz, który twój motyw próbuje odwołać, a element lokalny spadnie przed samym tematem w odnośnikach. Jeśli tak się stanie, twój motyw nie będzie zachowywał się zgodnie z oczekiwaniami.

- Używasz zasobów, aby ustawić dużą liczbę właściwości zależności. Właściwości zależności mają efektywne buforowanie wartości, jak włączone przez system właściwości, więc jeśli podasz wartość dla właściwości zależności, które mogą być oceniane w czasie ładowania, właściwość zależności nie musi sprawdzać ponownie ocenione wyrażenie i może zwrócić ostatnią wartość efektywną. Ta technika może być korzyścią dla wydajności.

- Chcesz zmienić zasób bazowy dla wszystkich odbiorców lub chcesz zachować oddzielne zapisywalne wystąpienia dla każdego konsumenta przy użyciu [atrybutu x:Shared](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Zachowanie wyszukiwania zasobów statycznych

Poniżej opisano proces odnośnia, który automatycznie odbywa się, gdy zasób statyczny odwołuje się do właściwości lub elementu:

01. Proces odnośnia sprawdza żądany klucz w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość.

01. Następnie proces wyszukiwania przechodzi przez drzewo logiczne w górę do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany, dopóki nie zostanie osiągnięty element główny.

01. Zasoby aplikacji są sprawdzane. Zasoby aplikacji są te zasoby w słowniku <xref:System.Windows.Application> zasobów, który jest zdefiniowany przez obiekt dla aplikacji WPF.

Odwołania do zasobów statycznych z poziomu słownika zasobów muszą odwoływać się do zasobu, który został już zdefiniowany leksykowo przed odwołaniem do zasobu. Odwołania do przekazywania nie mogą być rozpoznawane przez odwołanie do zasobu statycznego. Z tego powodu zaprojektuj strukturę słownika zasobów w taki sposób, aby zasoby były definiowane na początku każdego słownika zasobów lub w jego pobliżu.

Statyczne wyszukiwanie zasobów można rozszerzyć na motywy lub do zasobów systemowych, ale to wyszukiwanie jest obsługiwane tylko dlatego, że moduł ładujący XAML odracza żądanie. Odroczenie jest konieczne, aby motyw środowiska wykonawczego w momencie ładowania strony stosuje się prawidłowo do aplikacji. Jednak odwołania do zasobów statycznych do kluczy, o których wiadomo, że istnieją tylko w motywach lub jako zasoby systemowe, nie są zalecane, ponieważ takie odwołania nie są ponownie ocenione, jeśli motyw zostanie zmieniony przez użytkownika w czasie rzeczywistym. Dynamiczne odwołanie do zasobu jest bardziej niezawodne, gdy żądasz motywu lub zasobów systemowych. Wyjątek jest, gdy element tematu sam żąda innego zasobu. Odwołania te powinny być statyczne odwołania do zasobów, z powodów wymienionych wcześniej.

Zachowanie wyjątku, jeśli nie znaleziono odwołania do zasobu statycznego, jest różna. Jeśli zasób został odroczony, wyjątek występuje w czasie wykonywania. Jeśli zasób nie został odroczony, wyjątek występuje w czasie ładowania.

## <a name="dynamic-resources"></a>Zasoby dynamiczne

Zasoby dynamiczne działają najlepiej, gdy:

- Wartość zasobu, w tym zasobów systemowych lub zasobów, które w przeciwnym razie można ustawić przez użytkownika, zależy od warunków, które nie są znane do czasu uruchomienia. Na przykład można utworzyć wartości ustawiacza, które odwołują się do właściwości systemu jako udostępniane przez <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>lub <xref:System.Windows.SystemParameters>. Te wartości są naprawdę dynamiczne, ponieważ ostatecznie pochodzą ze środowiska wykonawczego użytkownika i systemu operacyjnego. Może również mieć motywy na poziomie aplikacji, które można zmienić, gdzie dostęp do zasobów na poziomie strony musi również przechwycić zmiany.

- Tworzysz lub odwołujesz się do stylów motywu dla formantu niestandardowego.

- Zamierzasz dostosować zawartość <xref:System.Windows.ResourceDictionary> a w okresie istnienia aplikacji.

- Masz skomplikowaną strukturę zasobów, która ma współzależności, gdzie może być wymagane odwołanie do przodu. Odwołania do zasobów statycznych nie obsługują odwołań do przodu, ale odwołania do zasobów dynamicznych obsługują je, ponieważ zasób nie musi być oceniany do czasu środowiska uruchomieniowego, a odwołania do przodu nie są zatem odpowiednią koncepcją.

- Odwołujesz się do zasobu, który jest duży z punktu widzenia zestawu kompilacji lub pracy, a zasób może nie być używany natychmiast po załadowaniu strony. Odwołania do zasobów statycznych zawsze ładują się z XAML po załadowaniu strony. Jednak odwołanie do zasobu dynamicznego nie ładuje się, dopóki nie jest używane.

- Tworzysz styl, w którym wartości ustawiające mogą pochodzić z innych wartości, na które mają wpływ motywy lub inne ustawienia użytkownika.

- Stosujesz zasoby do elementów, które mogą być ponownie wynajęta w drzewie logicznym w okresie istnienia aplikacji. Zmiana elementu nadrzędnego również potencjalnie zmienia zakres wyszukiwania zasobów, więc jeśli chcesz, aby zasób dla elementu rearented miał zostać ponownie oceniony na podstawie nowego zakresu, należy zawsze używać dynamicznego odwołania do zasobu.

### <a name="dynamic-resource-lookup-behavior"></a>Dynamiczne zachowanie wyszukiwania zasobów

Zachowanie wyszukiwania zasobów dla odwołania do zasobu dynamicznego jest równoległe do zachowania odnośnika w kodzie, jeśli wywołasz <xref:System.Windows.FrameworkElement.FindResource%2A> lub: <xref:System.Windows.FrameworkElement.SetResourceReference%2A>

01. Wyszukiwanie sprawdza żądany klucz w słowniku zasobów zdefiniowanym przez element, który ustawia właściwość:

    - Jeśli element definiuje <xref:System.Windows.FrameworkElement.Style%2A> właściwość, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> element ma <xref:System.Windows.Style.Resources> jego słownika zaznaczone.

    - Jeśli element definiuje <xref:System.Windows.Controls.Control.Template%2A> właściwość, <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> słownik elementu jest sprawdzany.

01. Wyszukiwanie przechodzi przez drzewo logiczne w górę do elementu nadrzędnego i jego słownika zasobów. Ten proces jest kontynuowany, dopóki nie zostanie osiągnięty element główny.

01. Zasoby aplikacji są sprawdzane. Zasoby aplikacji są te zasoby w słowniku <xref:System.Windows.Application> zasobów, które są zdefiniowane przez obiekt dla aplikacji WPF.

01. Słownik zasobów motywu jest sprawdzany pod kątem aktualnie aktywnego motywu. Jeśli motyw zmieni się w czasie wykonywania, wartość jest ponownie wyceniana.

01. Zasoby systemowe są sprawdzane.

Zachowanie wyjątku (jeśli istnieje) różni się:

- Jeśli zasób został <xref:System.Windows.FrameworkElement.FindResource%2A> poproszony przez wywołanie i nie został znaleziony, wyjątek.

- Jeśli zasób został <xref:System.Windows.FrameworkElement.TryFindResource%2A> poproszony przez wywołanie i nie został znaleziony, `null`nie jest zgłaszany wyjątek, a zwracana wartość jest . Jeśli ustawiona właściwość nie `null`akceptuje , to nadal jest możliwe, że zostanie zgłoszony głębszy wyjątek, w zależności od ustawionej pojedynczej właściwości.

- Jeśli zasób został poproszony przez odwołanie do zasobu dynamicznego w XAML i nie został znaleziony, zachowanie zależy od ogólnego systemu właściwości. Ogólne zachowanie jest tak, jakby żadna operacja ustawiania właściwości nie wystąpiła na poziomie, na którym istnieje zasób. Na przykład jeśli spróbujesz ustawić tło na pojedynczy element przycisku przy użyciu zasobu, który nie może być oceniony, a następnie nie ma wyników zestawu wartości, ale wartość efektywna może nadal pochodzić od innych uczestników w systemie właściwości i pierwszeństwo wartości. Na przykład wartość tła może nadal pochodzić z lokalnie zdefiniowanego stylu przycisku lub ze stylu motywu. Dla właściwości, które nie są zdefiniowane przez style motywu, wartość efektywna po nieudanej oceny zasobów może pochodzić z wartości domyślnej w metadanych właściwości.

### <a name="restrictions"></a>Ograniczenia

Odwołania do zasobów dynamicznych mają pewne znaczące ograniczenia. Musi być spełniony co najmniej jeden z następujących warunków:

- Właściwość, która jest ustawiona, musi być właściwością <xref:System.Windows.FrameworkElement> na lub . <xref:System.Windows.FrameworkContentElement> Ta właściwość musi <xref:System.Windows.DependencyProperty>być poparta przez .

- Odwołanie jest dla wartości `StyleSetter`w .

- Właściwość, <xref:System.Windows.Freezable> która jest ustawiona musi być właściwość na, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> który jest <xref:System.Windows.Setter> dostarczany jako wartość lub właściwości lub wartości.

Ponieważ ustawiona właściwość <xref:System.Windows.DependencyProperty> musi <xref:System.Windows.Freezable> być lub właściwości, większość zmian właściwości może propagować do interfejsu użytkownika, ponieważ zmiana właściwości (zmieniona wartość zasobu dynamicznego) jest potwierdzana przez system właściwości. Większość formantów zawiera logikę, która <xref:System.Windows.DependencyProperty> wymusi inny układ formantu, jeśli zmiany i ta właściwość może mieć wpływ na układ. Jednak nie wszystkie właściwości, które mają [Rozszerzenie znaczników DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) jako ich wartość są gwarantowane do zapewnienia aktualizacji w czasie rzeczywistym w interfejsie użytkownika. Ta funkcja nadal może się różnić w zależności od właściwości, a także w zależności od typu, który jest właścicielem właściwości lub nawet logicznej struktury aplikacji.

## <a name="styles-datatemplates-and-implicit-keys"></a>Style, tablice danych i klucze niejawne

Chociaż wszystkie elementy <xref:System.Windows.ResourceDictionary> w musi mieć klucz, to nie znaczy, `x:Key`że wszystkie zasoby muszą mieć jawne . Kilka typów obiektów obsługuje klucz niejawny, gdy jest zdefiniowany jako zasób, gdzie wartość klucza jest powiązana z wartością innej właściwości. Ten typ klucza jest znany jako klucz `x:Key` niejawny, podczas gdy atrybut jest kluczem jawnym. Można zastąpić dowolny klucz niejawny, określając jawny klucz.

Jednym z ważnych scenariuszy dla <xref:System.Windows.Style>zasobów jest podczas definiowania . W rzeczywistości <xref:System.Windows.Style> a jest prawie zawsze zdefiniowane jako wpis w słowniku zasobów, ponieważ style są z natury przeznaczone do ponownego użycia. Aby uzyskać więcej informacji o stylach, zobacz [Stylowanie i tworzenie szablonów](styles-templates-overview.md).

Style formanty mogą być tworzone z kluczem niejawnym i do których się odwołują. Style motywu, które definiują domyślny wygląd formantu, opierają się na tym kluczu niejawnym. Z punktu widzenia żądania go, klucz niejawny <xref:System.Type> jest sam formantu. Z punktu widzenia definiowania zasobów klucz niejawny <xref:System.Windows.Style.TargetType%2A> jest stylu. W związku z tym w przypadku tworzenia motywów dla formantów niestandardowych lub tworzenia stylów, które współdziałają z istniejącymi stylami motywu, nie trzeba określać [x:Key Dyrektywy](../xaml-services/xkey-directive.md) dla tego <xref:System.Windows.Style>. A jeśli chcesz używać stylów tematowych, nie musisz w ogóle określać żadnego stylu. Na przykład działa następująca definicja <xref:System.Windows.Style> stylu, nawet jeśli zasób nie wydaje się mieć klucza:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Ten styl naprawdę ma klucz: `typeof(System.Windows.Controls.Button)`klucz niejawny . W znacznikach można określić <xref:System.Windows.Style.TargetType%2A> bezpośrednio jako nazwę typu (lub opcjonalnie użyć [{x:Type...}](../xaml-services/xtype-markup-extension.md) , aby <xref:System.Type>zwrócić plik .

Za pomocą mechanizmów stylu motywu domyślnego używanego przez WPF, <xref:System.Windows.Controls.Button> ten styl jest <xref:System.Windows.Controls.Button> stosowany jako styl środowiska <xref:System.Windows.FrameworkElement.Style%2A> wykonawczego na stronie, mimo że sam nie próbuje określić jego właściwości lub określonego odwołania do zasobu do stylu. Styl zdefiniowany na stronie znajduje się wcześniej w sekwencji odnośna niż styl słownika motywu, przy użyciu tego samego klucza, który ma styl słownika motywu. Możesz po `<Button>Hello</Button>` prostu określić w dowolnym miejscu <xref:System.Windows.Style.TargetType%2A> na `Button` stronie, a styl, który został zdefiniowany, będzie miał zastosowanie do tego przycisku. Jeśli chcesz, nadal można jawnie klucz styl z <xref:System.Windows.Style.TargetType%2A> tej samej wartości typu, jak dla jasności w znacznikach, ale jest to opcjonalne.

Klucze niejawne dla stylów <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> `true`nie mają zastosowania do formantu, jeśli jest . (Należy również <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> zauważyć, że może być ustawiona jako część zachowania macierzystego dla klasy formantu, a nie jawnie na wystąpienie formantu.) Ponadto w celu obsługi kluczy niejawnych dla scenariuszy klasy <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> pochodnej, formant musi zastąpić (wszystkie istniejące formanty dostarczone jako część WPF obejmują to zastąpienie). Aby uzyskać więcej informacji na temat stylów, motywów i projektowania formantu, zobacz [Wskazówki dotyczące projektowania formantów stylizujących](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>posiada również klucz niejawny. Klucz niejawny dla <xref:System.Windows.DataTemplate> a <xref:System.Windows.DataTemplate.DataType%2A> jest wartość właściwości. <xref:System.Windows.DataTemplate.DataType%2A>można również określić jako nazwę typu, a nie jawnie używając [{x:Type...}](../xaml-services/xtype-markup-extension.md). Aby uzyskać szczegółowe informacje, zobacz [Omówienie tworzenia szablonów danych](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.ResourceDictionary>
- [Zasoby aplikacji](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Zasoby i kod](../../framework/wpf/advanced/resources-and-code.md)
- [Definiowanie i odwoływanie się do zasobu](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Omówienie zarządzania aplikacjami](../../framework/wpf/app-development/application-management-overview.md)
- [x:Wpisz rozszerzenie znaczników](../xaml-services/xtype-markup-extension.md)
- [Rozszerzenie znaczników StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [Rozszerzenie znaczników DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
