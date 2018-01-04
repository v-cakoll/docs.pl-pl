---
title: "Typy konwerterów dla XAML — Omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b59b88c38b6fa7f810bb3a12de09a962eb5679c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="type-converters-for-xaml-overview"></a>Typy konwerterów dla XAML — Omówienie
Logika dostaw konwertery typu dla edytora obiektu, który konwertuje z ciągu w kodzie XAML, w szczególności obiektów na wykresie obiektu. W programie .NET Framework XAML Services konwertera typu musi być klasą pochodzącą z <xref:System.ComponentModel.TypeConverter>. Niektóre konwertery również obsługują XAML ścieżkę zapisu i może służyć do szeregowania obiektu do postaci ciągu w znaczniku serializacji. W tym temacie opisano, jak i kiedy są wywoływane konwertery typu w XAML i zapewnia implementacji porady zastępuje metodę z <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typu  
 W poniższych sekcjach opisano podstawowe pojęcia o używaniu ciągi XAML, i sposobie używania przez autorów obiektu w usługach programu .NET Framework XAML konwertery typu przetwarzania niektórych wartości ciągu, które występują w źródle XAML.  
  
### <a name="xaml-and-string-values"></a>XAML i wartości ciągu  
 Po ustawieniu wartości atrybutu w pliku XAML początkowej typ wartości jest ciąg w sposób ogólny, a wartość atrybutu ciągu w tym sensie XML. Nawet w przypadku innych podstawowych, takich jak <xref:System.Double> są początkowo ciągi procesor XAML.  
  
 W większości przypadków procesora XAML musi informacje, które można przetworzyć wartości atrybutu. Pierwszy element danych jest typ wartości właściwości, która jest ustawiona. Dowolny ciąg, który definiuje wartość atrybutu i przetworzony w języku XAML ostatecznie muszą być konwertowane lub został rozpoznany jako wartość tego typu. Jeśli wartość jest typu pierwotnego, który jest rozpoznawany przez parser XAML (na przykład wartość liczbowa), próbą bezpośredniego Konwersja ciągu. Jeśli wartość atrybutu odwołuje się do wyliczenia, podany ciąg jest sprawdzany pod kątem dopasowania nazwy do nazwanej stałej w tym wyliczeniu. Jeśli wartość jest typu pierwotnego zrozumiał analizator ani stałej nazwy z wyliczenia, odpowiedni typ musi mieć możliwość zapewnienia wartości lub odwołania, który bazuje na skonwertowany ciąg.  
  
> [!NOTE]
>  Dyrektywy języka XAML nie należy używać konwertery typu.  
  
### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników  
 Użycia rozszerzenia znacznika musi być obsługiwane przez procesor XAML przed sprawdza typ właściwości oraz inne kwestie. Na przykład jeśli właściwość jest ustawiona jako atrybut ma zwykle konwersji typu, ale w przypadku ustawiono przez użycie rozszerzenia znaczników, następnie zachowania rozszerzeń znaczników przetwarza najpierw. Jeden typowych sytuacji, gdy jest konieczne rozszerzenie znaczników jest odwołanie do obiektu, który już istnieje. W tym scenariuszu konwertera typów bezstanowych można generować tylko nowe wystąpienie nie może być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Konwertery typu macierzystego  
 W implementacji usługi WPF i języka XAML .NET istnieją pewne typy CLR, które mają Obsługa konwersji typu macierzystego, jednak te typy CLR są nie tradycyjnie traktować jako typów podstawowych. Przykładem takiego typu <xref:System.DateTime>. Jest jednym z powodów dla tego działania architektury .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w mscorlib, najbardziej podstawowa Biblioteka programu .NET. <xref:System.DateTime>nie może mieć atrybut atrybut, który pochodzi z innego zestawu, który wprowadzono zależność (<xref:System.ComponentModel.TypeConverterAttribute> z systemu); w związku z tym mechanizm odnajdywania konwertera typu zwykle poprzez przypisywanie nie może być obsługiwana. Zamiast tego analizatora XAML zawiera listę typów natywnych przetworzenia i przetwarza te typy podobny do sposobu przetwarzania podstawowych wartość true. W przypadku liczby <xref:System.DateTime>, to przetwarzanie obejmuje wywołania <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
 W poniższych sekcjach omówiono interfejsu API z <xref:System.ComponentModel.TypeConverter> klasy.  
  
### <a name="typeconverter"></a>TypeConverter  
 W obszarze usług .NET Framework XAML, wszystkie typy konwerterów, które są używane do celów XAML są klasy, które pochodzi od klasy podstawowej <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Klasy istniał w wersji programu .NET Framework, przed wprowadzeniem XAML; jedną z oryginalnym <xref:System.ComponentModel.TypeConverter> scenariusze było zapewnienie Konwersja ciągu dla właściwości edytory w wizualnych projektantów.  
  
 Dla języka XAML, rola <xref:System.ComponentModel.TypeConverter> jest rozwinięta. Do celów XAML <xref:System.ComponentModel.TypeConverter> jest klasą bazową dla zapewnienie wsparcia dla niektórych do ciągu i konwersje z ciągu. Z ciągu umożliwia analizowanie wartość ciągu atrybutu z XAML. Do ciągu może umożliwić przetwarzania wartość czasu wykonywania właściwości określonego obiektu do atrybutu w języku XAML do serializacji.  
  
 <xref:System.ComponentModel.TypeConverter>definiuje cztery elementy członkowskie, które mają zastosowanie do konwersji na ciągi znaków i z ciągu w celu przetwarzania XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych elementów członkowskich jest metoda najważniejszych <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, który konwertuje ciągu wejściowego z typem obiektu wymagane. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Metody można stosować do przekonwertowania na typ przeznaczenia konwerter większej liczby typów. W związku z tym może służyć do celów, które wykraczają poza XAML, takich jak obsługa konwersje czasu wykonywania. Jednak do użytku w języku XAML, ścieżka kodu, który może przetwarzać <xref:System.String> dane wejściowe są ważne.  
  
 Drugim najważniejszym metoda jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja została przekonwertowana na reprezentację za pomocą znacznika (na przykład, jeśli plik jest zapisywany w języku XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> uczestniczy w scenariuszu większych XAML produktu zapisywania tekstu reprezentacji znacznika. W takim przypadku ścieżka ważne kodu XAML jest gdy obiekt wywołujący `destinationType` z <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> metod obsługi, które są używane, gdy usługa wysyła zapytanie do możliwości <xref:System.ComponentModel.TypeConverter> implementacji. Musisz zaimplementować tych metod, aby zwrócić `true` dla określonego typu przypadków, które obsługują metody konwersji w równoważnych z konwertera. Do celów XAML, zwykle oznacza to <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o ustawieniach kulturowych i typy konwerterów dla XAML  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacja może jednoznacznie interpretować, co to jest prawidłowy ciąg dla konwersji i można również użyć lub zignorować opisu typu, który jest przekazywany jako parametry. Ważną kwestią kultury i języka XAML konwersja typu jest następująca: przy użyciu Lokalizowalny ciągi jako wartości atrybutu jest obsługiwana przez XAML, ale nie można użyć te Lokalizowalny ciągi jako dane wejściowe konwertera typu wymagania określoną kulturę. Jest to ograniczenie, ponieważ typy konwerterów dla XAML wartości atrybutów wymagają zachowanie przetwarzania XAML musi stałym języka, które używa `en-US` kultury. Aby uzyskać więcej informacji na temat projektowania powody to ograniczenie, zobacz specyfikację języka XAML ([\[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)) lub [WPF globalizacja i lokalizacja omówienie](../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Na przykład gdy kultura może być problemem, niektóre kultur użyć przecinka zamiast okres jako separator dziesiętny liczb w postaci ciągu. To powoduje konflikt z zachowanie, że wiele istniejących konwertery typu, który jest zastosowanie spacji, jak ogranicznik. Przekazywanie kultury za pośrednictwem `xml:lang` w otaczającego XAML nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementacja obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metody dla tego konwertera, musisz zaakceptować ciąg jako `value` parametru. Jeśli ciąg jest w nieprawidłowym formacie i może zostać skonwertowana za <xref:System.ComponentModel.TypeConverter> implementacji zwrócony obiekt musi obsługiwać Rzutowanie na typ oczekiwany przez właściwość. W przeciwnym razie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musi zwracać implementację `null`.  
  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacja może jednoznacznie interpretować, co stanowi prawidłowy ciąg dla konwersji, a można też użyć lub zignorować typ opisu lub kultury kontekstach, które są przekazywane jako parametry. Jednak WPF XAML przetwarzania nie może przekazać wartości w kontekście opisu typu we wszystkich przypadkach, także nie może przekazać opartą na `xml:lang`.  
  
> [!NOTE]
>  Nie należy używać nawiasy klamrowe ({}), w szczególności nawiasu otwierającego ({}), jako element formatu ciągu. Następujące znaki są zastrzeżone dla wejścia i wyjścia sekwencji rozszerzenia znaczników.  
  
 Należy zgłosić wyjątek, gdy Twoje konwerter typów musi mieć dostęp do usługi języka XAML z edytora obiektu usługi XAML .NET Framework, ale <xref:System.IServiceProvider.GetService%2A> wywołaniu, które staje się przed kontekstu nie może zwracać tej usługi.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>potencjalnie jest używana do obsługi serializacji. Obsługa serializacji za pośrednictwem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla danego typu niestandardowego i jej typ konwertera nie jest bezwzględnie spełniony. Jednak jeśli implementacja formantu, lub za pomocą serializacji jako część funkcji lub projekt klasy, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementacja obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody dla tego konwertera, musisz zaakceptować wystąpienia typu (lub wartość), które jest obsługiwany jako `value` parametru. Gdy `destinationType` parametr jest typu <xref:System.String>, zwrócony obiekt musi mieć możliwość można rzutować jako <xref:System.String>. Zwracany ciąg musi reprezentować serializacji wartości `value`. W idealnym przypadku format serializacji, którą można wybrać powinno być możliwe do generowania taką samą wartość tak, jakby tego ciągu zostały przekazane do <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji konwertera tego samego, bez znaczny poziom utraty danych.  
  
 Jeśli wartość nie może być serializowany lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musi zwracać implementację `null` i może zgłosić wyjątek. Jednak jeśli zgłaszają wyjątki, zgłoś używaniem tej konwersji w ramach Twojej <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, aby najlepsze rozwiązanie polegające na sprawdzanie z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> najpierw w celu uniknięcia wyjątków jest obsługiwana.  
  
 Jeśli `destinationType` parametru nie jest typu <xref:System.String>, możesz wybrać własne Obsługa konwertera. Zazwyczaj przywrócić implementacji podstawowej obsługi, które w podstawowym <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zgłasza wyjątek.  
  
 Należy zgłosić wyjątek, gdy Twoje konwerter typów musi mieć dostęp do usługi języka XAML z edytora obiektu usługi XAML .NET Framework, ale <xref:System.IServiceProvider.GetService%2A> wywołaniu, które staje się przed kontekstu nie może zwracać tej usługi.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementacji powinien zwrócić `true` dla `sourceType` typu <xref:System.String> , a w przeciwnym razie odroczenie do podstawowej implementacji. Nie zgłaszają wyjątki od <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji powinien zwrócić `true` dla `destinationType` typu <xref:System.String>, a w przeciwnym razie odroczenie do podstawowej implementacji. Nie zgłaszają wyjątki od <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Dla Twojego konwertera typu niestandardowego ma być używany jako działający konwerter typów dla niestandardowej klasy przez usług .NET Framework XAML, należy najpierw zastosować [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Użytkownika za pomocą atrybutu musi być nazwą typu z konwertera typu niestandardowego. W przypadku zastosowania tego atrybutu, gdy procesor XAML obsługi wartości, których typ właściwości używa danego typu klasy niestandardowej, jego parametrów wejściowych i zwrócić wystąpienia obiektu.  
  
 Można też podać konwertera typów, na podstawie poszczególnych właściwości. Zamiast stosowania [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy zastosować je do definicji właściwości (główny definicji nie `get` / `set` implementacji w niej). Typ właściwości musi odpowiadać typowi przetwarzanego przez użytkownika konwertera typu niestandardowego. Z tym atrybutem zastosowane procesor XAML, obsługując wartości właściwości, można przetwarzać ciągów wejściowych i zwrócić wystąpienia obiektu. Dla właściwości typu konwertera technika jest szczególnie przydatne, jeśli chcesz użyć typu właściwości z [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] lub z niektórych biblioteki, której nie można kontrolować definicji klasy i nie można zastosować <xref:System.ComponentModel.TypeConverterAttribute> istnieje.  
  
 Przydzielenie zachowanie konwersji typu niestandardowych elementu członkowskiego dołączone, zastosuj <xref:System.ComponentModel.TypeConverterAttribute> do `Get` metodę dostępu implementacji wzorca dołączone elementu członkowskiego.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Uzyskiwanie dostępu do kontekstu dostawcy usług z implementacji rozszerzenia znaczników  
 Usługi dostępne są takie same dla dowolnego konwertera wartości. Różnica polega na tym w sposób każdego konwerter wartości odbiera kontekstu usługi. Dostęp do usług i usług dostępnych opisano w temacie [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Konwertery typu w strumieniu węzłów XAML  
 Jeśli pracujesz z strumień węzłów XAML, akcji lub zakończenia wynik konwertera typów nie została jeszcze wykonana. W ścieżce obciążenia ciąg atrybutu, który ostatecznie musi być typu skonwertowany nim będzie mógł załadować pozostaje jako wartość tekstową w elementy członkowskie rozpoczęcia i zakończenia. Konwerter typu, który ostatecznie jest wymagana dla tej operacji można określić za pomocą <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> właściwości. Jednak uzyskiwania prawidłową wartość z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> opiera się na potrzeby kontekst schematu XAML, który ma dostęp do takich informacji za pośrednictwem podstawowego elementu członkowskiego lub typu wartość obiektu, który używa elementu członkowskiego. Wywoływanie zachowanie konwersji typu wymaga również kontekst schematu XAML ponieważ wymagający mapowanie typu i utworzenia wystąpienia konwertera.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 [Typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
