---
title: PropertyPath — Składnia XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 17c8982a66960626a5d049fa2da90f5f2d995d14
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559771"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath — Składnia XAML

Obiekt <xref:System.Windows.PropertyPath> obsługuje złożoną składnię wbudowaną [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do ustawiania różnych właściwości, które przyjmują <xref:System.Windows.PropertyPath> typ jako ich wartość. W tym temacie opisano składnię <xref:System.Windows.PropertyPath>, która została zastosowana do składni powiązań i animacji.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Gdzie jest używany PropertyPath

<xref:System.Windows.PropertyPath> jest wspólnym obiektem, który jest używany w kilku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcjach. Mimo że wspólna <xref:System.Windows.PropertyPath> do przekazywania informacji o ścieżce właściwości, użycie dla każdego obszaru funkcji, gdzie <xref:System.Windows.PropertyPath> jest używany jako typ różny. W związku z tym bardziej praktyczne jest udokumentowanie składni dla poszczególnych funkcji.

Głównie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.PropertyPath> do opisywania ścieżek modelu obiektów do przechodzenia przez właściwości źródła danych obiektu oraz do opisywania ścieżki docelowej dla animacji ukierunkowanych.

Niektóre właściwości stylu i szablonu, takie jak <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType>, mają kwalifikowaną nazwę właściwości, która jest mniej podobna do <xref:System.Windows.PropertyPath>. Nie jest to jednak prawdziwe <xref:System.Windows.PropertyPath>; Zamiast tego jest to kwalifikowany *właściciel.* użycie formatu ciągu właściwości, które jest włączone przez procesor WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w połączeniu z konwerterem typów dla <xref:System.Windows.DependencyProperty>.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath dla obiektów w powiązaniu danych

Powiązanie danych jest funkcją [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], za pomocą której można powiązać z wartością docelową dowolnej właściwości zależności. Jednak Źródło takich powiązań danych nie musi być właściwością zależności; może to być dowolny typ właściwości, który jest rozpoznawany przez odpowiedniego dostawcę danych. Ścieżki właściwości są szczególnie używane dla <xref:System.Windows.Data.ObjectDataProvider>, które są używane do uzyskiwania źródeł powiązań z obiektów środowiska uruchomieniowego języka wspólnego (CLR) i ich właściwości.

Należy zauważyć, że powiązanie danych z XML nie używa <xref:System.Windows.PropertyPath>, ponieważ nie używa <xref:System.Windows.Data.Binding.Path%2A> w <xref:System.Windows.Data.Binding>. Zamiast tego należy użyć <xref:System.Windows.Data.Binding.XPath%2A> i określić prawidłową składnię XPath w Document Object Model XML (DOM) danych. <xref:System.Windows.Data.Binding.XPath%2A> jest również określony jako ciąg, ale nie jest tutaj udokumentowany. Zobacz [powiąż z danymi XML przy użyciu XmlDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Kluczem do interpretacji ścieżek właściwości w powiązaniu danych jest możliwość kierowania powiązania do pojedynczej wartości właściwości lub można utworzyć powiązanie z właściwościami docelowymi, które pobierają listy lub kolekcje. Jeśli kolekcje są powiązaniami, na przykład powiązanie <xref:System.Windows.Controls.ListBox>, które zostanie rozwinięte w zależności od liczby elementów danych w kolekcji, wówczas ścieżka właściwości powinna odwoływać się do obiektu kolekcji, a nie do poszczególnych elementów kolekcji. Aparat powiązań danych będzie pasował do kolekcji używanej jako źródło danych dla typu elementu docelowego powiązania automatycznie, co spowodowało zachowanie, takie jak wypełnianie <xref:System.Windows.Controls.ListBox> z tablicą Items.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Pojedyncza właściwość w obiekcie bezpośrednim jako kontekst danych

```xml
<Binding Path="propertyName" .../>
```

Funkcja *PropertyName* musi zostać rozpoznana jako nazwa właściwości, która znajduje się w bieżącej <xref:System.Windows.FrameworkElement.DataContext%2A> dla <xref:System.Windows.Data.Binding.Path%2A> użycia. Jeśli powiązanie aktualizuje źródło, ta właściwość musi mieć wartość odczyt/zapis, a obiekt źródłowy musi być modyfikowalny.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Pojedynczy indeksator na obiekcie bezpośrednim jako kontekst danych

```xml
<Binding Path="[key]" .../>
```

`key` musi być albo indeksowanym indeksem lub tabelą skrótów, albo indeksem liczb całkowitych tablicy. Ponadto wartość klucza musi być typem, który jest bezpośrednio powiązany z właściwością, w której jest stosowany. Na przykład można użyć tabeli skrótów zawierającej klucze ciągów i wartości ciągu, aby powiązać ją z tekstem dla <xref:System.Windows.Controls.TextBox>. Lub, jeśli klucz wskazuje kolekcję lub indeks, można użyć tej składni do powiązania z właściwością kolekcji docelowej. W przeciwnym razie należy odwołać się do określonej właściwości za pomocą składni, takiej jak `<Binding Path="[key].propertyName" .../>`.

W razie potrzeby można określić typ indeksu. Aby uzyskać szczegółowe informacje na temat tego aspektu ścieżki właściwości indeksowanej, zobacz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Wiele właściwości (Określanie wartości docelowej właściwości pośredniej)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName` musi być rozpoznawana jako nazwa właściwości, która jest bieżącą <xref:System.Windows.FrameworkElement.DataContext%2A>. Właściwości ścieżki `propertyName` i `propertyName2` mogą być wszelkimi właściwościami, które istnieją w relacji, gdzie `propertyName2` jest właściwością, która istnieje w typie, który jest wartością `propertyName`.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Pojedyncza właściwość, dołączona lub w inny sposób kwalifikowana dla typu

```xml
<object property="(ownerType.propertyName)" .../>
```

Nawiasy wskazują, że ta właściwość w <xref:System.Windows.PropertyPath> powinna być skonstruowana przy użyciu częściowej kwalifikacji. Może użyć przestrzeni nazw XML, aby znaleźć typ z odpowiednim mapowaniem. `ownerType` wyszukuje typy, do których ma dostęp procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], za pomocą deklaracji <xref:System.Windows.Markup.XmlnsDefinitionAttribute> w każdym zestawie. Większość aplikacji ma domyślną przestrzeń nazw XML zamapowana na przestrzeń nazw `http://schemas.microsoft.com/winfx/2006/xaml/presentation`, więc prefiks jest zwykle niezbędny tylko w przypadku typów niestandardowych lub typów poza tą przestrzenią nazw.  `propertyName` musi być rozpoznawana jako nazwa właściwości istniejącej w `ownerType`. Ta składnia jest zwykle używana w jednym z następujących przypadków:

- Ścieżka jest określona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], która znajduje się w stylu lub szablonie, który nie ma określonego typu docelowego. Kwalifikowane użycie zwykle nie jest prawidłowe w przypadku przypadków innych niż to, ponieważ w przypadku braku szablonów, właściwość istnieje w wystąpieniu, a nie w typie.

- Właściwość jest dołączoną właściwością.

- Tworzysz powiązanie z właściwością statyczną.

Aby można było użyć jako elementu docelowego scenorysu, właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Przechodzenie źródłowe (powiązanie z hierarchiami kolekcji)

```xml
<object Path="propertyName/propertyNameX" .../>
```

Składnia/w tej składni jest używana do nawigowania w obrębie hierarchicznego obiektu źródła danych, a wiele kroków do hierarchii z kolejnymi/znakami są obsługiwane. Źródłowe konta przechodzenia dla bieżącego położenia wskaźnika rekordu, które są określane przez synchronizację danych z interfejsem użytkownika widoku. Aby uzyskać szczegółowe informacje na temat powiązania z obiektami hierarchicznych źródeł danych i koncepcji bieżącego wskaźnika rekordu w powiązaniu danych, zobacz [Korzystanie ze wzorca wzorzec-szczegóły z danymi hierarchicznymi lub z](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) [omówieniem powiązań danych](../../../desktop-wpf/data/data-binding-overview.md).

> [!NOTE]
> Niemniej ta składnia przypomina wyrażenie XPath. Prawdziwe wyrażenie XPath dla powiązania ze źródłem danych XML nie jest używane jako wartość <xref:System.Windows.Data.Binding.Path%2A> i powinno być używane dla wzajemnie wykluczających się właściwości <xref:System.Windows.Data.Binding.XPath%2A>.

### <a name="collection-views"></a>Widoki kolekcji

Aby odwołać się do widoku nazwanego kolekcji, należy prefiksować nazwę widoku kolekcji ze znakiem skrótu (`#`).

### <a name="current-record-pointer"></a>Bieżący wskaźnik rekordu

Aby odwołać się do bieżącego wskaźnika rekordu dla tego widoku kolekcji lub scenariusza powiązania danych głównych, należy uruchomić ciąg ścieżki z ukośnikiem (`/`). Wszystkie ścieżki poprzedzające ukośnik są przenoszone od bieżącego wskaźnika rekordu.

### <a name="multiple-indexers"></a>Wiele indeksatorów

```xaml
<object Path="[index1,index2...]" .../>
```

lub

```xaml
<object Path="propertyName[index,index2...]" .../>
```

Jeśli dany obiekt obsługuje wiele indeksatorów, te indeksatory mogą być określone w kolejności podobnej do składni odwołującej się do tablicy. Dany obiekt może być bieżącym kontekstem lub wartością właściwości, która zawiera obiekt z wieloma indeksami.

Domyślnie wartości indeksatora są wpisywane przy użyciu cech obiektu bazowego. W razie potrzeby można określić typ indeksu. Aby uzyskać szczegółowe informacje na temat wpisywania indeksatorów, zobacz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Mieszanie składni

Każda składnia pokazana powyżej może zostać przeplatana. Na przykład, poniżej można utworzyć ścieżkę właściwości do koloru na określonej x, y właściwości `ColorGrid`, która zawiera tablicę siatki pikseli obiektów <xref:System.Windows.Media.SolidColorBrush>:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Ucieczki ciągów ścieżki właściwości

W przypadku niektórych obiektów firmy można napotkać przypadek, w którym ciąg ścieżki właściwości wymaga sekwencji ucieczki w celu poprawnego przeanalizowania. Konieczność ucieczki powinna być rzadki, ponieważ wiele z tych znaków ma podobne problemy z interakcją nazewnictwa w językach, które zwykle są używane do definiowania obiektu biznesowego.

- Wewnątrz indeksatorów ([]), znak karetki (^) wyprowadza następny znak.

- Należy wyjść z określonych znaków (przy użyciu jednostek XML), które są specyficzne dla definicji języka XML. Użyj `&` do ucieczki znaku "&". Użyj `>` do ucieczki znacznika końcowego ">".

- Należy wypróbować (za pomocą znaków ukośnika odwrotnego `\`), które są specyficzne dla zachowań analizatora XAML WPF do przetwarzania rozszerzenia znaczników.

  - Ukośnik odwrotny (`\`) jest samym znakiem ucieczki.

  - Znak równości (`=`) oddziela nazwę właściwości od wartości właściwości.

  - Przecinek (`,`) oddziela właściwości.

  - Prawy nawias klamrowy (`}`) jest końcem rozszerzenia znacznika.

> [!NOTE]
> Technicznie te wyjścia dla ścieżki właściwości scenorysu również są zwykle przenoszone przez modele obiektów dla istniejących obiektów WPF, a ucieczki nie powinny być potrzebne.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath dla celów animacji

Właściwość Target animacji musi być właściwością zależności, która przyjmuje <xref:System.Windows.Freezable> lub typ pierwotny. Jednak właściwość target typu i ostateczna Właściwość animowana może istnieć w różnych obiektach. W przypadku animacji ścieżka właściwości jest używana do definiowania połączenia między właściwością nazwanego obiektu docelowego animacji a zamierzoną właściwością animacji docelowej, przez przechodzenie między relacjami obiektu i właściwości w wartościach właściwości.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Ogólne zagadnienia dotyczące właściwości obiektów dla animacji

Aby uzyskać więcej informacji na temat ogólnych pojęć dotyczących animacji, zobacz Omówienie [scenorysów](../graphics-multimedia/storyboards-overview.md) i Omówienie [animacji](../graphics-multimedia/animation-overview.md).

Typ wartości lub animowana właściwość musi być typem <xref:System.Windows.Freezable> lub elementem pierwotnym. Właściwość rozpoczynająca ścieżkę musi być rozpoznawana jako nazwa właściwości zależności, która istnieje w określonym typie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>.

Aby można było obsłużyć klonowanie na potrzeby animowania <xref:System.Windows.Freezable>, która jest już zamrożona, obiekt określony przez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> musi być klasą pochodną <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement>.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Pojedyncza właściwość w obiekcie docelowym

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName` musi rozpoznać jako nazwę właściwości zależności, która istnieje w określonym typie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Określanie wartości docelowej właściwości pośredniej

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName` musi być właściwością, która jest <xref:System.Windows.Freezable> typem wartości lub elementem pierwotnym, który istnieje w określonym typie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>.

`propertyName2` musi być nazwą właściwości zależności, która istnieje w obiekcie, który jest wartością `propertyName`. Innymi słowy, `propertyName2` musi istnieć jako właściwość zależności w typie, który jest <xref:System.Windows.DependencyProperty.PropertyType%2A>`propertyName`.

Pośredni cel animacji jest konieczny ze względu na zastosowane style i szablony. Aby można było utworzyć animację, potrzebujesz <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> w obiekcie docelowym, a nazwa jest określana przez [x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) lub <xref:System.Windows.FrameworkElement.Name%2A>. Chociaż elementy szablonu i stylu mogą także mieć nazwy, te nazwy są prawidłowe tylko w namescope stylu i szablonu. (Jeśli szablony i style współużytkują Zakresy nazw WPF z znacznikiem aplikacji, nazwy nie mogły być unikatowe. Style i szablony są dosłownie współużytkowane przez wystąpienia i perpetuate zduplikowane nazwy.) W takim przypadku, jeśli poszczególne właściwości elementu, który można animować, pochodzą z stylu lub szablonu, należy rozpocząć od wystąpienia nazwanego elementu, który nie jest z szablonu stylu, a następnie skierować do drzewa wizualnego stylu lub szablonu, aby dotrzeć do właściwości chcesz animować.

Na przykład właściwość <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel> jest kompletną <xref:System.Windows.Media.Brush> (w rzeczywistości <xref:System.Windows.Media.SolidColorBrush>), która pochodzi z szablonu motywu. Aby animować <xref:System.Windows.Media.Brush> w całości, należy mieć BrushAnimation (prawdopodobnie jeden dla każdego typu <xref:System.Windows.Media.Brush>) i nie istnieje taki typ. Aby animować pędzla, należy zamiast tego animować właściwości określonego typu <xref:System.Windows.Media.Brush>. Musisz uzyskać od <xref:System.Windows.Media.SolidColorBrush> do <xref:System.Windows.Media.SolidColorBrush.Color%2A>, aby zastosować <xref:System.Windows.Media.Animation.ColorAnimation> tam. Ścieżka właściwości dla tego przykładu byłaby `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Dołączone właściwości

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Nawiasy wskazują, że ta właściwość w <xref:System.Windows.PropertyPath> powinna być skonstruowana przy użyciu częściowej kwalifikacji. Można użyć przestrzeni nazw XML, aby znaleźć typ. `ownerType` wyszukuje typy, do których ma dostęp procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], za pomocą deklaracji <xref:System.Windows.Markup.XmlnsDefinitionAttribute> w każdym zestawie. Większość aplikacji ma domyślną przestrzeń nazw XML zamapowana na przestrzeń nazw `http://schemas.microsoft.com/winfx/2006/xaml/presentation`, więc prefiks jest zwykle niezbędny tylko w przypadku typów niestandardowych lub typów poza tą przestrzenią nazw. `propertyName` musi być rozpoznawana jako nazwa właściwości istniejącej w `ownerType`. Właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>. (Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone właściwości są implementowane jako właściwości zależności, więc ten problem dotyczy tylko niestandardowych dołączanych właściwości.)

<a name="indexanim"></a>

### <a name="indexers"></a>Indeksatory

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

Większość właściwości zależności lub typów <xref:System.Windows.Freezable> nie obsługuje indeksatora. W związku z tym jedynym sposobem użycia indeksatora w ścieżce animacji jest pośrednia pozycja między właściwością, która uruchamia łańcuch w nazwanym miejscu docelowym i Właściwość animowane. W podanej składni, która jest `propertyName2`. Na przykład użycie indeksatora może być konieczne, jeśli właściwość pośrednia jest kolekcją, taką jak <xref:System.Windows.Media.TransformGroup>, w ścieżce właściwości, takiej jak `RenderTransform.Children[1].Angle`.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath w kodzie

Użycie kodu dla <xref:System.Windows.PropertyPath>, w tym sposób konstruowania <xref:System.Windows.PropertyPath>, jest udokumentowane w temacie referencyjnym dla <xref:System.Windows.PropertyPath>.

Ogólnie rzecz biorąc, <xref:System.Windows.PropertyPath> zaprojektowano tak, aby korzystały z dwóch różnych konstruktorów, jednej do użycia powiązań i najprostszych użycia animacji oraz jednego dla złożonych zastosowań animacji. Użyj podpisu <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>, aby powiązać użycie, gdzie obiekt jest ciągiem. Użyj podpisu <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> dla ścieżek animacji jednoetapowych, gdzie obiekt jest <xref:System.Windows.DependencyProperty>. Użyj podpisu <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> w przypadku złożonych animacji. Ten drugi Konstruktor używa ciągu tokenu dla pierwszego parametru i tablicy obiektów, które wypełniają pozycje w ciągu tokenu, aby zdefiniować relację ścieżki właściwości.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.PropertyPath>
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Scenorysy — przegląd](../graphics-multimedia/storyboards-overview.md)
