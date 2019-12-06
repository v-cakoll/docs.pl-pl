---
title: Typy konwerterów dla XAML — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 65210d8224b145ab23c7bc9ed76997c0892a5f59
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837262"
---
# <a name="type-converters-for-xaml-overview"></a>Typy konwerterów dla XAML — Omówienie
Typy konwerterów dostarczają logiki dla składnika zapisywania obiektów, który konwertuje z ciągu znaków XAML na określone obiekty w grafie obiektów. W .NET Framework usługach XAML konwerter typów musi być klasą pochodzącą z <xref:System.ComponentModel.TypeConverter>. Niektóre konwertery obsługują również ścieżkę zapisu XAML i mogą służyć do serializacji obiektu w postaci ciągu w znaczniku serializacji. W tym temacie opisano, jak i kiedy są wywoływane konwertery typów w języku XAML, i przedstawiono porady dotyczące implementacji metod zastąpień <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typów  
 W poniższych sekcjach objaśniono podstawowe pojęcia dotyczące korzystania z ciągów przez XAML oraz sposób, w jaki autorzy obiektów w .NET Framework usługach XAML używają konwerterów typów do przetwarzania niektórych wartości ciągów, które są napotkane w źródle XAML.  
  
### <a name="xaml-and-string-values"></a>Wartości XAML i String  
 Po ustawieniu wartości atrybutu w pliku XAML, początkowy typ tej wartości jest ciągiem w ogólnym sensie, a wartość atrybutu String w sensie XML. Nawet inne elementy podstawowe, takie jak <xref:System.Double>, są początkowo ciągami do procesora XAML.  
  
 W większości przypadków procesor XAML wymaga dwóch informacji do przetworzenia wartości atrybutu. Pierwsza część informacji jest typem wartości właściwości, która jest ustawiana. Dowolny ciąg, który definiuje wartość atrybutu i który jest przetwarzany w języku XAML, musi ostatecznie być konwertowany lub rozpoznany jako wartość tego typu. Jeśli wartość jest typem podstawowym, który jest zrozumiały dla analizatora XAML (na przykład wartość liczbowa), podejmowana jest bezpośrednia Konwersja ciągu. Jeśli wartość atrybutu odwołuje się do wyliczenia, dostarczony ciąg jest sprawdzany pod kątem zgodności nazw z nazwaną stałą w tym wyliczeniu. Jeśli wartość nie jest rozpoznawana jako pierwotna ani stała z wyliczeniem, odpowiedni typ musi być w stanie podać wartość lub odwołanie, które jest oparte na przekonwertowanym ciągu.  
  
> [!NOTE]
> Dyrektywy języka XAML nie używają konwerterów typów.  
  
### <a name="type-converters-and-markup-extensions"></a>Konwertery typów i rozszerzenia znaczników  
 Użycie rozszerzeń znaczników musi być obsługiwane przez procesor XAML przed sprawdzeniem typu właściwości i innych zagadnień. Na przykład, jeśli właściwość ustawiana jako atrybut zwykle ma konwersję typu, ale w konkretnym przypadku jest ustawiana za pomocą rozszerzenia znaczników, wówczas zachowanie rozszerzenia znaczników jest najpierw przetwarzane. Jedną z typowych sytuacji, gdy wymagane jest rozszerzenie znaczników, jest odwołanie do obiektu, który już istnieje. W tym scenariuszu konwerter typu bezstanowego może generować tylko nowe wystąpienie, które może nie być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [znaczniki rozszerzeń dla języka XAML — Omówienie](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Konwertery typów natywnych  
 W implementacjach usług WPF i .NET XAML istnieją pewne typy CLR, które mają obsługę konwersji typu natywnego, ale te typy CLR nie są zwyczajowo uważane za elementy pierwotne. Przykładem takiego typu jest <xref:System.DateTime>. Jednym z powodów tego jest to, jak działa architektura .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w bibliotece Mscorlib, a najbardziej podstawowa Biblioteka w programie .NET. <xref:System.DateTime> nie może mieć atrybutu, który pochodzi z innego zestawu, który wprowadza zależność (<xref:System.ComponentModel.TypeConverterAttribute> pochodzi z systemu); w związku z tym nie można obsługiwać standardowego mechanizmu wykrywania konwertera typów przez przypisanie. Zamiast tego Analizator XAML ma listę typów, które wymagają przetwarzania natywnego, i przetwarza te typy podobnie jak w przypadku przetwarzania prawdziwych elementów podstawowych. W przypadku <xref:System.DateTime>przetwarzanie obejmuje wywołanie <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
 W poniższych sekcjach omówiono interfejs API klasy <xref:System.ComponentModel.TypeConverter>.  
  
### <a name="typeconverter"></a>TypeConverter  
 W obszarze .NET Framework usług XAML wszystkie konwertery typów, które są używane na potrzeby języka XAML, są klasami pochodnymi od klasy bazowej <xref:System.ComponentModel.TypeConverter>. Klasa <xref:System.ComponentModel.TypeConverter> istniała w wersjach .NET Framework przed istniejącą XAML; jednym z oryginalnych scenariuszy <xref:System.ComponentModel.TypeConverter> było zapewnienie konwersji ciągów dla edytorów właściwości w projektantach wizualizacji.  
  
 W przypadku języka XAML rola <xref:System.ComponentModel.TypeConverter> jest rozwinięta. W celach XAML <xref:System.ComponentModel.TypeConverter> jest klasą bazową w celu zapewnienia obsługi określonych ciągów i konwersji ciągów. Parametry from umożliwiają analizowanie wartości atrybutu String z XAML. Ciąg może umożliwiać przetwarzanie wartości właściwości określonego obiektu z powrotem do atrybutu w kodzie XAML dla serializacji.  
  
 <xref:System.ComponentModel.TypeConverter> definiuje cztery składowe, które mają zastosowanie do konwertowania ciągu na ciąg i ciągu na potrzeby przetwarzania kodu XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych elementów członkowskich jest <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>najważniejsze metody, które konwertuje ciąg wejściowy na wymagany typ obiektu. Metodę <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> można zaimplementować w celu przekonwertowania szerszego zakresu typów na zamierzony typ docelowy konwertera. W związku z tym może obsługiwać cele wykraczające poza kod XAML, takie jak obsługa konwersji w czasie wykonywania. Jednak w przypadku użycia XAML tylko ścieżka kodu, która może przetwarzać dane wejściowe <xref:System.String>, jest ważna.  
  
 Druga z najważniejszych metod jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentację znaczników (na przykład jeśli została zapisana w języku XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest uwzględniany w większym scenariuszu autorów tekstu XAML, generującym reprezentację znaczników. W takim przypadku ważnym ścieżką kodu dla języka XAML jest, gdy wywołujący przekaże `destinationType` <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metodami obsługi, które są używane, gdy usługa wysyła zapytanie do możliwości implementacji <xref:System.ComponentModel.TypeConverter>. Należy zaimplementować te metody, aby zwracać `true` dla przypadków specyficznych dla typów, które są równoważnymi metodami konwersji konwertera. Na potrzeby języka XAML zazwyczaj oznacza to, że typ <xref:System.String>.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o kulturze i konwertery typów dla języka XAML  
 Każda implementacja <xref:System.ComponentModel.TypeConverter> może jednoznacznie interpretować, co jest prawidłowym ciągiem dla konwersji, i może również używać lub ignorować opis typu, który jest przesyłany jako parametry. Ważnym zagadnieniem dotyczącym konwersji kultury i języka XAML są następujące: Chociaż użycie lokalizowalnych ciągów jako wartości atrybutów jest obsługiwane przez język XAML, nie można używać tych lokalizowalnych ciągów jako danych wejściowych konwertera typów z określonymi wymaganiami kultury. To ograniczenie wynika z faktu, że konwertery typów dla wartości atrybutów XAML obejmują niekoniecznie stosowane w języku XAML zachowanie w zakresie przetwarzania, które używa `en-US` kulturę. Aby uzyskać więcej informacji na temat przyczyn związanych z projektowaniem tego ograniczenia, zobacz Specyfikacja języka XAML ([\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))) lub [Omówienie globalizacji i lokalizacji platformy WPF](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Przykładowo, gdy kultura może być problemem, niektóre kultury używają przecinka zamiast kropki jako ogranicznika przecinka dziesiętnego dla liczb w postaci ciągów. To użycie koliduje z zachowaniem wielu istniejących konwerterów typów, które ma używać przecinka jako ogranicznika. Przekazanie kultury przez `xml:lang` w otaczającym XAML nie rozwiąże problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Aby można było użyć implementacji <xref:System.ComponentModel.TypeConverter>, która obsługuje XAML, Metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> dla tego konwertera musi akceptować ciąg jako parametr `value`. Jeśli ciąg jest w prawidłowym formacie i może zostać przekonwertowany przez implementację <xref:System.ComponentModel.TypeConverter>, zwracany obiekt musi obsługiwać rzutowanie do typu, który jest oczekiwany przez właściwość. W przeciwnym razie implementacja <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musi zwracać `null`.  
  
 Każda implementacja <xref:System.ComponentModel.TypeConverter> może jednoznacznie interpretować, co stanowi prawidłowy ciąg dla konwersji, i może również używać lub ignorować opis typu lub kontekstów kultury, które są przenoszone jako parametry. Jednak przetwarzanie kodu XAML WPF może nie przekazywać wartości do kontekstu opisu typu we wszystkich przypadkach, a także może nie przekazywać kultury na podstawie `xml:lang`.  
  
> [!NOTE]
> Nie używaj nawiasów klamrowych ({}), a w odniesieniu do nawiasu otwierającego ({) jako elementu w formacie ciągu. Te znaki są zarezerwowane jako wejście i wyjście dla sekwencji rozszerzenia znaczników.  
  
 Jest to konieczne, aby zgłosić wyjątek, gdy konwerter typu musi mieć dostęp do usługi XAML z .NET Framework zapisywania obiektów usług XAML, ale wywołanie <xref:System.IServiceProvider.GetService%2A>, które jest wykonywane względem kontekstu, nie zwraca tej usługi.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest potencjalnie używany do obsługi serializacji. Obsługa serializacji za pomocą <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla typu niestandardowego i jego konwertera typów nie jest wymaganiem bezwzględnym. Jednakże w przypadku implementowania kontrolki lub korzystania z serializacji jako części funkcji lub projektu klasy należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby można było użyć implementacji <xref:System.ComponentModel.TypeConverter>, która obsługuje XAML, Metoda <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla tego konwertera musi akceptować wystąpienie typu (lub wartość), które jest obsługiwane jako parametr `value`. Gdy parametr `destinationType` jest typu <xref:System.String>, zwracany obiekt musi być w stanie rzutować jako <xref:System.String>. Zwrócony ciąg musi reprezentować serializowaną wartość `value`. W idealnym przypadku wybrany przez Ciebie format serializacji powinien być w stanie generować tę samą wartość, co w przypadku, gdy ten ciąg został przekazano do implementacji <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> tego samego konwertera, bez znacznej utraty informacji.  
  
 Jeśli wartość nie może być serializowana lub konwerter nie obsługuje serializacji, implementacja <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musi zwrócić `null` i może zgłosić wyjątek. Jednakże w przypadku zgłaszania wyjątków należy zgłosić niezdolność do użycia tej konwersji w ramach implementacji <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>, dzięki czemu najlepszym rozwiązaniem w zakresie sprawdzania z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>, aby uniknąć wyjątków.  
  
 Jeśli parametr `destinationType` nie jest typu <xref:System.String>, można wybrać własny sposób obsługi konwertera. Zwykle przywracana jest podstawowa obsługa implementacji, która w podstawowym <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> wywołuje konkretny wyjątek.  
  
 Jest to konieczne, aby zgłosić wyjątek, gdy konwerter typu musi mieć dostęp do usługi XAML z .NET Framework zapisywania obiektów usług XAML, ale wywołanie <xref:System.IServiceProvider.GetService%2A>, które jest wykonywane względem kontekstu, nie zwraca tej usługi.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna zwracać `true` `sourceType` typu <xref:System.String> i w przeciwnym razie przełożyć na implementację podstawową. Nie zgłaszaj wyjątków z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna zwracać `true` `destinationType` typu <xref:System.String>i w przeciwnym razie odroczyć na implementację podstawową. Nie zgłaszaj wyjątków z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Dla niestandardowego konwertera typów, który ma być używany jako typ działającego konwertera klasy niestandardowej przez .NET Framework usług XAML, należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> określona za pomocą atrybutu musi być nazwą typu niestandardowego konwertera typów. W przypadku zastosowania tego atrybutu, gdy procesor XAML obsługuje wartości, w których typ właściwości używa typu klasy niestandardowej, może wprowadzać ciągi i zwracać wystąpienia obiektów.  
  
 Można również udostępnić konwerter typów dla poszczególnych właściwości. Zamiast stosowania <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy, należy zastosować je do definicji właściwości (głównej definicji, a nie `get`/`set` implementacji w ramach tego elementu). Typ właściwości musi być zgodny z typem, który jest przetwarzany przez konwerter typów niestandardowych. Po zastosowaniu tego atrybutu, gdy procesor XAML obsługuje wartości tej właściwości, może przetwarzać ciągi wejściowe i zwracać wystąpienia obiektów. Technika konwertera typów dla właściwości jest szczególnie przydatna, jeśli zdecydujesz się użyć typu właściwości z Microsoft .NET Framework lub z innej biblioteki, w której nie można kontrolować definicji klasy i nie można zastosować <xref:System.ComponentModel.TypeConverterAttribute> tam.  
  
 Aby podać zachowanie konwersji typu dla niestandardowego dołączonego elementu członkowskiego, Zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do metody dostępu `Get` wzorca implementacji dla dołączonego elementu członkowskiego.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenia znaczników  
 Dostępne usługi są takie same dla dowolnego konwertera wartości. Różnica polega na tym, jak każdy konwerter wartości otrzymuje kontekst usługi. Dostęp do usług i dostępnych usług są udokumentowane w sekcji [konwertery typów i rozszerzenia znaczników dla języka XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typów w strumieniu węzła XAML  
 Jeśli pracujesz ze strumieniem węzła XAML, Akcja lub wynik końcowy konwertera typów nie został jeszcze wykonany. W ścieżce ładowania ciąg atrybutu, który ostatecznie musi być przekonwertowany na typ, w celu załadowania pozostanie jako wartość tekstowa w obrębie początkowego elementu członkowskiego i końcowego elementu członkowskiego. Konwerter typu, który jest ostatecznie potrzebny do wykonania tej operacji można określić za pomocą właściwości <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType>. Jednak uzyskanie prawidłowej wartości z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> polega na wykorzystaniu kontekstu schematu XAML, który może uzyskać dostęp do takich informacji za pośrednictwem bazowego elementu członkowskiego lub typu wartości obiektu używanej przez element członkowski. Wywoływanie zachowania konwersji typu wymaga również kontekstu schematu XAML, ponieważ wymaga on mapowania typów i tworzenia wystąpienia konwertera.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
