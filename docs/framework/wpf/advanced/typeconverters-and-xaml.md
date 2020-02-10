---
title: TypeConverters i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 6b8b58228e94ed12557e97406e55cc4165753076
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095089"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters i XAML
W tym temacie przedstawiono przeznaczenie typu konwersji z ciągu jako ogólnej funkcji języka XAML. W .NET Framework Klasa <xref:System.ComponentModel.TypeConverter> służy do określonego celu jako część implementacji zarządzanej klasy niestandardowej, która może być używana jako wartość właściwości w użyciu atrybutu XAML. Jeśli napiszesz klasę niestandardową i chcesz, aby wystąpienia klasy mogły być używane jako wartości atrybutów XAML settable, może być konieczne zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do klasy, napisanie niestandardowej klasy <xref:System.ComponentModel.TypeConverter> lub obu tych elementów.  

## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typów  
  
### <a name="xaml-and-string-values"></a>Wartości XAML i String  
 Po ustawieniu wartości atrybutu w pliku XAML, początkowy typ tej wartości jest ciągiem w postaci czystego tekstu. Nawet inne elementy podstawowe, takie jak <xref:System.Double>, są pierwszymi ciągami tekstowymi procesora XAML.  
  
 Procesor XAML wymaga dwóch informacji w celu przetworzenia wartości atrybutu. Pierwsza część informacji jest typem wartości właściwości, która jest ustawiana. Dowolny ciąg, który definiuje wartość atrybutu i który jest przetwarzany w języku XAML, musi ostatecznie być konwertowany lub rozpoznany jako wartość tego typu. Jeśli wartość jest typem podstawowym, który jest zrozumiały dla analizatora XAML (na przykład wartość liczbowa), podejmowana jest bezpośrednia Konwersja ciągu. Jeśli wartość jest wyliczeniem, ciąg jest używany do sprawdzania, czy nazwa jest zgodna z nazwą stałą w tym wyliczeniu. Jeśli wartość nie jest typem pierwotnym ani wyliczeniem rozpoznanym przez analizator, wówczas typ, który musi być w stanie dostarczyć wystąpienie typu lub wartość, na podstawie przekonwertowanego ciągu. Jest to realizowane przez wskazanie klasy konwertera typów. Konwerter typu jest efektywnie klasą pomocniczą do udostępniania wartości innej klasy, obu dla scenariusza XAML, a także dla wywołań kodu w kodzie .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Używanie istniejącego zachowania konwersji typu w języku XAML  
 W zależności od posiadanej znajomości języka XAML można już użyć zachowania konwersji typu w języku XAML aplikacji Basic bez jego realizacji. Na przykład, WPF definiuje dosłownie setki właściwości, które przyjmują wartość typu <xref:System.Windows.Point>. <xref:System.Windows.Point> jest wartością opisującą współrzędną w dwuwymiarowej przestrzeni współrzędnych i naprawdę tylko ma dwie ważne właściwości: <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A>. Po określeniu punktu w języku XAML należy określić go jako ciąg z ogranicznikiem (zwykle przecinkiem) między wartością <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A>. Na przykład: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Nawet ten prosty typ <xref:System.Windows.Point> i jego proste użycie w języku XAML obejmuje konwerter typów. W tym przypadku jest to Klasa <xref:System.Windows.PointConverter>.  
  
 Konwerter typów dla <xref:System.Windows.Point> zdefiniowane na poziomie klasy usprawnia użycie znaczników wszystkich właściwości, które pobierają <xref:System.Windows.Point>. Bez konwertera typów w tym miejscu potrzebna jest następująca znacznie większa ilość znaczników dla tego samego przykładu:  

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
  
 Określa, czy należy używać ciągu konwersji typu, czy bardziej pełnej, równoważnej składni jest wybór stylu kodowania. Przepływ pracy narzędzi XAML może również mieć wpływ na sposób ustawiania wartości. Niektóre narzędzia XAML przeważnie emitują najbardziej pełną postać znaczników, ponieważ ułatwiają one przekazanie widoków projektanta lub ich własnego mechanizmu serializacji.  
  
 Istniejące konwertery typów można ogólnie odnaleźć dla WPF i .NET Framework typów, sprawdzając klasę (lub właściwość) dla obecności zastosowanego <xref:System.ComponentModel.TypeConverterAttribute>. Ten atrybut będzie określał nazwę klasy, która jest konwerterem typu pomocniczego dla wartości tego typu, w celach XAML, jak również w innych celach.  
  
### <a name="type-converters-and-markup-extensions"></a>Konwertery typów i rozszerzenia znaczników  
 Rozszerzenia znaczników i konwertery typów wypełniają role ortogonalne w warunkach zachowania procesora XAML i scenariusze, do których są stosowane. Chociaż kontekst jest dostępny dla użycia rozszerzenia znaczników, zachowanie konwersji typu dla właściwości, w których rozszerzenie znacznika zapewnia wartość, zazwyczaj nie jest zaznaczone w implementacjach rozszerzenia znaczników. Innymi słowy, nawet jeśli rozszerzenie znacznika zwraca ciąg tekstowy jako `ProvideValue` dane wyjściowe, zachowanie konwersji typu dla tego ciągu jako zastosowane do określonej właściwości lub typu wartości właściwości nie jest wywoływane, ogólnie rzecz biorąc, przeznaczenie rozszerzenia znacznika ma przetwarzać ciąg i zwracać obiekt bez żadnego z nich.  
  
 Jedna powszechna sytuacja, w której wymagane jest rozszerzenie znaczników, a nie konwertera typów, to odwołanie do obiektu, który już istnieje. W najlepszym przypadku konwerter typu bezstanowego może generować tylko nowe wystąpienie, które może nie być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Konwertery typów natywnych  
 W WPF i .NET Framework implementacji analizatora XAML istnieją pewne typy, które mają obsługę konwersji typu natywnego, ale nie są typami, które mogą być traktowane jako elementy pierwotne. Przykładem takiego typu jest <xref:System.DateTime>. Przyczyna tego problemu jest oparta na sposobie działania architektury .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w bibliotece Mscorlib, a najbardziej podstawowa Biblioteka w programie .NET. <xref:System.DateTime> nie może mieć atrybutu, który pochodzi z innego zestawu, który wprowadza zależność (<xref:System.ComponentModel.TypeConverterAttribute> pochodzi z systemu), dlatego nie można obsługiwać standardowego mechanizmu odnajdywania konwertera typów przez przypisanie. Zamiast tego Analizator XAML ma listę typów, które wymagają takiego przetwarzania natywnego, i przetwarza je podobnie jak prawdziwe elementy podstawowe są przetwarzane. (W przypadku <xref:System.DateTime> obejmuje to wywołanie <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
  
### <a name="typeconverter"></a>TypeConverter  
 W podanym wcześniej przykładzie <xref:System.Windows.Point> klasy <xref:System.Windows.PointConverter>. W przypadku implementacji platformy .NET języka XAML wszystkie konwertery typów, które są używane na potrzeby języka XAML, są klasami pochodnymi od klasy bazowej <xref:System.ComponentModel.TypeConverter>. Klasa <xref:System.ComponentModel.TypeConverter> istniała w wersjach .NET Framework, które poprzedzają istnienie języka XAML; jednym z jego oryginalnych zastosowań było zapewnienie konwersji ciągów dla okien dialogowych Właściwości w projektantach wizualizacji. W przypadku języka XAML rola <xref:System.ComponentModel.TypeConverter> jest rozwinięta, aby uwzględnić jako klasę bazową dla ciągów do-String i przeliczeń ciągów, które umożliwiają analizowanie wartości atrybutu String i mogą przetwarzać wartość właściwości określonego obiektu z powrotem do ciągu na potrzeby serializacji jako atrybut.  
  
 <xref:System.ComponentModel.TypeConverter> definiuje cztery składowe, które są istotne dla konwersji do i z ciągów dla celów przetwarzania XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych metod najważniejszy jest <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Ta metoda konwertuje ciąg wejściowy na wymagany typ obiektu. Mówiąc ściślej, Metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> może zostać zaimplementowana w celu przeprowadzenia konwersji znacznie szerszego zakresu typów na zamierzony typ docelowy konwertera. w związku z tym służą one do przetworzenia, które wykraczają poza kod XAML, na przykład obsługują konwersje w czasie wykonywania, ale na potrzeby języka XAML jest tylko ścieżka kodu, która może przetwarzać <xref:System.String> dane wejściowe.  
  
 Kolejna najważniejsza Metoda jest <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentację znaczników (na przykład jeśli jest zapisywana w języku XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest odpowiedzialny za tworzenie reprezentacji znaczników. W takim przypadku ścieżką kodu, która ma znaczenie dla języka XAML, jest przekazanie `destinationType` <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metodami obsługi, które są używane, gdy usługa wysyła zapytanie do możliwości implementacji <xref:System.ComponentModel.TypeConverter>. Należy zaimplementować te metody, aby zwracać `true` dla przypadków specyficznych dla typów, które są równoważnymi metodami konwersji konwertera. Na potrzeby języka XAML zazwyczaj oznacza to, że typ <xref:System.String>.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o kulturze i konwertery typów dla języka XAML  

 Każda implementacja <xref:System.ComponentModel.TypeConverter> może mieć własną interpretację, co stanowi prawidłowy ciąg dla konwersji, i może również użyć lub zignorować opis typu przesłany jako parametry. Istnieje ważne zagadnienie dotyczące konwersji typów kulturowych i XAML. Używanie lokalizowalnych ciągów jako wartości atrybutów jest całkowicie obsługiwane przez język XAML. Ale użycie tego lokalizowalnego ciągu jako danych wejściowych konwertera typów z określonymi wymaganiami kultury nie jest obsługiwane, ponieważ konwertery typów dla wartości atrybutów XAML obejmują niekonieczną analizę języka o stałym rozmiarze przy użyciu kultury `en-US`. Aby uzyskać więcej informacji na temat przyczyn związanych z projektowaniem tego ograniczenia, należy zapoznać się ze specyfikacją języka XAML ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 Przykładowo, gdy kultura może być problemem, niektóre kultury używają przecinka jako ogranicznika przecinka dziesiętnego dla liczb. Spowoduje to kolizję z zachowaniem, które ma wiele konwerterów typu XAML WPF, czyli użycie przecinka jako ogranicznika (w oparciu o historyczne poprzedniki, takie jak typowa postać X, Y lub listy rozdzielane przecinkami). Nawet przekazanie kultury w otaczającym XAML (ustawienie `Language` lub `xml:lang` do kultury `sl-SI`, przykład kultury, która używa przecinka dla dziesiętnego w ten sposób, w ten sposób) nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Aby można było użyć implementacji <xref:System.ComponentModel.TypeConverter>, która obsługuje XAML, Metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> dla tego konwertera musi akceptować ciąg jako parametr `value`. Jeśli ciąg jest w prawidłowym formacie i może zostać przekonwertowany przez implementację <xref:System.ComponentModel.TypeConverter>, zwracany obiekt musi obsługiwać rzutowanie do typu oczekiwanego przez właściwość. W przeciwnym razie implementacja <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musi zwracać `null`.  
  
 Każda implementacja <xref:System.ComponentModel.TypeConverter> może mieć własną interpretację, co stanowi prawidłowy ciąg dla konwersji, i może również używać lub ignorować opis typu lub kontekstów kultury przekazaną jako parametry. Jednak przetwarzanie kodu XAML WPF może nie przekazywać wartości do kontekstu opisu typu we wszystkich przypadkach, a także nie może przekazywać kultury na podstawie `xml:lang`.  
  
> [!NOTE]
> Nie używaj znaków nawiasów klamrowych, szczególnie {, jako możliwego elementu formatu ciągu. Te znaki są zarezerwowane jako wejście i wyjście dla sekwencji rozszerzenia znaczników.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest potencjalnie używany do obsługi serializacji. Obsługa serializacji za pomocą <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla typu niestandardowego i jego konwertera typów nie jest wymaganiem bezwzględnym. Jednakże w przypadku implementowania kontrolki lub korzystania z serializacji jako części funkcji lub projektu klasy należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby można było użyć jako implementacji <xref:System.ComponentModel.TypeConverter>, która obsługuje XAML, Metoda <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla tego konwertera musi akceptować wystąpienie typu (lub wartość) obsługiwane jako parametr `value`. Gdy parametr `destinationType` jest typem <xref:System.String>, zwracany obiekt musi być w stanie rzutować jako <xref:System.String>. Zwrócony ciąg musi reprezentować serializowaną wartość `value`. W idealnym przypadku wybrany format serializacji powinien być w stanie generować tę samą wartość, jeśli ten ciąg został przesłany do implementacji <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> tego samego konwertera, bez znacznej utraty informacji.  
  
 Jeśli wartość nie może być serializowana lub konwerter nie obsługuje serializacji, implementacja <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musi zwrócić `null`i może zgłosić wyjątek w tym przypadku. Ale w przypadku zgłaszania wyjątków należy zgłosić niezdolność do użycia tej konwersji w ramach implementacji <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>, dzięki czemu najlepszym rozwiązaniem w zakresie sprawdzania z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>, aby uniknąć wyjątków.  
  
 Jeśli parametr `destinationType` nie jest typu <xref:System.String>, można wybrać własny sposób obsługi konwertera. Zazwyczaj można przywrócić podstawową obsługę implementacji, która w <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> basemost zgłasza konkretny wyjątek.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna zwracać `true` `destinationType` typu <xref:System.String>i w przeciwnym razie odroczyć na implementację podstawową.  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna zwracać `true` `sourceType` typu <xref:System.String>i w przeciwnym razie odroczyć na implementację podstawową.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Aby konwerter typu niestandardowego był używany jako typ działającego konwertera klasy niestandardowej przez procesor XAML, należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> określona za pomocą atrybutu musi być nazwą typu niestandardowego konwertera typów. Po zastosowaniu tego atrybutu, gdy procesor XAML obsługuje wartości, w których typ właściwości używa typu klasy niestandardowej, może wprowadzać ciągi i zwracać wystąpienia obiektów.  
  
 Można również udostępnić konwerter typów dla poszczególnych właściwości. Zamiast stosowania <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy, należy zastosować je do definicji właściwości (głównej definicji, a nie `get`/`set` implementacji w ramach tego elementu). Typ właściwości musi być zgodny z typem, który jest przetwarzany przez konwerter typów niestandardowych. Po zastosowaniu tego atrybutu, gdy procesor XAML obsługuje wartości tej właściwości, może przetwarzać ciągi wejściowe i zwracać wystąpienia obiektów. Technika konwertera typów dla właściwości jest szczególnie przydatna, jeśli zdecydujesz się użyć typu właściwości z Microsoft .NET Framework lub z innej biblioteki, w której nie można kontrolować definicji klasy i nie można zastosować <xref:System.ComponentModel.TypeConverterAttribute> tam.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.TypeConverter>
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
