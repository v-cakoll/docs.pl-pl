---
title: TypeConverters i XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187295"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters i XAML
W tym temacie przedstawiono cel konwersji typu z ciągu jako ogólną funkcję języka XAML. W .NET Framework <xref:System.ComponentModel.TypeConverter> klasa służy określonego celu jako część implementacji dla zarządzanej klasy niestandardowej, która może służyć jako wartość właściwości w użyciu atrybutu XAML. Jeśli piszesz klasę niestandardową i chcesz, aby wystąpienia klasy były użyteczne jako wartości atrybutów xaml settable, może być konieczne zastosowanie a <xref:System.ComponentModel.TypeConverterAttribute> do klasy, napisz klasę niestandardową <xref:System.ComponentModel.TypeConverter> lub obie.  

## <a name="type-conversion-concepts"></a>Pojęcia konwersji typu  
  
### <a name="xaml-and-string-values"></a>Wartości XAML i string  
 Po ustawieniu wartości atrybutu w pliku XAML początkowy typ tej wartości jest ciągiem w czystym tekście. Nawet inne podstawowe, takie <xref:System.Double> jak początkowo ciągi tekstowe do procesora XAML.  
  
 Procesor XAML potrzebuje dwóch informacji w celu przetworzenia wartości atrybutu. Pierwszą informacją jest typ wartości właściwości, która jest ustawiana. Każdy ciąg definiujący wartość atrybutu i przetwarzany w języku XAML musi ostatecznie zostać przekonwertowany lub rozpoznany na wartość tego typu. Jeśli wartość jest prymitywne, który jest rozumiany przez analizatora XAML (na przykład wartość liczbową), podejmowana jest bezpośrednia konwersja ciągu. Jeśli wartość jest wyliczeniem, ciąg jest używany do sprawdzania, czy nazwa pasuje do nazwanej stałej w tym wyliczeniu. Jeśli wartość nie jest ani analizatora zrozumiane pierwotne, ani wyliczenia, a następnie typ, o jakiej mowa musi być w stanie podać wystąpienie typu lub wartość, na podstawie przekonwertowanego ciągu. Odbywa się to poprzez wskazanie klasy konwertera typu. Konwerter typów jest skutecznie klasy pomocnika do dostarczania wartości innej klasy, zarówno dla scenariusza XAML, a także potencjalnie dla wywołań kodu w kodzie .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Korzystanie z istniejącego zachowania konwersji typów w języku XAML  
 W zależności od znajomości podstawowych pojęć XAML może być już przy użyciu zachowania konwersji typu w podstawowej aplikacji XAML, nie zdając sobie z tego sprawy. Na przykład WPF definiuje dosłownie setki właściwości, które mają <xref:System.Windows.Point>wartość typu. A <xref:System.Windows.Point> jest wartością, która opisuje współrzędną w dwuwymiarowej przestrzeni <xref:System.Windows.Point.X%2A> <xref:System.Windows.Point.Y%2A>współrzędnych i naprawdę ma tylko dwie ważne właściwości: i . Po określeniu punktu w XAML należy określić go jako ciąg z ogranicznikiem (zazwyczaj przecinkiem) między <xref:System.Windows.Point.X%2A> wartościami i <xref:System.Windows.Point.Y%2A> wartościami, które podajesz. Na przykład: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Nawet ten prosty <xref:System.Windows.Point> typ i jego proste użycie w XAML obejmują konwerter typu. W tym przypadku jest <xref:System.Windows.PointConverter>to klasa .  
  
 Konwerter typów <xref:System.Windows.Point> zdefiniowany na poziomie klasy usprawnia użycie znaczników <xref:System.Windows.Point>wszystkich właściwości, które przyjmują . Bez konwertera typów w tym miejscu, trzeba by o wiele bardziej pełne znaczników dla tego samego przykładu pokazano wcześniej:  

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
  
 Czy użyć ciągu konwersji typu lub bardziej pełnej składni równoważnej jest zazwyczaj wybór stylu kodowania. Przepływ pracy narzędzi XAML może również wpływać na sposób ustawiania wartości. Niektóre narzędzia XAML mają tendencję do emitowania najbardziej pełnej formy znaczników, ponieważ łatwiej jest w obie strony do widoków projektanta lub własnego mechanizmu serializacji.  
  
 Istniejące konwertery typów można zazwyczaj wykryć na typach WPF i .NET Framework, sprawdzając klasę (lub właściwość) pod kątem obecności zastosowanego <xref:System.ComponentModel.TypeConverterAttribute>. Ten atrybut będzie nazwać klasę, która jest konwerter typu pomocniczego dla wartości tego typu, do celów XAML, jak również potencjalnie innych celów.  
  
### <a name="type-converters-and-markup-extensions"></a>Typy konwerterów i rozszerzeń znaczników  
 Rozszerzenia znaczników i konwertery typów wypełniają role ortogonalne pod względem zachowania procesora XAML i scenariuszy, do których są stosowane. Chociaż kontekst jest dostępny dla użycia rozszerzenia znaczników, zachowanie konwersji typu właściwości, w których rozszerzenie znaczników zapewnia wartość, zazwyczaj nie jest sprawdzane w implementacjach rozszerzenia znaczników. Innymi słowy, nawet jeśli rozszerzenie znaczników zwraca `ProvideValue` ciąg tekstowy jako jego dane wyjściowe, zachowanie konwersji typu na tym ciągu, stosowane do określonej właściwości lub typ wartości właściwości nie jest wywoływana, Ogólnie rzecz biorąc, celem rozszerzenia znaczników jest przetwarzanie ciągu i zwracanie obiektu bez udziału konwertera typu.  
  
 Jedną z typowych sytuacji, w której rozszerzenie znaczników jest konieczne, a nie konwerter typu jest odwołanie do obiektu, który już istnieje. W najlepszym wypadku konwerter typu bezstanowego może generować tylko nowe wystąpienie, co może nie być pożądane. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników i WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Konwertery typów natywnych  
 W WPF I .NET Framework implementacji analizatora XAML istnieją pewne typy, które mają obsługi konwersji typu macierzystego, ale nie są typy, które mogą być konwencjonalnie traktowane jako prymitywy. Przykładem takiego typu <xref:System.DateTime>jest . Przyczyna tego jest oparta na tym, jak <xref:System.DateTime> działa architektura .NET Framework: typ jest zdefiniowany w mscorlib, najbardziej podstawowej bibliotece w .NET. <xref:System.DateTime>nie jest dozwolone, aby być przypisane z atrybutem, który pochodzi<xref:System.ComponentModel.TypeConverterAttribute> z innego zestawu, który wprowadza zależność (jest z systemu), więc mechanizm odnajdowania konwertera typ zwykle przez przypisanie nie mogą być obsługiwane. Zamiast tego analizator XAML ma listę typów, które wymagają takiego przetwarzania macierzystego i przetwarza je podobnie do sposobu przetwarzania prawdziwych elementów pierwotnych. (W przypadku <xref:System.DateTime> tego wiąże się <xref:System.DateTime.Parse%2A>wezwanie do .)  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>Implementowanie konwertera typów  
  
### <a name="typeconverter"></a>TypeConverter  
 W <xref:System.Windows.Point> przykładzie podanym wcześniej, klasa <xref:System.Windows.PointConverter> została wymieniona. W przypadku implementacji platformy .NET XAML wszystkie konwertery typów używane do celów XAML są klasami pochodzącymi z klasy podstawowej <xref:System.ComponentModel.TypeConverter>. Klasa <xref:System.ComponentModel.TypeConverter> istniała w wersjach programu .NET Framework, które poprzedzają istnienie kodu XAML; jednym z jego oryginalnych zastosowań było zapewnienie konwersji ciągów dla okien dialogowych właściwości w projektantów wizualnych. W przypadku języka XAML rola <xref:System.ComponentModel.TypeConverter> jest rozwijana o klasę podstawową dla konwersji ciągów i ciągów, które umożliwiają analizowanie wartości atrybutu ciągu i ewentualnie przetwarzanie wartości w czasie wykonywania właściwości określonego obiektu z powrotem do ciągu do serializacji jako atrybutu.  
  
 <xref:System.ComponentModel.TypeConverter>definiuje cztery elementy członkowskie, które są istotne dla konwersji do i z ciągów do celów przetwarzania XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z tych, najważniejszą <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>metodą jest . Ta metoda konwertuje ciąg wejściowy na wymagany typ obiektu. Ściśle rzecz biorąc, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metoda może być zaimplementowana w celu konwersji znacznie szerszy zakres typów do zamierzonego typu docelowego konwertera, a tym samym służyć do celów, które wykraczają <xref:System.String> poza XAML, takich jak obsługa konwersji w czasie wykonywania, ale do celów XAML jest tylko ścieżka kodu, który może przetwarzać dane wejściowe, które mają znaczenie.  
  
 Następną najważniejszą <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>metodą jest . Jeśli aplikacja jest konwertowana na reprezentację znaczników (na przykład, jeśli <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> jest zapisywana w formacie XAML jako plik), jest odpowiedzialna za tworzenie reprezentacji znaczników. W takim przypadku ścieżka kodu, która ma znaczenie dla `destinationType` <xref:System.String> XAML jest po przejściu a .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>i <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> są metody pomocy technicznej, które są używane, <xref:System.ComponentModel.TypeConverter> gdy usługa wysyła zapytanie możliwości implementacji. Należy zaimplementować `true` te metody, aby zwrócić dla przypadków specyficznych dla typu, które równoważne metody konwersji obsługi konwertera. Do celów XAML oznacza to <xref:System.String> zazwyczaj typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informacje o kulturze i konwertery typów dla XAML  

 Każda <xref:System.ComponentModel.TypeConverter> implementacja może mieć własną interpretację tego, co stanowi prawidłowy ciąg konwersji, a także może używać lub ignorować opis typu przekazany jako parametry. Istnieje ważne znaczenie w odniesieniu do kultury i konwersji typu XAML. Przy użyciu localizable ciągów jako wartości atrybutów jest całkowicie obsługiwane przez XAML. Jednak przy użyciu tego localizable ciąg jako typ konwerter danych wejściowych z określonymi wymaganiami kultury nie jest obsługiwany, ponieważ `en-US` konwertery typów dla wartości atrybutów XAML obejmują koniecznie stały język analizowania zachowanie przy użyciu kultury. Aby uzyskać więcej informacji na temat przyczyn projektowych tego ograniczenia, należy zapoznać się ze specyfikacją języka XAML[\[(MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 Jako przykład, gdzie kultura może być problemem, niektóre kultury użyć przecinka jako ich ogranicznik punktu dziesiętnego dla liczb. Spowoduje to zderzenie się z zachowaniem, które ma wiele konwerterów typu WPF XAML, które ma użycie przecinka jako ogranicznika (na podstawie historycznych precedensów, takich jak wspólny formularz X,Y lub rozdzielane przecinkami listy). Nawet przekazywanie kultury w otaczającym `Language` XAML (ustawienie lub `xml:lang` do `sl-SI` kultury, przykład kultury, która używa przecinka do przecinka dziesiętnego w ten sposób) nie rozwiązuje problemu.  
  
### <a name="implementing-convertfrom"></a>Implementowanie convertfrom  
 Aby być użytecznym <xref:System.ComponentModel.TypeConverter> jako implementacja, która <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> obsługuje XAML, metoda dla `value` tego konwertera musi zaakceptować ciąg jako parametr. Jeśli ciąg był w prawidłowym formacie i <xref:System.ComponentModel.TypeConverter> mogą być konwertowane przez implementację, a następnie zwrócony obiekt musi obsługiwać rzutowania do typu oczekiwanego przez właściwość. W przeciwnym <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> razie `null`implementacja musi zwrócić .  
  
 Każda <xref:System.ComponentModel.TypeConverter> implementacja może mieć własną interpretację tego, co stanowi prawidłowy ciąg konwersji, a także może używać lub ignorować opis typu lub konteksty kultury przekazywane jako parametry. Jednak przetwarzanie WPF XAML może nie przekazać wartości do kontekstu opisu typu we `xml:lang`wszystkich przypadkach, a także może nie przekazać kultury na podstawie .  
  
> [!NOTE]
> Nie należy używać kręconych znaków nawiasów klamrowych, szczególnie {, jako możliwego elementu formatu ciągu. Znaki te są zarezerwowane jako wejście i wyjście dla sekwencji rozszerzenia znaczników.  
  
### <a name="implementing-convertto"></a>Implementowanie convertto  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>jest potencjalnie używany do obsługi serializacji. Obsługa serializacji <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> dla typu niestandardowego i jego konwertera typu nie jest bezwzględnym wymaganiem. Jednak jeśli implementujesz formant lub używasz serializacji jako części funkcji lub projektu klasy, należy zaimplementować <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>program .  
  
 Aby być użytecznym <xref:System.ComponentModel.TypeConverter> jako implementacja, która <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> obsługuje XAML, metoda dla tego konwertera musi zaakceptować wystąpienie typu (lub wartość) obsługiwane jako `value` parametr. Gdy `destinationType` parametr jest <xref:System.String>typem, zwracany obiekt musi być <xref:System.String>w stanie być rzutowy jako . Zwrócony ciąg musi reprezentować `value`wartość serializowany . W idealnym przypadku format serializacji, który wybierzesz powinien być zdolny do <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> generowania tej samej wartości, jeśli ten ciąg zostały przekazane do implementacji tego samego konwertera, bez znacznej utraty informacji.  
  
 Jeśli wartość nie może być serializowany lub konwerter <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> nie `null`obsługuje serializacji, implementacja musi zwrócić i może zgłosić wyjątek w tym przypadku. Ale jeśli zgłosisz wyjątki, należy zgłosić niemożność <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> użycia tej konwersji jako <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> część implementacji, tak aby najlepsze praktyki sprawdzania z pierwszym, aby uniknąć wyjątków jest obsługiwana.  
  
 Jeśli `destinationType` parametr nie <xref:System.String>jest typu, można wybrać własną obsługę konwertera. Zazwyczaj należy przywrócić do obsługi implementacji podstawowej, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> która w podstawie zgłasza określony wyjątek.  
  
### <a name="implementing-canconvertto"></a>Implementacja CanConvertTo  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> powinna `true` `destinationType` powrócić <xref:System.String>do typu i w inny sposób odroczyć do implementacji podstawowej.  
  
### <a name="implementing-canconvertfrom"></a>Implementacja CanConvertFrom  
 Implementacja <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> powinna `true` `sourceType` powrócić <xref:System.String>do typu i w inny sposób odroczyć do implementacji podstawowej.  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>Stosowanie atrybutu TypeConverterAttribute  
 Aby konwerter typów niestandardowych był używany jako konwerter typów działających dla klasy niestandardowej <xref:System.ComponentModel.TypeConverterAttribute> przez procesor XAML, należy zastosować do definicji klasy. Określony <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> przez atrybut musi być nazwą typu konwertera typu niestandardowego. Zastosowany ten atrybut, gdy procesor XAML obsługuje wartości, w których typ właściwości używa niestandardowego typu klasy, może wprowadzać ciągi i zwracać wystąpienia obiektów.  
  
 Można również podać konwerter typów na podstawie dla właściwości. Zamiast stosować <xref:System.ComponentModel.TypeConverterAttribute> a do definicji klasy, należy zastosować go do definicji `get` / `set` właściwości (główna definicja, a nie implementacje w niej). Typ właściwości musi odpowiadać typowi, który jest przetwarzany przez konwerter typu niestandardowego. Zastosowany ten atrybut, gdy procesor XAML obsługuje wartości tej właściwości, może przetwarzać ciągi wejściowe i zwracać wystąpienia obiektów. Technika konwertera typu na właściwość jest szczególnie przydatna, jeśli wybierzesz typ właściwości z programu Microsoft .NET <xref:System.ComponentModel.TypeConverterAttribute> Framework lub innej biblioteki, w której nie można kontrolować definicji klasy i nie można zastosować tam.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.TypeConverter>
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
