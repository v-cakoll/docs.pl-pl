---
title: TypeConverters i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: a6d41b5ad519302016ed7fa1d6a103af0f4f14d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549685"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters i XAML
W tym temacie przedstawiono celem konwersji typu z ciągu jako ogólne funkcji języka XAML. W programie .NET Framework <xref:System.ComponentModel.TypeConverter> klasy służy określonego celu jako część wdrożenia dla zarządzanej klasy niestandardowych, które mogą być używane jako wartości właściwości w języku XAML, użycie atrybutu. Jeśli zapisu niestandardowej klasy, a ma wystąpień klasy może być używany jako wartości można ustawić atrybutów pliku XAML, może być konieczne zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do własnej klasy zapisu niestandardowego <xref:System.ComponentModel.TypeConverter> lub klasę.  
  

  
## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typu  
  
### <a name="xaml-and-string-values"></a>XAML i wartości ciągu  
 Gdy wartość atrybutu jest ustawiona w pliku XAML, typ początkowej wartości to ciąg w formie czystego tekstu. Nawet w przypadku innych podstawowych, takich jak <xref:System.Double> są początkowo ciągów tekstowych procesora XAML.  
  
 Procesor XAML wymaga dwóch rodzajów informacji, aby przetworzyć wartości atrybutu. Pierwszy element danych jest typ wartości właściwości, która jest ustawiona. Dowolny ciąg, który definiuje wartość atrybutu i przetworzony w języku XAML ostatecznie muszą być konwertowane lub został rozpoznany jako wartość tego typu. Jeśli wartość jest typu pierwotnego, który jest rozpoznawany przez parser XAML (na przykład wartość liczbowa), próbą bezpośredniego Konwersja ciągu. Jeśli wartość to wyliczanie, ten ciąg jest używany do sprawdzenia pod kątem dopasowania nazwy do nazwanej stałej w tym wyliczeniu. Jeśli wartość jest ani typu pierwotnego zrozumiał analizator ani wyliczeniem, a następnie danego typu musi mieć możliwość zapewnienia wystąpienia typu lub wartości, w oparciu o skonwertowany ciąg. Jest to realizowane wskazując klasa konwertera typu. Konwerter typów jest klasa pomocy dla zapewniający wartości z innej klasy, zarówno w przypadku scenariusza XAML i również potencjalnie kod wywołuje w kodu platformy .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Przy użyciu istniejących zachowanie konwersji typu w XAML  
 W zależności od użytkownika znajomości podstawowe pojęcia języka XAML już używasz zachowanie konwersji typu w aplikacji w warstwie podstawowa XAML bez wiedzy. Na przykład WPF definiuje dosłownie setki właściwości, które przyjmują wartości typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> to wartość, która opisuje współrzędnych w dwuwymiarowa przestrzeni współrzędnych i naprawdę właśnie ma dwie ważne właściwości: <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A>. Po określeniu punktu w języku XAML, możesz podać go jako ciąg ogranicznikiem (zazwyczaj przecinkami) między <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A> podanie wartości. Na przykład: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`.  
  
 Nawet tego prostego typu <xref:System.Windows.Point> i jego prosty sposób użycia w języku XAML może dotyczyć konwertera typów. W tym przypadku jest to klasa <xref:System.Windows.PointConverter>.  
  
 Konwerter typu dla <xref:System.Windows.Point> zdefiniowana w klasie poziomu usprawnia użycia znaczników wszystkich właściwości, które przyjmują <xref:System.Windows.Point>. Bez konwertera typów w tym miejscu, będzie potrzebny następujące pełniejsze znaczników o tym samym przykładzie pokazano wcześniej:  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 Ogólnie jest typu string konwersji lub więcej Pełna składnia równoważne wybór styl kodowania. Narzędzia XAML przepływu pracy mogą również mieć wpływ jak wartości są ustawiane. Niektóre narzędzia XAML zazwyczaj Emituj najpełniejszych formę kod znaczników, ponieważ ułatwia przesłania danych do projektanta widoków lub mechanizm serializacji.  
  
 Istniejące typy konwerterów zazwyczaj mogły być odnajdowane w typach WPF i .NET Framework przez sprawdzanie obecności zastosowane klasy (lub właściwości) <xref:System.ComponentModel.TypeConverterAttribute>. Ten atrybut zostanie nazwę klasy, która jest obsługi konwerter typów dla wartości tego typu, dla celów XAML oraz potencjalnie innych celów.  
  
### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników  
 Konwertery rozszerzenia i typ znaczników pełnienia ról prostopadły pod względem zachowanie procesora XAML i scenariusze, które są stosowane do. Mimo że kontekst jest dostępny do użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, gdy rozszerzenie znaczników zapewnia wartość jest zazwyczaj nie zostanie zaznaczona w implementacji rozszerzenia znaczników. Innymi słowy nawet wtedy, gdy rozszerzenie znaczników zwraca ciąg tekstowy jako jego `ProvideValue` output, zachowanie konwersji typu dla tego ciągu jako dotyczą określoną właściwość lub typ wartości właściwości nie jest wywoływany, ogólnie rzecz biorąc, rozszerzeniem znacznika ma na celu procesu ciąg i zwracać obiekt bez żadnych konwerter typów związane.  
  
 Jeden sytuacja rozszerzenie znaczników w przypadku potrzeby zamiast konwertera typów jest odwołanie do obiektu, który już istnieje. W najlepszym konwertera typów bezstanowych można generować tylko nowe wystąpienie nie może być pożądane. Aby uzyskać więcej informacji na rozszerzenia znaczników, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Konwertery typu macierzystego  
 W implementacji WPF i .NET Framework analizatora języka XAML Brak niektórych typów, które mają Obsługa konwersji typu macierzystego, jeszcze nie są typy, które tradycyjnie mogą być uważane za nim elementów podstawowych. Przykładem takiego typu <xref:System.DateTime>. Przyczyną tego jest oparta na działanie architektury .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w mscorlib, najbardziej podstawowa Biblioteka programu .NET. <xref:System.DateTime> nie może mieć atrybut atrybut, który pochodzi z innego zestawu, który wprowadzono zależność (<xref:System.ComponentModel.TypeConverterAttribute> z System), mechanizmu odnajdywania konwertera typu zwykle poprzez przypisywanie nie może być obsługiwana. Zamiast tego analizatora XAML zawiera listę typów, które wymagają natywnego przetwarzania i przetwarza je podobnie do sposobu przetwarzania podstawowych wartość true. (W przypadku liczby <xref:System.DateTime> obejmuje to wywołanie <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
  
### <a name="typeconverter"></a>TypeConverter  
 W <xref:System.Windows.Point> przykładzie wcześniej, klasa <xref:System.Windows.PointConverter> wspomniano. W przypadku implementacji .NET XAML, wszystkie typy konwerterów, które są używane do celów XAML są klasy, które pochodzi od klasy podstawowej <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Klasy istniał w wersji programu .NET Framework, które należy poprzedzić istnienie XAML; jeden z jego oryginalnej użycia jest zapewnienie Konwersja ciągu w oknach dialogowych właściwości w wizualnych projektantów. Dla języka XAML, rola <xref:System.ComponentModel.TypeConverter> jest rozszerzona w celu uwzględnienia jest klasą bazową dla konwersji do ciągu i z ciągu, które umożliwiają analizowanie wartość ciągu atrybutu i prawdopodobnie przetwarzania wartość czasu wykonywania właściwości określonego obiektu na ciąg w celu Serializacja jako atrybut.  
  
 <xref:System.ComponentModel.TypeConverter> definiuje cztery elementów członkowskich, które mają zastosowanie do konwertowania do i z ciągów w celu przetwarzania XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z powyższych najważniejszych metoda jest <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Ta metoda konwertuje ciągu wejściowego z typem wymaganego obiektu. Mówiąc ściślej <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji konwertować znacznie większej liczby typów konwertera typu przeznaczenia i w związku z tym służyć do celów, które wykraczają poza XAML, takich jak obsługa konwersje czasu wykonywania, ale dla celów XAML — metoda jest to ścieżka kodu, który może przetwarzać <xref:System.String> danych wejściowych, który ma znaczenie.  
  
 Metoda najważniejszych dalej jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentacji znacznika (na przykład, jeśli plik jest zapisywany w języku XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest odpowiedzialny za tworzenie reprezentacji znacznika. W takim przypadku ścieżkę kodu, który ma znaczenie dla XAML jest podczas przekazywania `destinationType` z <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> metod obsługi, które są używane, gdy usługa wysyła zapytanie do możliwości <xref:System.ComponentModel.TypeConverter> implementacji. Musisz zaimplementować tych metod, aby zwrócić `true` dla określonego typu przypadków, które obsługują metody konwersji w równoważnych z konwertera. Do celów XAML, zwykle oznacza to <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o ustawieniach kulturowych i typy konwerterów dla XAML  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacji ma własną interpretacji, co stanowi prawidłowy ciąg dla konwersji i można również użyć lub Ignoruj opisu typu przekazywane jako parametry. Brak ważną kwestią w odniesieniu do kultury i konwersji typu XAML. Przy użyciu Lokalizowalny ciągi jako wartości atrybutu jest całkowicie obsługiwana przez XAML. Jednak przy użyciu tego ciągu Lokalizowalny jako dane wejściowe konwertera typu wymagania określoną kulturę, nie jest obsługiwana, ponieważ typy konwerterów dla XAML wartości atrybutów wymagają zachowania podczas analizowania niekoniecznie stałe języka, używając `en-US` kultury. Aby uzyskać więcej informacji na projekt powody to ograniczenie, należy skonsultować się specyfikacja języka XAML ([\[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Na przykład gdy kultura może być problem niektórych kultur użyć przecinka jako ich separator dziesiętny liczb. Spowoduje to kolidują z ma wiele konwertery typu WPF XAML, który jest zastosowanie spacji, jak ogranicznik zachowanie (w oparciu o historycznych poprzedników, takich jak wspólne X, Y formularza lub przecinkami przecinkami listy). Nawet przekazując kultury otaczającego XAML (ustawienie `Language` lub `xml:lang` do `sl-SI` kultury przykład kultura, która używa przecinek miejsc dziesiętnych w ten sposób) nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementacja obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metody dla tego konwertera, musisz zaakceptować ciąg jako `value` parametru. Jeśli ciąg został nieprawidłowe formatowanie i może zostać skonwertowana za <xref:System.ComponentModel.TypeConverter> wdrożenia, a następnie zwrócony obiekt musi obsługiwać Rzutowanie na typ oczekiwany przez właściwość. W przeciwnym razie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musi zwracać implementację `null`.  
  
 Każdy <xref:System.ComponentModel.TypeConverter> implementacji ma własną interpretacji, co stanowi prawidłowy ciąg dla konwersji i można również użyć lub Ignoruj kontekstów opis lub kultury typu przekazywane jako parametry. Jednak nie może przekazać wartości w kontekście opisu typu we wszystkich przypadkach WPF XAML przetwarzania, a także nie może przekazać opartą na `xml:lang`.  
  
> [!NOTE]
>  Nie używaj znaków nawias klamrowy, szczególnie {, jako element możliwe formatu ciągu. Następujące znaki są zastrzeżone dla wejścia i wyjścia sekwencji rozszerzenia znaczników.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potencjalnie jest używana do obsługi serializacji. Obsługa serializacji za pośrednictwem <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla danego typu niestandardowego i jej typ konwertera nie jest bezwzględnie spełniony. Jednak jeśli implementacja formantu, lub za pomocą serializacji jako część funkcji lub projekt klasy, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Może być używany jako <xref:System.ComponentModel.TypeConverter> implementacja obsługuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody dla tego konwertera, musisz zaakceptować wystąpienia typu (lub wartość) są obsługiwane jako `value` parametru. Gdy `destinationType` parametr jest typu <xref:System.String>, a następnie zwrócony obiekt musi mieć możliwość można rzutować jako <xref:System.String>. Zwracany ciąg musi reprezentować serializacji wartości `value`. W idealnym przypadku powinien być może generować taką samą wartość, jeśli ten ciąg zostały przekazane do formatu serializacji, możesz wybrać <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacji konwertera tego samego, bez znaczny poziom utraty danych.  
  
 Jeśli wartość nie może być serializowany lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musi zwracać implementację `null`i może zgłosić wyjątek, w tym przypadku. Ale jeśli zgłaszają wyjątki, zgłoś używaniem tej konwersji w ramach Twojej <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, aby najlepsze rozwiązanie polegające na sprawdzanie z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> najpierw w celu uniknięcia wyjątków jest obsługiwana.  
  
 Jeśli `destinationType` parametru nie jest typu <xref:System.String>, możesz wybrać własne Obsługa konwertera. Zazwyczaj powodują implementacji podstawowej obsługi, które w basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zgłasza wyjątek.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji powinien zwrócić `true` dla `destinationType` typu <xref:System.String>, a w przeciwnym razie odroczenie do podstawowej implementacji.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Twoje <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementacji powinien zwrócić `true` dla `sourceType` typu <xref:System.String>, a w przeciwnym razie odroczenie do podstawowej implementacji.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Aby Twoje konwertera typu niestandardowego ma być używany jako działający konwerter typów dla niestandardowej klasy przez procesor XAML, należy najpierw zastosować [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Użytkownika za pomocą atrybutu musi być nazwą typu z konwertera typu niestandardowego. Z tym atrybutem stosowane gdy procesor XAML obsługi wartości, których typ właściwości używa danego typu klasy niestandardowej, można wejściowych ciągów i zwrócić wystąpienia obiektu.  
  
 Można też podać konwertera typów, na podstawie poszczególnych właściwości. Zamiast stosowania [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy zastosować je do definicji właściwości (główny definicji nie `get` / `set` implementacji w niej). Typ właściwości musi odpowiadać typowi przetwarzanego przez użytkownika konwertera typu niestandardowego. Z tym atrybutem zastosowane XAMLprocessor, obsługując wartości właściwości, można przetwarzać ciągów wejściowych i zwrócić wystąpienia obiektu. Dla właściwości typu konwertera technika jest szczególnie przydatne, jeśli chcesz użyć typu właściwości z programu Microsoft .NET Framework lub niektóre biblioteki, której nie można kontrolować definicji klasy i nie można zastosować <xref:System.ComponentModel.TypeConverterAttribute> istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.TypeConverter>  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
