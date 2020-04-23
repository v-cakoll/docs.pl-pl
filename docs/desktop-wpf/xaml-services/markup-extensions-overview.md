---
title: Rozszerzenia znaczników dla przeglądu XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: c0ca8e7d0d68d4730173385540cbcec66c7bf03a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071718"
---
# <a name="overview-of-markup-extensions-for-xaml"></a>Omówienie rozszerzeń znaczników dla XAML

Rozszerzenia znaczników są techniką XAML w celu uzyskania wartości, która nie jest pierwotnym lub określonym typem XAML. W przypadku użycia atrybutu rozszerzenia znaczników używają znanej sekwencji `{` znaków otwierającego nawiasu klamrowego, aby wprowadzić `}` zakres rozszerzenia znaczników, i zamykającego nawias klamrowy do zakończenia. Korzystając z usług .NET XAML, można użyć niektórych wstępnie zdefiniowanych rozszerzeń znaczników języka XAML z zestawu System.Xaml. Można również podklasy z klasy zdefiniowanej <xref:System.Windows.Markup.MarkupExtension> w System.Xaml i zdefiniować własne rozszerzenia znaczników. Lub można użyć rozszerzenia znaczników zdefiniowane przez określoną strukturę, jeśli już odwołujesz się do tej struktury.

Gdy uzyskuje się dostęp do rozszerzenia znaczników, moduł zapisujący obiekt <xref:System.Windows.Markup.MarkupExtension> XAML może świadczyć usługi do klasy niestandardowej za pośrednictwem punktu połączenia usługi w <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> zastąpieniu. Usługi mogą służyć do uzyskiwania kontekstu dotyczące użycia, określonych możliwości modułu zapisującego obiekt, kontekstu schematu XAML i tak dalej.

## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane przez XAML

Kilka rozszerzeń znaczników są implementowane przez usługi .NET XAML dla obsługi języka XAML. Te rozszerzenia znaczników odpowiadają części specyfikacji XAML jako języka. Są one zazwyczaj identyfikowalne przez `x:` prefiks w składni, jak widać w typowym użyciu. Implementacje usług .NET XAML services dla tych elementów języka XAML pochodzą z klasy podstawowej. <xref:System.Windows.Markup.MarkupExtension>

> [!NOTE]
> `x:` Prefiks jest używany do typowego mapowania przestrzeni nazw XAML obszaru nazw języka XAML w elemencie głównym produkcji XAML. Na przykład projekt programu Visual Studio i szablony stron dla różnych określonych `x:` struktur inicjują plik XAML przy użyciu tego mapowania. Można wybrać inny token prefiksu w mapowaniu przestrzeni nazw XAML, ale w tej dokumentacji przyjęto domyślne `x:` mapowanie jako sposób identyfikacji tych jednostek, które są zdefiniowaną częścią przestrzeni nazw XAML języka XAML języka XAML, w przeciwieństwie do domyślnej przestrzeni nazw XAML określonej struktury lub innych dowolnych obszarów nazw CLR lub XML.

### <a name="xtype"></a>x:Typ

`x:Type`dostarcza <xref:System.Type> obiekt dla nazwanego typu. Ta funkcja jest najczęściej używana w mechanizmach odroczenia, które używają podstawowych typu i typu CLR wyprowadzania jako monikera grupowania lub identyfikatora. Style i szablony WPF i `TargetType` ich użycie właściwości są określonym przykładem. Aby uzyskać więcej informacji, zobacz [x:Wpisz rozszerzenie znaczników](xtype-markup-extension.md).

### <a name="xstatic"></a>x:Statyczne

`x:Static`tworzy wartości statyczne z jednostek kodu typu wartości, które nie są bezpośrednio typem wartości właściwości, ale mogą być oceniane do tego typu. Jest to przydatne do określania wartości, które już istnieją jako dobrze znane stałe w definicji typu. Aby uzyskać więcej informacji, zobacz [x:Static Markup Extension](xstatic-markup-extension.md).

### <a name="xnull"></a>x:Wartość null

`x:Null`określa `null` jako wartość dla elementu członkowskiego XAML. W zależności od projektu określonych typów lub `null` większych pojęć framework, nie zawsze jest wartością domyślną dla właściwości lub dorozumianą wartość atrybutu pusty ciąg. Aby uzyskać więcej informacji, zobacz [x:Null Markup Extension](xnull-markup-extension.md).

### <a name="xarray"></a>x:Tablica

`x:Array`obsługuje tworzenie tablic ogólnych w składni XAML w przypadkach, gdy obsługa kolekcji, która jest dostarczana przez podstawowe elementy i modele kontroli nie jest celowo używany. Aby uzyskać więcej informacji, zobacz [x:Array Markup Extension](xarray-markup-extension.md). W XAML 2009 w szczególności tablice są dostępne jako podstawowe języka, a nie jako rozszerzenie. Aby uzyskać więcej informacji, zobacz [Funkcje języka XAML 2009](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Odwołanie

`x:Reference`jest częścią XAML 2009, rozszerzenia oryginalnego (2006) zestawu językowego. `x:Reference`reprezentuje odwołanie do innego istniejącego obiektu na wykresie obiektu. Ten obiekt jest identyfikowany przez jego `x:Name`. Aby uzyskać więcej informacji, zobacz [x:Reference Markup Extension](xreference-markup-extension.md).

### <a name="other-x-constructs"></a>Inne x: Konstrukcje

Istnieją `x:` inne konstrukcje do obsługi funkcji języka XAML, ale nie są one implementowane jako rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [obszar nazw XAML (x:) Funkcje językowe](namespace-language-features.md).

## <a name="the-markupextension-base-class"></a>Klasa podstawowa Naciśnienia znaczników

Aby zdefiniować niestandardowe rozszerzenie znaczników, które może wchodzić w interakcje z domyślnymi implementacjami czytników XAML <xref:System.Windows.Markup.MarkupExtension> i modułów zapisujących XAML w systemie.Xaml, należy wyprowadzić klasę z klasy abstrakcyjnej. Ta klasa ma jedną metodę zastąpienia, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>która jest . Może być również konieczne zdefiniowanie dodatkowych konstruktorów do obsługi argumentów do użycia rozszerzenia znaczników i pasujące właściwości settable.

Through <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, niestandardowe rozszerzenie znaczników ma dostęp do kontekstu usługi, który raportuje środowisko, w którym rozszerzenie znaczników jest wywoływane przez procesor XAML. W ścieżce obciążenia jest to <xref:System.Xaml.XamlObjectWriter>zazwyczaj plik . W ścieżce zapisywania jest <xref:System.Xaml.XamlXmlWriter>to zazwyczaj plik . Każdy raport kontekstu usługi jako wewnętrznej klasy kontekstu dostawcy usług XAML, który implementuje wzorzec dostawcy usług. Aby uzyskać więcej informacji na temat dostępnych usług i ich reprezentujących, zobacz [Konwertery typów i Rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

Klasa rozszerzenia znaczników musi używać poziomu dostępu publicznego; Procesory XAML zawsze muszą mieć możliwość wystąpienia klasy pomocy technicznej rozszerzenia znaczników, aby móc korzystać z jego usług.

## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definiowanie typu pomocy technicznej dla niestandardowego rozszerzenia znaczników

Korzystając z usług .NET XAML Services lub struktur, które opierają się na usługach .NET XAML, masz dwie możliwości, jak nadać nazwę typu obsługi rozszerzenia znaczników. Nazwa typu jest odpowiednia dla sposobu, w jaki moduły zapisu obiektów XAML próbują uzyskać dostęp i wywołać typ obsługi rozszerzenia znaczników, gdy napotkają użycie rozszerzenia znaczników w języku XAML. Użyj jednej z następujących strategii nazewnictwa:

- Nazwij nazwę typu, która ma być dokładnie zgodna z tokenem użycia znaczników XAML. Na przykład, aby `{Collate ...}` obsługiwać użycie rozszerzenia, nazwij typ `Collate`pomocy technicznej .
- Nazwij nazwę typu tokenem ciągu użycia `Extension`plus sufiks . Na przykład, aby `{Collate ...}` obsługiwać użycie rozszerzenia, nazwij typ `CollateExtension`pomocy technicznej .

Kolejność wyszukiwania jest najpierw wyszukać `Extension`nazwę klasy sufiksów, a następnie `Extension` poszukać nazwy klasy bez sufiksu.

Z punktu widzenia użycia znaczników, w tym sufiks `Extension` jako część użycia jest prawidłowy. Jednak to zachowuje się `Extension` tak, jakby jest naprawdę częścią nazwy klasy i autorzy obiektów XAML nie można rozpoznać klasy `Extension` obsługi rozszerzenia znaczników dla tego użycia, jeśli klasa pomocy technicznej nie ma sufiksu.

### <a name="the-parameterless-constructor"></a>Konstruktor bez parametrów

Dla wszystkich typów obsługi rozszerzenia znaczników należy udostępnić publiczny konstruktor bez parametrów. Konstruktor bez parametrów jest wymagany w każdym przypadku, gdy moduł zapisujący obiekt XAML tworzy wystąpienie rozszerzenia znaczników z użycia elementu obiektu. Obsługa użycia elementu obiektu jest uczciwe oczekiwanie dla rozszerzenia znaczników, szczególnie dla serializacji. Można jednak zaimplementować rozszerzenie znaczników bez konstruktora publicznego, jeśli zamierzasz obsługiwać tylko użycie atrybutów rozszerzenia znaczników.

Jeśli użycie rozszerzenia znaczników nie ma żadnych argumentów, konstruktor bez parametrów jest wymagany do obsługi użycia.

## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Szyki konstruktora i argumenty pozycyjne dla niestandardowego rozszerzenia znaczników

Dla rozszerzenia znaczników z zamierzonego użycia argumentu konstruktory publiczne muszą odpowiadać trybom zamierzonego użycia. Innymi słowy, jeśli rozszerzenie znaczników jest przeznaczony do wymagają jednego argumentu pozycyjnego jako prawidłowe użycie, należy obsługiwać konstruktora publicznego z jednego parametru wejściowego, który przyjmuje argument pozycyjny.

Załóżmy na `Collate` przykład, że rozszerzenie znaczników jest przeznaczone do obsługi tylko trybu, w `CollationMode` którym istnieje jeden argument pozycyjny reprezentujący jego tryb, określony jako stała wyliczania. W takim przypadku powinien istnieć konstruktor z następującym formularzem:

```csharp
public Collate(CollationMode collationMode) {...}
```

Na poziomie podstawowym argumenty przekazywane do rozszerzenia znaczników są ciągiem, ponieważ są przekazywane z wartości atrybutów znaczników. Można wykonać wszystkie ciągi argumentów i pracować z danymi wejściowymi na tym poziomie. Jednak masz dostęp do niektórych przetwarzania, które występuje przed argumenty rozszerzenia znaczników są przekazywane do klasy obsługi.

Przetwarzanie działa koncepcyjnie tak, jakby rozszerzenie znaczników jest obiektem, który ma zostać utworzony, a następnie jego wartości członkowskie są ustawiane. Każda określona właściwość do ustawionego jest oceniana podobnie do tego, jak określony element członkowski może być ustawiony na utworzonym obiekcie podczas analizowanie XAML. Istnieją dwie ważne różnice:

- Jak wspomniano wcześniej, typ obsługi rozszerzenia znaczników nie musi mieć konstruktora bez parametrów, aby można było utworzyć wystąpienie w języku XAML. Jego konstrukcja obiektu jest odroczona, dopóki jego możliwe argumenty w składni tekstu są tokenizowane i oceniane jako argumenty pozycyjne lub nazwane, a odpowiedni konstruktor jest wywoływany w tym czasie.
- Rozszerzenia znaczników użycia mogą być zagnieżdżone. Rozszerzenie narzutów wewnętrznych jest oceniane jako pierwsze. W związku z tym można założyć takie użycie i zadeklarować jeden z parametrów konstrukcji jako typ, który wymaga konwertera wartości (na przykład rozszerzenie znaczników) do produkcji.

W poprzednim przykładzie pokazano zależność od takiego przetwarzania. Program .NET XAML Services XAML modułu zapisującego obiekt przetwarza stałe nazwy wyliczania na wyliczone wartości na poziomie macierzystym.

Przetwarzanie składni tekstowej parametru pozycyjnego rozszerzenia znaczników może również polegać na konwerterze typów skojarzonym z typem, który znajduje się w argurze konstrukcyjnym.

Argumenty są nazywane argumentami pozycyjnymi, ponieważ kolejność napotkania tokenów w użyciu odpowiada kolejności pozycyjnej parametru konstruktora, do którego są przypisane. Rozważmy na przykład następującą sygnaturę konstruktora:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Procesor XAML oczekuje dwóch argumentów pozycyjnych dla tego rozszerzenia znaczników. Jeśli było użycie `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` token jest wysyłany do pierwszego `CollationMode` parametru i oceniane jako wyliczenie o nazwie stała. Wynik wewnętrznego `x:Reference` jest wysyłany do drugiego parametru i oceniany jako obiekt.

W xaml określonych reguł dla składni rozszerzenia znaczników i przetwarzania przecinek jest ogranicznik między argumentami, czy te argumenty są argumenty pozycyjne lub argumenty nazwane.

### <a name="duplicate-arity-of-positional-arguments"></a>Powielanie argumentów pozycyjnych

Jeśli moduł zapisujący obiekt XAML napotka użycie rozszerzenia znaczników z argumentami pozycyjnymi i istnieje wiele argumentów konstruktora, które przyjmują tę liczbę argumentów (duplikat arity), niekoniecznie jest to błąd. Zachowanie zależy od dostosowywanego ustawienia kontekstu schematu XAML, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Jeśli <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `true`tak jest , moduł zapisujący obiekt XAML nie powinien zgłaszać wyjątku tylko ze względu na zduplikowane arity. Zachowanie poza tym punktem nie jest ściśle zdefiniowane. Podstawowe założenie projektu jest, że kontekst schematu ma informacje o typie dostępne dla określonych parametrów i można spróbować jawnych rzutowania, które pasują do zduplikowanych kandydatów, aby zobaczyć, który podpis może być najlepszym rozwiązaniem. Wyjątek może być nadal zgłaszany, jeśli żadne podpisy nie mogą przekazywać testów, które są nakładane przez ten kontekst określonego schematu, który jest uruchomiony na modułu zapisującego obiekt XAML.

Domyślnie <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> znajduje `false` się w programie <xref:System.Xaml.XamlSchemaContext> CLR dla usług XAML .NET. W związku <xref:System.Xaml.XamlObjectWriter> z tym domyślne zgłasza wyjątki, jeśli napotka użycie rozszerzenia znaczników, gdzie istnieje duplikat arity w konstruktorów typu kopii zapasowej.

## <a name="named-arguments-for-a-custom-markup-extension"></a>Nazwane argumenty dla niestandardowego rozszerzenia znaczników

Rozszerzenia znaczników określone przez XAML można również użyć nazwanego formularza argumentów do użycia. Na pierwszym poziomie tokenizacji składnia tekstu jest podzielona na argumenty. Obecność znaku równości (=) w dowolnym argum identyfikuje argument jako argument nazwany. Taki argument jest również tokenized do pary nazwa/wartość. Nazwa w tym przypadku nazwy publicznej settable właściwości typu obsługi rozszerzenia znaczników. Jeśli zamierzasz obsługiwać użycie argumentu o nazwie, należy podać te właściwości publicznej settable. Właściwości mogą być dziedziczone właściwości tak długo, jak pozostają one publiczne.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenia znaczników

Dostępne usługi są takie same dla każdego konwertera wartości. Różnica polega na tym, jak każdy konwerter wartości odbiera kontekst usługi. Dostęp do usług i dostępnych usług są udokumentowane w temacie [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

## <a name="property-element-usage-of-a-markup-extension"></a>Użycie elementu właściwości rozszerzenia znaczników

Scenariusze użycia rozszerzenia znaczników są często zaprojektowane wokół przy użyciu rozszerzenia znaczników w użyciu atrybutu. Jednak jest również potencjalnie możliwe do zdefiniowania klasy kopii do obsługi użycia elementu właściwości.

Aby obsługiwać użycie elementu właściwości rozszerzenia znaczników, zdefiniuj konstruktora bez parametrów publicznych. Powinien to być konstruktor wystąpienia, a nie konstruktor statyczny. Jest to wymagane, ponieważ procesor XAML musi ogólnie wywołać konstruktora bez parametrów na dowolny element obiektu przetwarza z znaczników, a to obejmuje klasy rozszerzenia znaczników jako elementy obiektu. W przypadku scenariuszy zaawansowanych można zdefiniować ścieżki budowy nieobe domyślnie dla klas. (Aby uzyskać więcej informacji, zobacz [x:FactoryMethod Dyrektywy](xfactorymethod-directive.md).) Jednak nie należy używać tych wzorców do celów rozszerzenia znaczników, ponieważ to sprawia, że odnajdywanie wzorca użycia znacznie trudniejsze, zarówno dla projektantów, jak i dla użytkowników nieprzetworzonych znaczników.

## <a name="attributing-for-a-custom-markup-extension"></a>Przypisywanie niestandardowego rozszerzenia znaczników

Aby obsługiwać zarówno środowiska projektowe, jak i niektóre scenariusze modułu zapisującego obiekt XAML, należy przypisać typ obsługi rozszerzenia znaczników z kilkoma atrybutami CLR. Te atrybuty zgłaszają zamierzone użycie rozszerzenia znaczników.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>raportuje <xref:System.Type> informacje dla typu <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> obiektu, który zwraca. Dzięki czystemu <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> podpisowi zwraca <xref:System.Object>. Ale różni konsumenci mogą chcieć bardziej precyzyjne informacje o typie zwrotu. Obejmuje to:

- Projektanci i identyfikatory, którzy mogą być w stanie zapewnić obsługę użycia rozszerzeń znaczników.
- Zaawansowane implementacje programów `SetMarkupExtension` obsługi w klasach docelowych, które mogą polegać na odbicie, <xref:System.Windows.Markup.MarkupExtension> aby określić typ zwracania rozszerzenia znaczników zamiast rozgałęziania na określonych znanych implementacji według nazwy.

## <a name="serialization-of-markup-extension-usages"></a>Serializacja użycia rozszerzenia znaczników

Gdy moduł zapisujący obiekt XAML przetwarza <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>użycie rozszerzenia znaczników i wywołuje, kontekst dla niego wcześniej jest użyciem rozszerzenia znaczników, utrzymuje się w strumieniu węzła XAML, ale nie na wykresie obiektu. Na wykresie obiektu zachowana jest tylko wartość. Jeśli masz scenariusze projektowe lub inne powody utrwalania oryginalnego użycia rozszerzenia znaczników w szeregowanych danych wyjściowych, należy zaprojektować własną infrastrukturę do śledzenia użycia rozszerzenia znaczników ze strumienia węzła XAML ścieżki ładowania. Można zaimplementować zachowanie, aby odtworzyć elementy strumienia węzła ze ścieżki ładowania i odtworzyć je z powrotem do modułów zapisujących XAML w celu serializacji w ścieżce zapisywania, zastępując wartość w odpowiedniej pozycji strumienia węzła.

## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w strumieniu węzła XAML

Jeśli pracujesz ze strumieniem węzła XAML na ścieżce ładowania, użycie rozszerzenia znaczników pojawia się w strumieniu węzła jako obiekt.

Jeśli użycie rozszerzenia znaczników używa argumentów pozycyjnych, jest reprezentowany jako obiekt początkowy z wartością inicjowania. Jako przybliżone reprezentacji tekstu strumień węzła przypomina następujące:

`StartObject`(<xref:System.Xaml.XamlType> jest typem definicji rozszerzenia znaczników, a nie jego typem zwracania)

`StartMember`(nazwa <xref:System.Xaml.XamlMember> is) `_InitializationText`

`Value`(wartość jest argumentami pozycyjnymi jako ciągiem, w tym interweniującymi ogranicznikami)

`EndMember`

`EndObject`

Użycie rozszerzenia znaczników z nazwanymi argumentami jest reprezentowane jako obiekt z członkami odpowiednich nazw, z których każdy zestaw zawiera wartości tekstowych ciągów.

Faktycznie wywoływanie `ProvideValue` implementacji rozszerzenia znaczników wymaga kontekstu schematu XAML, ponieważ wymaga mapowania typu i tworzenia wystąpienia typu rozszerzenia znaczników. Jest to jeden z powodów, dla których użycie rozszerzenia znaczników są zachowywane w ten sposób w domyślnych strumieniach węzłów usług .NET XAML — część czytnika ścieżki ładowania często nie ma dostępnego kontekstu schematu XAML.

Jeśli pracujesz ze strumieniem węzła XAML na ścieżce zapisywania, zazwyczaj nie ma nic w reprezentacji wykresu obiektu, który może poinformować, że obiekt do serializacji został pierwotnie dostarczony przez użycie rozszerzenia znaczników `ProvideValue` i wynik. Scenariusze, które muszą utrzymywać użycie rozszerzenia znaczników dla potknięcia zaokrąglania, a także przechwytywanie innych zmian na wykresie obiektów, muszą opracować własne techniki zachowania wiedzy o użyciu rozszerzenia znaczników z oryginalnego danych wejściowych XAML. Na przykład, aby przywrócić użycie rozszerzenia znaczników, może być konieczne wykonanie pracy ze strumieniem węzła na ścieżce zapisywania w celu przywrócenia użycia rozszerzenia znaczników lub wykonanie pewnego rodzaju scalania między oryginalnym kodem XAML a zaokrąglonym kodem XAML. Niektóre struktury implementujące XAML, takie jak WPF, używają typów pośrednich (wyrażeń), aby pomóc w reprezentowaniu przypadków, w których użycie rozszerzenia znaczników dostarczyło wartości.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Markup.MarkupExtension>
- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md)
- [Rozszerzenia znacznikowania i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
