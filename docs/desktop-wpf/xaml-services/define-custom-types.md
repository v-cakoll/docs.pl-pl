---
title: Definiowanie typów niestandardowych do użytku z usługami .NET XAML
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: ff7e4229450e801a6d618c5141efde8cdcbef03d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071858"
---
# <a name="define-custom-types-for-use-with-net-xaml-services"></a>Definiowanie typów niestandardowych do użytku z usługami .NET XAML

Podczas definiowania typów niestandardowych, które są obiektami biznesowymi lub są typami, które nie mają zależności od określonych struktur, istnieją pewne najlepsze rozwiązania dla XAML, które można wykonać. Jeśli zastosujesz się do tych praktyk, usługi .NET XAML Services i ich czytniki XAML i moduły zapisu XAML mogą odnajdywać cechy XAML danego typu i nadać mu odpowiednią reprezentację w strumieniu węzła XAML przy użyciu systemu typu XAML. W tym temacie opisano najlepsze rozwiązania dotyczące definicji typów, definicji elementów członkowskich i przypisywania typów lub elementów członkowskich CLR.

## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>Szyki konstruktora i definicje typów dla XAML

Aby utworzyć wystąpienie jako element obiektu w języku XAML, klasa niestandardowa musi spełniać następujące wymagania:

- Klasa niestandardowa musi być publiczna i musi ujawnić bez parametrów konstruktora publicznego. (Zobacz poniższą sekcję, aby zapoznać się z uwagami dotyczącymi struktur).

- Klasa niestandardowa nie może być klasą zagnieżdżoną. Dodatkowa "kropka" w ścieżce pełnej nazwy sprawia, że podział obszaru nazw klasy jest niejednoznaczny i koliduje z innymi funkcjami XAML, takimi jak dołączone właściwości.
Jeśli obiekt może zostać utworzony jako element obiektu, utworzony obiekt może wypełnić formę elementu właściwości wszystkich właściwości, które przyjmują obiekt jako ich typ podstawowy.

Nadal można podać wartości obiektów dla typów, które nie spełniają tych kryteriów, jeśli włączysz konwerter wartości. Aby uzyskać więcej informacji, zobacz [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

### <a name="structures"></a>Struktury

Struktury są zawsze w stanie być konstruowane w XAML, według definicji CLR. Dzieje się tak, ponieważ kompilator CLR niejawnie tworzy konstruktora bez parametrów dla struktury. Ten konstruktor inicjuje wszystkie wartości właściwości do ich wartości domyślnych.

W niektórych przypadkach domyślne zachowanie konstrukcji dla struktury nie jest pożądane. Może to być spowodowane strukturą jest przeznaczony do wypełniania wartości i funkcji koncepcyjnie jako unii. Jako związek zawarte wartości mogą mieć wzajemnie wykluczające się interpretacje, a zatem żadna z jego właściwości nie jest ustawiona. Przykładem takiej struktury w słownictwie WPF jest <xref:System.Windows.GridLength>. Takie struktury należy zaimplementować konwerter typów, tak aby wartości mogą być wyrażone w formie atrybutu, przy użyciu konwencji ciągów, które tworzą różne interpretacje lub tryby wartości struktury. Struktura powinna również uwidaczniać podobne zachowanie dla konstrukcji kodu za pośrednictwem konstruktora bez parametrów.

### <a name="interfaces"></a>Interfejsy

Interfejsy mogą być używane jako podstawowe typy elementów członkowskich. System typu XAML sprawdza listę przypisywaną i oczekuje, że obiekt, który jest dostarczany jako wartość może być przypisany do interfejsu. Nie istnieje pojęcie, jak interfejs musi być przedstawiony jako typ XAML tak długo, jak odpowiedni typ przypisywania obsługuje wymagania konstrukcyjne XAML.

### <a name="factory-methods"></a>Metody fabryczne

Metody fabryczne są funkcją XAML 2009. Modyfikują zasadę XAML, że obiekty muszą mieć konstruktory bez parametrów. Metody fabryczne nie są opisane w tym artykule. Zobacz [x:FactoryMethod Dyrektywy](xfactorymethod-directive.md).

## <a name="enumerations"></a>Wyliczenia

Wyliczenia mają zachowanie konwersji typu natywnego XAML. Nazwy stałych wyliczenia określone w języku XAML są rozpoznawane względem podstawowego typu wyliczenia i zwracają wartość wyliczenia do modułu zapisującego obiekt XAML.

XAML obsługuje użycie w stylu flagi dla <xref:System.FlagsAttribute> wyliczenia z zastosowanym. Aby uzyskać więcej informacji, zobacz Szczegółowo [składnię XAML](../../framework/wpf/advanced/xaml-syntax-in-detail.md). [(Składnia XAML w szczegółach](../../framework/wpf/advanced/xaml-syntax-in-detail.md) jest napisana dla odbiorców WPF, ale większość informacji w tym temacie jest istotne dla XAML, który nie jest specyficzny dla określonej struktury implementacji.)

## <a name="member-definitions"></a>Definicje elementów członkowskich

Typy można zdefiniować elementy członkowskie dla użycia XAML. Jest możliwe dla typów do definiowania elementów członkowskich, które są użyteczne xaml, nawet jeśli ten określony typ nie jest użyteczny xaml. Jest to możliwe ze względu na dziedziczenie CLR. Tak długo, jak jakiś typ, który dziedziczy element członkowski obsługuje użycie XAML jako typ, a element członkowski obsługuje użycie XAML dla jego typu bazowego lub ma dostępną składnię XAML, ten element członkowski jest użyteczny dla języka XAML.

### <a name="properties"></a>Właściwości

Jeśli właściwości są definiowane jako publiczna właściwość `get` `set` CLR przy użyciu typowych wzorców CLR i akcesorów oraz słów kluczowych <xref:System.Xaml.XamlMember> odpowiednich dla <xref:System.Xaml.XamlMember.IsReadPublic%2A> języka, system typów XAML może zgłaszać właściwość jako element członkowski z odpowiednimi informacjami dla właściwości, takimi jak i <xref:System.Xaml.XamlMember.IsWritePublic%2A>.

Określone właściwości można włączyć składnię tekstu, stosując <xref:System.ComponentModel.TypeConverterAttribute>. Aby uzyskać więcej informacji, zobacz [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

W przypadku braku składni tekstu lub natywnej konwersji XAML i w przypadku braku dalszych pośrednich, takich jak użycie rozszerzenia znaczników, typ właściwości (w<xref:System.Xaml.XamlMember.TargetType%2A> systemie typu XAML) musi mieć możliwość zwrócenia wystąpienia do modułu zapisującego obiekt XAML, traktując typ docelowy jako typ CLR.

W przypadku korzystania z XAML 2009, [x:Reference Markup Extension](xreference-markup-extension.md) może służyć do dostarczania wartości, jeśli poprzednie uwagi nie są spełnione; jednak jest to bardziej problem użycia niż problem z definicją typu.

### <a name="events"></a>Zdarzenia

Jeśli zdarzenia są definiowane jako publiczne zdarzenie CLR, system typu XAML może zgłaszać zdarzenie jako element członkowski jako <xref:System.Xaml.XamlMember.IsEvent%2A> `true`. Okablowanie programów obsługi zdarzeń nie jest w zakresie funkcji usług .NET XAML Services; okablowanie pozostawia się określonym ramom i implementacjom.

### <a name="methods"></a>Metody

Wbudowany kod metod nie jest domyślną funkcją XAML. W większości przypadków nie bezpośrednio odwołać się do elementów członkowskich metody z XAML, a rola metod w XAML jest tylko w celu zapewnienia obsługi określonych wzorców XAML. [x:Dyrektywa FactoryMethod](xfactorymethod-directive.md) jest wyjątkiem.

### <a name="fields"></a>Pola

Wytyczne dotyczące projektowania PROGRAMU CLR zniechęcają do pól niestatycznych. W przypadku pól statycznych można uzyskiwać dostęp do wartości pól statycznych tylko za pośrednictwem [x:Static Markup Extension](xstatic-markup-extension.md); w takim przypadku nie robisz nic specjalnego w definicji CLR, aby udostępnić pole dla [x:Static](xstatic-markup-extension.md) użycia.

## <a name="attachable-members"></a>Członkowie dołączani

Dołączane elementy członkowskie są narażone na XAML za pośrednictwem wzorca metody akcesora na typ definiujący. Sam typ definiujący nie musi być użyteczny jako obiekt XAML. W rzeczywistości typowy pattern jest zadeklarować klasę usługi, której rolą jest właścicielem dołączanego elementu członkowskiego i implementowania powiązanych zachowań, ale nie obsługują żadnej innej funkcji, takiej jak reprezentacja interfejsu użytkownika. W poniższych sekcjach symbol zastępczy *PropertyName* reprezentuje nazwę dołączanego elementu członkowskiego. Ta nazwa musi być prawidłowa w [XamlName Grammar](xamlname-grammar.md).

Należy zachować ostrożność kolizji nazw między tymi wzorcami i innych metod typu. Jeśli istnieje element członkowski, który pasuje do jednego z wzorców, może być interpretowany jako dołączany element członkowski ścieżki użycia przez procesor XAML, nawet jeśli nie było to intencją.

#### <a name="the-getpropertyname-accessor"></a>Akcesor GetPropertyName

Podpis akcesora `GetPropertyName` musi być:

`public static object GetPropertyName(object target)`

- Obiekt `target` można określić jako bardziej szczegółowy typ w implementacji. Można użyć tego do zakresu użycia członka dołączane; użycia poza zamierzonym zakresem będzie zgłaszać nieprawidłowe wyjątki rzutowanie, które są następnie powierzchniowe przez błąd analizy XAML. Nazwa `target` parametru nie jest wymaganiem, ale jest nazwany `target` przez konwencję w większości implementacji.

- Zwracana wartość może być określona jako bardziej szczegółowy typ w implementacji.

Aby obsługiwać włączoną składnię <xref:System.ComponentModel.TypeConverter> tekstu dla użycia atrybutu dołączanego elementu członkowskiego, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do `GetPropertyName` akcesora. Zastosowanie do `get` zamiast `set` może wydawać się nie intuicyjne; jednak ta konwencja może obsługiwać koncepcję tylko do odczytu dołączanych elementów członkowskich, które są serializable, co jest przydatne w scenariuszach projektanta.

#### <a name="the-setpropertyname-accessor"></a>Akcesor SetPropertyName

Podpis akcesora `SetPropertyName` musi być:

`public static void SetPropertyName(object target, object value)`

- Obiekt `target` można określić jako bardziej szczegółowy typ w implementacji, z taką samą logiką i konsekwencjami, jak opisano w poprzedniej sekcji.

- Obiekt `value` można określić jako bardziej szczegółowy typ w implementacji.

Należy pamiętać, że wartość dla tej metody jest dane wejściowe pochodzące z użycia XAML, zazwyczaj w formie atrybutu. Z formularza atrybutu musi być obsługa konwertera wartości dla składni `GetPropertyName`tekstu i atrybut na akcesor s.

### <a name="attachable-member-stores"></a>Dołączane sklepy członkowskie

Metody akcesora zazwyczaj nie są wystarczające, aby zapewnić środki do umieszczenia dołączanych wartości elementów członkowskich na wykresie obiektu lub do pobierania wartości z wykresu obiektu i serializować je poprawnie. Aby zapewnić tę funkcję, `target` obiekty w poprzednich podpisów akcesor musi być zdolny do przechowywania wartości. Mechanizm magazynowania powinny być zgodne z zasadą dołączania elementu członkowskiego, że element członkowski jest dołączony do obiektów docelowych, gdzie dołączany element członkowski nie znajduje się na liście członków. Usługi .NET XAML services zapewniają technikę implementacji dla <xref:System.Xaml.IAttachedPropertyStore> <xref:System.Xaml.AttachablePropertyServices>dołączanych magazynów elementów członkowskich za pośrednictwem interfejsów API i . <xref:System.Xaml.IAttachedPropertyStore>jest używany przez moduły zapisu XAML do odnajdowania implementacji magazynu i powinny być implementowane na typ, który jest `target` akcesorów. Statyczne <xref:System.Xaml.AttachablePropertyServices> interfejsy API są używane w treści akcesorów i <xref:System.Xaml.AttachableMemberIdentifier>odnoszą się do dołączanego elementu członkowskiego przez jego .

## <a name="xaml-related-clr-attributes"></a>Atrybuty CLR związane z XAML

Poprawne przypisywanie typów, elementów członkowskich i zestawów jest ważne w celu raportowania informacji o systemie typu XAML do usług .NET XAML Services. Raportowanie informacji o systemie typu XAML jest istotne, jeśli ma zastosowanie do jednej z następujących sytuacji:

- Typy mają być używane z systemami XAML, które są bezpośrednio oparte na czytnikach XAML usług .NET XAML i modułach zapisu XAML.
- Definiujesz lub używasz platformy wykorzystującej XAML, która jest oparta na tych czytnikach XAML i modułach zapisujących XAML.

Aby uzyskać listę każdego atrybutu związanego z XAML, który jest odpowiedni dla obsługi XAML typów niestandardowych, zobacz [Atrybuty CLR związane z XAML dla typów niestandardowych i bibliotek](clr-attributes-with-custom-types-and-libraries.md).

## <a name="usage"></a>Sposób użycia

Użycie typów niestandardowych wymaga, aby autor znaczników mapować prefiks dla zestawu i obszaru nazw CLR, które zawierają typ niestandardowy. Ta procedura nie jest udokumentowana w tym temacie.

## <a name="access-level"></a>Poziom dostępu

XAML zapewnia możliwość ładowania i tworzenia wystąpienia `internal` typów, które mają poziom dostępu. Ta możliwość jest dostępna, dzięki czemu kod użytkownika można zdefiniować własne typy, a następnie utworzyć wystąpienia tych klas z znaczników, który jest również częścią tego samego zakresu kodu użytkownika.

Przykład z WPF jest zawsze, gdy <xref:System.Windows.Controls.UserControl> kod użytkownika definiuje, który jest przeznaczony jako sposób refaktoryzacji zachowanie interfejsu użytkownika, ale nie jako `public` część dowolnego mechanizmu rozszerzenia możliwe, które mogą być implikowane przez zadeklarowanie klasy pomocniczej z poziomem dostępu. Takie <xref:System.Windows.Controls.UserControl> można zadeklarować `internal` z dostępem, jeśli kod zapasowy jest kompilowany do tego samego zestawu, z którego odwołuje się jako typ XAML.

Dla aplikacji, która ładuje XAML w <xref:System.Xaml.XamlObjectWriter>pełnej `internal` relacji zaufania i używa, ładowanie klas z poziomem dostępu jest zawsze włączone.

Dla aplikacji, która ładuje XAML w ramach częściowego zaufania, <xref:System.Xaml.Permissions.XamlAccessLevel> można kontrolować charakterystyki poziomu dostępu przy użyciu interfejsu API. Ponadto mechanizmy odroczenia (takie jak system szablonów WPF) muszą mieć możliwość propagowania wszelkich uprawnień na poziomie dostępu i zachowywania ich dla ewentualnych ocen czasu wykonywania; jest to obsługiwane wewnętrznie przez <xref:System.Xaml.Permissions.XamlAccessLevel> przekazywanie informacji.

### <a name="wpf-implementation"></a>Implementacja WPF

WPF XAML używa modelu dostępu częściowego zaufania, gdzie jeśli BAML jest <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> ładowany w ramach częściowego zaufania, dostęp jest ograniczony do zestawu, który jest źródłem BAML. Dla odroczenia WPF <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> używa jako mechanizm przekazywania informacji o poziomie dostępu.

W terminologii WPF XAML *typ wewnętrzny* jest typem zdefiniowanym przez ten sam zestaw, który zawiera również odwołanie XAML. Taki typ można mapować za pomocą przestrzeni nazw XAML, która celowo pomija assembly= `xmlns:local="clr-namespace:WPFApplication1"`część mapowania, na przykład . Jeśli BAML odwołuje się do typu `internal` wewnętrznego i ten `GeneratedInternalTypeHelper` typ ma poziom dostępu, generuje klasę dla zestawu. Jeśli chcesz uniknąć `GeneratedInternalTypeHelper`, należy użyć `public` poziomu dostępu lub musi czynnikiem odpowiedniej klasy w oddzielnym zestawie i uzależnić ten zestaw.

## <a name="see-also"></a>Zobacz też

- [Atrybuty CLR związane z XAML dla niestandardowych typów i bibliotek](clr-attributes-with-custom-types-and-libraries.md)
- [Usługi XAML](../../../api/index.md)
