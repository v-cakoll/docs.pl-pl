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
ms.openlocfilehash: 562eea34af44a8fb24199e81477a4cb2ddb1046c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991829"
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozszerzenia znacznikowania i WPF XAML
W tym temacie przedstawiono koncepcję rozszerzeń znaczników dla języka XAML, w tym ich reguły składni, przeznaczenie i model obiektów klasy, które są na siebie zależne. Rozszerzenia znaczników są ogólną cechą języka XAML i implementacją platformy .NET usług XAML. W tym temacie szczegółowo opisano rozszerzenia znaczników do użycia w języku XAML WPF.  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML i rozszerzenia znaczników  
 Ogólnie mówiąc, Analizator XAML może interpretować wartość atrybutu jako ciąg literału, który można przekonwertować na typ pierwotny, lub przekonwertować go na obiekt za pomocą pewnego środka. Takie oznacza, że odwołuje się do konwertera typów; jest to udokumentowane w temacie [TypeConverters i XAML](typeconverters-and-xaml.md). Istnieją jednak scenariusze, w których wymagane jest inne zachowanie. Na przykład procesora XAML można wydać, że wartość atrybutu nie powinna powodować, że nowy obiekt na grafie obiektów. Zamiast tego atrybut powinien skutkować wykresem obiektu, który tworzy odwołanie do już skonstruowanego obiektu w innej części grafu lub statycznego obiektu. Innym scenariuszem jest to, że procesor XAML można wydać, aby użyć składni, która zawiera argumenty inne niż domyślne do konstruktora obiektu. Są to typy scenariuszy, w których rozszerzenie znaczników może zapewnić rozwiązanie.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Podstawowa składnia rozszerzenia znaczników  
 Rozszerzenie znaczników można zaimplementować, aby zapewnić wartości właściwości w użyciu atrybutu, właściwości w użyciu elementu właściwości lub obu.  
  
 Gdy jest używany do podania wartości atrybutu, składnia odróżniająca sekwencję rozszerzenia znaczników do procesora XAML jest obecność otwierających i zamykających nawiasów klamrowych ({i}). Typ rozszerzenia znacznika jest następnie identyfikowany przez token ciągu bezpośrednio po otwierającym nawiasie klamrowym.  
  
 Gdy jest używany w składni elementu właściwości, rozszerzenie znaczników jest wizualnie takie samo jak każdy inny element, który jest używany do udostępniania wartości elementu właściwości: Deklaracja elementu XAML, która odwołuje się do klasy rozszerzenia znacznika jako element, ujęty w nawiasy kątowe (< > ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane w języku XAML  
 Istnieje kilka rozszerzeń znaczników, które nie są specyficzne dla implementacji języka XAML w języku WPF, ale zamiast nich są implementacje wewnętrznych lub funkcji języka XAML jako język. Te rozszerzenia znaczników są zaimplementowane w zestawie System. XAML jako część ogólnych usług XAML .NET Framework i znajdują się w przestrzeni nazw XAML języka XAML. W przypadku typowego użycia znaczników te rozszerzenia znaczników są zwykle identyfikowane przez `x:` prefiks w użyciu. Klasa <xref:System.Windows.Markup.MarkupExtension> bazowa (zdefiniowana również w pliku System. XAML) zawiera wzorzec, który powinien być używany przez wszystkie rozszerzenia znaczników w celu obsługi czytników XAML i autorów języka XAML, w tym w języku XAML WPF.  
  
- `x:Type`<xref:System.Type> dostarcza obiekt dla nazwanego typu. Ta funkcja jest używana najczęściej w stylach i szablonach. Aby uzyskać szczegółowe informacje, zobacz [X:Type — Markup Extension](../../xaml-services/x-type-markup-extension.md).  
  
- `x:Static`tworzy wartości statyczne. Wartości pochodzą z jednostek kodu typu wartości, które nie są bezpośrednio typem wartości właściwości docelowej, ale mogą być oceniane dla tego typu. Aby uzyskać szczegółowe informacje, zobacz [X:Static — Markup Extension](../../xaml-services/x-static-markup-extension.md).  
  
- `x:Null`Określa `null` jako wartość właściwości i może być używana dla atrybutów lub wartości elementów właściwości. Aby uzyskać szczegółowe informacje, zobacz [X:null — Markup Extension](../../xaml-services/x-null-markup-extension.md).  
  
- `x:Array`zapewnia obsługę tworzenia ogólnych tablic w składni języka XAML, w przypadkach, gdy obsługa kolekcji dostarczonych przez elementy bazowe WPF i modele kontroli nie jest świadomie używana. Aby uzyskać szczegółowe informacje, zobacz [X:Array Markup Extension](../../xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
> `x:` Prefiks jest używany dla typowego mapowania przestrzeni nazw XAML języka XAML, w elemencie głównym pliku XAML lub produkcji. Na przykład szablony programu Visual Studio dla aplikacji WPF inicjują plik XAML przy użyciu tego `x:` mapowania. Można wybrać inny token prefiksu we własnym mapowaniu przestrzeni nazw XAML, ale ta dokumentacja będzie zależeć od domyślnego `x:` mapowania jako metody identyfikacji tych jednostek, które są zdefiniowanej częścią przestrzeni nazw XAML dla języka XAML, w przeciwieństwie do do domyślnej przestrzeni nazw WPF lub innych przestrzeni nazw XAML niezwiązanych z konkretną strukturą.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozszerzenia znaczników specyficzne dla WPF  
 Najpopularniejsze rozszerzenia znaczników używane w programowaniu WPF to te, które obsługują odwołania do zasobów`StaticResource` ( `DynamicResource`i) oraz te, które obsługują powiązanie danych`Binding`().  
  
- `StaticResource`udostępnia wartość właściwości, zastępując wartość już zdefiniowanego zasobu. `StaticResource` Ocena jest ostatecznie wykonywana w czasie ładowania XAML i nie ma dostępu do grafu obiektów w czasie wykonywania. Aby uzyskać szczegółowe informacje, zobacz [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- `DynamicResource`udostępnia wartość właściwości przez odroczenie tej wartości jako odwołania w czasie wykonywania do zasobu. Dynamiczne odwołanie do zasobów wymusza nowe wyszukiwanie przy każdym dostępie do tego zasobu i ma dostęp do grafu obiektów w czasie wykonywania. Aby uzyskać ten dostęp, `DynamicResource` koncepcja jest obsługiwana przez właściwości zależności w systemie właściwości WPF i ocenia wyrażenia. W związku z tym można `DynamicResource` używać tylko dla celu właściwości zależności. Aby uzyskać szczegółowe informacje, zobacz [DynamicResource — Markup Extension](dynamicresource-markup-extension.md).  
  
- `Binding`udostępnia wartość powiązaną z danymi dla właściwości przy użyciu kontekstu danych, który ma zastosowanie do obiektu nadrzędnego w czasie wykonywania. To rozszerzenie znacznika jest stosunkowo skomplikowane, ponieważ umożliwia określenie poważnej składni wbudowanej w celu określenia powiązania danych. Aby uzyskać szczegółowe informacje, zobacz [Binding Markup Extension](binding-markup-extension.md).  
  
- `RelativeSource`zawiera informacje <xref:System.Windows.Data.Binding> źródłowe, które mogą nawigować po kilku możliwych relacjach w drzewie obiektów czasu wykonywania. Zapewnia to wyspecjalizowane źródła dla powiązań, które są tworzone w szablonach z wielojęzycznym użyciem lub utworzonych w kodzie bez pełnej znajomości drzewa otaczających obiektów. Aby uzyskać szczegółowe informacje, zobacz [RelativeSource MarkupExtension](relativesource-markupextension.md).  
  
- `TemplateBinding`umożliwia szablonowi kontrolki używanie wartości właściwości szablonu, które pochodzą z właściwości obiektów zdefiniowanych przez model klasy, która będzie używać szablonu. Innymi słowy, właściwość w ramach definicji szablonu może uzyskać dostęp do kontekstu, który istnieje tylko po zastosowaniu szablonu. Aby uzyskać szczegółowe informacje, zobacz [TemplateBinding Markup Extension](templatebinding-markup-extension.md). Aby uzyskać więcej informacji na temat praktycznego `TemplateBinding`zastosowania, zobacz [Style z przykładem elementy ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
- `ColorConvertedBitmap`obsługuje stosunkowo zaawansowany scenariusz tworzenia obrazu. Aby uzyskać szczegółowe informacje, zobacz [ColorConvertedBitmap — Markup Extension](colorconvertedbitmap-markup-extension.md).  
  
- `ComponentResourceKey`i `ThemeDictionary` obsługują aspekty wyszukiwania zasobów, szczególnie w przypadku zasobów i motywów, które są spakowane z kontrolkami niestandardowymi. Aby uzyskać więcej informacji, zobacz [ComponentResourceKey Markup Extension](componentresourcekey-markup-extension.md), [ThemeDictionary — Markup Extension](themedictionary-markup-extension.md)lub [Authoring Control Overview](../controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>\*Klasy rozszerzeń  
 W przypadku ogólnego języka XAML i rozszerzeń znaczników specyficznych dla platformy WPF zachowanie każdego rozszerzenia znacznika jest identyfikowane dla procesora XAML za pośrednictwem `*Extension` klasy, która pochodzi z <xref:System.Windows.Markup.MarkupExtension>i <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> zapewnia implementację Method. Ta metoda dla każdego rozszerzenia zapewnia obiekt, który jest zwracany, gdy rozszerzenie znacznika jest oceniane. Zwrócony obiekt jest zwykle oceniany na podstawie różnych tokenów ciągów, które są przesyłane do rozszerzenia znacznika.  
  
 Na przykład <xref:System.Windows.StaticResourceExtension> Klasa zawiera implementację rzeczywistego wyszukiwania zasobów, dzięki czemu jego <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementacja zwraca żądany obiekt, z danymi wejściowymi tej konkretnej implementacji jest ciąg, który jest używany do Zapoznaj się z zasobem `x:Key`. Większość tych szczegółów implementacji jest nieważna, jeśli używasz istniejącego rozszerzenia znaczników.  
  
 Niektóre rozszerzenia znaczników nie używają argumentów tokenów ciągów. Jest to spowodowane tym, że zwracają statyczną lub spójną wartość lub kontekst, dla którego powinna zostać zwrócona wartość, jest dostępny za pomocą jednej z usług `serviceProvider` przekazana przez parametr.  
  
 Wzorzec `*Extension` nazewnictwa ma na celu wygodę i spójność. Nie jest konieczne, aby procesor XAML zidentyfikował tę klasę jako obsługę rozszerzenia znaczników. Dopóki baza kodu zawiera system. XAML i używa .NET Framework implementacji usług XAML, wszystkie te, które są niezbędne do rozpoznania jako rozszerzenie języka XAML, pochodzą od <xref:System.Windows.Markup.MarkupExtension> i do obsługi składni konstrukcji. WPF definiuje klasy rozszerzeń znaczników, które nie są zgodne ze `*Extension` wzorcem nazewnictwa, na przykład. <xref:System.Windows.Data.Binding> Zazwyczaj przyczyną jest to, że Klasa obsługuje scenariusze wykraczające poza obsługę rozszerzenia czystego znacznika. W przypadku <xref:System.Windows.Data.Binding>, ta klasa obsługuje dostęp do metod i właściwości obiektu w czasie wykonywania dla scenariuszy, które nie mają nic robić z XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Interpretacja tekstu inicjującego klasy rozszerzenia  
 Tokeny ciągów po nazwie rozszerzenia znacznika i w nawiasach klamrowych są interpretowane przez procesor XAML w jeden z następujących sposobów:  
  
- Przecinek zawsze reprezentuje separator lub ogranicznik poszczególnych tokenów.  
  
- Jeśli pojedyncze tokeny oddzielone nie zawierają żadnych znaków równości, każdy token jest traktowany jako argument konstruktora. Każdy parametr konstruktora musi być określony jako typ oczekiwany przez ten podpis, a w odpowiedniej kolejności oczekiwanej przez ten podpis.  
  
    > [!NOTE]
    > Procesor XAML musi wywoływać konstruktora, który jest zgodny z liczbą argumentów liczby par. Z tego powodu w przypadku implementowania niestandardowego rozszerzenia znaczników nie należy podawać wielu konstruktorów o tej samej liczbie argumentów. Zachowanie w przypadku działania procesora XAML, jeśli istnieje więcej niż jedna ścieżka konstruktora rozszerzenia znacznika o tej samej liczbie parametrów, ale należy oczekiwać, że procesor XAML może zgłosić wyjątek w przypadku użycia, jeśli ta sytuacja istnieje w Definicje typu rozszerzenia znaczników.  
  
- Jeśli pojedyncze tokeny oddzielające zawierają znak równości, wówczas procesor XAML najpierw wywołuje konstruktora bez parametrów dla rozszerzenia znaczników. Następnie każda para nazwa = wartość jest interpretowana jako nazwa właściwości, która istnieje w rozszerzeniu znacznika i wartość, która ma zostać przypisana do tej właściwości.  
  
- Jeśli istnieje równoległy wynik między zachowaniem konstruktora i zachowaniem ustawienia właściwości w rozszerzeniu znacznika, nie ma znaczenia, którego zachowania używasz. Jest to bardziej powszechne użycie, aby użyć par*wartości* *Właściwości*`=`dla rozszerzeń znaczników, które mają więcej niż jedną właściwość settable, jeśli tylko jest to możliwe, ponieważ sprawia, że znaczniki są bardziej zamierzone i nie można przypadkowo przestawiać parametry konstruktora. (W przypadku określania par właściwość = wartość te właściwości mogą być w dowolnej kolejności). Ponadto nie ma gwarancji, że rozszerzenie znaczników dostarcza parametr konstruktora, który ustawia każdą jedną z właściwości settable. Na przykład <xref:System.Windows.Data.Binding> jest rozszerzeniem znaczników z wieloma właściwościami, które są settable przez rozszerzenie w formularzu wartości *Właściwości*`=`, ale <xref:System.Windows.Data.Binding> obsługuje tylko dwa konstruktory: Konstruktor bez parametrów i jeden ustawia ścieżkę początkową.  
  
- Nie można przesłać przecinka w postaci literału do rozszerzenia znacznika bez ucieczki.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Sekwencje unikowe i rozszerzenia znaczników  
 Obsługa atrybutów w procesorze XAML używa nawiasów klamrowych jako wskaźników sekwencji rozszerzenia znaczników. Istnieje również możliwość utworzenia literału wartości atrybutu znaku nawiasu klamrowego, w razie potrzeby, wprowadzając sekwencję ucieczki przy użyciu pustej pary nawiasów klamrowych, po której następuje literał klamrowy. [ Zobacz{} rozszerzenie sekwencji unikowej](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Zagnieżdżanie rozszerzeń znaczników w użyciu XAML  
 Zagnieżdżanie wielu rozszerzeń znaczników jest obsługiwane, a każde rozszerzenie znacznika zostanie ocenione najwcześniej. Rozważmy na przykład następujące użycie:  
  
```xaml  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 W tym użyciu `x:Static` instrukcja jest szacowana jako pierwsza i zwraca ciąg. Ten ciąg jest następnie używany jako argument dla `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozszerzenia znaczników i składnia elementu właściwości  
 Gdy jest używany jako element obiektu, który wypełnia wartość elementu właściwości, Klasa rozszerzenia znaczników jest wizualnie odróżnienia od typowego elementu obiektu, który jest używany w języku XAML. Praktyczne różnice między typowym elementem obiektu a rozszerzeniem znaczników jest to, że rozszerzenie znacznika jest oceniane do wartości wpisanej lub odroczone jako wyrażenie. W związku z tym mechanizmy dowolnego błędu typu wartości właściwości dla rozszerzenia znacznika będą różne, podobnie jak w przypadku, gdy właściwość późnego wiązania jest traktowana w innych modelach programowania. Zwykły element obiektu zostanie oceniony pod kątem dopasowania typu względem właściwości docelowej, która jest ustawiana podczas analizowania kodu XAML.  
  
 Większość rozszerzeń znaczników, gdy jest używana w składni elementu obiektu do wypełniania elementu właściwości, nie ma zawartości ani żadnej dalszej składni elementu właściwości w. W ten sposób można zamknąć tag elementu obiektu i nie udostępniać elementów podrzędnych. Za każdym razem, gdy każdy element obiektu zostanie napotkany przez procesor XAML, wywoływany jest Konstruktor dla tej klasy, który tworzy wystąpienie obiektu utworzonego na podstawie przeanalizowanego elementu. Klasa rozszerzenia znaczników nie jest różna: Jeśli chcesz, aby rozszerzenie znacznika było użyteczne w składni elementu obiektu, musisz podać konstruktora bez parametrów. Niektóre istniejące rozszerzenia znaczników mają co najmniej jedną wymaganą wartość właściwości, która musi zostać określona dla efektywnej inicjalizacji. Jeśli tak, ta wartość właściwości jest zazwyczaj podawana jako atrybut właściwości w elemencie obiektu. W przestrzeni nazw XAML (x:) [ Zostaną odnotowane strony referencyjne funkcji](../../xaml-services/xaml-namespace-x-language-features.md) języka i [rozszerzeń XAML WPF](wpf-xaml-extensions.md) , rozszerzenia znaczników, które mają wymagane właściwości (i nazwy wymaganych właściwości). Na stronach referencyjnych należy również zauważyć, że składnia elementu obiektu lub Składnia atrybutu jest niedozwolona dla określonych rozszerzeń znaczników. Istotnym przypadkiem jest [rozszerzenie znaczników x:Array](../../xaml-services/x-array-markup-extension.md), które nie obsługuje składni atrybutów, ponieważ zawartość tej tablicy musi być określona w oznakowaniu jako zawartość. Zawartość tablicy jest obsługiwana jako obiekty ogólne, dlatego nie jest możliwe ustawienie domyślnego konwertera typów dla atrybutu. Ponadto [rozszerzenie znacznika x:Array](../../xaml-services/x-array-markup-extension.md) wymaga `type` parametru.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
- [Przestrzeń nazw XAML (x:) Funkcje języka](../../xaml-services/xaml-namespace-x-language-features.md)
- [Rozszerzenia WPF XAML](wpf-xaml-extensions.md)
- [StaticResource, rozszerzenie znaczników](staticresource-markup-extension.md)
- [Rozszerzenie znaczników powiązania](binding-markup-extension.md)
- [DynamicResource, rozszerzenie znaczników](dynamicresource-markup-extension.md)
- [x:Type, rozszerzenie znaczników](../../xaml-services/x-type-markup-extension.md)
