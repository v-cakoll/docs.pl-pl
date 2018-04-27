---
title: Rozszerzenia znacznikowania i WPF XAML
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf1d7fda58c3bca0f9d76c3c4d3b8d22545a9912
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="markup-extensions-and-wpf-xaml"></a>Rozszerzenia znacznikowania i WPF XAML
W tym temacie przedstawiono koncepcję rozszerzenia znaczników dla XAML, łącznie z ich składni reguł, cel i model obiektów klasy źródłowej je. Rozszerzenia znaczników są funkcją ogólne języka XAML i stosowania usługi XAML .NET. W tym temacie szczegółowo w szczególności rozszerzenia znaczników do użycia w WPF XAML.  
  
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>Procesory XAML i rozszerzenia znaczników  
 Ogólnie rzecz biorąc analizatora składni języka XAML albo można zinterpretować wartości atrybutu jako ciąg literału, które mogą być konwertowane do typu pierwotnego lub przekonwertować go do obiektu w sposób. Takie środki jest odwołując konwertera typów; jest to opisane w temacie [TypeConverters i języka XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md). Istnieją jednak scenariuszy, w którym wymagany jest inaczej. Na przykład procesora XAML może się instrukcja wartość atrybutu nie powinny powodować w nowym obiekcie na grafie obiektu. Zamiast tego atrybutu powinno spowodować wykresu obiektu, który odwołuje się do obiektu już utworzone w innej części wykresu lub statycznego obiektu. Inny scenariusz polega na tym, że procesor XAML mogą być zalecane jest używanie składnię, która zawiera argumenty z systemem innym niż domyślny konstruktor obiektu. Są to typy scenariuszy, w którym rozszerzenie znaczników można podać rozwiązania.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>Składnia rozszerzenia znaczników podstawowe  
 Rozszerzenie znaczników można zaimplementować o podanie wartości właściwości użycie atrybutu, właściwości użycie elementu właściwości lub oba.  
  
 W przypadku podania wartości atrybutu składni, która odróżnia sekwencję rozszerzenia znaczników procesor XAML jest obecność otwierający i zamykający nawiasy klamrowe ({i}). Typ rozszerzenia znacznika następnie jest identyfikowany przez token ciągu bezpośrednio po otwierającym nawiasie klamrowym.  
  
 Używana w składni elementu właściwości, rozszerzenie znaczników wizualnie jest taki sam jak inny element używane w celu dostarczania wartości właściwości elementu: deklarację elementu XAML, który odwołuje się do klasa rozszerzenia struktury znaczników jako elementu ujętą w nawiasy klamrowe nawiasy (<> ).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozszerzenia znaczników zdefiniowane XAML  
 Istnieje kilka rozszerzeń znaczników, które nie są specyficzne dla wdrożenia WPF XAML, ale zamiast tego są implementacje funkcje wewnętrzne lub funkcje XAML jako język. Te rozszerzenia znaczników są implementowane w zestawie System.Xaml jako część ogólne usługi .NET Framework XAML i znajdują się w przestrzeni nazw XAML języka XAML. Pod względem wspólnego użycia znaczników, są zazwyczaj do zidentyfikowania przez te rozszerzenia znaczników `x:` prefiks w użycia. <xref:System.Windows.Markup.MarkupExtension> Klasy podstawowej (też definiowany w System.Xaml) zawiera wzorzec, który ma być używany przez wszystkie rozszerzenia znaczników aby być obsługiwana w przypadku czytników XAML i moduły zapisujące XAML, w tym w WPF XAML.  
  
-   `x:Type` dostarcza <xref:System.Type> obiektu dla typu nazwanego. Tej funkcji jest najczęściej używane style i szablony. Aby uzyskać więcej informacji, zobacz [x: Type — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
-   `x:Static` Tworzy wartości statyczne. Wartości pochodzą z jednostek kodu typ wartości, które nie są bezpośrednio typ wartości właściwości docelowych, ale może przyjąć typu. Aby uzyskać więcej informacji, zobacz [x: Static — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
-   `x:Null` Określa `null` jako wartość właściwości i mogą być używane dla atrybutów lub wartości elementów właściwości. Aby uzyskać więcej informacji, zobacz [x: Null — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
-   `x:Array` zapewnia obsługę tworzenia ogólne tablic w składni języka XAML w przypadkach, gdy obsługa kolekcji zapewniana przez WPF podstawowych elementów i modele kontroli celowo nie jest używana. Aby uzyskać więcej informacji, zobacz [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  `x:` Prefiks jest używany do typowych mapowania przestrzeni nazw XAML funkcji XAML language wewnętrznych, na w elemencie głównym pliku XAML lub produkcji. Na przykład szablony programu Visual Studio dla aplikacji WPF zainicjować pliku XAML, za pomocą tej `x:` mapowania. Można wybrać inny token w własne mapowania przestrzeni nazw XAML, ale w tej dokumentacji przyjmie wartość domyślna `x:` mapowania jako sposób identyfikacji tych jednostek, które należą do określonych przestrzeni nazw XAML dla języka XAML, a nie WPF domyślnej przestrzeni nazw lub innych przestrzeniach nazw XAML nie dotyczą określonej platformy.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>Rozszerzenia znaczników specyficzne dla WPF  
 Najczęstsze rozszerzenia znacznika używany w programowaniu WPF to takie, które obsługują odwołania do zasobów (`StaticResource` i `DynamicResource`) oraz te, które obsługuje powiązanie danych (`Binding`).  
  
-   `StaticResource` dostarcza wartość dla właściwości, zastępując wartości zasobu już zdefiniowane. A `StaticResource` oceny staje się ostatecznie w czasie ładowania XAML i nie ma dostępu do obiektu wykresu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [StaticResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   `DynamicResource` udostępnia wartość właściwości przez odkładanie tej wartości jako odwołanie do zasobu czasu wykonywania. Odwołanie do zasobu dynamicznego wymusza nowego wyszukiwania zawsze czy taki zasób jest dostępny i ma dostęp do obiektu wykresu w czasie wykonywania. Aby uzyskać dostęp, `DynamicResource` koncepcja jest obsługiwana przez właściwości zależności w systemie właściwości WPF i oceniane wyrażenia. W związku z tym można używać tylko `DynamicResource` dla docelowej właściwości zależności. Aby uzyskać więcej informacji, zobacz [DynamicResource — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
-   `Binding` zawiera wartość właściwości, za pomocą kontekstu danych, która ma zastosowanie do obiektu nadrzędnego w czasie wykonywania powiązany z danymi. Tego rozszerzenia znacznika jest dość złożone, ponieważ dzięki składnię znacznej wbudowanego Określanie powiązania danych. Aby uzyskać więcej informacji, zobacz [powiązanie — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
-   `RelativeSource` zawiera informacje o źródle <xref:System.Windows.Data.Binding> który Przejdź kilka możliwych relacji drzewa obiektów czasu wykonywania. Zapewnia to specjalne sourcing dla powiązań, które są w szablonach wielokrotnego użytku lub tworzony kodu bez pełnej znajomości otaczającego drzewa obiektów. Aby uzyskać więcej informacji, zobacz [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md).  
  
-   `TemplateBinding` Umożliwia szablon formantu użyć wartości dla właściwości opartego na szablonie, które pochodzą z właściwości zdefiniowane przez model obiektu klasy, który będzie używany przez szablon. Innymi słowy właściwości w definicji szablonu mogą uzyskiwać dostęp do kontekstu, który istnieje tylko po zastosowaniu tego szablonu. Aby uzyskać więcej informacji, zobacz [rozszerzenie znacznika TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md). Aby uzyskać więcej informacji na praktyczne wykorzystanie `TemplateBinding`, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
-   `ColorConvertedBitmap` obsługuje stosunkowo zaawansowanym scenariuszu przetwarzania obrazów. Aby uzyskać więcej informacji, zobacz [ColorConvertedBitmap — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md).  
  
-   `ComponentResourceKey` i `ThemeDictionary` obsługują aspekty wyszukiwania zasobów, szczególnie w przypadku zasobów i motywów, które są dostarczane z Kontrolki niestandardowe. Aby uzyskać więcej informacji, zobacz [ComponentResourceKey — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md), [ThemeDictionary — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md), lub [informacje o formancie tworzenia](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>* Rozszerzenie klasy  
 Dla języka XAML ogólne i WPF rozszerzenia znaczników, zachowania poszczególnych rozszerzeń znaczników jest identyfikowany procesor XAML za pośrednictwem `*Extension` klasą pochodzącą z <xref:System.Windows.Markup.MarkupExtension>i udostępnia implementację elementu <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> Metoda. Tej metody na każde rozszerzenie zawiera obiekt, który jest zwracany, gdy rozszerzenie znaczników jest obliczane. Zwrócony obiekt jest zwykle obliczane oparte na różnych tokeny ciągów, które są przekazywane do rozszerzenia znacznika.  
  
 Na przykład <xref:System.Windows.StaticResourceExtension> klasa udostępnia powierzchni wykonania wyszukiwania rzeczywistych zasobów, aby jego <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> implementacja zwraca obiekt, którego zażądano, przy użyciu danych wejściowych tej konkretnej implementacji jest ciąg, który służy do Wyszukiwanie zasobów przez jego `x:Key`. Większość tych szczegółów implementacji jest bez znaczenia, jeśli używane są istniejące rozszerzenie znacznika.  
  
 Niektóre rozszerzenia znaczników nie należy używać tokenu argumenty typu string. Jest to ponieważ zwracają wartość statyczny lub spójne lub kontekst dla wartości, które powinny być zwracane jest dostępna za pośrednictwem usług przekazywane `serviceProvider` parametru.  
  
 `*Extension` Jest wzorzec nazewnictwa dla wygody i spójności. Nie jest konieczne w kolejności dla procesora XAML do identyfikowania tej klasy, jak pomocy technicznej dla rozszerzenia znacznika. Tak długo, jak baza kodu zawiera System.Xaml i korzysta z usług .NET Framework XAML implementacji, wszystko jest rozpoznana jako rozszerzenie znaczników w XAML pochodzi od <xref:System.Windows.Markup.MarkupExtension> i obsługuje składni konstrukcji. Włączenie rozszerzenia klasy znaczników, które nie wykonuj definiuje WPF `*Extension` nazewnictwa wzorzec, na przykład <xref:System.Windows.Data.Binding>. Zazwyczaj przyczyną jest że klasa obsługuje scenariusze poza czysty znaczników rozszerzenia obsługi. W przypadku liczby <xref:System.Windows.Data.Binding>, że klasa obsługuje środowiska wykonawczego dostęp do metody i właściwości obiektu w scenariuszach, które nie mają nic wspólnego z XAML.  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>Rozszerzenie klasy interpretacji inicjowania tekstu  
 Tokeny ciąg następujące rozszerzenie znaczników w nazwie i nadal w nawiasy klamrowe są interpretowane przez procesor XAML w jednym z następujących sposobów:  
  
-   Przecinek zawsze stanowi separatora lub ogranicznik poszczególnych tokenów.  
  
-   Jeśli pojedynczych rozdzielonych tokenów nie zawierają jakiekolwiek oznaki equals, każdy token jest traktowany jako argument konstruktora. Każdy parametr konstruktora muszą zostać podane jako typ oczekiwany przez tego podpisu, a w prawidłowej kolejności oczekiwany przez ten podpis.  
  
    > [!NOTE]
    >  Procesor XAML musi wywołać konstruktora, który odpowiada liczba argumentów określona liczba par. Z tego powodu w przypadku wdrażania rozszerzeń znaczników niestandardowych nie udostępniają wiele parametrów o tej samej liczby argumentów. To zachowanie występujące w sposób zachowania procesora XAML, jeśli istnieje więcej niż jedną ścieżkę konstruktora rozszerzenia znaczników z tej samej liczby parametrów nie jest zdefiniowany, ale należy przewidzieć procesora XAML będzie mógł zgłosić wyjątek, użycia, jeśli ta sytuacja występuje w Definicje typu rozszerzenia znaczników.  
  
-   Gdy osoba rozdzielone tokeny zawierają znaki równości, a następnie procesora XAML najpierw wywołuje konstruktor domyślny dla rozszerzenia znacznika. Następnie każda para nazwa = wartość jest interpretowana jako nazwy właściwości, która istnieje na rozszerzenia znaczników i wartość do przypisania do tej właściwości.  
  
-   W przypadku równoległego wynik między zachowanie Konstruktor i ustawienia zachowania w rozszerzeniu znaczników właściwości, nie ma znaczenia, jakie zachowanie, należy użyć. Jest bardziej popularne użycia do użycia *właściwości*`=`*wartość* pary dla rozszerzenia znaczników, które mają więcej niż jedną właściwość można ustawić, jeśli tylko, ponieważ Twoje znaczników ułatwia więcej zamierzone i jesteś zmniejszyć prawdopodobieństwo przypadkowego Przestaw parametrami konstruktora. (Po określeniu właściwości = pary wartości tych właściwości można w dowolnej kolejności.) Ponadto nie ma żadnej gwarancji, że rozszerzenie znaczników dostarcza parametru konstruktora, który ustawia każdego z jego właściwości można ustawić jeden. Na przykład <xref:System.Windows.Data.Binding> jest rozszerzeniem znacznika o wiele właściwości, które są można ustawić za pomocą rozszerzenia w *właściwości*`=`*wartość* formularza, ale <xref:System.Windows.Data.Binding> obsługuje tylko dwa Konstruktory: konstruktora domyślnego i jedną, która ustawia ścieżkę początkowej.  
  
-   Nie można przekazać literału przecinkami do rozszerzenia znacznika bez escapement.  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>Sekwencje unikowe i rozszerzeń znaczników  
 Atrybut Obsługa w XAML procesor używa nawiasów klamrowych jako wskaźników sekwencji rozszerzenia znaczników. Istnieje również możliwość utworzenia literału nawias klamrowy znak wartości atrybutu w razie potrzeby, wprowadzając — sekwencja specjalna przy użyciu pary pusty nawias klamrowy następuje literału nawias klamrowy. Zobacz [ {} sekwencji — rozszerzenie znaczników specjalnej](../../xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>Rozszerzenia znaczników w XAML użycia zagnieżdżania  
 Zagnieżdżenia wiele rozszerzeń znaczników jest obsługiwany, a każde rozszerzenie znacznika zostaną ocenione najgłębszym najpierw. Na przykład Rozważ użycie następujących:  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 W ten sposób użycia `x:Static` instrukcji jest szacowana jako pierwsza i zwraca wartość typu ciąg. Czy ciąg jest następnie używany jako argument dla `DynamicResource`.  
  
## <a name="markup-extensions-and-property-element-syntax"></a>Rozszerzenia znaczników i składni elementu właściwości  
 Gdy jest używany jako elementu obiektu, który wypełnia właściwości wartość elementu, klasa rozszerzenia struktury znaczników jest wizualnie można odróżnić od elementu typowe kopii typu obiektu, który może być używana w języku XAML. Praktyczne różnica między element typowego obiektu i rozszerzenia znaczników jest czy rozszerzenie znaczników jest obliczane do wartości typu lub odroczone jako wyrażenia. W związku z tym mechanizmów błędy możliwe typ wartości właściwości dla rozszerzenia znacznika będzie inny, podobnie jak właściwość późnym wiązaniem jest traktowany w innych modeli programowania. Element zwykłej obiekt ma zostać obliczone dla typu metody match na właściwość target, który jest ustawienie, gdy zostanie przeanalizowany XAML.  
  
 Większość rozszerzenia znaczników, gdy są używane w składni elementu obiektu do wypełniania elementu właściwości nie będzie zawierało składni elementu zawartości i żadnych dodatkowych właściwości w ciągu. W związku z tym spowoduje zamknięcie tagu elementu obiektu i podaj nie podrzędnych elementów. Napotkaniu dowolny element obiektu przez procesor XAML, konstruktora dla tej klasy, nosi nazwę, która tworzy wystąpienie obiektu utworzone na podstawie przeanalizowany element. Nie różni się klasa rozszerzenia struktury znaczników: Jeśli chcesz, aby rozszerzenie znacznika może być używany w składni elementu obiektu, należy podać konstruktora domyślnego. Niektóre istniejące rozszerzenia znaczników ma co najmniej jedną wartość wymaganej właściwości, która musi być określona dla inicjowania skuteczne. Jeśli tak, wartości tej właściwości jest zazwyczaj podawana jako atrybut właściwości w elemencie obiektu. W [Namespace XAML (x:) Funkcje języka](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md) i [WPF XAML rozszerzenia](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md) odwołania stron, znaczników rozszerzeń, które mają wymagane właściwości (i nazwy właściwości wymagane) zostanie zapisany. Strony podręcznika również zauważyć, jeśli obiekt składni elementu lub atrybutu składni jest niedozwolone dla rozszerzenia znaczników określonego. Godne wielkość liter jest [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md), który nie obsługuje Składnia atrybutu, ponieważ zawartości tablicy muszą być określone w znakowanie jako zawartość. Zawartość tablicy są obsługiwane jako ogólne obiekty, dlatego żaden konwerter typów domyślnego atrybutu jest możliwe. Ponadto [x: Array — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-array-markup-extension.md) wymaga `type` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Przestrzeń nazw XAML (x:) — funkcje językowe](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [Rozszerzenia WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [StaticResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [Rozszerzenie znaczników powiązania](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)  
 [DynamicResource, rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)  
 [x:Type, rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
