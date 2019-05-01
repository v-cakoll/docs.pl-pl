---
title: Rozszerzenia znacznikowania i WPF XAML
ms.date: 03/30/2017
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
ms.openlocfilehash: 46539f0cfdcc478e2f5e4cd7aecf16ac059e6332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804588"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozszerzenia znacznikowania i WPF XAML
W tym temacie przedstawiono koncepcję — rozszerzenia znaczników dla XAML, w tym ich reguły składni, cel i model obiektów klasy, która jest podporządkowana narzędziu je. Rozszerzenia znaczników są ogólną funkcją języka XAML i implementacji .NET usług XAML. W tym temacie szczegółowo specjalnie do użytku w programie WPF XAML — rozszerzenia znaczników.  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML i rozszerzeń znaczników  
 Ogólnie rzecz biorąc analizator składni XAML albo może interpretować wartość atrybutu jako ciąg literału, który można przekonwertować elementu podstawowego lub przekonwertować obiekt za pomocą środków. Jednego takiego oznacza, że jest odwołując konwertera typów; jest to opisane w temacie [TypeConverters i XAML](typeconverters-and-xaml.md). Jednak istnieją scenariusze, w których wymagane są różne zachowanie. Na przykład procesora XAML może się instrukcja, że wartość atrybutu nie powinno spowodować nowy obiekt na grafie obiektu. Zamiast tego atrybutu powinno spowodować wykresu obiektu, który sprawia, że odwołanie do już skonstruowanego obiektu w innej części wykres lub obiekt statyczny. Inny scenariusz polega na tym, że procesor XAML może być zobowiązany do używania składni, która zawiera argumenty inne niż domyślne do konstruktora obiektu. Są to typy scenariuszy, w którym rozszerzenie znaczników mogą udostępniać rozwiązania.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Składni rozszerzenia znaczników podstawowych  
 Rozszerzenie znaczników można zaimplementować o podanie wartości właściwości użycie atrybutu, właściwości w użycie elementu właściwości lub obu.  
  
 W przypadku użycia, aby zapewnić wartość atrybutu, składnia, która odróżnia sekwencji rozszerzenia znaczników w celu procesora XAML jest obecność otwierający i zamykający nawias klamrowy ({i}). Typ — rozszerzenie znaczników następnie jest identyfikowany przez token ciągu bezpośrednio po otwierającym nawiasie klamrowym.  
  
 W przypadku użycia w składni elementu właściwości, rozszerzenie znaczników wizualnie jest taka sama jak inny element używane do zapewnienia wartości właściwości elementu: deklaracji elementu XAML, który odwołuje się klasa rozszerzenia struktury znaczników jako element, ujęte w nawiasach kątowych (<> ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane w XAML  
 Istnieją kilka rozszerzeń struktury znaczników, które nie są specyficzne dla implementacji WPF XAML, ale zamiast tego są w implementacji funkcji wewnętrznych lub funkcje XAML jako język. Te rozszerzenia znaczników są implementowane w zestawie System.Xaml jako część ogólnego usług .NET Framework XAML i znajdują się w przestrzeni nazw XAML dla języka XAML. Pod względem wspólne użycie znaczników, te rozszerzenia znaczników są zazwyczaj identyfikowane przez `x:` prefiks w użycia. <xref:System.Windows.Markup.MarkupExtension> Klasę bazową (również zdefiniowanej w System.Xaml) zawiera wzorzec, która powinna być używana wszystkie rozszerzenia znaczników, aby mogły być obsługiwane w XAML czytników i składników zapisywania XAML, w tym w WPF XAML.  
  
- `x:Type` dostarcza <xref:System.Type> obiektu dla typu nazwanego. Ten obiekt jest używana najczęściej w — style i szablony. Aby uzyskać więcej informacji, zobacz [x: Type Markup Extension](../../xaml-services/x-type-markup-extension.md).  
  
- `x:Static` Tworzy wartości statyczne. Wartości pochodzą z jednostki kodu typ wartości, które nie są bezpośrednio typ wartości właściwości docelowych, ale mogą być obliczane do tego typu. Aby uzyskać więcej informacji, zobacz [x: Static — rozszerzenie znaczników](../../xaml-services/x-static-markup-extension.md).  
  
- `x:Null` Określa `null` jako wartość właściwości i mogą być używane dla atrybutów lub wartości elementu właściwości. Aby uzyskać więcej informacji, zobacz [x: Null — rozszerzenie znaczników](../../xaml-services/x-null-markup-extension.md).  
  
- `x:Array` zapewnia obsługę tworzenia tablic ogólne w XAML składni w przypadkach, gdzie kolekcji pomoc techniczna świadczona przez elementy bazy WPF i modele kontroli celowo nie jest używana. Aby uzyskać więcej informacji, zobacz [x: Array — rozszerzenie znaczników](../../xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Prefiks jest używany dla typowych mapowania przestrzeni nazw XAML wewnętrzne języka XAML, w elemencie głównym pliku XAML lub produkcji. Na przykład szablony programu Visual Studio dla aplikacji WPF zainicjować pliku XAML, za pomocą tego `x:` mapowania. Możesz wybrać inny token własne mapowania przestrzeni nazw XAML, ale ta dokumentacja przyjmie domyślną `x:` mapowanie jako sposób identyfikacji tych jednostek, które są zdefiniowane części przestrzeni nazw XAML dla języka XAML, w przeciwieństwie Aby WPF domyślny obszar nazw lub w innych przestrzeniach nazw XAML nie związane z określonym środowiskiem.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozszerzenia znaczników charakterystyczne dla WPF  
 Najbardziej typowe rozszerzenia znaczników, używany w programowaniu WPF to te, które obsługuje odwołania do zasobów (`StaticResource` i `DynamicResource`) oraz te, które obsługuje powiązanie danych (`Binding`).  
  
- `StaticResource` zawiera wartość dla właściwości, zastępując wartości zasobu już zdefiniowane. A `StaticResource` oceny ostatecznie jest wykonywane w czasie ładowania XAML i nie ma dostępu do wykresu obiektu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [staticresource — rozszerzenie znaczników](staticresource-markup-extension.md).  
  
- `DynamicResource` zawiera wartość dla właściwości, opóźnienie tej wartości jako odwołanie do zasobu środowiska wykonawczego. Odwołanie do zasobu dynamicznego wymusza nowe wyszukiwanie każdym razem, że taki zasób jest dostępny i ma dostęp do wykresu obiektu w czasie wykonywania. Aby uzyskać dostęp, `DynamicResource` koncepcji jest obsługiwana przez właściwości zależności w systemie właściwości WPF i obliczone wyrażenia. W związku z tym można używać tylko `DynamicResource` dla obiektu docelowego właściwości zależności. Aby uzyskać więcej informacji, zobacz [dynamicresource — rozszerzenie znaczników](dynamicresource-markup-extension.md).  
  
- `Binding` zawiera wartość dla właściwości, za pomocą kontekstu danych, która ma zastosowanie do obiektu nadrzędnego w czasie wykonywania powiązany z danymi. Tego rozszerzenia znacznika jest dość złożone, ponieważ umożliwia wbudowane istotne składnia określająca powiązanie danych. Aby uzyskać więcej informacji, zobacz [— rozszerzenie znaczników powiązania](binding-markup-extension.md).  
  
- `RelativeSource` zawiera informacje o źródle <xref:System.Windows.Data.Binding> , można przejść kilka możliwych relacji w drzewie obiektów czasu wykonywania. Zapewnia to wyspecjalizowane określania źródła dla powiązań, które są w szablonach wielokrotnego użytku lub tworzony kod bez pełnej znajomości otaczającego drzewa obiektów. Aby uzyskać więcej informacji, zobacz [RelativeSource, rozszerzenie znaczników](relativesource-markupextension.md).  
  
- `TemplateBinding` Umożliwia szablonu kontrolki użyć wartości dla właściwości oparte na szablonach, które pochodzą z zdefiniowana przez model obiektu właściwości klasy, która będzie używać szablonu. Innymi słowy właściwości wewnątrz definicji szablonu mają dostęp do kontekstu, który istnieje tylko po zastosowaniu szablonu. Aby uzyskać więcej informacji, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md). Aby uzyskać więcej informacji na temat praktyczne wykorzystanie `TemplateBinding`, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap` obsługuje stosunkowo zaawansowanym scenariuszu przetwarzania obrazów. Aby uzyskać więcej informacji, zobacz [colorconvertedbitmap — rozszerzenie znaczników](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey` i `ThemeDictionary` obsługuje aspektów wyszukiwania zasobów, szczególnie w przypadku zasobów i motywów, które są dostarczane z formantami niestandardowymi. Aby uzyskać więcej informacji, zobacz [componentresourcekey — rozszerzenie znaczników](componentresourcekey-markup-extension.md), [themedictionary — rozszerzenie znaczników](themedictionary-markup-extension.md), lub [omówienie tworzenia kontrolek](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Rozszerzenie klasy  
 Dla języka XAML ogólnego i rozszerzenia znaczników charakterystyczne dla WPF, zachowanie każdego rozszerzenia znaczników jest identyfikowana procesor XAML za pośrednictwem `*Extension` klasę pochodzącą od <xref:System.Windows.Markup.MarkupExtension>i oferuje implementację <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> Metoda. Ta metoda na każde rozszerzenie zapewnia obiekt, który jest zwracany, jeśli rozszerzenie znaczników jest oceniany. Zwrócony obiekt zwykle jest oceniany na podstawie różnych tokenów parametrów, które są przekazywane do rozszerzenia znaczników.  
  
 Na przykład <xref:System.Windows.StaticResourceExtension> klasa udostępnia powierzchni implementacji wyszukiwania rzeczywistego zasobu, aby jego <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementacja zwraca obiekt, który jest wnioskowany z danymi wejściowymi tego określonego wykonania jest ciąg, który jest używany do wyszukiwania zasobów przez jego `x:Key`. Większość tych szczegółów implementacji nie jest ważna, jeśli używasz istniejącego rozszerzenia znaczników.  
  
 Niektóre rozszerzenia znaczników nie należy używać tokenu argumenty typu string. Jest to ponieważ zwracają wartość statycznych lub spójne lub kontekst powinna być zwracana wartość, jaką jest dostępna za pośrednictwem jednej z usług przekazywanych `serviceProvider` parametru.  
  
 `*Extension` Wzorzec nazewnictwa jest dla wygody i spójności. Nie jest konieczne w kolejności dla procesora XAML do identyfikowania tej klasy, jak pomoc techniczna dla rozszerzenia znaczników. Tak długo, jak baza kodu obejmuje System.Xaml i korzysta z usług programu .NET Framework XAML implementacji, wszystko co jest rozpoznawane, rozszerzenie znaczników XAML jest pochodną <xref:System.Windows.Markup.MarkupExtension> oraz zapewnić obsługę składni konstrukcji. WPF definiuje Włączanie rozszerzenia klasy znaczników, które nie podlegają `*Extension` nazewnictwa wzorca, na przykład <xref:System.Windows.Data.Binding>. Zazwyczaj przyczyną jest klasy obsługuje scenariusze poza obsługą rozszerzenia znaczników czysty. W przypadku właściwości <xref:System.Windows.Data.Binding>, że klasa obsługuje dostępu do metod i właściwości obiektu w czasie wykonywania dla scenariuszy, w których mają one nic wspólnego z XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Rozszerzenie klasy interpretacji inicjowania tekstu  
 Tokeny ciągu następujące rozszerzenie znaczników nazwy, a nadal mieszczą się w nawiasy klamrowe są interpretowane przez procesor XAML w jednym z następujących sposobów:  
  
- Przecinek zawsze odzwierciedla separator lub ogranicznika oddzielne tokeny.  
  
- Jeśli oddzielne tokeny rozdzielonych nie zawierają żadnych znaków równości, każdy token jest traktowany jako argument konstruktora. Każdy parametr konstruktora musi zostać podany jako typ oczekiwany przez ten podpis i w odpowiedniej kolejności, oczekiwany przez ten podpis.  
  
    > [!NOTE]
    >  Procesor XAML musi wywołać konstruktora, który jest zgodna z liczbą argumentów liczby pary. Z tego powodu w przypadku wdrażania jako rozszerzenie znacznika niestandardowego nie udostępniają wiele konstruktorów z tej samej liczby argumentów. Zachowanie jak procesor XAML zachowuje się, jeśli istnieje więcej niż jedną ścieżkę Konstruktor rozszerzenia znaczników przy użyciu tego samego liczba parametrów nie jest zdefiniowany, ale powinien przewidywać procesora XAML będzie mógł zgłosić wyjątek użycia, jeśli ta sytuacja występuje w Definicje typu rozszerzenia znaczników.  
  
- Jeśli poszczególne oddzielone tokeny zawierają znaki równości, a następnie procesora XAML najpierw wywołuje konstruktor domyślny dla rozszerzenia znaczników. Następnie w każdej pary nazwa =-wartość jest interpretowana jako nazwa właściwości, która istnieje na rozszerzenia znaczników i wartość do przypisania do właściwości.  
  
- W przypadku równoległego wynik między zachowanie konstruktora i ustawienia zachowania rozszerzenia znaczników właściwości nie ma znaczenia, zachowanie, których używasz. To bardziej powszechne, użycia, aby użyć *właściwość*`=`*wartość* pary — rozszerzenia znaczników, które mają więcej niż jedną konfigurowalną właściwość, jeśli jest to jedyna, ponieważ dzięki niemu znaczników bardziej celowe i jesteś mniej prawdopodobne przypadkowo TRANSPONUJ parametry konstruktora. (Po określeniu właściwość = para kluczy, te właściwości mogą być w dowolnej kolejności.) Ponadto nie ma żadnej gwarancji, że rozszerzenie znaczników dostarcza parametr konstruktora, który ustawia każdego z jego właściwości można ustawić jeden. Na przykład <xref:System.Windows.Data.Binding> jest rozszerzeniem znacznika o wiele właściwości, które można za pomocą rozszerzenia w *właściwość*`=`*wartość* formularza, ale <xref:System.Windows.Data.Binding> obsługuje tylko dwa Konstruktory: domyślny konstruktor a, który ustawia ścieżkę początkowej.  
  
- Literał przecinek nie można przekazać do rozszerzenia znacznika bez escapement.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Sekwencje unikowe i rozszerzeń znaczników  
 Obsługa w XAML procesor atrybutu używa nawiasów klamrowych jako wskaźniki sekwencji rozszerzenia znaczników. Istnieje również możliwość utworzenia nawiasów klamrowych literału znaku wartością atrybutu w razie potrzeby, wprowadzając sekwencji unikowej za pomocą pary pustych nawiasów klamrowych, następuje nawiasów klamrowych literału. Zobacz [ {} ucieczki sekwencja — rozszerzenie znaczników](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Rozszerzenia znaczników w XAML użycie zagnieżdżania  
 Zagnieżdżanie wiele rozszerzeń znaczników jest obsługiwany, a każde rozszerzenie znaczników zostaną ocenione najgłębiej zagnieżdżoną najpierw. Na przykład należy wziąć pod uwagę następujące użycie:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 W tym użycie `x:Static` instrukcji jest stosowana jako pierwsza i zwraca wartość typu ciąg. Czy ciąg jest następnie używany jako argument dla `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozszerzenia znacznikowania i składnia elementu właściwości  
 Gdy jest używana jako elementu obiektu, który wypełnia wartością elementu właściwości, klasa rozszerzenia struktury znaczników jest wizualnie nie do odróżnienia od elementu typowe opartych na typ obiektu, który może być używana w XAML. Praktyczne różnią się element typowego obiektu i rozszerzenia znaczników, rozszerzenie znaczników jest obliczane do wartości typizowane lub jest odroczone jako wyrażenie. W związku z tym mechanizmów pod kątem błędów możliwych typów wartości właściwości rozszerzenia znaczników będą różne, podobnie jak właściwość późno wiązana są używane w innych modeli programowania. Element zwykłej obiektu zostanie obliczone dla typu dopasowania wyników właściwość docelowa, który jest ustawienie, jeśli XAML jest analizowany.  
  
 Większość rozszerzenia znaczników, gdy są używane w składni obiektów do wypełnienia elementu właściwości, nie będzie zawierało składnia elementu zawartości lub więcej właściwości, w ramach. Ten sposób będzie zamknięcie tagu elementu obiektu i zapewniają nie podrzędnych elementów. Napotkaniu każdy element obiektu przez procesor XAML, Konstruktor dla klasy, nosi nazwę, która tworzy wystąpienie obiektu utworzonego na podstawie przeanalizowany element. Klasa rozszerzenia struktury znaczników nie różni się: Jeśli chcesz, rozszerzenie znaczników w składni obiektów można używać, należy podać domyślnego konstruktora. Niektóre istniejące rozszerzenia znaczników mają co najmniej jedną wartość wymagana właściwość, która musi być określona dla inicjowania skuteczne. Jeśli tak, wartości tej właściwości jest zazwyczaj podawana jako atrybut właściwości w elemencie obiektu. W [Namespace XAML (x:) Funkcje języka](../../xaml-services/xaml-namespace-x-language-features.md) i [WPF XAML rozszerzenia](wpf-xaml-extensions.md) odwoływać się do strony, znaczników, które będą wyświetlane informacje dotyczące rozszerzeń, które mają wymagane właściwości (i nazwy właściwości wymagane). Strony podręcznika udostępniamy również Jeśli składnia elementu obiektu lub Składnia atrybutu jest niedozwolona dla rozszerzenia znaczników określonej. Jest istotne [x: Array — rozszerzenie znaczników](../../xaml-services/x-array-markup-extension.md), który nie obsługuje składni atrybutów zawartości tej tablicy muszą być określone w tagowania jako zawartość. Zawartość tablicy są obsługiwane jako obiekty ogólne, w związku z tym nie konwertera typów domyślna dla atrybutu jest to możliwe. Ponadto [x: Array — rozszerzenie znaczników](../../xaml-services/x-array-markup-extension.md) wymaga `type` parametru.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Namespace XAML (x:) Funkcje językowe](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
- [DynamicResource, rozszerzenie znaczników](dynamicresource-markup-extension.md)
- [x:Type, rozszerzenie znaczników](../../xaml-services/x-type-markup-extension.md)
