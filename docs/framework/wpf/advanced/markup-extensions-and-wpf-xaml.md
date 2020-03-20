---
title: Rozszerzenia znaczników i XAML
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
ms.openlocfilehash: c288055a27cbab75a5cdf541e539ea20e490c965
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141058"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozszerzenia znacznikowania i WPF XAML
W tym temacie przedstawiono pojęcie rozszerzeń znaczników dla XAML, w tym ich reguły składni, cel i model obiektu klasy, który jest u ich podstaw. Rozszerzenia znaczników są ogólną cechą języka XAML i implementacji usług XAML .NET. W tym temacie szczegółowo rozszerzenia znaczników do użycia w WPF XAML.  

<a name="XAML_Processors_and_Markup_Extensions"></a>
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML i rozszerzenia znaczników  
 Ogólnie rzecz biorąc, analizator XAML może interpretować wartość atrybutu jako ciąg literał, który można przekonwertować na element pierwotny, lub przekonwertować go na obiekt za pomocą niektórych środków. Jednym z takich środków jest odwoływanie się do konwertera typu; jest to udokumentowane w temacie [TypeConverters i XAML](typeconverters-and-xaml.md). Istnieją jednak scenariusze, w których wymagane jest inne zachowanie. Na przykład procesor XAML można poinstruować, że wartość atrybutu nie powinna spowodować nowego obiektu na wykresie obiektu. Zamiast tego atrybut powinien spowodować wykres obiektu, który sprawia, że odwołanie do już skonstruowany obiekt w innej części wykresu lub obiektu statycznego. Innym scenariuszem jest to, że procesor XAML może być poinstruowany, aby użyć składni, która zapewnia domyślne argumenty do konstruktora obiektu. Są to typy scenariuszy, w których rozszerzenie znaczników może zapewnić rozwiązanie.  
  
<a name="Basic_Markup_Extension_Syntax"></a>
## <a name="basic-markup-extension-syntax"></a>Składnia rozszerzenia znacznika podstawowego  
 Rozszerzenie znaczników można zaimplementować, aby zapewnić wartości właściwości w użyciu atrybutu, właściwości w użyciu elementu właściwości lub obu.  
  
 W przypadku podania wartości atrybutu składnia, która odróżnia sekwencję rozszerzenia znaczników od procesora XAML, jest obecnością nawiasów klamrowych otwierających i zamykających ({ i }). Typ rozszerzenia znaczników jest następnie identyfikowany przez token ciągu bezpośrednio po otwarciu nawiasu klamrowego.  
  
 W przypadku użycia w składni elementu właściwości rozszerzenie znaczników jest wizualnie takie samo jak każdy inny element używany do zapewnienia wartości elementu właściwości: deklaracja elementu XAML, która odwołuje się do klasy rozszerzenia znaczników jako elementu, ujętego w nawiasy kątowe (<>).  
  
<a name="XAML_Defined_Markup_Extensions"></a>
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowanych przez XAML  
 Istnieje kilka rozszerzeń znaczników, które nie są specyficzne dla implementacji WPF XAML, ale zamiast tego są implementacje wewnętrznego lub funkcje XAML jako język. Te rozszerzenia znaczników są implementowane w zestawie System.Xaml jako część ogólnych usług XAML programu .NET Framework i znajdują się w obszarze nazw XAML języka XAML języka XAML. Jeśli chodzi o typowe użycie znaczników, te rozszerzenia znaczników `x:` są zazwyczaj identyfikowalne przez prefiks w użyciu. Klasa <xref:System.Windows.Markup.MarkupExtension> podstawowa (również zdefiniowana w systemie.Xaml) udostępnia wzorzec, który wszystkie rozszerzenia znaczników powinny być używane w celu zapewnienia obsługi w czytnikach XAML i modułach zapisujących XAML, w tym w WPF XAML.  
  
- `x:Type`dostarcza <xref:System.Type> obiekt dla nazwanego typu. Ta funkcja jest najczęściej używana w stylach i szablonach. Aby uzyskać szczegółowe informacje, zobacz [x:Wpisz rozszerzenie znaczników](../../../desktop-wpf/xaml-services/xtype-markup-extension.md).  
  
- `x:Static`tworzy wartości statyczne. Wartości pochodzą z jednostek kodu typu wartości, które nie są bezpośrednio typu wartości właściwości docelowej, ale mogą być oceniane do tego typu. Aby uzyskać szczegółowe informacje, zobacz [x:Static Markup Extension](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md).  
  
- `x:Null`określa `null` jako wartość właściwości i może być używany dla atrybutów lub wartości elementu właściwości. Aby uzyskać szczegółowe informacje, zobacz [x:Rozszerzenie znaczników zerowych](../../../desktop-wpf/xaml-services/xnull-markup-extension.md).  
  
- `x:Array`zapewnia obsługę tworzenia tablic ogólnych w składni XAML, w przypadkach, gdy obsługa kolekcji zapewniana przez podstawowe elementy WPF i modele kontroli nie jest celowo używana. Aby uzyskać szczegółowe informacje, zobacz [x:Rozszerzenie znaczników tablicy](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).  
  
> [!NOTE]
> `x:` Prefiks jest używany do typowego mapowania przestrzeni nazw XAML wewnętrznego języka XAML w elemencie głównym pliku lub produkcji XAML. Na przykład szablony programu Visual Studio dla aplikacji WPF inicjują plik XAML przy użyciu tego `x:` mapowania. Można wybrać inny token prefiksu w mapowaniu przestrzeni nazw XAML, ale w tej dokumentacji przyjęto domyślne `x:` mapowanie jako sposób identyfikowania tych jednostek, które są zdefiniowaną częścią obszaru nazw XAML dla języka XAML, w przeciwieństwie do domyślnego obszaru nazw WPF lub innych obszarów nazw XAML niezwiązanych z określoną strukturą.  
  
<a name="WPF_Specific_Markup_Extensions"></a>
## <a name="wpf-specific-markup-extensions"></a>Rozszerzenia znaczników specyficznych dla WPF  
 Najczęstsze rozszerzenia znaczników używane w programowaniu WPF są`StaticResource` te, które obsługują odwołania do zasobów ( i `DynamicResource`), i te, które obsługują powiązanie danych (`Binding`).  
  
- `StaticResource`zapewnia wartość właściwości, zastępując wartość już zdefiniowanego zasobu. Ocena `StaticResource` jest ostatecznie dokonywana w czasie ładowania XAML i nie ma dostępu do wykresu obiektu w czasie wykonywania. Aby uzyskać szczegółowe informacje, zobacz [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- `DynamicResource`zapewnia wartość właściwości przez odroczenie tej wartości, aby być odwołaniem w czasie wykonywania do zasobu. Odwołanie do zasobu dynamicznego wymusza nowe wyszukiwanie za każdym razem, gdy taki zasób jest dostępny i ma dostęp do wykresu obiektu w czasie wykonywania. Aby uzyskać ten dostęp, `DynamicResource` koncepcja jest obsługiwana przez właściwości zależności w systemie właściwości WPF i oceniane wyrażenia. W związku z `DynamicResource` tym można używać tylko dla obiektu docelowego właściwości zależności. Aby uzyskać szczegółowe informacje, zobacz [Rozszerzenie znaczników dynamicresource](dynamicresource-markup-extension.md).  
  
- `Binding`zapewnia wartość powiązaną z danymi dla właściwości, przy użyciu kontekstu danych, który ma zastosowanie do obiektu nadrzędnego w czasie wykonywania. To rozszerzenie znaczników jest stosunkowo złożone, ponieważ umożliwia istotne składnię w ykań do określania powiązania danych. Aby uzyskać szczegółowe informacje, zobacz [Rozszerzenie znaczników powiązania](binding-markup-extension.md).  
  
- `RelativeSource`zawiera informacje źródłowe dla, <xref:System.Windows.Data.Binding> które można poruszać się kilka możliwych relacji w drzewie obiektów w czasie wykonywania. Zapewnia to specjalistyczne pozyskiwanie powiązań, które są tworzone w szablonach wielofunkcyjnych lub tworzone w kodzie bez pełnej wiedzy otaczającego drzewa obiektów. Aby uzyskać szczegółowe informacje, zobacz [RelativeSource MarkupExtension](relativesource-markupextension.md).  
  
- `TemplateBinding`umożliwia szablon formantu do używania wartości dla właściwości szablonu, które pochodzą z właściwości zdefiniowanych przez model obiektu klasy, która będzie używać szablonu. Innymi słowy właściwość w definicji szablonu można uzyskać dostęp do kontekstu, który istnieje tylko po zastosowaniu szablonu. Aby uzyskać szczegółowe informacje, zobacz [Rozszerzenie znaczników przywiązywania szablonu.](templatebinding-markup-extension.md) Aby uzyskać więcej informacji `TemplateBinding`na temat praktycznego stosowania programu , zobacz [Stylowanie za pomocą przykładu ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`obsługuje stosunkowo zaawansowany scenariusz obrazowania. Aby uzyskać szczegółowe informacje, zobacz [ColorConvertedBitmap Markup Extension](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey`i `ThemeDictionary` obsługuje aspekty wyszukiwania zasobów, szczególnie dla zasobów i tematów, które są pakowane z formantami niestandardowymi. Aby uzyskać więcej informacji, zobacz [ComponentResourceKey Markup Extension](componentresourcekey-markup-extension.md), [ThemeDictionary Markup Extension](themedictionary-markup-extension.md)lub [Control Authoring Overview](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>
## <a name="extension-classes"></a>\*Klasy rozszerzeń  
 W przypadku ogólnego języka XAML i wyszerzeń znaczników specyficznych dla WPF zachowanie każdego rozszerzenia `*Extension` znaczników jest <xref:System.Windows.Markup.MarkupExtension>identyfikowane z <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> procesorem XAML za pośrednictwem klasy, która wywodzi się z metody i zapewnia implementację metody. Ta metoda na każdym rozszerzeniu zapewnia obiekt, który jest zwracany podczas oceny rozszerzenia znaczników. Zwrócony obiekt jest zazwyczaj oceniane na podstawie różnych tokenów ciąg, które są przekazywane do rozszerzenia znaczników.  
  
 Na przykład <xref:System.Windows.StaticResourceExtension> klasa zapewnia implementacji powierzchni rzeczywistego wyszukiwania <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> zasobów, tak aby jego implementacja zwraca obiekt, który jest wymagany, z danych wejściowych tej konkretnej implementacji jest ciąg, który jest używany do wyszukiwania zasobu przez jego `x:Key`. Wiele z tych szczegółów implementacji jest nieistotne, jeśli używasz istniejącego rozszerzenia znaczników.  
  
 Niektóre rozszerzenia znaczników nie używają argumentów tokenu ciągu. Jest to spowodowane zwróceniem wartości statycznej lub spójnej lub ponieważ kontekst dla wartości, która powinna `serviceProvider` zostać zwrócona, jest dostępny za pośrednictwem jednej z usług przekazanych przez parametr.  
  
 Wzorzec `*Extension` nazewnictwa jest dla wygody i spójności. Nie jest konieczne, aby procesor XAML zidentyfikować tę klasę jako obsługę rozszerzenia znaczników. Tak długo, jak codebase zawiera System.Xaml i używa .NET Framework XAML Services implementacje, wszystko, co jest <xref:System.Windows.Markup.MarkupExtension> niezbędne do rozpoznania jako rozszerzenie znaczników XAML jest pochodzić z i do obsługi składni konstrukcji. WPF WPF definiuje klasy włączania rozszerzenia znaczników, które nie są zgodne ze wzorcem `*Extension` nazewnictwa, na przykład <xref:System.Windows.Data.Binding>. Zazwyczaj powodem tego jest, że klasa obsługuje scenariusze poza czystej obsługi rozszerzenia znaczników. W przypadku <xref:System.Windows.Data.Binding>, że klasa obsługuje dostęp w czasie wykonywania do metod i właściwości obiektu dla scenariuszy, które nie mają nic wspólnego z XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Interpretacja klasy rozszerzenia tekstu inicjowania  
 Tokeny ciągu po nazwie rozszerzenia znaczników i nadal w nawiasach klamrowych są interpretowane przez procesor XAML w jeden z następujących sposobów:  
  
- Przecinek zawsze reprezentuje separator lub ogranicznik poszczególnych tokenów.  
  
- Jeśli poszczególne tokeny oddzielone nie zawierają żadnych znaków równości, każdy token jest traktowany jako argument konstruktora. Każdy parametr konstruktora musi być podany jako typ oczekiwany przez ten podpis i w odpowiedniej kolejności oczekiwanej przez ten podpis.  
  
    > [!NOTE]
    > Procesor XAML musi wywołać konstruktora, który pasuje do liczby argumentów liczby par. Z tego powodu jeśli implementujesz niestandardowe rozszerzenie znaczników, nie podaj wielu konstruktorów z tą samą liczbą argumentów. Zachowanie procesora XAML zachowuje się, jeśli istnieje więcej niż jedna ścieżka konstruktora rozszerzenia znaczników z tą samą liczbą parametrów, ale należy przewidzieć, że procesor XAML może zgłaszać wyjątek dotyczący użycia, jeśli taka sytuacja występuje w definicje typów rozszerzeń znaczników.  
  
- Jeśli poszczególne oddzielone tokeny zawierają znaki równe, procesor XAML najpierw wywołuje konstruktora bez parametrów dla rozszerzenia znaczników. Następnie każda para name=value jest interpretowana jako nazwa właściwości, która istnieje w rozszerzeniu znaczników i wartość do przypisania do tej właściwości.  
  
- Jeśli istnieje równoległy wynik między zachowaniem konstruktora i zachowanie ustawienie właściwości w rozszerzeniu znaczników, nie ma znaczenia, które zachowanie używasz. Jest bardziej powszechne użycie do korzystania z par*wartości* *właściwości*`=`dla rozszerzeń znaczników, które mają więcej niż jedną właściwość settable, jeśli tylko dlatego, że sprawia, że znaczników bardziej zamierzone i są mniej prawdopodobne, aby przypadkowo transponować parametry konstruktora. (Po określeniu par property=value te właściwości mogą być w dowolnej kolejności). Ponadto nie ma żadnej gwarancji, że rozszerzenie znaczników dostarcza parametr konstruktora, który ustawia każdą z jego właściwości settable. Na przykład <xref:System.Windows.Data.Binding> jest rozszerzenie znaczników, z wielu właściwości, które są settable <xref:System.Windows.Data.Binding> za pośrednictwem rozszerzenia w postaci*wartości* *właściwości,*`=`ale obsługuje tylko dwa konstruktory: konstruktor bez parametrów i jeden, który ustawia ścieżkę początkową.  
  
- Przecinek dosłowny nie może być przekazany do rozszerzenia znaczników bez wychwytu.  
  
<a name="EscapeSequences"></a>
## <a name="escape-sequences-and-markup-extensions"></a>Sekwencje ucieczki i rozszerzenia znaczników  
 Obsługa atrybutów w procesorze XAML używa nawiasów klamrowych jako wskaźników sekwencji rozszerzenia znaczników. Istnieje również możliwość uzyskania dosłownej wartości atrybutu nawiasu klamrowego, jeśli to konieczne, wprowadzając sekwencję ucieczki przy użyciu pustej pary nawiasów klamrowych, po której następuje dosłowny nawias klamrowy. Zobacz [ {} Sekwencja ucieczki — rozszerzenie znaczników](../../../desktop-wpf/xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Zagnieżdżanie rozszerzeń znaczników w użyciu XAML  
 Zagnieżdżanie wielu rozszerzeń znaczników jest obsługiwane, a każde rozszerzenie znaczników zostanie najpierw ocenione najgłębniej. Rozważmy na przykład następujące użycie:  
  
```xaml  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 W tym użyciu `x:Static` instrukcja jest oceniane najpierw i zwraca ciąg. Ten ciąg jest następnie używany `DynamicResource`jako argument dla .  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozszerzenia znaczników i składnia elementu właściwości  
 Gdy jest używany jako element obiektu, który wypełnia wartość elementu właściwości, klasa rozszerzenia znaczników jest wizualnie nie do odróżnienia od typowego elementu obiektu, który może być używany w XAML. Praktyczna różnica między typowym elementem obiektu a rozszerzeniem znaczników polega na tym, że rozszerzenie znaczników jest oceniane na wartość wpisaną lub odroczone jako wyrażenie. W związku z tym mechanizmy dla wszystkich możliwych błędów typu wartości właściwości dla rozszerzenia znaczników będą różne, podobnie jak późno powiązana właściwość jest traktowana w innych modelach programowania. Zwykły element obiektu będą oceniane dla dopasowania typu do właściwości docelowej jest ustawienie, gdy XAML jest analizowany.  
  
 Większość rozszerzeń znaczników, gdy jest używana w składni elementu obiektu do wypełnienia elementu właściwości, nie będzie miała zawartości ani żadnej dalszej składni elementu właściwości w obrębie. W związku z tym należy zamknąć znacznik elementu obiektu i nie podaj żadnych elementów podrzędnych. Za każdym razem, gdy dowolny element obiektu zostanie napotkany przez procesor XAML, wywoływany jest konstruktor dla tej klasy, który tworzy wystąpienia obiektu utworzonego na podstawie analizowanego elementu. Klasa rozszerzenia znaczników nie różni się inaczej: jeśli rozszerzenie znaczników ma być użyteczne w składni elementu obiektu, musisz podać konstruktor bez parametrów. Niektóre istniejące rozszerzenia znaczników mają co najmniej jedną wymaganą wartość właściwości, która musi być określona dla efektywnego inicjowania. Jeśli tak, ta wartość właściwości jest zazwyczaj podana jako atrybut właściwości w elemencie obiektu. W [obszarze nazw XAML (x:) Funkcje języka](../../../desktop-wpf/xaml-services/namespace-language-features.md) i [WPF XAML Rozszerzenia](wpf-xaml-extensions.md) stron odwołania, rozszerzenia znaczników, które mają wymagane właściwości (i nazwy wymaganych właściwości) zostaną odnotowane. Strony odwołań będą również pamiętać, jeśli składnia elementu obiektu lub składnia atrybutów jest niedozwolona dla określonych rozszerzeń znaczników. Godnym uwagi przypadkiem jest [x:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md), które nie obsługuje składni atrybutów, ponieważ zawartość tej tablicy musi być określona w tagowaniu jako zawartość. Zawartość tablicy są obsługiwane jako obiekty ogólne, w związku z tym nie domyślny konwerter typu dla atrybutu jest możliwe. Ponadto [x:Rozszerzenie znaczników tablicy](../../../desktop-wpf/xaml-services/xarray-markup-extension.md) wymaga parametru. `type`  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Przestrzeń nazwa (x:) XAML — Funkcje językowe](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [StaticResource — Rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
- [DynamicResource — Rozszerzenie znaczników](dynamicresource-markup-extension.md)
- [x:Type — Rozszerzenie znaczników](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
