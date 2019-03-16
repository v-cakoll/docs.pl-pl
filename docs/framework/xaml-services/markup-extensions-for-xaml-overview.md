---
title: Rozszerzenia znaczników dla przeglądu XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 81e142a6989ad2c2c365def4ad43e1bad505c411
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58019158"
---
# <a name="markup-extensions-for-xaml-overview"></a>Rozszerzenia znaczników dla przeglądu XAML
Rozszerzenia znaczników są to technika XAML do uzyskania wartość, która nie jest podstawowy ani określonego typu XAML. Użycie atrybutu rozszerzenia znaczników użytku sekwencję znaków znanych otwierającym nawiasie klamrowym `{` zakres rozszerzenia znaczników i zamykający nawias klamrowy `}` aby wyjść. Korzystając z usług programu .NET Framework XAML, możesz korzystać z niektórych wstępnie zdefiniowanych rozszerzeń znaczników języka XAML z zestawu System.Xaml. Możesz również podklasy z <xref:System.Windows.Markup.MarkupExtension> klasy zdefiniowane w System.Xaml i zdefiniować własne rozszerzenia znaczników. Lub możesz użyć rozszerzenia znaczników zdefiniowana przez strukturę określonego, jeśli są już odwołanie do tej struktury.  
  
 Podczas uzyskiwania dostępu do użycia rozszerzenia znaczników modułu zapisywania obiektu XAML może zapewnić usług do niestandardowego <xref:System.Windows.Markup.MarkupExtension> klasa za pośrednictwem połączenia usługi do punktu w <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> zastąpienia. Usługi można uzyskać kontekst dotyczący użycia, konkretne funkcje modułu zapisywania obiektu, kontekst schematu XAML i tak dalej.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane w XAML  
 Kilka rozszerzenia znaczników są implementowane przez .NET Framework XAML Services pod względem obsługi języka XAML. Te rozszerzenia znaczników odnoszą się do części specyfikacji XAML jako język. Są to zazwyczaj można go rozpoznać po `x:` prefiks w składni, jak pokazano w typowych użycia. Implementacje usług programu .NET Framework XAML dla tych elementów języka XAML, wszystkie dziedziczyć <xref:System.Windows.Markup.MarkupExtension> klasy bazowej.  
  
> [!NOTE]
>  `x:` Prefiks jest używany dla typowych mapowania przestrzeni nazw XAML przestrzeni nazw języka XAML, w elemencie głównym produkcji XAML. Na przykład szablonów projektów i stron programu Visual Studio dla różnych platform określonych zainicjować pliku XAML, za pomocą tego `x:` mapowania. Możesz wybrać inny token własne mapowania przestrzeni nazw XAML, ale ta dokumentacja przyjmie domyślną `x:` mapowanie jako sposób identyfikacji tych jednostek, które są zdefiniowane częścią przestrzeni nazw XAML języka XAML, w przeciwieństwie do przestrzeń nazw XAML domyślną określonym środowiskiem lub innych dowolnego przestrzeniach nazw środowiska CLR i XML.  
  
### <a name="xtype"></a>x: Type  
 `x:Type` dostarcza <xref:System.Type> obiektu dla typu nazwanego. Ta funkcja jest używana najczęściej w mechanizmów opóźnienia, które należy użyć podstawowy typ środowiska CLR i wpisać pochodnym jako moniker grupowania lub identyfikator. WPF style i szablony i ich użycie funkcji `TargetType` właściwości, znajdują się konkretnemu przykładowi. Aby uzyskać więcej informacji, zobacz [x: Type Markup Extension](x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` Tworzy statyczny wartości z jednostki kodu typ wartości, które nie są bezpośrednio typ wartości właściwości, ale mogą być obliczane do tego typu. Jest to przydatne do określenia wartości, które już istnieją jako stałe dobrze znane w definicji typu. Aby uzyskać więcej informacji, zobacz [x: Static — rozszerzenie znaczników](x-static-markup-extension.md).  
  
### <a name="xnull"></a>x:Null  
 `x:Null` Określa `null` jako wartość dla elementu członkowskiego XAML. W zależności od projektu określonych typów lub większych pojęcia framework `null` nie zawsze jest wartość domyślną dla właściwości lub sugerowanej wartości atrybutu pusty ciąg. Aby uzyskać więcej informacji, zobacz [x: Null — rozszerzenie znaczników](x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` obsługuje tworzenie ogólne tablic przy użyciu składni XAML w przypadkach, w których obsługę kolekcji, która jest świadczona przez elementy bazy i modeli kontroli celowo nie jest używany. Aby uzyskać więcej informacji, zobacz [x: Array — rozszerzenie znaczników](x-array-markup-extension.md). W XAML 2009 ściślej mówiąc, tablice są dostępne jako elementów podstawowych języka zamiast jako rozszerzenie. Aby uzyskać więcej informacji, zobacz [XAML 2009 — funkcje językowe](xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` jest częścią XAML 2009, rozszerzenie oryginalnego zestawu języka (2006). `x:Reference` reprezentuje odwołanie do innego istniejącego obiektu wykresu obiektu. Ten obiekt jest identyfikowany przez jego `x:Name`. Aby uzyskać więcej informacji, zobacz [x: Reference — rozszerzenie znaczników](x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Inne x: Konstrukcje  
 Inne `x:` istnieją konstrukcji do obsługi funkcji języka XAML, ale nie są one implementowane jako rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>Klasa bazowa MarkupExtension  
 Aby zdefiniować rozszerzenie niestandardowych znaczników, które mogą prowadzić interakcję z domyślnej implementacji XAML czytników i składników zapisywania XAML System.Xaml, możesz dziedziczyć klasy abstrakcyjnej <xref:System.Windows.Markup.MarkupExtension> klasy. Czy klasa ma jednej metody do przesłonięcia, czyli <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Może trzeba będzie również zdefiniować dodatkowe konstruktorów do obsługi argumenty do użycia rozszerzenia znaczników i pasującą do ustawienia właściwości.  
  
 Za pomocą <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, rozszerzenie znaczników niestandardowych ma dostęp do kontekstu usługi, który zgłasza, środowisko, w której rozszerzenie znaczników faktycznie jest wywoływany przez procesor XAML. W ścieżce obciążenia zazwyczaj jest to <xref:System.Xaml.XamlObjectWriter>. W polu Zapisz ścieżkę zazwyczaj jest to <xref:System.Xaml.XamlXmlWriter>. Każdy raport kontekst usługi jako wewnętrzny XAML usługi dostawcy kontekstu klasy, która implementuje wzorzec dostawcy usług. Aby uzyskać więcej informacji na temat dostępnych usług i ich znaczenie, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
 Klasy rozszerzenia znaczników, należy użyć poziom dostępu publicznego; Procesory XAML musi zawsze można utworzyć wystąpienia klasy pomocy technicznej rozszerzenie znaczników, aby można było używać swoich usług.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definiowanie typ pomocy technicznej dla rozszerzenia znaczników niestandardowe  
 Korzystając z usług programu .NET Framework XAML lub struktur, które są kompilowane na .NET Framework XAML Services, dostępne są dwie opcje dotyczące nazw typu Obsługa rozszerzenia znaczników. Nazwa typu jest istotne jak składników zapisywania obiektu XAML próbują uzyskać dostęp i wywołania typ pomocy technicznej rozszerzenia znaczników, gdy napotkają użycie rozszerzenia znaczników w XAML. Użyj jednej z następujących strategii nazewnictwa:  
  
-   Nazwa, nazwa typu, który ma być dokładnie dopasowany do tokenu użycia znaczników XAML. Na przykład w celu obsługi `{Collate ...}` użycie rozszerzenia, nazwa typu obsługi `Collate`.  
  
-   Nazwa typu, który ma być token ciągu użycia oraz sufiks nazwy `Extension`. Na przykład w celu obsługi `{Collate ...}` użycie rozszerzenia, nazwa typu obsługi `CollateExtension`.  
  
 Kolejność wyszukiwania to wyszukiwanie `Extension`— klasa sufiksami nazwę najpierw, a następnie poszukaj nazwy klasy bez `Extension` sufiks.  
  
 Z punktu widzenia użycia znaczników w tym `Extension` sufiks jako część użycia jest nieprawidłowy. Jednak to zachowuje się tak, jakby `Extension` jest naprawdę częścią nazwy klasy i moduły zapisujące obiektu XAML może zakończyć się niepowodzeniem rozpoznać Klasa pomocy technicznej rozszerzenia struktury znaczników w ten sposób użycia, jeśli nie ma klasy pomocy technicznej `Extension` sufiks.  
  
### <a name="the-default-constructor"></a>Domyślny konstruktor  
 Wszystkie rozszerzenia znaczników obsługi typów, powinny ujawniać publicznego konstruktora domyślnego. Domyślny konstruktor jest wymagana dla każdy przypadek, w którym obiekt Edytor XAML tworzy rozszerzenie znaczników, od użycie elementu obiektu. Obsługa użycie elementu obiektu jest uczciwe oczekiwania dla rozszerzenia znaczników, szczególnie w przypadku serializacji. Jednak można zaimplementować jako rozszerzenie znacznika bez publicznego konstruktora, jeśli zamierzasz obsługiwać użycia atrybutu rozszerzenia znaczników.  
  
 Jeśli użycie rozszerzenia znaczników nie ma argumentów, domyślny konstruktor jest wymagany do obsługi użycia.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Wzorce konstruktora i argumentów pozycyjnych rozszerzenia znaczników niestandardowe  
 Rozszerzenia znaczników przy użyciu argumentu zamierzone użycie konstruktorów publicznych musi odpowiadać trybów zamierzonego użycia. Innymi słowy rozszerzenia znaczników jest przeznaczony do wymagają jeden argument pozycyjny jako prawidłowe użycie, powinien obsługiwać jeden parametr wejściowy, która przyjmuje argument pozycyjny konstruktorem publicznym.  
  
 Na przykład, załóżmy, że `Collate` — rozszerzenie znaczników jest przeznaczony do obsługi trybu tylko w przypadku jeden argument pozycyjny, który reprezentuje jej tryb, określony jako `CollationMode` stała wyliczenia. W tym przypadku powinna być konstruktora o następującej postaci:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Na poziomie podstawowym Argumenty przekazane do rozszerzenia znaczników są ciągu, ponieważ są przekazywane z wartości atrybutów znaczników. Można wszystkie Twoimi ciągami argumentów i pracować z danymi wejściowymi na tym samym poziomie. Jednak masz dostęp do niektórych przetwarzania, które występuje, zanim argumenty rozszerzenia znaczników są przekazywane do klasy pomocy technicznej.  
  
 Przetwarzania działa pod względem koncepcyjnym tak, jakby rozszerzenie znaczników jest obiektem, ma zostać utworzony, a następnie jego wartości składowych są ustawione. Każda określona właściwość można ustawić jest oceniany, podobnie jak określony element członkowski może zostać ustawiona na utworzony obiekt gdy XAML jest analizowany. Istnieją dwie ważne różnice:  
  
-   Jak wspomniano wcześniej, typ pomocy technicznej rozszerzenia znaczników nie musi mieć domyślnego konstruktora, aby można było, można utworzyć wystąpienia w XAML. Konstrukcja obiektu jest odroczone do czasu jego możliwe argumenty w składni tekstu jest stokenizowana i jego ocenie jako argumenty pozycyjne i nazwane, a odpowiedni konstruktor jest wywoływany w tym czasie.  
  
-   Może być zagnieżdżona użycia rozszerzenia znaczników. Rozszerzenie znaczników najbardziej jest stosowana jako pierwsza. W związku z tym można założyć tych danych użycia i Zadeklaruj jeden z parametrów konstrukcji, jako typ, który wymaga konwertera wartości (na przykład rozszerzenie znaczników), aby utworzyć.  
  
 Poleganie na takie przetwarzanie został wyświetlony w poprzednim przykładzie. Moduł zapisywania obiektów platformy .NET Framework XAML Services XAML przetwarzania nazwy stałe wyliczeń do wartości wyliczenia na poziomie natywnych.  
  
 Przetwarzanie składni tekstu parametr pozycyjne rozszerzenia znaczników również polegać na konwerter typu, który jest skojarzony z typem, który znajduje się w argumencie konstrukcji.  
  
 Argumenty są nazywane argumenty pozycyjne, ponieważ kolejność wystąpił tokenów w użycie odnosi się do pozycyjne kolejność parametr konstruktora, do którego są przypisane. Na przykład rozważmy następujący podpis konstruktora:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Procesor XAML oczekuje dwóch argumentów pozycyjnych dla tego rozszerzenia znaczników. Jeśli podczas użycia `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` token jest wysyłany do pierwszego parametru i jego ocenie jako `CollationMode` wyliczeń o nazwie — stała. Wynik wewnętrzny `x:Reference` jest wysyłane do drugiego parametru oraz ocenione jako obiekt.  
  
 XAML określonej reguły składni rozszerzenia znaczników i przetwarzanie, przecinek jest ogranicznik między argumentami, czy te argumenty są argumenty pozycyjne i nazwane argumenty.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Duplikuj Specifikaci argumenty pozycyjne  
 Jeśli Edytor XAML obiektu napotka to użycia rozszerzenia znaczników przy użyciu argumentów pozycyjnych, wiąże się z wielu argumentów konstruktora, które przyjmują tę liczbę argumentów (zduplikowane liczby argumentów), niekoniecznie jest błąd. Zachowanie zależy od można dostosować ustawienia kontekst schematu XAML, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Jeśli <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> jest `true`, Edytor XAML obiekt nie należy zgłosić wyjątek tylko ze względów zduplikowane liczby argumentów. Zachowanie poza ten punkt nie jest ściśle zdefiniowana. Podstawowy projekt zakłada się, że kontekst schematu zawiera informacje o typie dostępnych dla określonych parametrów i można próba ma jawnych rzutowań, które odpowiadają zduplikowane kandydatów, aby zobaczyć, które podpisu może być najlepsze dopasowanie. Wyjątek nadal może zostać wygenerowany, jeśli podpisy nie można przekazać testy, które narzuca tego kontekstu określonego schematu, działającego na Edytor XAML obiektu.  
  
 Domyślnie <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> jest `false` podstawie CLR <xref:System.Xaml.XamlSchemaContext> dla usług programu .NET Framework XAML. W efekcie domyślnie <xref:System.Xaml.XamlObjectWriter> zgłasza wyjątki, jeśli wykryje nieważną użycie rozszerzenia znaczników w przypadku, gdy ma zduplikowane liczby argumentów w konstruktorach zapasowego typu.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Argumenty nazwane rozszerzenia znaczników niestandardowe  
 Rozszerzenia znaczników określony przez XAML umożliwia również formularzem argumentów nazwanych do użycia. Na pierwszy poziom tokenizacji składni tekstu jest podzielony na argumenty. Obecność znak równości (=) w ramach wszystkich argumentów identyfikuje argument jako argumentu nazwanego. Takie argument jest również podzielić na tokeny w pary nazwa/wartość. Nazwa nazwy w takim przypadku można ustawić właściwość publiczną rozszerzenie znaczników typ pomocy technicznej. Jeśli zamierzasz obsługiwać użycie argumentu nazwanego, należy podać te właściwości można ustawić publiczne. Właściwości mogą być dziedziczone właściwości, tak długo, jak są one nadal publicznych.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenie znaczników  
 Dostępność usług są identyczne dla dowolnego konwertera wartości. Różnica polega na w sposób każdego konwertera wartości odbiera kontekst usługi. Dostęp do usług i usługi dostępne są udokumentowane w temacie [typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Użycie elementu właściwości rozszerzenia znaczników  
 Scenariusze użycia rozszerzenia znaczników często są projektowane na podstawie przy użyciu rozszerzenia znaczników w użycie atrybutu. Jednak użytkownik może również potencjalnie w celu zdefiniowania zapasowy klasy do obsługi użycie elementu właściwości.  
  
 Aby umożliwić użycie elementu właściwości rozszerzenia znaczników, zdefiniuj publicznego konstruktora domyślnego. Powinna to być konstruktora wystąpień nie Konstruktor statyczny. Jest to wymagane, ponieważ procesor XAML ogólnie musi wywołać konstruktora domyślnego w dowolnym elemencie obiektu, który przetwarza z kodu znaczników, a w tym klasy rozszerzenia znaczników jako elementy obiektu. W przypadku zaawansowanych scenariuszy można zdefiniować konstrukcji innych niż domyślne ścieżki dla klasy. (Aby uzyskać więcej informacji, zobacz [x: FactoryMethod — dyrektywa](x-factorymethod-directive.md).) Jednak nie należy używać tych wzorców w celach rozszerzenia znaczników, ponieważ dzięki temu odnajdywania z wzorcem użycia dużo bardziej skomplikowane, zarówno dla projektantów, jak i dla użytkowników pierwotne znaczników.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Przypisywanie rozszerzenia znaczników niestandardowe  
 Aby zapewnić obsługę zarówno w środowiska projektowe, jak i w niektórych scenariuszach zapisywania obiektu XAML, typ pomocy technicznej rozszerzenia znaczników powinien atrybutem kilka atrybutów CLR. Te atrybuty raport użycia rozszerzenia znaczników zamierzone.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> Raporty <xref:System.Type> informacje dla obiektu typu <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> zwraca. Podpisem czystego <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> zwraca <xref:System.Object>. Ale różnych użytkowników może być bardziej precyzyjne informacje o typie zwracanym. Możliwości obejmują:  
  
-   Projektanci i środowiskami IDE, który może mieć możliwość zapewnienia obsługujących typu Obsługa użycia rozszerzenia znaczników.  
  
-   Zaawansowane implementacje `SetMarkupExtension` programów obsługi na klas docelowych, które może polegać na podstawie odbicia w celu określenia typu zwracanego rozszerzenia znaczników zamiast rozgałęzianie na określone znane <xref:System.Windows.Markup.MarkupExtension> implementacje według nazwy.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serializacja użycia rozszerzenia znaczników  
 Podczas zapisywania obiektu XAML przetwarza użycie rozszerzenia znaczników i wywołania <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontekst dla jej wcześniej użycie rozszerzenia znaczników będzie się powtarzać, strumień węzłów XAML, ale nie na grafie obiektu. Na wykresie obiektu tylko wartość są zachowywane. Jeśli masz scenariusze dotyczące projektów lub inne przyczyny utrwalania oryginalnego użycie rozszerzenia znaczników w Zserializowany danych wyjściowych, należy zaprojektować własną infrastrukturę do śledzenia użycia rozszerzenia znaczników ze strumienia węzłów XAML ścieżki obciążenia. Możesz zaimplementować zachowanie, aby ponownie utworzyć elementy strumień węzłów ze ścieżki obciążenia i odtwarzać je autorom XAML do serializacji w Zapisz ścieżkę, zastępując wartości w odpowiedniej pozycji w strumieniu węzła.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w XAML Stream węzła  
 Jeśli pracujesz z strumień węzłów XAML w ścieżce obciążenia, użycie rozszerzenia znaczników pojawia się w strumień węzłów jako obiekt.  
  
 Użycie rozszerzenia znaczników używa argumenty pozycyjne, jest przedstawiana jako obiekt start z wartością inicjowania. Jako reprezentację nierównej tekstu strumień węzłów jest podobny do następującego:  
  
 `StartObject` (<xref:System.Xaml.XamlType> jest rozszerzenie znaczników definicji typu, nie typem zwracanym)  
  
 `StartMember` (nazwa <xref:System.Xaml.XamlMember> jest `_InitializationText`)  
  
 `Value` (wartość jest argumenty pozycyjne jako ciąg, w tym pośredniczące ograniczniki)  
  
 `EndMember`  
  
 `EndObject`  
  
 Użycie rozszerzenia znaczników z argumentami nazwanego jest reprezentowany jako obiekt z elementami członkowskimi odpowiednich nazw, każdy zestaw z wartości ciągów tekstowych.  
  
 Faktycznie wywoływania `ProvideValue` implementacji rozszerzenie znaczników wymaga kontekst schematu XAML, ponieważ wymaga mapowanie typu i utworzyć wystąpienie typu obsługi rozszerzenia znaczników. To jest jednym z powodów dlaczego użycia rozszerzenia znaczników są zachowywane w ten sposób w strumieniach węzła usług programu .NET Framework XAML domyślne — czytnika części ścieżki obciążenia, który jest często nie ma potrzeby kontekst schematu XAML dostępne.  
  
 Jeśli pracujesz z strumień węzłów XAML Zapisz ścieżkę, zazwyczaj żadne działania w reprezentację wykresu obiektu, który może wcześniej poinformować, obiekt do zserializowania pierwotnie został dostarczony przez użycie rozszerzenia znaczników i `ProvideValue` wynik. Scenariusze, które musisz zachować użycia rozszerzenia znaczników dla Pełna zgodnooć wersji, a także Przechwytywanie inne zmiany na grafie obiektu musi należy opracować własne techniki zachowaniu wiedzy o użycie rozszerzenia znaczników, od oryginału wejściowe XAML. Na przykład, aby przywrócić użycia rozszerzenia znaczników, konieczne może być pracę w usłudze stream węzła w Zapisz ścieżkę, aby można było przywrócić użycia rozszerzenia znaczników lub wykonać pewien rodzaj scalania między oryginalnego XAML i XAML zwrotnego —. Niektórych platform Implementowanie XAML, takich jak WPF użyć typów pośrednich (wyrażenia) do reprezentowania przypadki, w którym użycia rozszerzenia znaczników podane wartości.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Markup.MarkupExtension>
- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
