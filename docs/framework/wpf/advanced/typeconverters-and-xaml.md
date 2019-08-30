---
title: TypeConverters i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 8c39fe75eea5042657cab533a0a557d966802a1b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169025"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters i XAML
W tym temacie przedstawiono przeznaczenie typu konwersji z ciągu jako ogólnej funkcji języka XAML. W .NET Framework <xref:System.ComponentModel.TypeConverter> Klasa służy do określonego celu jako część implementacji zarządzanej klasy niestandardowej, która może być używana jako wartość właściwości w użyciu atrybutu XAML. Jeśli napiszesz klasę niestandardową i chcesz, aby wystąpienia klasy mogły być używane jako wartości atrybutów XAML settable, może być konieczne zastosowanie <xref:System.ComponentModel.TypeConverterAttribute> do klasy, zapisanie klasy niestandardowej <xref:System.ComponentModel.TypeConverter> lub obu tych elementów.  

## <a name="type-conversion-concepts"></a>Pojęcia dotyczące konwersji typów  
  
### <a name="xaml-and-string-values"></a>Wartości XAML i String  
 Po ustawieniu wartości atrybutu w pliku XAML, początkowy typ tej wartości jest ciągiem w postaci czystego tekstu. Nawet inne elementy podstawowe, takie <xref:System.Double> jak, są początkowo ciągami tekstowymi procesora XAML.  
  
 Procesor XAML wymaga dwóch informacji w celu przetworzenia wartości atrybutu. Pierwsza część informacji jest typem wartości właściwości, która jest ustawiana. Dowolny ciąg, który definiuje wartość atrybutu i który jest przetwarzany w języku XAML, musi ostatecznie być konwertowany lub rozpoznany jako wartość tego typu. Jeśli wartość jest typem podstawowym, który jest zrozumiały dla analizatora XAML (na przykład wartość liczbowa), podejmowana jest bezpośrednia Konwersja ciągu. Jeśli wartość jest wyliczeniem, ciąg jest używany do sprawdzania, czy nazwa jest zgodna z nazwą stałą w tym wyliczeniu. Jeśli wartość nie jest typem pierwotnym ani wyliczeniem rozpoznanym przez analizator, wówczas typ, który musi być w stanie dostarczyć wystąpienie typu lub wartość, na podstawie przekonwertowanego ciągu. Jest to realizowane przez wskazanie klasy konwertera typów. Konwerter typu jest efektywnie klasą pomocniczą do udostępniania wartości innej klasy, obu dla scenariusza XAML, a także dla wywołań kodu w kodzie .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Używanie istniejącego zachowania konwersji typu w języku XAML  
 W zależności od posiadanej znajomości języka XAML można już użyć zachowania konwersji typu w języku XAML aplikacji Basic bez jego realizacji. Na przykład, WPF definiuje dosłownie setki właściwości, które przyjmują wartość typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> jest wartością opisującą współrzędną w dwuwymiarowej przestrzeni współrzędnych i naprawdę tylko ma dwie ważne właściwości: <xref:System.Windows.Point.X%2A> i <xref:System.Windows.Point.Y%2A>. Gdy określisz punkt w języku XAML, określisz go jako ciąg z ogranicznikiem (zwykle przecinkiem) między <xref:System.Windows.Point.X%2A> wartościami i. <xref:System.Windows.Point.Y%2A> Na przykład: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Nawet ten prosty typ <xref:System.Windows.Point> i jego proste użycie w języku XAML obejmuje konwerter typów. W tym przypadku jest to Klasa <xref:System.Windows.PointConverter>.  
  
 Konwerter <xref:System.Windows.Point> typu, który jest zdefiniowany na poziomie klasy, usprawnia użycie znaczników wszystkich właściwości, które są wykonywane <xref:System.Windows.Point>. Bez konwertera typów w tym miejscu potrzebna jest następująca znacznie większa ilość znaczników dla tego samego przykładu:  

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
  
 Istniejące konwertery typów można ogólnie odnaleźć dla WPF i .NET Framework typów, sprawdzając klasę (lub właściwość) dla obecności zastosowanej <xref:System.ComponentModel.TypeConverterAttribute>. Ten atrybut będzie określał nazwę klasy, która jest konwerterem typu pomocniczego dla wartości tego typu, w celach XAML, jak również w innych celach.  
  
### <a name="type-converters-and-markup-extensions"></a>Konwertery typów i rozszerzenia znaczników  
 Rozszerzenia znaczników i konwertery typów wypełniają role ortogonalne w warunkach zachowania procesora XAML i scenariusze, do których są stosowane. Chociaż kontekst jest dostępny dla użycia rozszerzenia znaczników, zachowanie konwersji typu dla właściwości, w których rozszerzenie znacznika zapewnia wartość, zazwyczaj nie jest zaznaczone w implementacjach rozszerzenia znaczników. Innymi słowy, nawet jeśli rozszerzenie znacznika zwraca ciąg tekstowy jako `ProvideValue` dane wyjściowe, zachowanie konwersji typu dla tego ciągu jako zastosowany do określonej właściwości lub typu wartości właściwości nie jest wywoływane, zazwyczaj celem rozszerzenia znacznika jest przetworzenie ciąg i zwraca obiekt bez żadnego z konwertera typów.  
  
 Jedna powszechna sytuacja, w której wymagane jest rozszerzenie znaczników, a nie konwertera typów, to odwołanie do obiektu, który już istnieje. W najlepszym przypadku konwerter typu bezstanowego może generować tylko nowe wystąpienie, które może nie być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników i XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Konwertery typów natywnych  
 W WPF i .NET Framework implementacji analizatora XAML istnieją pewne typy, które mają obsługę konwersji typu natywnego, ale nie są typami, które mogą być traktowane jako elementy pierwotne. Przykładem takiego typu jest <xref:System.DateTime>. Powód tego jest oparty na sposobie działania architektury .NET Framework: typ <xref:System.DateTime> jest zdefiniowany w bibliotece Mscorlib, a najbardziej podstawowa Biblioteka w programie .NET. <xref:System.DateTime>nie jest dozwolone, aby mieć atrybut pochodzący z innego zestawu, który wprowadza zależność (<xref:System.ComponentModel.TypeConverterAttribute> pochodzi z systemu), dlatego nie można obsługiwać standardowego mechanizmu odnajdywania konwertera typów przez przypisanie. Zamiast tego Analizator XAML ma listę typów, które wymagają takiego przetwarzania natywnego, i przetwarza je podobnie jak prawdziwe elementy podstawowe są przetwarzane. (W przypadku <xref:System.DateTime> tego dotyczy <xref:System.DateTime.Parse%2A>wywołania.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
  
### <a name="typeconverter"></a>TypeConverter  
 W podanym <xref:System.Windows.PointConverter>przykładzieokreślonowcześniejklasę <xref:System.Windows.Point> . W przypadku implementacji platformy .NET języka XAML wszystkie konwertery typów, które są używane na potrzeby języka XAML, są klasami <xref:System.ComponentModel.TypeConverter>pochodnymi od klasy bazowej. <xref:System.ComponentModel.TypeConverter> Klasa istniała w wersjach .NET Framework, które poprzedzają istnienie języka XAML; jednym z jego oryginalnych zastosowań było zapewnienie konwersji ciągów dla okien dialogowych Właściwości w projektantach wizualizacji. Dla języka XAML rola <xref:System.ComponentModel.TypeConverter> jest rozwinięta, aby uwzględniać jako klasę bazową dla ciągów do-String i przeliczeń ciągów, które umożliwiają analizowanie wartości atrybutu String i mogą przetwarzać wartość właściwości określonego obiektu z powrotem do ciągu dla Serializacja jako atrybut.  
  
 <xref:System.ComponentModel.TypeConverter>definiuje cztery składowe, które są istotne dla konwersji do i z ciągów dla celów przetwarzania XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych metod najważniejszych jest <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Ta metoda konwertuje ciąg wejściowy na wymagany typ obiektu. Mówiąc ściślej, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Metoda może zostać zaimplementowana w celu przekonwertowania znacznie szerszego zakresu typów na zamierzony typ docelowy konwertera i w ten sposób obsłużyć do celów, które wykraczają poza kod XAML, taki jak obsługa konwersji w czasie wykonywania, ale dla celów XAML jest to tylko ścieżka kodu, która może przetwarzać <xref:System.String> dane wejściowe.  
  
 Kolejna najważniejsza Metoda to <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Jeśli aplikacja jest konwertowana na reprezentację znaczników (na przykład jeśli jest zapisywana w języku XAML jako plik), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest odpowiedzialna za tworzenie reprezentacji znaczników. W takim przypadku ścieżka kodu, która ma znaczenie dla języka XAML, jest w przypadku `destinationType` przekazania <xref:System.String> elementu.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> obsługują metody, które są używane, gdy usługa wysyła zapytanie o możliwości <xref:System.ComponentModel.TypeConverter> implementacji. Należy zaimplementować te metody, aby zwrócić `true` się do przypadków specyficznych dla typów, które są równoważnymi metodami konwersji konwertera. Na potrzeby języka XAML zazwyczaj oznacza <xref:System.String> to typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o kulturze i konwertery typów dla języka XAML  
 Każda <xref:System.ComponentModel.TypeConverter> implementacja może mieć własną interpretację, co stanowi prawidłowy ciąg dla konwersji, i może również użyć lub zignorować opis typu przesłany jako parametry. Istnieje ważne zagadnienie dotyczące konwersji typów kulturowych i XAML. Używanie lokalizowalnych ciągów jako wartości atrybutów jest całkowicie obsługiwane przez język XAML. Ale użycie tego lokalizowalnego ciągu jako danych wejściowych konwertera typów z określonymi wymaganiami kultury nie jest obsługiwane, ponieważ konwertery typów dla wartości atrybutów XAML wymagają niepotrzebnych do analizy `en-US` języka, przy użyciu kultury. Aby uzyskać więcej informacji na temat przyczyn związanych z projektowaniem tego ograniczenia, należy zapoznać się ze specyfikacją języka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Przykładowo, gdy kultura może być problemem, niektóre kultury używają przecinka jako ogranicznika przecinka dziesiętnego dla liczb. Spowoduje to kolizję z zachowaniem, które ma wiele konwerterów typu XAML WPF, czyli użycie przecinka jako ogranicznika (w oparciu o historyczne poprzedniki, takie jak typowa postać X, Y lub listy rozdzielane przecinkami). Nawet w przypadku przekazywania kultury w otaczającym XAML ( `Language` ustawieniu `xml:lang` lub `sl-SI` kulturze) przykładem kultury, która używa przecinka dla dziesiętnego w ten sposób, nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie ConvertFrom  
 Aby można było używać ich <xref:System.ComponentModel.TypeConverter> jako implementacji, która obsługuje XAML <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , metoda dla tego konwertera musi `value` akceptować ciąg jako parametr. Jeśli ciąg jest w prawidłowym formacie i może być konwertowany przez <xref:System.ComponentModel.TypeConverter> implementację, zwracany obiekt musi obsługiwać rzutowanie do typu oczekiwanego przez właściwość. W przeciwnym `null`razie <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementacja musi zwrócić.  
  
 Każda <xref:System.ComponentModel.TypeConverter> implementacja może mieć własną interpretację, co stanowi prawidłowy ciąg dla konwersji, i może również użyć lub zignorować opis typu lub kontekst kultury przekazaną jako parametry. Jednak przetwarzanie kodu XAML WPF może nie przekazywać wartości do kontekstu opisu typu we wszystkich przypadkach, a także może nie przekazywać kultury na podstawie `xml:lang`.  
  
> [!NOTE]
> Nie używaj znaków nawiasów klamrowych, szczególnie {, jako możliwego elementu formatu ciągu. Te znaki są zarezerwowane jako wejście i wyjście dla sekwencji rozszerzenia znaczników.  
  
### <a name="implementing-convertto"></a>Implementowanie ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>jest potencjalnie używany do obsługi serializacji. Obsługa serializacji za <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pomocą dla typu niestandardowego i jego konwertera typów nie jest wymaganiem bezwzględnym. Jednak jeśli wdrażasz kontrolkę lub korzystasz z serializacji jako części funkcji lub projektu klasy, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby można było używać ich <xref:System.ComponentModel.TypeConverter> jako implementacji, która obsługuje XAML <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> , metoda dla tego konwertera musi akceptować wystąpienie typu (lub wartość `value` ) obsługiwane jako parametr. Gdy parametr jest typem <xref:System.String>, zwracany obiekt musi być w stanie rzutować jako <xref:System.String>. `destinationType` Zwrócony ciąg musi reprezentować wartość `value`serializowaną. W idealnym przypadku wybrany format serializacji powinien być w stanie generować tę samą wartość, jeśli ten ciąg został przesłany <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> do implementacji tego samego konwertera, bez znacznej utraty informacji.  
  
 Jeśli wartość nie może być serializowana lub konwerter nie obsługuje serializacji, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementacja musi zwracać `null`i może zgłosić wyjątek w tym przypadku. Ale w przypadku zgłaszania wyjątków należy zgłosić niezdolność do korzystania z tej konwersji w ramach <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementacji, tak aby najlepszym rozwiązaniem w zakresie <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> sprawdzania od początku, aby uniknąć wyjątków.  
  
 Jeśli `destinationType` parametr nie jest typu <xref:System.String>, można wybrać własny sposób obsługi konwertera. Zazwyczaj można przywrócić podstawową obsługę implementacji, która w basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> wywołuje konkretny wyjątek.  
  
### <a name="implementing-canconvertto"></a>Implementowanie CanConvertTo  
 Implementacja powinna zwracać `true` dla `destinationType` typu<xref:System.String>i w inny sposób odroczyć na implementację podstawową. <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
### <a name="implementing-canconvertfrom"></a>Implementowanie CanConvertFrom  
 Implementacja powinna zwracać `true` dla `sourceType` typu<xref:System.String>i w inny sposób odroczyć na implementację podstawową. <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Stosowanie TypeConverterAttribute  
 Aby konwerter typu niestandardowego był używany jako typ działającego konwertera klasy niestandardowej przez procesor XAML, należy zastosować <xref:System.ComponentModel.TypeConverterAttribute> do definicji klasy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Określony za pomocą atrybutu musi być nazwą typu niestandardowego konwertera typów. Po zastosowaniu tego atrybutu, gdy procesor XAML obsługuje wartości, w których typ właściwości używa typu klasy niestandardowej, może wprowadzać ciągi i zwracać wystąpienia obiektów.  
  
 Można również udostępnić konwerter typów dla poszczególnych właściwości. Zamiast stosować `get` / `set` do definicji klasy, zastosuj ją do definicji właściwości (głównej definicji, a nie w ramach jej implementacji). <xref:System.ComponentModel.TypeConverterAttribute> Typ właściwości musi być zgodny z typem, który jest przetwarzany przez konwerter typów niestandardowych. Po zastosowaniu tego atrybutu, gdy procesor XAML obsługuje wartości tej właściwości, może przetwarzać ciągi wejściowe i zwracać wystąpienia obiektów. Technika konwertera typów dla właściwości jest szczególnie przydatna, jeśli zdecydujesz się użyć typu właściwości z Microsoft .NET Framework lub z innej biblioteki, w której nie można kontrolować definicji klasy i nie można jej <xref:System.ComponentModel.TypeConverterAttribute> zastosować.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.TypeConverter>
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
