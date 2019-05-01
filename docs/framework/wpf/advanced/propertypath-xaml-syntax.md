---
title: PropertyPath — Składnia XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 7db435e45ddc55346af5ea5fdbcce611173c774b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053538"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath — Składnia XAML
<xref:System.Windows.PropertyPath> Obiekt obsługuje złożone wbudowane [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnię ustawiania różne właściwości, które przyjmują <xref:System.Windows.PropertyPath> typ jako ich wartość. Ten temat dokumenty <xref:System.Windows.PropertyPath> składni, jakie mają zastosowanie do powiązania i animacji składni.  

<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>Gdy jest używany atrybut PropertyPath  
 <xref:System.Windows.PropertyPath> jest wspólne obiekt, który jest używany w kilku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcji. Pomimo przy użyciu wspólnej <xref:System.Windows.PropertyPath> w celu przekazania informacji o ścieżce właściwości, metody użycia dla każdego obszaru funkcji gdzie <xref:System.Windows.PropertyPath> jest używany jako typ różnią się. Dlatego jest praktyczniejsze w dokumencie składni na podstawie poszczególnych funkcji.  
  
 Przede wszystkim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.PropertyPath> do opisania ścieżki modelu obiektów do przechodzenia przez właściwości obiektu źródła danych i do opisania ścieżka docelowa dla docelowych animacji.  
  
 Niektóre właściwości, stylu i szablonu, takie jak <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> zająć nazwy kwalifikowanej właściwości, która przypomina pozornie <xref:System.Windows.PropertyPath>. Ale nie jest to wartość PRAWDA <xref:System.Windows.PropertyPath>; zamiast tego jest kwalifikowana *owner.property* ciąg formatu użycia, która została włączona przez WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora w połączeniu z konwerter typów dla <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>Atrybut PropertyPath dla obiektów w powiązaniu danych  
 Wiązanie danych jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji zgodnie z którymi możesz powiązać docelowa wartość wskaźnika dowolną właściwość zależności. Jednak źródło powiązania danych nie musi być właściwość zależności; może być dowolnego typu właściwości, który jest rozpoznawany przez dostawcę odpowiednich danych. Ścieżki właściwości szczególnie są używane do <xref:System.Windows.Data.ObjectDataProvider>, używanej do uzyskiwania źródeł powiązania z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów i ich właściwości.  
  
 Należy pamiętać, że powiązania danych [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nie używa <xref:System.Windows.PropertyPath>, ponieważ nie używa <xref:System.Windows.Data.Binding.Path%2A> w <xref:System.Windows.Data.Binding>. Zamiast tego należy użyć <xref:System.Windows.Data.Binding.XPath%2A> i określ prawidłową składnię języka XPath do [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] danych. <xref:System.Windows.Data.Binding.XPath%2A> jest również określona jako ciąg znaków, ale nie jest opisane w tym miejscu; zobacz [powiązania danych XML przy użyciu XMLDataProvider i zapytań XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Kluczem do zrozumienia ścieżki właściwości w powiązaniu danych to, czy możliwe jest określanie powiązania wartości pojedynczej właściwości lub zamiast tego można powiązać właściwości obiektu docelowego, przyjmujące list lub kolekcji. Jeśli dokonywane jest wiązanie kolekcji, na przykład powiązanie <xref:System.Windows.Controls.ListBox> rozwinie, w zależności od tego, ile elementów danych znajdują się w kolekcji, a następnie ścieżki właściwości powinny odwoływać się obiekt kolekcji, nie do poszczególnych kolekcji elementów. Aparat powiązanie danych będzie odpowiadał kolekcji używany jako źródło danych na typ elementu docelowego powiązania automatycznie, co spowoduje zachowanie, na przykład podczas wypełniania <xref:System.Windows.Controls.ListBox> z elementów tablicy.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Jedną właściwość do bezpośredniego obiektu jako kontekst danych  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* musi rozpoznać nazwę właściwości, która jest w bieżącym <xref:System.Windows.FrameworkElement.DataContext%2A> dla <xref:System.Windows.Data.Binding.Path%2A> użycia. Jeśli Twoje powiązanie aktualizuje źródło, tej właściwości musi być odczytu/zapisu, a obiekt źródłowy musi być modyfikowalna.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Indeksator jednego natychmiastowego obiektu jako kontekst danych  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` musi być wpisane indeksu do słownika lub Tabela skrótów lub liczba całkowita indeksu tablicy. Ponadto wartość klucza musi być typu, który jest bezpośrednio możliwej do wiązania dla właściwości, której jest stosowany. Na przykład tabelę mieszania, który zawiera ciąg kluczy i wartości ciągu można w ten sposób można powiązać Text dla <xref:System.Windows.Controls.TextBox>. Lub, jeśli klucz wskazuje kolekcję lub podindeks, można użyć tej składni można powiązać właściwości kolekcji docelowej. W przeciwnym razie należy odwoływać się do konkretnej właściwości, za pomocą składni takich jak `<Binding Path="[key].propertyName" .../>`.  
  
 Jeśli to konieczne, można określić typ indeksu. Aby uzyskać szczegółowe informacje na ten aspekt ścieżką indeksowanej właściwości, zobacz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Wiele właściwości (właściwość pośrednich określania wartości docelowej.)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` należy rozwiązać nazwę właściwości, która jest bieżącą <xref:System.Windows.FrameworkElement.DataContext%2A>. Właściwości ścieżki `propertyName` i `propertyName2` może mieć żadnych właściwości, które istnieją w relacji, gdzie `propertyName2` jest właściwością, która istnieje na typ, który jest wartością `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Jedną właściwość dołączone lub w przeciwnym razie kwalifikowaną typu  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Nawiasy wskazują, że tę właściwość w <xref:System.Windows.PropertyPath> powinien być skonstruowany przy użyciu częściowe kwalifikacji. Można odnaleźć typu o odpowiednie mapowanie może używać przestrzeni nazw XML. `ownerType` Wyszukiwania typów, które [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor ma dostęp, za pomocą <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklaracji w każdym zestawie. Większość aplikacji ma domyślny obszar nazw XML, mapowane na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw, dzięki czemu prefiks, który zazwyczaj jest tylko niezbędne dla niestandardowych typów lub typy w przeciwnym razie spoza tej przestrzeni nazw.  `propertyName` należy rozwiązać nazwę właściwości istniejących `ownerType`. Ta składnia jest zazwyczaj używana do jednej z następujących przypadkach:  
  
- Ścieżka nie jest określona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w stylu lub szablonu, który ma określony typ docelowy. Użycie kwalifikowanej zwykle nie jest prawidłowy w przypadku innych niż ten, ponieważ w przypadkach-style, nieszablonowe właściwość nie istnieje w wystąpieniu, nie typu.  
  
- Właściwość jest dołączona właściwość.  
  
- Dokonywane jest wiązanie właściwości statycznej.  
  
 Do użytku jako docelowego scenorysu, właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Przechodzenie źródła (powiązanie z hierarchii kolekcji)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / W tym składnia jest używana do nawigacji w ramach obiektu źródłowego danych hierarchicznych i wiele kroków do hierarchii z kolejnych / znaki są obsługiwane. Konta przechodzenie źródłowej bieżącą pozycję wskaźnika rekordu jest określany przez synchronizację danych przy użyciu interfejsu użytkownika, jego widoku. Aby uzyskać szczegółowe informacje w powiązaniu z obiekty źródła danych hierarchicznych i koncepcji bieżący wskaźnik rekordu w powiązaniu danych, zobacz [Użyj wzorca szczegółowego z danymi hierarchicznymi](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) lub [Data Binding Overview](../data/data-binding-overview.md).  
  
> [!NOTE]
>  Pozornie przypomina tej składni [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Wartość true [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] wyrażenie powiązanie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] źródła danych nie jest używana jako <xref:System.Windows.Data.Binding.Path%2A> wartości, a zamiast tego należy używać w przypadku wzajemnie się wykluczają <xref:System.Windows.Data.Binding.XPath%2A> właściwości.  
  
### <a name="collection-views"></a>Widoki kolekcji  
 Aby odwołać się do widoku nazwane zbiory prefiks nazwy widoku kolekcji za pomocą znaku skrótu (`#`).  
  
### <a name="current-record-pointer"></a>Bieżący wskaźnik rekordu  
 Aby odwołać się do bieżącego rekordu wskaźnik nie zawiera widok kolekcji lub scenariusza powiązania danych master szczegółów rozpoczynać ciąg ścieżki kreski ułamkowej (`/`). Dowolną ścieżkę ostatnie ukośnik, o ile począwszy od bieżącego wskaźnika rekordu.  
  
### <a name="multiple-indexers"></a>Wiele indeksatorów  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Jeśli dany obiekt obsługuje wiele indeksatorów, można określić te indeksatorów w kolejności, podobnie jak tablica odwołujące się do składni. Danego obiektu może być bieżącym kontekście lub wartość właściwości, która zawiera wiele obiektów indeksu.  
  
 Domyślnie wartości indeksatora są wpisane za pomocą właściwości obiektu źródłowego. Jeśli to konieczne, można określić typ indeksu. Szczegółowe informacje na temat pisania indeksatorów, <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Mieszanie składni  
 Mogą występować naprzemiennie każdego składni pokazanych powyżej. Na przykład poniżej przedstawiono przykład, który tworzy ścieżkę właściwości do koloru w szczególności x, y `ColorGrid` właściwość, która zawiera tablicą siatka pikseli <xref:System.Windows.Media.SolidColorBrush> obiektów:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Sekwencje ucieczki dla ciągów ścieżki właściwości  
 W przypadku niektórych obiektów biznesowych, mogą wystąpić przypadek, w którym ciąg ścieżki właściwości wymaga sekwencji ucieczki, aby można było poprawnie przeanalizować. Powinny być rzadkie, trzeba ucieczki, ponieważ wiele z tych znaków ma podobne problemy nazewnictwa interakcji w językach, które zazwyczaj będzie służyć do definiowania obiektem biznesowym.  
  
- Wewnątrz indeksatorów ([]) znak daszka (^) specjalne następny znak.  
  
- Musisz wyjść (przy użyciu jednostki XML) niektórych znaków, które są specjalne do definicji języka XML. Użyj `&` jako znak ucieczki dla znaku "&". Użyj `>` jako znak ucieczki dla tagu końcowego ">".  
  
- Należy wprowadzić (przy użyciu ukośnik odwrotny `\`) znaki, które są charakterystyczne dla WPF XAML zachowanie analizatora przetwarzania rozszerzenia znaczników.  
  
    - Ukośnik odwrotny (`\`) jest sam znak ucieczki.  
  
    - Znak równości (`=`) oddziela nazwy właściwości od wartości właściwości.  
  
    - Przecinek (`,`) oddziela właściwości.  
  
    - Prawy nawias klamrowy (`}`) na końcu rozszerzeniem znacznika.  
  
> [!NOTE]
>  Technicznie rzecz biorąc te sekwencje ucieczki działa w przypadku ścieżki właściwości scenorysu również są zwykle przechodzenie przez modele obiektów dla istniejących obiektów WPF — a anulowania zapewnianego element powinien być niepotrzebne.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>Propertypath — dla celów animacji  
 Właściwość target animacji musi być właściwość zależności, która przyjmuje albo <xref:System.Windows.Freezable> lub typu pierwotnego. Jednak może istnieć dla różnych obiektów docelowych właściwości w typie i ostateczną animowany. Animacji ścieżkę właściwości służy do definiowania połączenia między obiekt docelowy nazwane animacji właściwości i zamierzonego celu animacji, przez nakierowanych relacji właściwości obiektu w wartości właściwości.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Właściwości obiektu Ogólne zagadnienia dotyczące animacji  
 Aby uzyskać więcej informacji na temat animacji pojęć, zobacz [Przegląd Scenorysy](../graphics-multimedia/storyboards-overview.md) i [Przegląd animacja](../graphics-multimedia/animation-overview.md).  
  
 Typ wartości lub właściwości jest animowany musi być albo <xref:System.Windows.Freezable> typu lub elementu podstawowego. Właściwość, która rozpoczyna się ścieżkę należy rozwiązać nazwę właściwości zależności, która istnieje na określonym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 W celu obsługi klonowania animowania <xref:System.Windows.Freezable> , jest już zablokowany, określony przez obiekt <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> musi być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasy pochodnej.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Jednej właściwości w obiekcie docelowym  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` należy rozwiązać nazwę właściwości zależności, która istnieje na określonym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Właściwość pośrednich określania wartości docelowej.  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musi być właściwością, która jest albo <xref:System.Windows.Freezable> wartości typu lub elementu podstawowego, która istnieje na wskazanym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 `propertyName2` musi być nazwą właściwości zależności, który istnieje w obiekcie, który jest wartością `propertyName`. Innymi słowy `propertyName2` musi istnieć jako właściwość zależności od typu, który jest `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Pośrednie przeznaczonych dla animacji jest konieczne ze względu zastosowane style i szablony. Aby skierować je do animacji, konieczne będzie <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> na obiekt docelowy, a nazwa zostaje ustanowione przy [x: Name](../../xaml-services/x-name-directive.md) lub <xref:System.Windows.FrameworkElement.Name%2A>. Mimo że szablonu i elementy stylu także mogą mieć nazwy, te nazwy są prawidłowe tylko w ramach namescope stylów i szablonów. (Jeśli szablony i style udostępniona zakresy nazw zaznaczaniu aplikacji, nazwy nie może być unikatowe. Style i szablony dosłownie są współdzielone między wystąpieniami i będzie widoczny przy obsłudze często takich samych nazwach.) W związku z tym jeśli poszczególne właściwości elementu, który chcesz animować pochodzi ze stylu lub szablonu, należy uruchomić przy użyciu wystąpienia nazwanego elementu, który nie pochodzi z szablon stylu, a następnie wskazać do drzewa wizualnego, stylu lub szablonu zostanie dostarczona wartość właściwości chcesz animować.  
  
 Na przykład <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Panel> jest kompletna <xref:System.Windows.Media.Brush> (faktycznie <xref:System.Windows.Media.SolidColorBrush>) dostarczonej z szablonu motywu. Aby animować <xref:System.Windows.Media.Brush> całkowicie, musi być BrushAnimation (prawdopodobnie jednym dla każdego <xref:System.Windows.Media.Brush> typu) i nie ma żadnego takiego typu. Aby animować pędzla, zamiast tego animować właściwości określonego <xref:System.Windows.Media.Brush> typu. Należy uzyskać od <xref:System.Windows.Media.SolidColorBrush> do jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> do zastosowania <xref:System.Windows.Media.Animation.ColorAnimation> istnieje. Ścieżka właściwości w tym przykładzie byłaby `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Dołączone właściwości  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Nawiasy wskazują, że tę właściwość w <xref:System.Windows.PropertyPath> powinien być skonstruowany przy użyciu częściowe kwalifikacji. Aby znaleźć typ może używać przestrzeni nazw XML. `ownerType` Wyszukiwania typów, które [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor ma dostęp, za pomocą <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklaracji w każdym zestawie. Większość aplikacji ma domyślny obszar nazw XML, mapowane na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw, dzięki czemu prefiks, który zazwyczaj jest tylko niezbędne dla niestandardowych typów lub typy w przeciwnym razie spoza tej przestrzeni nazw. `propertyName` należy rozwiązać nazwę właściwości istniejących `ownerType`. Właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>. (Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone właściwości są implementowane jako właściwości zależności, więc ten problem występuje tylko z kwestią w przypadku niestandardowych dołączone właściwości.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Indeksatory  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Większość właściwości zależności lub <xref:System.Windows.Freezable> typów nie obsługują indeksatora. W związku z tym tylko użycie indeksatora w ścieżce animacji jest pozycja pośredni między właściwość, która uruchamia łańcuch dla nazwanego elementu docelowego i ostateczną właściwość animowany. Podana składnię, która jest `propertyName2`. Na przykład użycie indeksatora może być konieczne w przypadku pośredniego właściwości jest kolekcją, takich jak <xref:System.Windows.Media.TransformGroup>, ścieżki właściwości, takie jak `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>Atrybut PropertyPath w kodzie  
 Użycie kodu <xref:System.Windows.PropertyPath>, włącznie ze sposobem konstruowania <xref:System.Windows.PropertyPath>, opisano w temacie dotyczącym <xref:System.Windows.PropertyPath>.  
  
 Ogólnie rzecz biorąc <xref:System.Windows.PropertyPath> jest przeznaczony do stosowania dwa różne konstruktory, jeden dla powiązań i najprostszą zastosowania animacji i jeden dla użycia złożonej animacji. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpisu dla powiązania użycia, gdy obiekt jest ciąg. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis dla jednoetapowy Animacja ścieżki, w którym obiekt jest <xref:System.Windows.DependencyProperty>. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> podpis dla złożonych animacji. Ten konstruktor ostatnie używa ciąg tokenu dla pierwszego parametru i tablicę obiektów, które wypełniają pozycji w ciąg tokenu, aby zdefiniować relację ścieżki właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.PropertyPath>
- [Powiązanie danych — omówienie](../data/data-binding-overview.md)
- [Scenorysy — przegląd](../graphics-multimedia/storyboards-overview.md)
