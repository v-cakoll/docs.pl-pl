---
title: Typy konwerterów dla XAML — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: cf9eda484d184b9be70a02bac7ced5b85a2dd211
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617218"
---
# <a name="type-converters-for-xaml-overview"></a>Typy konwerterów dla XAML — Omówienie
Typ logika dostawa konwerterów modułu zapisywania obiektu, który konwertuje z ciągu w znaczniku XAML, w szczególności obiekty wykresu obiektu. W programie .NET Framework XAML Services konwertera typów musi być klasą pochodzącą z <xref:System.ComponentModel.TypeConverter>. Niektóre konwertery również obsługuje XAML ścieżka zapisu i może służyć do serializacji obiektu do postaci ciągu w znacznikach serializacji. W tym temacie opisano, jak i kiedy są wywoływane konwerterów typów w XAML i zawiera porady, implementacja dla przesłonięć metod elementu <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typu  
 W poniższych sekcjach opisano podstawowe pojęcia o używaniu XAML na ciągi znaków, i sposobie używania przez obiekt zapisujących usług programu .NET Framework XAML konwerterów typów do przetwarzania niektórych wartości ciągów, które występują w źródle XAML.  
  
### <a name="xaml-and-string-values"></a>Wartości parametrów i XAML  
 Gdy wartość atrybutu jest ustawiona w pliku XAML, początkowy typ tej wartości jest ciąg znaków w ogólnym sensie, a wartość atrybutu ciągu w sensie XML. Nawet w innych elementów podstawowych, takich jak <xref:System.Double> są początkowo ciągi z procesorem XAML.  
  
 W większości przypadków procesora XAML potrzebuje dwóch informacji w celu przetworzenia wartość atrybutu. Pierwsza część informacji jest typ wartości właściwości, która jest ustawiona. Dowolny ciąg, który definiuje wartość atrybutu i przetworzony w XAML ostatecznie musi być konwertowany lub rozwiązać wartość tego typu. Jeśli wartość jest elementu podstawowego, który zrozumieniu przez parser XAML (na przykład wartość liczbowa), to bezpośrednia konwersji ciągu zostanie podjęta. Jeśli wartość atrybutu odwołuje się do wyliczenia, podany ciąg jest sprawdzany pod kątem dopasowania nazwy do nazwanej stałej w tym wyliczeniu. Jeśli wartość jest podstawowy rozumieć analizatora ani nazwę stałe, wyliczenia, odpowiedni typ musi być możliwość zapewnienia wartości lub odwołania, który jest oparty na ciąg przekonwertowany.  
  
> [!NOTE]
>  Dyrektywy języka XAML, nie należy używać konwerterów typów.  
  
### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników  
 Użycia rozszerzenia znaczników muszą być obsługiwane przez procesor XAML, przed zarejestrowaniem typ właściwości i inne zagadnienia. Na przykład jeśli właściwość zostanie ustawiony, ponieważ atrybut ma zwykle konwersji typu, ale w przypadku określonego jest ustawiony przez użycie rozszerzenia znaczników, następnie zachowania rozszerzeń znaczników przetwarza najpierw. Jedna sytuacja typowe, gdy jest konieczne rozszerzenie znaczników jest odwołaniem do obiektu, który już istnieje. W tym scenariuszu konwertera typów o bezstanowa może generować jedynie nowe wystąpienie nie może być pożądane. Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Konwertery typu natywnego  
 W implementacji usług WPF i .NET, XAML istnieją pewne typy CLR, które mają obsługi konwersji typu natywnego, jednak te typy CLR są nie tradycyjnie traktować jako elementów podstawowych. Na przykład taki typ <xref:System.DateTime>. Co dzieje się jak architektura .NET Framework działa: typ <xref:System.DateTime> jest zdefiniowany w mscorlib, podstawowe biblioteki na platformie .NET. <xref:System.DateTime> nie ma zezwolenia na można przypisać za pomocą atrybutu, który pochodzi z innego zestawu, który wprowadza zależność (<xref:System.ComponentModel.TypeConverterAttribute> pochodzi z systemu); w związku z tym, mechanizm odnajdywania konwertera typu zwykle poprzez przypisywanie nie są obsługiwane. Zamiast tego analizatora XAML zawiera listę typów, które muszą natywne przetwarzanie i przetwarza te typy, które są podobne do przetwarzaniu prymitywów wartość true. W przypadku właściwości <xref:System.DateTime>, przetwarzania obejmuje wywołanie <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
 W poniższych sekcjach omówiono interfejsu API <xref:System.ComponentModel.TypeConverter> klasy.  
  
### <a name="typeconverter"></a>TypeConverter  
 W obszarze usług .NET Framework XAML, wszystkie konwerterów typów, które są używane do celów XAML są klas, które pochodzą z klasy bazowej <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Klasy istniał w wersjach programu .NET Framework, przed wprowadzeniem XAML; jeden z oryginalnym <xref:System.ComponentModel.TypeConverter> scenariuszy było zapewnienie konwersji ciągu dla właściwości edytorów w projektantów wizualnych.  
  
 Dla XAML, rola <xref:System.ComponentModel.TypeConverter> jest rozwinięty. Ze względów XAML <xref:System.ComponentModel.TypeConverter> jest klasą bazową dla świadczenie pomocy technicznej dla niektórych do ciągu i konwersje z ciągu. Z ciągu umożliwia analizowanie wartość ciągu atrybutu z XAML. Do ciągu może to umożliwić przetwarzanie wartość czasu wykonywania właściwości określonego obiektu do atrybutu w XAML do serializacji.  
  
 <xref:System.ComponentModel.TypeConverter> definiuje cztery elementy członkowskie, które mają zastosowanie do konwersji na ciągi znaków i z ciągu w celu przetwarzania XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych składowych jest najważniejszą metodą <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, która konwertuje ciąg wejściowy typ wymaganego obiektu. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Można zaimplementować metodę do konwertowania szerszego zakresu typów do typu miejsca docelowego konwertera. Dlatego może służyć do celów, które wykraczają poza XAML, takich jak Obsługa konwersji w czasie wykonywania. Jednak w przypadku użycia XAML, ścieżka kodu, która może przetwarzać <xref:System.String> dane wejściowe są ważne.  
  
 Po drugie najważniejszą metodą jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentację w postaci znaczników (na przykład, jeśli jest zapisywany w XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest zaangażowane w scenariuszu większych XAML produktu moduły zapisujące tekst reprezentujący znaczników. W tym przypadku ścieżce kodu ważne dla XAML jest, gdy obiekt wywołujący `destinationType` z <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metody pomocy technicznej, które są używane, gdy usługa zapytania z funkcjami <xref:System.ComponentModel.TypeConverter> implementacji. Musisz zaimplementować te metody, aby zwrócić `true` dla przypadków specyficznych dla typu, który obsługuje metody konwersji równoważne usługi konwertera. Do celów XAML, zwykle oznacza to <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o ustawieniach kulturowych i typy konwerterów dla XAML  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacji może jednoznacznie interpretować, co to jest prawidłowy ciąg dla konwersji i można także użyć lub zignorować opis typu, który jest przekazywany jako parametry. Ważną kwestią konwersja typu kultury i XAML jest następująca: przy użyciu możliwych do zlokalizowania ciągi jako wartości atrybutów są obsługiwane przez XAML, nie można użyć tych ciągów Lokalizowalny — wejście typ konwertera z wymaganiami określonej kultury. Jest to ograniczenie, ponieważ typy konwerterów dla XAML wartości atrybutów obejmują zachowanie przetwarzania XAML zawsze stałej języka, które używa `en-US` kultury. Aby uzyskać więcej informacji na temat projektowania powody to ograniczenie, zobacz temat specyfikacji języka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) lub [WPF przeglądanie globalizacji i lokalizacji](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Na przykład gdy kultury może być problemem niektórych kultur należy użyć przecinka zamiast kropki jako separator dziesiętny liczb w postaci ciągu. To wykorzystania powoduje konflikt z zachowaniem, który ma wiele istniejących konwerterów typów, czyli jako ogranicznik, należy użyć przecinka. Przekazywanie kultury za pośrednictwem `xml:lang` w otaczających XAML nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementację, która obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metody dla tego konwertera musi zaakceptować ciąg jako `value` parametru. Jeśli ten ciąg jest w prawidłowym formacie i może zostać skonwertowana za <xref:System.ComponentModel.TypeConverter> implementacji zwracany obiekt musi obsługiwać Rzutowanie na typ, który jest oczekiwany przez właściwość. W przeciwnym razie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacja musi zwracać `null`.  
  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacji może jednoznacznie interpretować, co stanowi prawidłowy ciąg dla konwersji i można także użyć lub zignorować wpisz opis lub kultury kontekstów, które są przekazywane jako parametry. Jednak WPF XAML, przetwarzania nie może przekazać wartości do kontekstu opis typu we wszystkich przypadkach, a także nie może zostać przekazany na podstawie kultury `xml:lang`.  
  
> [!NOTE]
>  Nie używaj nawiasy klamrowe ({}), wyraźnie nawiasu otwierającego ({}), jako element formatu ciągu. Następujące znaki są zastrzeżone dla wejścia i wyjścia, dla sekwencji rozszerzenia znaczników.  
  
 Należy zgłosić wyjątek, gdy usługi konwertera typów musi mieć dostęp do usługi XAML z modułu zapisywania obiektu usług programu .NET Framework XAML, ale <xref:System.IServiceProvider.GetService%2A> wykonanego względem Kontekst wywołania nie zwraca tej usługi.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potencjalnie służy do obsługi serializacji. Serializacja pomocy technicznej w ramach <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla niestandardowego typu i jego typ konwerter nie jest bezwzględnie. Jednak jeśli są Implementowanie formantu lub jako część funkcji lub konstrukcji klasy za pomocą serializacji, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementację, która obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody dla tego konwertera musi zaakceptować wystąpienie tego typu (lub wartość), które jest obsługiwany jako `value` parametru. Gdy `destinationType` parametr jest typu <xref:System.String>, zwracany obiekt musi być w stanie można rzutować jako <xref:System.String>. Zwracany ciąg musi reprezentować wartość Zserializowany `value`. W idealnym przypadku format serializacji, który wybierzesz powinien móc wygenerować tę samą wartość tak, jakby te parametry zostały przekazane do <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji tych samych konwertera, bez znaczącą utratę informacji.  
  
 Jeśli wartość nie może być serializowany lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementacja musi zwracać `null` i może zgłosić wyjątek. Jednak jeśli zgłaszają wyjątki, należy zgłaszać z brakiem, aby użyć tej konwersji jako część usługi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, aby najlepszym rozwiązaniem jest sprawdzania przy użyciu <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> najpierw w celu uniknięcia wyjątków jest obsługiwana.  
  
 Jeśli `destinationType` parametr nie jest typu <xref:System.String>, możesz wybrać własną obsługę konwertera. Zazwyczaj przywrócić implementację podstawową obsługę, która w podstawowym <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zgłasza określonego wyjątku.  
  
 Należy zgłosić wyjątek, gdy usługi konwertera typów musi mieć dostęp do usługi XAML z modułu zapisywania obiektu usług programu .NET Framework XAML, ale <xref:System.IServiceProvider.GetService%2A> wykonanego względem Kontekst wywołania nie zwraca tej usługi.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna zwrócić implementację `true` dla `sourceType` typu <xref:System.String> a w przeciwnym razie jest odroczone do podstawowej implementacji. Nie zgłaszają wyjątki od <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna zwrócić implementację `true` dla `destinationType` typu <xref:System.String>, a w przeciwnym razie jest odroczone do podstawowej implementacji. Nie zgłaszają wyjątki od <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Usługi konwertera typu niestandardowego ma być używany jako działający konwerter typów dla niestandardowej klasy .NET Framework XAML Services, należy najpierw zastosować [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do swojej definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Należy określić za pomocą atrybutu musi być nazwą typu usługi konwertera typu niestandardowego. Jeśli zastosujesz tego atrybutu, gdy procesor XAML obsługuje wartości, których typ właściwości używa niestandardowej klasy typu, jego parametry wejściowe i zwrócić wystąpienia obiektu.  
  
 Możesz także podać konwertera typów, na podstawie poszczególnych właściwości. Zamiast stosowania [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy, zastosuj ją do definicji właściwości (głównej definicji nie `get` / `set` implementacji znajdujący się w nim). Typ właściwości musi być zgodna typ, który jest przetwarzany przez usługi konwertera typu niestandardowego. Z tym atrybutem zastosowane procesor XAML, obsługując wartości tej właściwości, można przetwarzać ciągów wejściowych i zwrócić wystąpienia obiektu. Dla właściwości typu konwertera techniką jest szczególnie przydatne, gdy użytkownik wybierze korzystanie z platformy Microsoft .NET Framework lub niektóre inne biblioteki, w której nie można kontrolować definicji klasy i nie można zastosować typ właściwości <xref:System.ComponentModel.TypeConverterAttribute> istnieje.  
  
 Przydzielenie zachowanie konwersji typu niestandardowego dołączonego elementu członkowskiego, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do `Get` metody dostępu implementacji wzorca dla dołączonych elementu członkowskiego.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenie znaczników  
 Dostępne usługi są identyczne dla dowolnego konwertera wartości. Różnica polega na w sposób każdego konwertera wartości odbiera kontekst usługi. Dostęp do usług i usługi dostępne są udokumentowane w temacie [typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Typy konwerterów w Stream węzłów XAML  
 Jeśli pracujesz z strumień węzłów XAML, akcji lub wynik końcowy konwertera typów nie będą jeszcze wykonane. W ścieżce obciążenia ciąg atrybutu, który ostatecznie trzeba można przekonwertować w celu załadowania pozostaje jako wartości tekstowej w ramach należysz do rozpoczęcia i zakończenia. Konwerter typu, który ostatecznie jest wymagana dla tej operacji można określić za pomocą <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> właściwości. Jednak uzyskiwanie prawidłową wartość z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> opiera się na potrzeby kontekst schematu XAML, który ma dostęp do takich informacji za pomocą podstawowego elementu członkowskiego lub typu wartości obiektu, który używa elementu członkowskiego. Wywoływanie zachowanie konwersji typu wymaga także kontekst schematu XAML, ponieważ wymaga mapowanie typu i utworzyć wystąpienie konwertera.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Typy konwerterów i rozszerzenia znaczników dla XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
