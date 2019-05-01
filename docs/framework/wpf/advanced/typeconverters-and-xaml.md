---
title: TypeConverters i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: ec6eaadae1dd7a7db84538c24e396a14db1a65a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007320"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters i XAML
W tym temacie przedstawiono celem typ Konwersja ciągu jako ogólna funkcja języka XAML. W .NET Framework <xref:System.ComponentModel.TypeConverter> klasy służy określonego celu, jako część wdrożenia na klasę niestandardową zarządzanego, który może służyć jako wartość właściwości użycie atrybutu XAML. Jeśli piszesz klasę niestandardową i chcesz, aby wystąpienia klasy może być używany jako wartości można ustawić atrybutu XAML, może być konieczne zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do klasy, należy napisać niestandardowy <xref:System.ComponentModel.TypeConverter> lub klasę.  

## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typu  
  
### <a name="xaml-and-string-values"></a>Wartości parametrów i XAML  
 Gdy wartość atrybutu jest ustawiona w pliku XAML, początkowy typ tej wartości jest ciągiem w postaci czystego tekstu. Nawet w innych elementów podstawowych, takich jak <xref:System.Double> są początkowo ciągów tekstowych i procesorów XAML.  
  
 Procesor XAML potrzebuje dwóch informacji w celu przetworzenia wartość atrybutu. Pierwsza część informacji jest typ wartości właściwości, która jest ustawiona. Dowolny ciąg, który definiuje wartość atrybutu i przetworzony w XAML ostatecznie musi być konwertowany lub rozwiązać wartość tego typu. Jeśli wartość jest elementu podstawowego, który zrozumieniu przez parser XAML (na przykład wartość liczbowa), to bezpośrednia konwersji ciągu zostanie podjęta. Jeśli wartość jest wyliczeniem, ten ciąg jest używany do sprawdzenia pod kątem dopasowania nazwy do nazwanej stałej w tym wyliczeniu. Jeśli wartość jest ani podstawowy rozumieć analizatora ani wyliczeniem, a następnie danego typu musi mieć możliwość zapewnienia wystąpienia typu lub wartości, na podstawie ciągu przekonwertowanego. To zrobić, wskazując klasy konwertera typu. Konwerter typu jest faktycznie Klasa pomocy umożliwiająca dostarczanie wartości z innej klasy, zarówno dla scenariusza XAML, a także potencjalnie dla kodu wywołania w kodzie .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Przy użyciu istniejącego zachowania konwersji typu w XAML  
 W zależności od Twojego znajomość XAML pojęć już używasz zachowanie konwersji typu w podstawowej aplikacji XAML bez wiedzy. Na przykład WPF definiuje dosłownie setki właściwości, które przyjmują wartości typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> jest wartością, która opisuje współrzędnych w dwuwymiarowej przestrzeni współrzędnych i rzeczywistości po prostu ma dwie ważne właściwości: <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A>. Po określeniu punktu w XAML można określić go jako ciąg znaków z ogranicznika (zazwyczaj przecinkami) między <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A> należy podać wartości. Na przykład: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Nawet tego prostego typu <xref:System.Windows.Point> i prosty sposób jej użycia w XAML może dotyczyć konwertera typów. W tym przypadku jest to klasa <xref:System.Windows.PointConverter>.  
  
 Konwerter typu dla <xref:System.Windows.Point> zdefiniowany z numerem upraszczają poziomu klasa użycia znaczników wszystkich właściwości, które przyjmują <xref:System.Windows.Point>. Bez konwertera typów w tym miejscu, będziesz potrzebować następujących znacznie bardziej szczegółowy kod znaczników dla tego samego przykładu przedstawionego wcześniej:  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 Czy używać typu string konwersji lub bardziej szczegółowy równoważny składni ogólnie jest wybranie stylu kodowania. Narzędzia przepływu pracy XAML mogą również mieć wpływ na sposób wartości są ustawione. Niektóre narzędzia XAML są zwykle do emitowania najpełniejszych formularza znaczniki, ponieważ jest łatwiejsza do przesłania danych do projektanta widoków lub własny mechanizm serializacji.  
  
 Ogólnie można odnaleźć istniejącego konwerterów typów w typach WPF i .NET Framework, sprawdzając klasy (lub właściwości) na obecność zastosowane <xref:System.ComponentModel.TypeConverterAttribute>. Ten atrybut będzie nazwa klasy, która jest pomocnicze konwertera typów dla wartości typu, a dla celów XAML oraz potencjalnie innych celów.  
  
### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników  
 Konwertery rozszerzenia i typu znaczników wypełnienia prostopadły ról pod kątem zachowania procesora XAML i scenariusze, które są stosowane względem. Mimo że kontekstu jest dostępna do użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, których rozszerzenie znaczników zawiera wartość jest zazwyczaj nie zostanie zaznaczona w implementacji rozszerzenia znaczników. Innymi słowy nawet jeśli rozszerzenie znaczników zwraca ciąg tekstowy jako jego `ProvideValue` dane wyjściowe, zachowanie konwersji typu dla tego ciągu jako dotyczą określoną właściwość lub typ wartości właściwości nie zostanie wywołany, ogólnie, rozszerzenie znaczników ma na celu procesu ciąg i zwraca obiekt bez żadnych konwertera typów zaangażowanych.  
  
 Typowe sytuacji kiedy rozszerzenie znaczników jest konieczne zamiast konwertera typów jest odwołaniem do obiektu, który już istnieje. W najlepszym konwertera typów o bezstanowa tylko może wygenerować nowe wystąpienie nie może być pożądane. Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Konwertery typu natywnego  
 W implementacji WPF i .NET Framework analizatora XAML istnieją pewne typy, które mają obsługi konwersji typu natywnego, jeszcze nie są typami, które może być powszechnie traktować jako podstawowych. Na przykład taki typ <xref:System.DateTime>. Przyczyną jest oparty na działania architektury .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w mscorlib, podstawowe biblioteki na platformie .NET. <xref:System.DateTime> nie ma zezwolenia na można przypisać za pomocą atrybutu, który pochodzi z innego zestawu, który wprowadza zależność (<xref:System.ComponentModel.TypeConverterAttribute> pochodzi z systemu), mechanizm odnajdywania konwertera typu zwykle poprzez przypisywanie nie są obsługiwane. Zamiast tego analizatora XAML zawiera listę typów, które są potrzebne takie natywne przetwarzanie i przetwarza je podobnie jak są przetwarzane prymitywów wartość true. (W przypadku właściwości <xref:System.DateTime> wiąże się to wywołanie <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
  
### <a name="typeconverter"></a>TypeConverter  
 W <xref:System.Windows.Point> przykład opisanych wcześniej, klasa <xref:System.Windows.PointConverter> wspomniane. Implementacji .NET XAML, wszystkie konwerterów typów, które są używane do celów XAML są klas, które pochodzą z klasy bazowej <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Klasy istniał w wersjach programu .NET Framework, które poprzedzają istnienie XAML; jeden z jego oryginalnym użycia było zapewnienie konwersji ciągów w oknach dialogowych właściwości, w projektantów wizualnych. Dla XAML, rola <xref:System.ComponentModel.TypeConverter> jest rozwinięta i obejmuje jest klasą bazową dla konwersji na ciągi znaków i z ciągu, które umożliwiają analizowanie wartość ciągu atrybutu i prawdopodobnie przetwarzania wartość czasu wykonywania właściwości określonego obiektu do ciąg Serializacja jako atrybut.  
  
 <xref:System.ComponentModel.TypeConverter> definiuje cztery elementy członkowskie, które mają zastosowanie do konwersji do i z ciągów w celu przetwarzania XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych opcji, jest najważniejszą metodą <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Ta metoda konwertuje ciąg wejściowy typ wymaganego obiektu. Ściśle rzecz ujmując <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji metody do przekonwertowania znacznie większej liczbie typów do typu miejsca docelowego konwerter, a zatem służyć do celów, które wykraczają poza XAML, takich jak Obsługa konwersji w czasie wykonywania, ale dla celów XAML jest ścieżka kodu, która może przetwarzać <xref:System.String> danych wejściowych, które są ważne.  
  
 Następna metoda najważniejsza jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowany na reprezentację znaczników, (na przykład, jeśli jest zapisywany w XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest odpowiedzialny za tworzenie reprezentacji znacznika. W takim przypadku ścieżka kodu, które są ważne dla XAML jest podczas przekazywania `destinationType` z <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metody pomocy technicznej, które są używane, gdy usługa zapytania z funkcjami <xref:System.ComponentModel.TypeConverter> implementacji. Musisz zaimplementować te metody, aby zwrócić `true` dla przypadków specyficznych dla typu, który obsługuje metody konwersji równoważne usługi konwertera. Do celów XAML, zwykle oznacza to <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o ustawieniach kulturowych i typy konwerterów dla XAML  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacja ma własną interpretację co stanowi prawidłowy ciąg do konwersji i można również użyć lub Ignoruj opis typu przekazywane jako parametry. Jest ważną kwestią w odniesieniu do kultury i konwersji typu XAML. Przy użyciu możliwych do zlokalizowania ciągi jako wartości atrybutów jest całkowicie obsługiwany przez XAML. Jednak przy użyciu możliwych do zlokalizowania ciąg jako danych wejściowych konwertera typu wymagania dotyczące określonej kultury nie jest obsługiwana, ponieważ typy konwerterów dla XAML wartości atrybutów obejmują zachowanie analizowania niekoniecznie stałej języka, przy użyciu `en-US` kultury. Aby uzyskać więcej informacji na temat przyczyn projektowania tego ograniczenia, powinni skontaktować się ze specyfikacją języka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Na przykład gdy kultury może być problemem niektórych kultur użyj przecinka jako ich separator dziesiętny liczb. Spowoduje to kolidować z zachowanie, które mają wiele konwerterów typów WPF XAML, i jest użycie przecinka jako ogranicznik (oparte na historyczne poprzedników, takie jak wspólne X, Y formularza lub przecinek przecinkami listy). Nawet przekazanie kultury w otaczających XAML (ustawienie `Language` lub `xml:lang` do `sl-SI` kultury i kultury, która używa przecinek dziesiętny w ten sposób przykład) nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementację, która obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metody dla tego konwertera musi zaakceptować ciąg jako `value` parametru. Jeśli ciąg było nieprawidłowe, formatowania i mogą być konwertowane przez <xref:System.ComponentModel.TypeConverter> wdrożenia, a następnie zwracany obiekt musi obsługiwać Rzutowanie na typ oczekiwany przez właściwość. W przeciwnym razie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacja musi zwracać `null`.  
  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacja ma własną interpretację co stanowi prawidłowy ciąg do konwersji i można również użyć lub Ignoruj typ kontekstów opis lub kultury przekazywane jako parametry. Jednak nie może przekazać wartości do kontekstu opis typu we wszystkich przypadkach WPF XAML, przetwarzania i również nie może przekazać kultury, na podstawie `xml:lang`.  
  
> [!NOTE]
>  Należy używać szczególnie znaki nawiasów klamrowych {, jako element możliwe w ciągu formatu. Następujące znaki są zastrzeżone dla wejścia i wyjścia, dla sekwencji rozszerzenia znaczników.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potencjalnie służy do obsługi serializacji. Serializacja pomocy technicznej w ramach <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla niestandardowego typu i jego typ konwerter nie jest bezwzględnie. Jednak jeśli są Implementowanie formantu lub jako część funkcji lub konstrukcji klasy za pomocą serializacji, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementację, która obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody dla tego konwertera musi zaakceptować wystąpienia tego typu (lub wartość), są obsługiwane jako `value` parametru. Gdy `destinationType` parametr jest typem <xref:System.String>, a następnie zwracany obiekt musi być w stanie można rzutować jako <xref:System.String>. Zwracany ciąg musi reprezentować wartość Zserializowany `value`. W idealnym przypadku powinien być może generować taką samą wartość, jeśli te parametry zostały przekazane do format serializacji, możesz wybrać <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji tych samych konwertera, bez znaczącą utratę informacji.  
  
 Jeśli wartość nie może być serializowany lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementacja musi zwracać `null`i jest dozwolone w tym przypadku zgłoszenie wyjątku. Ale jeśli zgłaszają wyjątki, powinien wysyłać raporty z brakiem, aby użyć tej konwersji jako część usługi <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, aby najlepszym rozwiązaniem jest sprawdzania przy użyciu <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> najpierw w celu uniknięcia wyjątków jest obsługiwana.  
  
 Jeśli `destinationType` parametr nie jest typu <xref:System.String>, możesz wybrać własną obsługę konwertera. Zazwyczaj będzie powracać do podstawowej implementacji obsługi, który w basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zgłasza określonego wyjątku.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna zwrócić implementację `true` dla `destinationType` typu <xref:System.String>, a w przeciwnym razie jest odroczone do podstawowej implementacji.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna zwrócić implementację `true` dla `sourceType` typu <xref:System.String>, a w przeciwnym razie jest odroczone do podstawowej implementacji.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Aby usługi konwertera typów niestandardowych, ma być używany jako działający konwerter typów dla niestandardowej klasy przez procesor XAML, należy najpierw zastosować [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do swojej definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Należy określić za pomocą atrybutu musi być nazwą typu usługi konwertera typu niestandardowego. Z tym atrybutem stosowane gdy procesor XAML obsługuje wartości, których typ właściwości używa niestandardowej klasy typu, można parametry wejściowe i zwrócić wystąpienia obiektu.  
  
 Możesz także podać konwertera typów, na podstawie poszczególnych właściwości. Zamiast stosowania [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy, zastosuj ją do definicji właściwości (głównej definicji nie `get` / `set` implementacji znajdujący się w nim). Typ właściwości musi być zgodna typ, który jest przetwarzany przez usługi konwertera typu niestandardowego. Z tym atrybutem zastosowania XAMLprocessor, obsługując wartości tej właściwości, można przetwarzać ciągów wejściowych i zwrócić wystąpienia obiektu. Dla właściwości typu konwertera techniką jest szczególnie przydatne, gdy użytkownik wybierze korzystanie z platformy Microsoft .NET Framework lub niektóre inne biblioteki, w której nie można kontrolować definicji klasy i nie można zastosować typ właściwości <xref:System.ComponentModel.TypeConverterAttribute> istnieje.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.TypeConverter>
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
