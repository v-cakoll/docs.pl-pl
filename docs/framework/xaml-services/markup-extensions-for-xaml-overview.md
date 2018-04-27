---
title: Rozszerzenia znaczników dla przeglądu XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
caps.latest.revision: 14
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 464c5f547089d47906f2e227effe821357196c16
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="markup-extensions-for-xaml-overview"></a>Rozszerzenia znaczników dla przeglądu XAML
Rozszerzenia znaczników to technika XAML do uzyskania wartość, która nie jest właściwością pierwotną ani określonego typu XAML. Dla użycie atrybutu rozszerzenia znaczników przy użyciu sekwencji znaków znane otwierający nawias klamrowy `{` zakres rozszerzenia znacznika i zamykający nawias klamrowy `}` aby zakończyć. Korzystając z usług .NET Framework XAML, można użyć pewnych wstępnie zdefiniowanych rozszerzeń znaczników języka XAML z System.Xaml zestawu. Możesz również podklasy z <xref:System.Windows.Markup.MarkupExtension> klasy, zdefiniowane w System.Xaml i zdefiniowanie własnego rozszerzenia znaczników. Lub może używać rozszerzeń znaczników zdefiniowane przez platformę określonego odwołuje się już w ramach tego.  
  
 Podczas uzyskiwania dostępu do użycia rozszerzenia znaczników twórcę obiektu XAML może zapewnić usługi do niestandardowego <xref:System.Windows.Markup.MarkupExtension> za pośrednictwem połączenia z usługą punktu w <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> zastąpienia. Usługi może zostać użyty do uzyskania kontekstu dotyczące użycia, możliwości zapisywania obiektów, kontekst schematu XAML i tak dalej.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane XAML  
 Kilka rozszerzeń znaczników są implementowane przez program .NET Framework XAML usługi do obsługi języka XAML. Te rozszerzenia znaczników odpowiadają części specyfikacji jako języka XAML. Są to zazwyczaj do zidentyfikowania przez `x:` prefiksu w składni widziany wspólną użycia. Implementacje usług .NET Framework XAML dla tych elementów języka XAML wszystkie pochodzi od <xref:System.Windows.Markup.MarkupExtension> klasy podstawowej.  
  
> [!NOTE]
>  `x:` Prefiks jest używany dla typowych mapowania przestrzeni nazw XAML obszaru nazw języka XAML, w elemencie głównym produkcji XAML. Na przykład szablony projektów i stron programu Visual Studio dla różnych platform określonych zainicjować pliku XAML, za pomocą tej `x:` mapowania. Można wybrać inny token w własne mapowania przestrzeni nazw XAML, ale w tej dokumentacji przyjmie wartość domyślna `x:` mapowania jako sposób identyfikacji tych jednostek, które należą do określonych przestrzeni nazw XAML języka XAML, w przeciwieństwie do przestrzeń nazw XAML domyślne określonej platformy lub innych dowolnego przestrzeniach nazw CLR lub XML.  
  
### <a name="xtype"></a>x: Type  
 `x:Type` dostarcza <xref:System.Type> obiektu dla typu nazwanego. Ta funkcja jest najczęściej używana w mechanizmów odroczenia, które używają podstawowego typu środowiska CLR i typu pochodnego jako krótka nazwa grupowania lub identyfikator. WPF style i szablony i ich użycie `TargetType` właściwości są określone przykładów. Aby uzyskać więcej informacji, zobacz [x: Type — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` Tworzy wartości statyczne z jednostek kodu typ wartości, które nie są bezpośrednio typ wartości właściwości, ale może przyjąć typu. Jest to przydatne w przypadku określania wartości, które już istnieją jako dobrze znanego stałe w definicji typu. Aby uzyskać więcej informacji, zobacz [x: Static — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### <a name="xnull"></a>x: Null  
 `x:Null` Określa `null` jako wartość dla elementu członkowskiego XAML. W zależności od projektu określonych typów lub większy pojęcia framework `null` nie zawsze jest wartość domyślna właściwości lub sugerowanej wartości atrybutu pusty ciąg. Aby uzyskać więcej informacji, zobacz [x: Null — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` obsługuje tworzenie tablic ogólne w składni języka XAML w przypadkach, których obsługa kolekcji są dostarczane przez podstawowe elementy i modele kontroli celowo nie jest używany. Aby uzyskać więcej informacji, zobacz [x: Array — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-array-markup-extension.md). W języku XAML 2009 w szczególności tablice są dostępne jako elementy podstawowe języka zamiast jako rozszerzenie. Aby uzyskać więcej informacji, zobacz [XAML 2009 — funkcje językowe](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` wchodzi w skład XAML 2009 rozszerzenia oryginalnego zestawu języka (2006). `x:Reference` reprezentuje odwołanie do innego obiektu istniejących na wykresie obiektu. Ten obiekt jest identyfikowany przez jego `x:Name`. Aby uzyskać więcej informacji, zobacz [x: Reference — rozszerzenie znaczników](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Inne konstrukcje x:  
 Inne `x:` konstrukcji, aby zapewnić obsługę funkcji języka XAML istnieje, ale nie są one zaimplementowane jako rozszerzenia znaczników. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>Klasa podstawowa MarkupExtension  
 Aby zdefiniować rozszerzenia znaczników niestandardowych, które mogą prowadzić interakcję z domyślnej implementacji czytników XAML i zapisywania XAML w System.Xaml, klasa pochodzi z klasy abstrakcyjnej <xref:System.Windows.Markup.MarkupExtension> klasy. Czy klasa ma jedną metodę do zastąpienia, która jest <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Konieczne może również do definiowania dodatkowych konstruktorów obsługuje argumentów użycia rozszerzenia znaczników i dopasowywania można ustawić właściwości.  
  
 Za pomocą <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, rozszerzeniem znacznika niestandardowego ma dostęp do kontekstu usługi, która raportuje środowiska faktycznie przywołane rozszerzenie znaczników przez procesor XAML. W ścieżce obciążenia jest to zazwyczaj <xref:System.Xaml.XamlObjectWriter>. W polu Zapisz zazwyczaj jest to ścieżka <xref:System.Xaml.XamlXmlWriter>. Każdy raport kontekstu usługi jako wewnętrzne XAML usługi dostawcy kontekstu klasy, która implementuje wzorzec dostawcy usługi. Aby uzyskać więcej informacji o dostępnych usług i ich znaczenie, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Klasy rozszerzenia znaczników muszą używać poziomu dostępu publicznego; Procesory XAML musi być zawsze można utworzyć wystąpienia klasy pomocy technicznej rozszerzenie znaczników, aby można było używać swoich usług.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Określenie typu pomocy technicznej dla rozszerzenia znacznika niestandardowych  
 Korzystając z usług .NET Framework XAML lub struktur w usług .NET Framework XAML, dostępne są dwie opcje dotyczące nazwy typu obsługi rozszerzenia znaczników. Nazwa typu jest odpowiedni sposób zapisywania obiektów XAML prób dostępu i wywołać typu obsługi rozszerzenia znaczników po napotkaniu użytkowania rozszerzenie znaczników w XAML. Użyj jednej z następujących strategii nazewnictwa:  
  
-   Nazwa Nazwa typu, który ma zostać dokładnego dopasowania do tokenu użycia znaczników XAML. Na przykład w celu obsługi `{Collate ...}` użycie rozszerzenia, nazwa typu pomocy technicznej `Collate`.  
  
-   Nazwa typu, który ma zostać token ciągu użycia oraz sufiks nazwy `Extension`. Na przykład w celu obsługi `{Collate ...}` użycie rozszerzenia, nazwa typu pomocy technicznej `CollateExtension`.  
  
 Kolejność wyszukiwania to wyszukiwanie `Extension`— klasa sufiks najpierw nazwę, a następnie wyszukaj nazwę klasy bez `Extension` sufiks.  
  
 Z punktu widzenia użycia znaczników łącznie z `Extension` sufiks jako część użycia jest nieprawidłowy. Jednak to zachowuje się tak, jakby `Extension` naprawdę jest częścią nazwy klasy i moduły zapisujące obiektu XAML nie powiedzie się rozpoznać klasy pomocy technicznej rozszerzenia znaczników dla tego użycia, jeśli nie miał klasy pomocy technicznej `Extension` sufiks.  
  
### <a name="the-default-constructor"></a>Konstruktor domyślny  
 Wszystkie rozszerzenia znaczników obsługi typów, powinny ujawniać publicznego konstruktora domyślnego. Domyślny konstruktor jest wymagane dla każdego przypadku, gdy Edytor obiektu XAML tworzy rozszerzenie znaczników z użycie elementu obiektu. Obsługa użycie elementu obiektu, jest odpowiedni oczekiwania dla rozszerzenia znacznika, szczególnie w przypadku serializacji. Jednak można zaimplementować rozszerzenie znacznika bez publicznego konstruktora, jeśli zamierzasz obsługi użycia atrybutu rozszerzenia znacznika.  
  
 Jeśli użycie rozszerzenia znaczników nie ma argumentów, domyślny konstruktor jest wymagany do obsługi użycia.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Konstruktor wzorców i argumenty pozycyjne rozszerzenia znaczników niestandardowych  
 Rozszerzenia znaczników z użyciem danego argumentu konstruktorów publicznych musi odpowiadać trybów zamierzonego użycia. Innymi słowy rozszerzenia znaczników zaprojektowano w celu wymaga jednego argumentu pozycyjnego jako prawidłowe użycie, powinien obsługiwać konstruktora publicznego o jeden parametr wejściowy, który przyjmuje argument pozycyjny.  
  
 Załóżmy na przykład, `Collate` — rozszerzenie znaczników jest przeznaczony do obsługi tylko tryb w przypadku jeden argument pozycyjny, który reprezentuje jej tryb, określony jako `CollationMode` stała wyliczenia. W takim przypadku powinien być konstruktora o następującej postaci:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Na poziomie podstawowym Argumenty przekazane do rozszerzenia znacznika są ciąg, ponieważ są przesyłane dalej z wartości atrybutu kod znaczników. Można wszystkie z ciągów argumentów i pracować z danych wejściowych na tym poziomie. Jednak masz dostęp do niektórych o przetwarzaniu uruchamianym przed argumenty rozszerzeń znaczników do klasy pomocy technicznej.  
  
 Przetwarzanie koncepcyjnie działa tak, jakby rozszerzenie znaczników jest obiekt ma zostać utworzony, a następnie ustaw są wartości jego elementów członkowskich. Każdej określonej właściwości można ustawić jest oceniany, podobnie jak określony element członkowski można ustawić na utworzony obiekt podczas analizowania XAML. Istnieją dwie ważne różnice:  
  
-   Jak wspomniano wcześniej, typ obsługi rozszerzenia znaczników nie musi mieć konstruktora domyślnego celu można utworzyć wystąpienia w języku XAML. Konstrukcji obiektu jest odłożona do możliwe argumenty w składni tekst są stokenizowanego i ocenione jako argumenty pozycyjne lub nazwanym, a odpowiedni konstruktor jest wywoływana w tym czasie.  
  
-   Mogą być zagnieżdżane użycia rozszerzenia znaczników. Rozszerzenie wewnętrzne znaczników jest oceniany, najpierw. W związku z tym można przyjmuje takie użycia i zadeklarować jeden z parametrów konstrukcji jako typ, który wymaga konwertera wartości (na przykład markup extension) do tworzenia.  
  
 Zależy od takich przetwarzania był wyświetlany w poprzednim przykładzie. Moduł zapisywania obiektów platformy .NET Framework XAML Services XAML przetwarzania nazwy stałej wyliczenia do wartości wyliczenia na poziomie macierzystego.  
  
 Przetwarzanie tekstu składnia parametrów pozycyjnych rozszerzenia znaczników może również polegać na konwerter typu, który jest skojarzony z typem, który znajduje się w argumencie konstrukcji.  
  
 Argumenty są nazywane argumentów pozycyjnych, ponieważ kolejność wystąpił tokeny przy używaniu odpowiada pozycyjnych kolejność parametru konstruktora, do której są przypisane. Na przykład wziąć pod uwagę następujące sygnatury konstruktora:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Procesor XAML oczekuje dwóch argumentów pozycyjnych dla tego rozszerzenia znacznika. Jeśli było użycie `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` token jest wysyłany do pierwszego parametru i ocenione jako `CollationMode` wyliczenie o nazwie stała. Wynik wewnętrzny `x:Reference` jest wysyłane do drugiego parametru i ocenione jako obiekt.  
  
 W kodzie XAML określonymi zasadami składni rozszerzenia znacznika i przetwarzania, przecinek jest ogranicznik między argumentami, czy te argumenty są argumenty pozycyjne lub nazwanych argumentów.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Zduplikowana argumentów argumenty pozycyjne  
 Jeśli Edytor obiektu XAML napotka użytkowania rozszerzenia znaczników argumentów pozycyjnych i wiele argumentów konstruktora przyjmujących tej liczby argumentów (zduplikowane argumentów), który nie jest zawsze wystąpił błąd. Zachowanie zależy od można dostosować ustawienia kontekst schematu XAML, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Jeśli <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> jest `true`, Edytor obiektu XAML nie powinien zgłoszenia wyjątku tylko ze względów o liczbie argumentów zduplikowane. Zachowanie poza ten punkt nie jest ściśle zdefiniowana. Podstawowy projekt zakłada się, że kontekst schematu ma informacji o typie dla określonych parametrów i można próba rzutowania jawnego zgodne zduplikowane kandydatów, aby zobaczyć podpisów mogą być najlepsze dopasowanie. Może nadal być wyjątek niepowodzenie nie podpisów można testów, które są narzucone w tym kontekście określonego schematu uruchomionego na Edytor obiektu XAML.  
  
 Domyślnie <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> jest `false` CLR oparty na <xref:System.Xaml.XamlSchemaContext> dla usług .NET Framework XAML. W związku z tym domyślna <xref:System.Xaml.XamlObjectWriter> zgłasza wyjątek wyjątków, jeśli wykryje użycie rozszerzenia znaczników przypadku zduplikowane liczby argumentów w konstruktorach typu zapasowy.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Nazwane argumenty dla rozszerzenia znacznika niestandardowych  
 Rozszerzenia znaczników określony przez XAML również mogą używać formularza nazwane argumenty do użycia. Na pierwszy poziom tokenizacji składni tekst jest podzielona na argumentów. Obecność znak równości (=) w ramach wszystkich argumentów wskazywany argumentu nazwanego argumentu. Takie argumentu jest również podzielić na tokeny do pary nazwa/wartość. Nazwa nazwy w takim przypadku można ustawić właściwości publicznej rozszerzenie znaczników typu pomocy technicznej. Jeśli planujesz obsługiwać użycie nazwanego argumentu, należy podać te właściwości można ustawić publiczne. Właściwości mogą być dziedziczone właściwości tak długo, jak są one nadal publicznego.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenia znaczników  
 Usługi dostępne są takie same dla dowolnego konwertera wartości. Różnica polega na tym w sposób każdego konwerter wartości odbiera kontekstu usługi. Dostęp do usług i usług dostępnych opisano w temacie [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Użycie elementu właściwości rozszerzenia znaczników  
 Scenariusze użycia rozszerzenia znaczników są często została zaprojektowana w użycie atrybutu przy użyciu rozszerzenia znaczników. Jednak również jest potencjalnie można zdefiniować klasy zapasowy umożliwia użycie elementu właściwości.  
  
 Aby umożliwić użycie elementu właściwości rozszerzenia znaczników, zdefiniuj publicznego konstruktora domyślnego. Powinno to być konstruktorem wystąpień nie Konstruktor statyczny. Jest to wymagane, ponieważ procesor XAML zazwyczaj należy wywołać konstruktora domyślnego w dowolnym elemencie obiektu, który przetwarza z poziomu znacznika i obejmuje znaczników rozszerzenie klasy jako elementy obiektu. Dla zaawansowanych scenariuszy można określić innych niż domyślne konstrukcji ścieżki dla klasy. (Aby uzyskać więcej informacji, zobacz [x: factorymethod — dyrektywa](../../../docs/framework/xaml-services/x-factorymethod-directive.md).) Jednak nie należy używać tych wzorców do celów rozszerzenia znaczników, ponieważ dzięki temu odnajdywania wzorca użycia znacznie trudniejsze, zarówno w przypadku projektantów, jak i użytkowników raw znaczników.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Przypisywanie rozszerzenia znaczników niestandardowych  
 Do obsługi środowisk projektowania i niektórych scenariuszy XAML obiektu składnika zapisywania, typ obsługi rozszerzenia znaczników powinien atrybutem kilka atrybutów CLR. Te atrybuty raportują użycie rozszerzenia znaczników zamierzone.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> Raporty <xref:System.Type> wpisz informacje dla obiekt, który <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> zwraca. Podpisem czystego <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> zwraca <xref:System.Object>. Ale różnych użytkowników może być bardziej dokładne informacji o typie zwracanym. Możliwości obejmują:  
  
-   Projektanci i IDEs, który może mieć możliwość zapewnienia obsługujący typ obsługę użycia rozszerzenia znaczników.  
  
-   Zaawansowane implementacje `SetMarkupExtension` programów obsługi na klasy docelowej, które mogą polegać na odbicia można ustalić typu zwracanego rozszerzenie znacznika zamiast rozgałęzianie na określone znane <xref:System.Windows.Markup.MarkupExtension> implementacje według nazwy.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serializacja użycia rozszerzenia znaczników  
 Podczas zapisywania obiektu XAML przetwarza użycie rozszerzenia znacznika i wywołania <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontekst dla niego wcześniej jest użycie rozszerzenia znaczników będzie się powtarzać, strumień węzłów XAML, ale nie w wykres obiektu. Na wykresie obiektu tylko wartość są zachowywane. Jeśli masz scenariusze projektowania lub inne przyczyny utrwalanie oryginalnego użycie rozszerzenia znaczników do serializacji danych wyjściowych, należy zaprojektować infrastruktury śledzenia użycia rozszerzenia znaczników strumienia węzłów XAML ścieżki obciążenia. Można zaimplementować zachowanie, aby odtworzyć elementy strumienia węzła ze ścieżki obciążenia i odtworzenie ich autorom XAML do serializacji w Zapisz ścieżkę, zastępując wartości w odpowiedniej pozycji strumienia węzłów.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozszerzenia znaczników w strumieniu węzłów XAML  
 Jeśli pracujesz z strumień węzłów XAML w ścieżce obciążenia, obciążenie rozszerzenia znaczników pojawia się w strumieniu węzłów jako obiekt.  
  
 Jeśli użycie rozszerzenia znaczników używa argumenty pozycyjne, jest reprezentowana jako obiekt start z wartością inicjowania. Jako reprezentacji nierównej tekst w strumieniu węzłów podobny do następującego:  
  
 `StartObject` (<xref:System.Xaml.XamlType> jest rozszerzenie znaczników definicji typu, nie jej typu zwracanego)  
  
 `StartMember` (nazwa <xref:System.Xaml.XamlMember> jest `_InitializationText`)  
  
 `Value` (wartość to argumenty pozycyjne jako ciąg razem z ogranicznikami pośredniczące)  
  
 `EndMember`  
  
 `EndObject`  
  
 Użycie rozszerzenia znaczników, z argumentami nazwanymi jest reprezentowany jako obiekt z elementami członkowskimi odpowiednie nazwy, każdy zestaw o wartości ciągów tekstowych.  
  
 Faktycznie wywoływania `ProvideValue` implementacji rozszerzenie znacznika wymaga kontekst schematu XAML, ponieważ wymagający mapowanie typu i tworzenie wystąpienia typu obsługi rozszerzenia znaczników. Jest to jeden powód, dlaczego użycia rozszerzenia znaczników zostaną zachowane w ten sposób w strumieniach węzła usług .NET Framework XAML domyślny — czytnik część ścieżki obciążenia często nie ma potrzeby kontekst schematu XAML dostępne.  
  
 Jeśli pracujesz z strumień węzłów XAML Zapisz ścieżkę, zazwyczaj nic nie stoi obecne w reprezentacji wykresu obiektu, który można informujące, że obiekt do zserializowania pierwotnie został dostarczony przez użycie rozszerzenia znacznika i `ProvideValue` wynik. Scenariusze, które potrzeba utrwalenia użycia rozszerzenia znaczników dla dwustronną komunikację, a także Przechwytywanie innych zmian wprowadzonych w wykres obiektu musi opracować własnych techniki zachowania wiedzy użycie rozszerzenia znaczników z oryginalnego XAML danych wejściowych. Na przykład, aby przywrócić użycia rozszerzenia znaczników, może być konieczne pracować z strumieniu węzłów na Zapisz ścieżkę, aby przywrócić użycia rozszerzenia znaczników lub wykonywać niektórych scalania między oryginalnego XAML i wysyłać, zwracać XAML. Niektóre Implementowanie XAML platform, takich jak WPF użyć typy pośredniego (wyrażenia) do reprezentowania przypadków, w którym użycia rozszerzenia znaczników podane wartości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Markup.MarkupExtension>  
 [Typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
