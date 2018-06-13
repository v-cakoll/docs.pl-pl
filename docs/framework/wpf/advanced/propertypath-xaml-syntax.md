---
title: PropertyPath — Składnia XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 547c7d009d2fecf863284324c7ea45006d20d20c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548990"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath — Składnia XAML
<xref:System.Windows.PropertyPath> Obiekt obsługuje złożone wbudowanego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnię ustawiania różne właściwości, które przyjmują <xref:System.Windows.PropertyPath> typu jako ich wartości. Ten temat dokumenty <xref:System.Windows.PropertyPath> składni jak stosować do składni powiązania i animacji.  
    
  
<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>Gdzie są używane PropertyPath  
 <xref:System.Windows.PropertyPath> jest typowe obiekt, który jest używany w kilku [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcji. Pomimo przy użyciu wspólnej <xref:System.Windows.PropertyPath> do przekazywania informacji o ścieżce właściwości, użycia dla każdej funkcji obszaru gdzie <xref:System.Windows.PropertyPath> jest używany jako typ różnią się. Dlatego jest bardziej praktyczne dokumentu składni na podstawie poszczególnych funkcji.  
  
 Przede wszystkim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa <xref:System.Windows.PropertyPath> opisujący ścieżki model obiektów dla przechodzących przez właściwości obiektu źródła danych i do opisywania ścieżka docelowa docelowej animacji.  
  
 Niektóre właściwości stylu i szablonu, takie jak <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> zająć nazwa kwalifikowana właściwości pozornie podobny <xref:System.Windows.PropertyPath>. Nie jest to wartość PRAWDA, ale <xref:System.Windows.PropertyPath>; zamiast tego jest kwalifikowany *owner.property* ciągu użycia formatu, który został włączony przez podsystem WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesora w połączeniu z konwerter typów dla <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath dla obiektów w powiązaniu danych  
 Powiązanie danych jest [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji, w którym można powiązać wartości docelowej dowolnej właściwości zależności. Jednakże źródle powiązania danych nie musi być właściwością zależności; może być dowolnego typu właściwości, który jest rozpoznawany przez dostawcę danych dotyczy. Ścieżki właściwości są szczególnie używane dla <xref:System.Windows.Data.ObjectDataProvider>, który służy do uzyskiwania źródeł powiązania z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów i ich właściwości.  
  
 Należy pamiętać, że wiązanie danych do [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nie używa <xref:System.Windows.PropertyPath>, ponieważ nie jest używane <xref:System.Windows.Data.Binding.Path%2A> w <xref:System.Windows.Data.Binding>. Zamiast tego należy użyć <xref:System.Windows.Data.Binding.XPath%2A> i określ prawidłową składnię wyrażenia XPath do [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] danych. <xref:System.Windows.Data.Binding.XPath%2A> jest też określona jako ciąg znaków, ale nie jest opisane w tym miejscu; zobacz [powiązania danych XML przy użyciu XMLDataProvider i kwerendy XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Kluczem do zrozumienia ścieżki właściwości w powiązaniu danych nie można wskazać powiązania wartość wybranej właściwości, lub zamiast tego można powiązać właściwości obiektu docelowego, które przyjmują list lub kolekcji. Kolekcji są wiązane, na przykład powiązanie <xref:System.Windows.Controls.ListBox> które rozszerzą w zależności od tego, ile elementów danych są w kolekcji, a następnie ścieżki właściwości powinien odwoływać się obiekt kolekcji, nie poszczególnych kolekcji elementów. Aparat wiązania danych będzie odpowiadała używany jako źródła danych na typ docelowy powiązanie automatycznie, co powoduje zachowanie, takich jak wypełnianie kolekcji <xref:System.Windows.Controls.ListBox> z tablicą elementów.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Jednej właściwości w obiekcie natychmiastowego jako kontekst danych  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* musi rozpoznać nazwę właściwości, która znajduje się w bieżącej <xref:System.Windows.FrameworkElement.DataContext%2A> dla <xref:System.Windows.Data.Binding.Path%2A> użycia. Jeśli Twoje powiązanie aktualizuje źródła, tej właściwości musi być odczytu/zapisu, a obiekt źródłowy musi być modyfikowalną.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Jeden indeksator natychmiastowego obiektu jako kontekst danych  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` musi być typu indeksu do słownika lub tablicy skrótów lub liczba całkowita indeksu tablicy. Ponadto wartość klucza musi być typu, który jest bezpośrednio powiązania dla właściwości, których jest stosowane. Na przykład tablicy skrótów, który zawiera ciąg kluczy i wartości ciągu można w ten sposób powiązać tekst <xref:System.Windows.Controls.TextBox>. Lub klucz wskazuje kolekcji lub podindeks, należy użyć następującej składni powiązać z właściwością kolekcji docelowej. W przeciwnym razie należy odwoływać konkretnej właściwości, za pomocą składni, takich jak `<Binding Path="[``key``].``propertyName``" .../>`.  
  
 Jeśli to konieczne, można określić typ indeksu. Aby uzyskać więcej informacji na ten aspekt ścieżki właściwości indeksowanych, zobacz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Wiele właściwości (właściwość pośrednie elementów docelowych)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` należy rozwiązać nazwę właściwości, która jest bieżącą <xref:System.Windows.FrameworkElement.DataContext%2A>. Właściwości ścieżki `propertyName` i `propertyName2` może mieć żadnych właściwości, które istnieją w relacji, której `propertyName2` jest właściwością, która istnieje na typ, który jest wartością `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Jednej właściwości dołączonych lub w przeciwnym razie kwalifikowaną typu  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Nawiasy wskazujące, że ta właściwość w <xref:System.Windows.PropertyPath> powinien być tworzony przy użyciu częściowego kwalifikacji. Służy do przestrzeni nazw XML można znaleźć typu z odpowiednie mapowanie. `ownerType` Wyszukiwania typy, które [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor ma dostęp do, za pomocą <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklaracji w każdym zestawie. Większość aplikacji ma domyślnej przestrzeni nazw XML, mapowane na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw, dlatego prefiks jest zwykle wymagane tylko dla typów niestandardowych lub typów w przeciwnym razie spoza tej przestrzeni nazw.  `propertyName` musi być rozpoznawana jako nazwa właściwości istniejących `ownerType`. Ta składnia jest zazwyczaj używana do jednej z następujących przypadkach:  
  
-   Ścieżka jest określona w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w stylu lub szablonie, który nie ma określonego typu docelowego. Użycie kwalifikowaną zwykle nie jest prawidłowy w przypadku innych niż to, ponieważ w przypadku-style, — do szablonu, właściwość istnieje w wystąpieniu, nie jest typem.  
  
-   Właściwość jest dołączona właściwość.  
  
-   Dokonywane jest wiązanie właściwości statycznej.  
  
 Do użytku jako docelowego scenorysu, właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Przechodzenie źródła (powiązanie z hierarchii kolekcji)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / W tej składni jest używany do nawigacji w obiekt źródła danych hierarchicznej i wielu kroków do hierarchii z kolejnych / są obsługiwane znaki. Przechodzenie źródła konta dla bieżącego położenia wskaźnika rekordów jest określany przez synchronizację danych przy użyciu interfejsu użytkownika, jego widoku. Aby uzyskać szczegółowe informacje na powiązanie z danymi hierarchicznymi obiekty źródła i pojęcia bieżącego rekordu wskaźnika w powiązaniu danych, zobacz [Użyj wzorca wzorzec-szczegół z danymi hierarchicznymi](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) lub [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  Pozornie podobny tej składni [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Wartość PRAWDA [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] wyrażenie dla powiązania [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] źródła danych nie jest używana jako <xref:System.Windows.Data.Binding.Path%2A> wartość, a zamiast tego należy używać do wykluczają się wzajemnie <xref:System.Windows.Data.Binding.XPath%2A> właściwości.  
  
### <a name="collection-views"></a>Kolekcja widoków  
 Aby odwołać widoku nazwanej kolekcji, nazwę widoku kolekcji znakiem skrótu prefiks (`#`).  
  
### <a name="current-record-pointer"></a>Bieżący wskaźnik rekordu  
 Aby odwołać bieżącego rekordu wskaźnika widok kolekcji lub scenariusz wiązania danych master szczegółów, uruchom ciąg ścieżki się ukośnikiem (`/`). Dowolną ścieżkę poza ukośnik jest przechodni, zaczynając od bieżącego wskaźnika rekordu.  
  
### <a name="multiple-indexers"></a>Wiele indeksatorów  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Jeśli dany obiekt obsługuje wiele indeksatorów, można określić te indeksatorów w kolejności, podobnie jak odwołania do składni tablicy. Bieżący kontekst lub wartość właściwości, która zawiera wiele obiektów indeksu, może być danego obiektu.  
  
 Domyślnie wartości indeksatora są wpisywane przy użyciu właściwości obiektu źródłowego. Jeśli to konieczne, można określić typ indeksu. Aby uzyskać więcej informacji o wpisanie indeksatorów, zobacz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Mieszanie składni  
 Mogą występować naprzemiennie każdego składni przedstawionych powyżej. Na przykład poniżej przedstawiono przykład tworzenia ścieżkę właściwości na kolor w szczególności x, y `ColorGrid` właściwość, która zawiera tablicę siatki pikseli z <xref:System.Windows.Media.SolidColorBrush> obiektów:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Specjalne dla ciągów ścieżki właściwości  
 Dla niektórych obiektów biznesowych może wystąpić przypadek, gdzie ciąg ścieżki właściwości wymagane — sekwencja specjalna analizowane poprawnie. Trzeba wprowadzić powinny być rzadko, ponieważ wiele z tych znaków ma podobne problemy nazewnictwa interakcji w językach, które zazwyczaj będzie służyć do definiowania obiektu biznesowego.  
  
-   Wewnątrz indeksatorów ([]) znaki daszek (^) specjalne następny znak.  
  
-   Użytkownik musi escape (przy użyciu jednostek XML) niektóre znaki specjalne do definicji języka XML. Użyj `&` Aby anulować znak "&". Użyj `>` ucieczki tag końcowy ">".  
  
-   Należy wprowadzić (przy użyciu ukośnik odwrotny `\`) znaki specjalne działanie analizatora składni WPF XAML przetwarzania rozszerzenia znaczników.  
  
    -   Ukośnik odwrotny (`\`) jest sam znak ucieczki.  
  
    -   Znak równości (`=`) oddziela nazwę właściwości od wartości właściwości.  
  
    -   Przecinek (`,`) oddziela właściwości.  
  
    -   Prawy nawias klamrowy (`}`) na końcu rozszerzenia znacznika.  
  
> [!NOTE]
>  Z technicznego punktu widzenia te specjalne pracy dla ścieżki właściwości scenorysu również, ale są zazwyczaj przechodzących przez modele obiektów dla istniejących obiektów WPF i anulowanie może nie być konieczne.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>PropertyPath dla celów animacji  
 Właściwość target animacji musi być właściwością zależności pobierającej albo <xref:System.Windows.Freezable> lub typu pierwotnego. Docelowa właściwość typu i właściwość animowany ewentualnych może jednak istnieć na różnych obiektów. Animacji ścieżka właściwości służy do definiowania połączenie między właściwości animacji nazwanego obiektu docelowego i właściwości animacji zamierzonego celu przez przechodzących przez właściwości obiektu relacji, w wartości właściwości.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Właściwości obiektu Ogólne zagadnienia dotyczące animacji  
 Aby uzyskać więcej informacji na temat animacji ogólnie rzecz biorąc, zobacz pojęcia [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md) i [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Typ wartości lub animowanej właściwości musi być równa albo <xref:System.Windows.Freezable> typu lub elementu podstawowego. Właściwość, która rozpoczyna się ścieżka musi być rozpoznawana jako nazwa właściwości zależności, czy istnieje na wskazanym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 Aby można było obsługiwać w klonowania animacji <xref:System.Windows.Freezable> który jest już zablokowany, określony przez obiekt <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> musi być <xref:System.Windows.FrameworkElement> lub <xref:System.Windows.FrameworkContentElement> klasy.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Jednej właściwości w obiekcie docelowym  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` należy rozwiązać nazwę właściwości zależności, czy istnieje na wskazanym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Pośrednie właściwości elementów docelowych  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musi być właściwością, która jest albo <xref:System.Windows.Freezable> wartość typu lub elementu podstawowego, która istnieje na wskazanym <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 `propertyName2` musi być nazwą właściwości zależności, czy istnieje dla obiektu, który jest wartością `propertyName`. Innymi słowy `propertyName2` musi istnieć jako właściwość zależności od typu, który jest `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Pośrednie przeznaczonych dla animacji jest konieczne z powodu zastosowane style i szablony. Aby skierować animacji, należy <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> na obiekt docelowy oraz że nazwa została ustanowiona przy [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) lub <xref:System.Windows.FrameworkElement.Name%2A>. Mimo że elementy szablonu i styl można również mają nazwy, tych nazw są poprawne tylko w namescope styl i szablonu. (Jeśli szablony i style udostępnić namescopes znaczników aplikacji, nazwy nie może być unikatowe. Style i szablony dosłownie są udostępniane między wystąpieniami i będzie widoczny przy obsłudze często takich samych nazwach.) W związku z tym jeśli poszczególnych właściwości elementu, którego ma być animowane pochodzi z stylu lub szablonie, należy uruchomić przy użyciu wystąpienia nazwanego elementu, który nie pochodzi z szablonu stylu i skierować w stylu lub szablonie drzewa wizualnego na właściwość chcesz animować.  
  
 Na przykład <xref:System.Windows.Controls.Panel.Background%2A> właściwość <xref:System.Windows.Controls.Panel> jest kompletna <xref:System.Windows.Media.Brush> (faktycznie <xref:System.Windows.Media.SolidColorBrush>) dostarczonej z szablonu motywu. Aby animować <xref:System.Windows.Media.Brush> całkowicie, musi być BrushAnimation (prawdopodobnie po jednej dla każdego <xref:System.Windows.Media.Brush> typ) i nie ma takiego typu. Aby animować Pędzel, zamiast tego animowania właściwości określonego <xref:System.Windows.Media.Brush> typu. Należy uzyskać z <xref:System.Windows.Media.SolidColorBrush> do jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> dotyczyć <xref:System.Windows.Media.Animation.ColorAnimation> istnieje. Ścieżka właściwości w tym przykładzie byłaby `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Dołączone właściwości  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Nawiasy wskazujące, że ta właściwość w <xref:System.Windows.PropertyPath> powinien być tworzony przy użyciu częściowego kwalifikacji. Służy do przestrzeni nazw XML można znaleźć typu. `ownerType` Wyszukiwania typy, które [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor ma dostęp do, za pomocą <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklaracji w każdym zestawie. Większość aplikacji ma domyślnej przestrzeni nazw XML, mapowane na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw, dlatego prefiks jest zwykle wymagane tylko dla typów niestandardowych lub typów w przeciwnym razie spoza tej przestrzeni nazw. `propertyName` musi być rozpoznawana jako nazwa właściwości istniejących `ownerType`. Właściwość określona jako `propertyName` musi być <xref:System.Windows.DependencyProperty>. (Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone właściwości są zaimplementowane jako właściwości zależności, więc tego problemu jest tylko jeden z kwestią w przypadku dołączonych właściwości niestandardowych.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Indeksatory  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Większość właściwości zależności lub <xref:System.Windows.Freezable> typów nie obsługują indeksatora. W związku z tym tylko dla indeksatora w ścieżce animacji jest na pośrednie pozycji między właściwość, która uruchamia łańcuch na elemencie docelowym nazwane i właściwość animowany ewentualnych. W składni udostępnionego, który jest `propertyName2`. Na przykład użycie indeksatora może być konieczne w przypadku pośredniego właściwość jest kolekcją, takich jak <xref:System.Windows.Media.TransformGroup>, w ścieżce właściwości, takie jak `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>PropertyPath w kodzie  
 Użycie kodu <xref:System.Windows.PropertyPath>, łącznie ze sposobem tworzenia <xref:System.Windows.PropertyPath>, opisano w temacie dotyczącym <xref:System.Windows.PropertyPath>.  
  
 Ogólnie rzecz biorąc <xref:System.Windows.PropertyPath> jest przeznaczony do użycia dwa różne konstruktory, jedno dla użycia powiązania i najprostszym zastosowania animacji i jeden do użycia złożonych animacji. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpisu dla powiązania ich użycia, gdy obiekt jest ciąg. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis dla ścieżki animacji jednoetapowy, gdy obiekt jest <xref:System.Windows.DependencyProperty>. Użyj <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> podpisu złożonych animacji. Ten konstruktor ostatnie używa ciąg tokenu pierwszy parametr i tablicę obiektów, które wypełnienia pozycji w ciągu tokenu, aby zdefiniować relację ścieżki właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.PropertyPath>  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
