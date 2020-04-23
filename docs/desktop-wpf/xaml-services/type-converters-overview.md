---
title: Typy konwerterów dla XAML — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: c3c69aebacd140a14e74545d601c0207cb8de681
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071634"
---
# <a name="overview-of-type-converters-for-xaml"></a>Omówienie konwerterów typów dla XAML

Konwertery typów dostarczają logikę modułu zapisującego obiekt, który konwertuje z ciągu w znacznikach XAML na określone obiekty na wykresie obiektu. W usługach .NET XAML konwerter typów musi być <xref:System.ComponentModel.TypeConverter>klasą wywodzącą się z . Niektóre konwertery obsługują również ścieżkę zapisywania XAML i mogą być używane do serializacji obiektu w formie ciągu w znacznikach serializacji. W tym temacie opisano sposób i kiedy wywoływane są konwertery typów w <xref:System.ComponentModel.TypeConverter>języku XAML oraz przedstawiono porady dotyczące implementacji zastąpienia metody .

## <a name="type-conversion-concepts"></a>Pojęcia konwersji typu

W poniższych sekcjach wyjaśniono podstawowe pojęcia dotyczące sposobu używania ciągów XAML i sposobu, w jaki moduły zapisu obiektów w usługach .NET XAML używają konwerterów typów do przetwarzania niektórych wartości ciągów napotkanych w źródle XAML.

### <a name="xaml-and-string-values"></a>Wartości XAML i string

Po ustawieniu wartości atrybutu w pliku XAML początkowy typ tej wartości jest ciągiem w sensie ogólnym i wartością atrybutu ciągu w sensie XML. Nawet inne podstawowe, takie <xref:System.Double> jak początkowo ciągi do procesora XAML.

W większości przypadków procesor XAML potrzebuje dwóch informacji do przetworzenia wartości atrybutu. Pierwszą informacją jest typ wartości właściwości, która jest ustawiana. Każdy ciąg definiujący wartość atrybutu i przetwarzany w języku XAML musi ostatecznie zostać przekonwertowany lub rozpoznany na wartość tego typu. Jeśli wartość jest prymitywne, który jest rozumiany przez analizatora XAML (na przykład wartość liczbową), podejmowana jest bezpośrednia konwersja ciągu. Jeśli wartość atrybutu odwołuje się do wyliczenia, podany ciąg jest sprawdzany pod kątem dopasowania nazwy do stałej o nazwie w tym wyliczeniu. Jeśli wartość nie jest analizatorem zrozumianym elementem pierwotnym lub stałą nazwą z wyliczenia, odpowiedni typ musi być w stanie podać wartość lub odwołanie oparte na przekonwertowanym ciągu.

> [!NOTE]
> Dyrektywy języka XAML nie używają konwerterów typów.

### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników

Użycie rozszerzenia znaczników musi być obsługiwane przez procesor XAML, zanim sprawdzi typ właściwości i inne zagadnienia. Na przykład jeśli właściwość ustawiona jako atrybut zwykle ma konwersję typu, ale w określonym przypadku jest ustawiana przez użycie rozszerzenia znaczników, a następnie najpierw procesy zachowania rozszerzenia znaczników. Jedną z typowych sytuacji, w której rozszerzenie znaczników jest konieczne jest odwołanie do obiektu, który już istnieje. W tym scenariuszu konwerter typu bezstanowego może generować tylko nowe wystąpienie, co może nie być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników dla XAML Overview](markup-extensions-overview.md).

### <a name="native-type-converters"></a>Konwertery typów natywnych

W windows presentation foundation (WPF) i .NET XAML services implements, istnieją pewne typy CLR, które mają obsługi konwersji typu macierzystego. Jednak te typy CLR nie są konwencjonalnie traktowane jako prymitywy. Przykładem takiego typu <xref:System.DateTime>jest . Jednym z powodów jest to, jak działa <xref:System.DateTime> architektura .NET Framework: typ jest zdefiniowany w mscorlib, najbardziej podstawowej biblioteki w .NET. <xref:System.DateTime>nie można przypisać z atrybutem, który pochodzi z innego zestawu,<xref:System.ComponentModel.TypeConverterAttribute> który wprowadza zależność (jest z systemu). W związku z tym mechanizm odnajdowania konwertera typ zwykle przez przypisanie nie mogą być obsługiwane. Zamiast tego analizator XAML ma listę typów, które wymagają przetwarzania natywnego i przetwarza te typy podobne do sposobu przetwarzania prawdziwych elementów pierwotnych. W przypadku <xref:System.DateTime>, przetwarzanie to wiąże <xref:System.DateTime.Parse%2A>się z wezwaniem do .

## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów

W poniższych sekcjach omówiono interfejs API <xref:System.ComponentModel.TypeConverter> klasy.

### <a name="typeconverter"></a>TypeConverter

W obszarze Usługi XAML .NET wszystkie konwertery typów używane do celów XAML są klasami pochodzącymi z klasy podstawowej <xref:System.ComponentModel.TypeConverter>. Klasa <xref:System.ComponentModel.TypeConverter> istniała w wersjach programu .NET Framework przed istnieniem kodu XAML; jednym z <xref:System.ComponentModel.TypeConverter> oryginalnych scenariuszy było zapewnienie konwersji ciągów dla edytorów właściwości w projektantów wizualnych.

W przypadku XAML <xref:System.ComponentModel.TypeConverter> rola jest rozszerzana. Dla celów XAML <xref:System.ComponentModel.TypeConverter> jest klasą podstawową zapewniającą obsługę niektórych konwersji ciągów i ciągów. From-string umożliwia analizowanie wartości atrybutu ciągu z XAML. Ciąg do ciągu może włączyć przetwarzanie wartości wykonywania właściwości określonego obiektu z powrotem do atrybutu w języku XAML do serializacji.

<xref:System.ComponentModel.TypeConverter>definiuje cztery elementy członkowskie, które są istotne dla konwersji do ciągu i z ciągu do celów przetwarzania XAML:

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Z tych elementów członkowskich <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>najważniejszą metodą jest , która konwertuje ciąg wejściowy na wymagany typ obiektu. Metodę <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> można zaimplementować w celu konwersji szerszego zakresu typów na zamierzony typ docelowy konwertera. W związku z tym może służyć do celów, które wykraczają poza XAML, takich jak obsługa konwersji w czasie wykonywania. Jednak dla użycia XAML tylko ścieżka kodu, <xref:System.String> który może przetwarzać dane wejściowe jest ważne.

Drugą najważniejszą metodą jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentację znaczników (na przykład, jeśli <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest zapisywana w formacie XAML jako plik), jest zaangażowana w większy scenariusz modułu zapisującego tekst XAML w celu uzyskania reprezentacji znaczników. W takim przypadku ważnego kodu ścieżki dla XAML `destinationType` jest, gdy wywołujący przechodzi z <xref:System.String>.

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metody pomocy technicznej, które są używane, <xref:System.ComponentModel.TypeConverter> gdy usługa wysyła zapytanie możliwości implementacji. Należy zaimplementować `true` te metody, aby zwrócić dla przypadków specyficznych dla typu, które równoważne metody konwersji obsługi konwertera. Do celów XAML oznacza to <xref:System.String> zazwyczaj typ.

### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o kulturze i konwertery typów dla XAML

Każda <xref:System.ComponentModel.TypeConverter> implementacja może jednoznacznie interpretować, co jest prawidłowym ciągiem dla konwersji, a także może użyć lub zignorować opis typu, który jest przekazywany jako parametry. Ważną kwestią dla kultury i konwersji typu XAML jest następująca: chociaż przy użyciu localizable ciągów jako wartości atrybutów jest obsługiwany przez XAML, nie można użyć tych ciągów localizable jako dane wejściowe konwertera typów z określonymi wymaganiami kultury. To ograniczenie jest, ponieważ konwertery typów dla wartości atrybutów XAML obejmują `en-US` koniecznie stałe zachowanie przetwarzania XAML języka, który używa kultury. Aby uzyskać więcej informacji na temat przyczyn projektowania tego ograniczenia, zobacz specyfikację języka XAML[\[(MS-XAML)\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))lub [Omówienie globalizacji i lokalizacji WPF.](../../framework/wpf/advanced/wpf-globalization-and-localization-overview.md)

Jako przykład, gdzie kultura może być problemem, niektóre kultury użyć przecinka zamiast kropki jako ogranicznik punktu dziesiętnego dla liczb w postaci ciągu. To użycie zderza się z zachowaniem, które ma wiele istniejących konwerterów typów, które ma używać przecinka jako ogranicznika. Przekazywanie kultury `xml:lang` w otaczającym XAML nie rozwiązuje problemu.

### <a name="implementing-convertfrom"></a>Implementowanie convertfrom

Aby być użytecznym <xref:System.ComponentModel.TypeConverter> jako implementacja, która <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> obsługuje XAML, metoda dla `value` tego konwertera musi zaakceptować ciąg jako parametr. Jeśli ciąg jest w prawidłowym formacie i <xref:System.ComponentModel.TypeConverter> mogą być konwertowane przez implementację, zwrócony obiekt musi obsługiwać rzutowania do typu, który jest oczekiwany przez właściwość. W przeciwnym <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> razie `null`implementacja musi zwrócić .

Każda <xref:System.ComponentModel.TypeConverter> implementacja może jednoznacznie interpretować, co stanowi prawidłowy ciąg dla konwersji, a także można użyć lub zignorować opis typu lub konteksty kultury, które są przekazywane jako parametry. Jednak przetwarzanie WPF XAML może nie przekazać wartości do kontekstu opisu typu `xml:lang`we wszystkich przypadkach, a także może nie przekazać kultury na podstawie .

> [!NOTE]
> Nie należy używać nawiasów klamrowych ({}), w szczególności nawiasu klamrowego otwierającego ({) jako elementu formatu ciągu. Znaki te są zarezerwowane jako wejście i wyjście dla sekwencji rozszerzenia znaczników.

Jest właściwe, aby zgłosić wyjątek, gdy konwerter typu musi mieć dostęp do usługi XAML z .NET XAML Services modułu zapisującego obiektów, ale <xref:System.IServiceProvider.GetService%2A> wywołanie, które jest wykonane w kontekście nie zwraca tej usługi.

### <a name="implementing-convertto"></a>Implementowanie convertto

<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>jest potencjalnie używany do obsługi serializacji. Obsługa serializacji <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla typu niestandardowego i jego konwertera typu nie jest bezwzględnym wymaganiem. Jednak jeśli implementujesz formant lub używasz serializacji jako części funkcji lub projektu klasy, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>program .

Aby być użytecznym <xref:System.ComponentModel.TypeConverter> jako implementacja, która <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> obsługuje XAML, metoda dla tego konwertera musi zaakceptować `value` wystąpienie typu (lub wartość), który jest obsługiwany jako parametr. Gdy `destinationType` parametr jest <xref:System.String>typu, zwracany obiekt musi być <xref:System.String>w stanie być rzutowy jako . Zwrócony ciąg musi reprezentować `value`wartość serializowany . W idealnym przypadku format serializacji, który wybierzesz powinien być w stanie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> wygenerować taką samą wartość, jak gdyby ten ciąg zostały przekazane do implementacji tego samego konwertera, bez znacznej utraty informacji.

Jeśli wartość nie może być serializowany lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementacja musi zwrócić `null` i może zgłosić wyjątek. Jednak jeśli zgłosisz wyjątki, należy zgłosić niemożność <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> użycia tej konwersji jako część <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, tak aby najlepsze rozwiązanie sprawdzania z pierwszym, aby uniknąć wyjątków jest obsługiwana.

Jeśli `destinationType` parametr nie jest <xref:System.String>typu, można wybrać własną obsługę konwertera. Zazwyczaj można przywrócić do obsługi implementacji podstawowej, która w bazie <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zgłasza określony wyjątek.

Jest właściwe, aby zgłosić wyjątek, gdy konwerter typu musi mieć dostęp do usługi XAML z .NET XAML Services modułu zapisującego obiektów, ale <xref:System.IServiceProvider.GetService%2A> wywołanie, które jest wykonane w kontekście nie zwraca tej usługi.

### <a name="implementing-canconvertfrom"></a>Implementacja CanConvertFrom

Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna `true` `sourceType` powrócić <xref:System.String> do typu i w inny sposób odroczyć do implementacji podstawowej. Nie zgłaszaj wyjątków od <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.

### <a name="implementing-canconvertto"></a>Implementacja CanConvertTo

Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna `true` `destinationType` powrócić <xref:System.String>do typu i w inny sposób odroczyć do implementacji podstawowej. Nie zgłaszaj wyjątków od <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.

## <a name="applying-the-typeconverterattribute"></a>Stosowanie atrybutu TypeConverterAttribute

Aby konwerter typów niestandardowych był używany jako konwerter typów działających dla klasy niestandardowej <xref:System.ComponentModel.TypeConverterAttribute> przez usługi .NET XAML services, należy zastosować do definicji klasy. Określony <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> przez atrybut musi być nazwą typu konwertera typu niestandardowego. Jeśli zastosujesz ten atrybut, gdy procesor XAML obsługuje wartości, w których typ właściwości używa niestandardowego typu klasy, może wprowadzać ciągi i zwracać wystąpienia obiektów.

Można również podać konwerter typów na podstawie dla właściwości. Zamiast stosować <xref:System.ComponentModel.TypeConverterAttribute> a do definicji klasy, należy zastosować go do definicji `get` / `set` właściwości (główna definicja, a nie implementacje w niej). Typ właściwości musi odpowiadać typowi, który jest przetwarzany przez konwerter typu niestandardowego. Zastosowany ten atrybut, gdy procesor XAML obsługuje wartości tej właściwości, może przetwarzać ciągi wejściowe i zwracać wystąpienia obiektów. Technika konwertera typu na właściwość jest przydatna, jeśli wybierzesz użycie typu właściwości z programu Microsoft .NET Framework lub innej biblioteki, w której nie można kontrolować definicji klasy i nie można <xref:System.ComponentModel.TypeConverterAttribute> jej zastosować.

Aby podać zachowanie konwersji typu dla niestandardowego dołączonego elementu członkowskiego, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do metody `Get` akcesora wzorca implementacji dołączonego elementu członkowskiego.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenia znaczników

Dostępne usługi są takie same dla każdego konwertera wartości. Różnica polega na tym, jak każdy konwerter wartości odbiera kontekst usługi. Dostęp do usług i dostępnych usług są udokumentowane w temacie [Konwertery typów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md).

## <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typów w strumieniu węzłów XAML

Jeśli pracujesz ze strumieniem węzła XAML, akcja lub wynik końcowy konwertera typu nie jest jeszcze wykonywany. W ścieżce ładowania ciąg atrybutu, który ostatecznie musi zostać przekonwertowany na typ, aby załadować pozostaje jako wartość tekstowa w obrębie elementu członkowskiego początkowego i końcowego. Konwerter typu, który jest ostatecznie potrzebny dla tej <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> operacji można określić za pomocą właściwości. Jednak uzyskanie prawidłowej wartości <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> z opiera się na posiadaniu kontekstu schematu XAML, który może uzyskać dostęp do takich informacji za pośrednictwem elementu członkowskiego lub typu wartości obiektu, który używa elementu członkowskiego. Wywoływanie zachowania konwersji typu wymaga również kontekstu schematu XAML, ponieważ wymaga to mapowania typu i tworzenia wystąpienia konwertera.

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions.md)
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
