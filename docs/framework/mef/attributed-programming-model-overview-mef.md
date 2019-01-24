---
title: Omówienie modelu programowania opartego na atrybutach (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5429dfbf7b318b60d6c3150315dbe22ee73b4792
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563447"
---
# <a name="attributed-programming-model-overview-mef"></a>Omówienie modelu programowania opartego na atrybutach (MEF)
W Managed Extensibility Framework (MEF), *model programowania* jest metodą określonego definiowania zestawu obiektów koncepcyjny, na których działa MEF. Te koncepcyjny obiekty obejmują elementy, importu i eksportu. MEF korzysta z tych obiektów, ale nie określa, jak powinna być reprezentowana. W związku z tym szerokiej gamy modele programowania są możliwe, w tym dostosowane modeli programowania.  
  
 Wartość domyślna jest model programowania, używany w MEF *model programowania opartego na atrybutach*. W opartego na atrybutach programowania części modelu importów, eksportów i inne obiekty są definiowane za pomocą atrybutów, które dekoracji zwykłych klas .NET Framework. W tym temacie wyjaśniono, jak używać atrybutów opartego na atrybutach model programowania do tworzenia aplikacji MEF.  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>Importowanie i eksportowanie podstawy  
 *Wyeksportować* jest wartością, która część zawiera z innymi częściami w kontenerze, oraz *zaimportować* jest to wymagane, określającym części do kontenera, do wypełnienia z dostępnych eksportowania. W modelu programowania opartego na atrybutach przywozu i wywozu są zadeklarowane przez urządzanie klas lub składowych o `Import` i `Export` atrybutów. `Export` Atrybut może dekoracji klasy, pola, właściwości lub metody podczas `Import` atrybut może dekoracji parametru pola, właściwości lub konstruktora.  
  
 Aby Importuj, aby można dopasować Eksport, import i eksport muszą mieć taką samą *kontraktu*. Umowa składa się ciągu o nazwie *Nazwa kontraktu*oraz typ wyeksportowane lub importowany obiekt o nazwie *typ kontraktu*. Tylko wtedy, gdy zarówno Nazwa kontraktu, jak i kontrakt typ dopasowania Eksport uznaje się do spełnienia określonego importu.  
  
 Jeden lub oba parametry kontrakt może być jawne lub niejawne. Poniższy kod przedstawia klasę, która deklaruje podstawowe importu.  
  
```vb  
Public Class MyClass1  
    <Import()>  
    Public Property MyAddin As IMyAddin  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public IMyAddin MyAddin { get; set; }  
}  
```  
  
 W tym importu `Import` atrybut nie ma typu kontraktu ani parametrem nazwy kontraktu dołączone. W związku z tym zarówno będzie można wywnioskować z ozdobione właściwości. W tym przypadku będzie typ kontraktu `IMyAddin`, Nazwa kontraktu. zostanie ona unikatowy ciąg utworzony na podstawie typu kontraktu. (Innymi słowy, Nazwa kontraktu pokaże tylko eksportu, których nazwy są również wnioskowany z typu `IMyAddin`.)  
  
 Na poniższym obrazie przedstawiono eksportu, które pasuje do poprzedniego importu.  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 W tym eksportu jest typ kontraktu `IMyAddin` ponieważ jest on parametr `Export` atrybutu. Wyeksportowanego typu musi być taki sam jak typ kontraktu, pochodzi od typu kontraktu lub implementować typ kontraktu, jeśli jest to interfejs. W tym eksportu, rzeczywisty typ `MyLogger` implementuje interfejs `IMyAddin`. Nazwa kontraktu jest wnioskowany z typu kontraktu, co oznacza, że tego eksportu będą zgodne poprzedniego importu.  
  
> [!NOTE]
>  Eksportów i importów zwykle powinny zostać zadeklarowane na publiczne klasy lub elementów członkowskich. Innych deklaracji są obsługiwane, ale eksportowanie lub importowanie prywatny, chroniony lub wewnętrzny element członkowski przerywa modelu izolacji dla części i dlatego nie zaleca się.  
  
 Typ kontraktu musi być zgodna dokładnie do eksportowania i importowania, aby być uznane za pasujące. Należy wziąć pod uwagę następującej operacji eksportowania.  
  
```vb  
<Export()> 'WILL NOT match the previous import!  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export] //WILL NOT match the previous import!  
public class MyLogger : IMyAddin { }  
```  
  
 W tym eksportu jest typ kontraktu `MyLogger` zamiast `IMyAddin`. Mimo że `MyLogger` implementuje `IMyAddin`i mogą być rzutowane na `IMyAddin` obiektu tego eksportu nie będą zgodne poprzedniego importowania, ponieważ typy kontraktu nie są takie same.  
  
 Ogólnie rzecz biorąc nie jest konieczne określić nazwę kontraktu i kontrakty większość powinna być zdefiniowana pod względem typu kontraktu i metadanych. Jednak w pewnych okolicznościach należy bezpośrednio określić nazwę umowy. Najbardziej często zdarza się, gdy klasa eksportuje wiele wartości, które mają wspólnego typu, na przykład w nim elementów podstawowych. Nazwa kontraktu, można określić jako pierwszy parametr `Import` lub `Export` atrybutu. Poniższy kod przedstawia importu i eksportu o nazwie określonej umowy `MajorRevision`.  
  
```vb  
Public Class MyExportClass  
  
    'This one will match  
    <Export("MajorRevision")>  
    Public ReadOnly Property MajorRevision As Integer  
        Get  
            Return 4  
        End Get  
    End Property  
  
    <Export("MinorRevision")>  
    Public ReadOnly Property MinorRevision As Integer  
        Get  
            Return 16  
        End Get  
    End Property  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("MajorRevision")]  
    public int MajorRevision { get; set; }  
}  
  
public class MyExportClass  
{   
    [Export("MajorRevision")] //This one will match.  
    public int MajorRevision = 4;  
  
    [Export("MinorRevision")]  
    public int MinorRevision = 16;  
}  
```  
  
 Jeśli nie określono typu kontraktu, nadal będzie można wywnioskować z typu importu lub eksportu. Jednak nawet jeśli nazwa kontraktu jest jawnie określona, typ kontraktu musi być również zgodna dokładnie do importowania i eksportowania do być uznane za pasujące. Na przykład jeśli `MajorRevision` pole było ciągu, typy kontraktu wywnioskowane nie będzie odpowiadać i eksportowania i importowania, pomimo o tej samej nazwie kontraktu nie będzie odpowiadać.  
  
### <a name="importing-and-exporting-a-method"></a>Importowanie i eksportowanie — metoda  
 `Export` Atrybut może także dekoracji metody, w taki sam sposób jak klasa, właściwość lub funkcji. Eksportuje metody należy określić typ kontraktu lub Nazwa kontraktu, ponieważ nie można wywnioskować typu. Określony typ może być niestandardowego delegata lub typ ogólny, taką jak `Func`. Następujące klasy eksportuje metodę o nazwie `DoSomething`.  
  
```vb  
Public Class MyAddin  
  
    'Explicitly specifying a generic type  
    <Export(GetType(Func(Of Integer, String)))>  
    Public Function DoSomething(ByVal TheParam As Integer) As String  
        Return Nothing 'Function body goes here  
    End Function  
  
End Class  
```  
  
```csharp  
public class MyAddin  
{  
    //Explicitly specifying a generic type.  
    [Export(typeof(Func<int, string>))]  
    public string DoSomething(int TheParam);  
}  
```  
  
 W tej klasie `DoSomething` metoda przyjmuje jeden `int` parametr i zwraca `string`. Aby dopasować tego eksportu, importowania część musi deklarować właściwego członka. Następujące klasy Importy `DoSomething` metody.  
  
```vb  
Public Class MyClass1  
  
    'Contract name must match!  
    <Import()>  
    Public Property MajorRevision As Func(Of Integer, String)  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import] //Contract name must match!  
    public Func<int, string> DoSomething { get; set; }  
}  
```  
  
 Aby uzyskać więcej informacji o sposobie użytkowania `Func<T, T>` obiektu, zobacz <xref:System.Func%602>.  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>Typy Importy  
 MEF wsparcia podmiotu trzeciego zaimportować niektóre typy w tym dynamiczne, z opóźnieniem, wstępnie wymagane i opcjonalne.  
  
### <a name="dynamic-imports"></a>Importy dynamiczne  
 W niektórych przypadkach importowania klasy może być zgodny eksportów wystąpień dowolnego typu, o nazwie określonej umowy. W tym scenariuszu można zadeklarować klasy *dynamicznego importowania*. Następujący import pasuje do dowolnego eksportu z nazwą kontraktu "TheString".  
  
```vb  
Public Class MyClass1  
  
    <Import("TheString")>  
    Public Property MyAddin  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("TheString")]  
    public dynamic MyAddin { get; set; }  
}  
```  
  
 Gdy typ kontraktu jest wnioskowany z `dynamic` — słowo kluczowe, będą one zgodne dowolny typ kontraktu. W takim przypadku należy import **zawsze** Określ nazwę kontraktu do dopasowania. (Jeśli określono bez nazwy kontraktu, importowania zostanie ono uznane za eksportuje żadnych danych.) Oba następujące eksporty umożliwi dopasowanie poprzedniego importu.  
  
```vb  
<Export("TheString", GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
  
<Export("TheString")>  
Public Class MyToolbar  
  
End Class  
```  
  
```csharp  
[Export("TheString", typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
  
[Export("TheString")]  
public class MyToolbar { }  
```  
  
 Oczywiście importowania klasy musi być przygotowana do czynienia z obiekt dowolnego typu.  
  
### <a name="lazy-imports"></a>Importy  
 W niektórych przypadkach importowania klasy mogą wymagać pośrednie odwołanie do obiektu importowanych tak, aby obiekt nie zostanie uruchomiony natychmiast. W tym scenariuszu można zadeklarować klasy *importu z opóźnieniem* za pomocą typu kontraktu `Lazy<T>`. Następująca właściwość importowania deklaruje importu z opóźnieniem.  
  
```vb  
Public Class MyClass1  
  
    <Import()>  
    Public Property MyAddin As Lazy(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public Lazy<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 Z punktu widzenia aparat kompozycji, typ kontraktu `Lazy<T>` uznaje się taka sama jak typ kontraktu `T`. W związku z tym poprzednie importu umożliwi dopasowanie następującej operacji eksportowania.  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 Nazwa kontraktu i typ umowy można określić w `Import` atrybutu do zaimportowania z opóźnieniem, zgodnie z wcześniejszym opisem w sekcji "Podstawowe przywozu i wywozu".  
  
### <a name="prerequisite-imports"></a>Importy wymagań wstępnych  
 Wyeksportowane części MEF są zwykle tworzone przez aparat kompozycji w odpowiedzi na żądanie bezpośredniego lub konieczność wypełnienia dopasowane importu. Domyślnie podczas tworzenia części aparat składu używa konstruktor bez parametrów. Aby aparat, użyj innego konstruktora, możesz oznaczyć go za pomocą `ImportingConstructor` atrybutu.  
  
 Każda część może mieć tylko jeden konstruktor do użycia przez aparat kompozycji. Brak domyślnego konstruktora i nie `ImportingConstructor` atrybutu lub podając więcej niż jeden `ImportingConstructor` atrybutu, spowoduje wygenerowanie błędu.  
  
 Aby wypełnić parametry do konstruktora oznaczonego `ImportingConstructor` atrybutu, wszystkie te parametry są automatycznie zadeklarowane jako import. Jest to wygodny sposób, aby zadeklarować importów, które są używane podczas inicjowania części. Następujące klasy używa `ImportingConstructor` do deklarowania importu.  
  
```vb  
Public Class MyClass1  
  
    Private _theAddin As IMyAddin  
  
    'Default constructor will NOT be used  
    'because the ImportingConstructor  
    'attribute is present.  
    Public Sub New()  
  
    End Sub  
  
    'This constructor will be used.  
    'An import with contract type IMyAddin  
    'is declared automatically.  
    <ImportingConstructor()>  
    Public Sub New(ByVal MyAddin As IMyAddin)  
        _theAddin = MyAddin  
    End Sub  
  
End Class  
```  
  
```csharp  
public class MyClass   
{  
    private IMyAddin _theAddin;  
  
    //Default constructor will NOT be  
    //used because the ImportingConstructor  
    //attribute is present.  
    public MyClass() { }  
  
    //This constructor will be used.  
    //An import with contract type IMyAddin is   
    //declared automatically.  
    [ImportingConstructor]   
    public MyClass(IMyAddin MyAddin)   
    {  
        _theAddin = MyAddin;  
    }  
}  
```  
  
 Domyślnie `ImportingConstructor` atrybutu używa wywnioskować typy kontraktu i kontrakt nazwy dla wszystkich importów parametru. Istnieje możliwość zastąpić to ustawienie przez urządzanie parametrów z `Import` atrybuty, które można zdefiniować typ kontraktu i Nazwa kontraktu jawnie. Poniższy kod demonstruje konstruktora, który używa tej składni, aby zaimportować klasy pochodnej zamiast klasy nadrzędnej.  
  
```vb  
<ImportingConstructor()>  
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)  
  
End Sub  
```  
  
```csharp  
[ImportingConstructor]   
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)   
{  
    _theAddin = MyAddin;  
}  
```  
  
 W szczególności należy zachować ostrożność przy użyciu kolekcji parametrów. Na przykład, jeśli określisz `ImportingConstructor` w Konstruktorze z parametrem typu `IEnumerable<int>`, importowanie będzie odpowiadał jednej Eksport typu `IEnumerable<int>`, zamiast zestawu eksportuje typ `int`. Do dopasowania zbiór eksportuje typ `int`, masz do dekorowania parametr o `ImportMany` atrybutu.  
  
 Parametry zadeklarowane jako Import przez `ImportingConstructor` atrybutu są również oznaczane jako *importuje wstępnie wymaganego składnika*. MEF zwykle umożliwia eksportowanie i importowanie do formularza *cyklu*. Na przykład cykl jest, gdzie Importy obiekt A obiekt B, który z kolei importuje A. obiektu W zwykłych okolicznościach cyklu nie stanowi to problemu, a kontener kompozycji zazwyczaj tworzy oba obiekty.  
  
 Przy importowany wartość jest wymagana przez Konstruktor części, ten obiekt nie może uczestniczyć w cyklu. Jeśli obiekt A wymaga można skonstruować obiekt B, zanim można skonstruować sam, a obiekt B importuje element obiektu, a następnie cyklu nie będzie można rozwiązać, i wystąpi błąd kompozycji. Importy zadeklarowanego w Konstruktorze parametry są w związku z tym Importy wymagań wstępnych, które wszystkie należy podać przed wszystkich eksporty od obiektu, który wymaga ich używać.  
  
### <a name="optional-imports"></a>Importy opcjonalne  
 `Import` Atrybut określa wymagania dla części do funkcji. Jeśli import nie mogą być spełnione, kompozycji tę część zakończy się niepowodzeniem, a część nie będą dostępne.  
  
 Można określić, że importowanie jest *opcjonalne* przy użyciu `AllowDefault` właściwości. W tym przypadku kompozycji zostanie wykonane pomyślnie nawet jeśli importowania jest niezgodny z dostępnych eksportowanie i importowanie właściwość zostanie ustawiona na domyślne dla tego typu właściwości (`null` dla właściwości obiektu `false` wartości logicznych lub wartości zero dla liczbowego Właściwości). Następujące klasy używa opcjonalny import.  
  
```vb  
Public Class MyClass1  
  
    <Import(AllowDefault:=True)>  
    Public Property thePlugin As Plugin  
  
    'If no matching export is available,  
    'thePlugin will be set to null.  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import(AllowDefault = true)]  
    public Plugin thePlugin { get; set; }  
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a>Importowanie wielu obiektów  
 `Import` Atrybut będzie tylko pomyślnie składać się podczas dopasowuje jeden i tylko jeden Eksport. Czasami powoduje wygenerowanie błędu kompozycji. Aby zaimportować więcej niż jeden Eksport, który odpowiada tej samej umowy, należy użyć `ImportMany` atrybutu. Importy z tym atrybutem zawsze są opcjonalne. Na przykład kompozycji zakończy się niepowodzeniem, jeśli podano pasującego eksportuje żadnych danych. Następujące klasy importuje dowolnej liczby eksportów typu `IMyAddin`.  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 Zaimportowane tablicy jest możliwy przy użyciu zwykłej `IEnumerable<T>` składni i metody. Istnieje również możliwość użycia zwykłych tablicy (`IMyAddin[]`) zamiast tego.  
  
 Ten wzorzec może być bardzo ważne, gdy jest on używany w połączeniu z `Lazy<T>` składni. Na przykład za pomocą `ImportMany`, `IEnumerable<T>`, i `Lazy<T>`, można importować pośredniego odwołania do dowolnej liczby obiektów i wystąpienia tylko te, które stały się niezbędne. Następujące klasy pokazuje tego wzorca.  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }  
}  
```  
  
<a name="avoiding_discovery"></a>   
## <a name="avoiding-discovery"></a>Unikanie odnajdywania  
 W niektórych przypadkach można zapobiec część odbywa się odnajdowanie w ramach katalogu. Na przykład części może być klasa bazowa mają być dziedziczone z, ale nie używane. Istnieją dwa sposoby, w tym celu. Najpierw należy użyć `abstract` — słowo kluczowe w klasie części. Klasy abstrakcyjne nigdy nie zapewniają eksportu, mimo że zapewniają one dziedziczone eksporty do klas, które wynikają z nich.  
  
 Jeżeli klasy abstrakcyjnej, mogą ją za pomocą dekoracji `PartNotDiscoverable` atrybutu. Część dekorowane za pomocą tego atrybutu będzie nieuwzględnione w dowolnym wykazów. W poniższym przykładzie pokazano te wzorce. `DataOne` spowoduje odnalezienie katalogu. Ponieważ `DataTwo` jest abstrakcyjny, go nie zostanie odnaleziona. Ponieważ `DataThree` używane `PartNotDiscoverable` atrybutu, nie zostanie odnaleziona.  
  
```vb  
<Export()>  
Public Class DataOne  
    'This part will be discovered   
    'as normal by the catalog.  
End Class  
  
<Export()>  
Public MustInherit Class DataTwo  
    'This part will not be discovered  
    'by the catalog.  
End Class  
  
<PartNotDiscoverable()>  
<Export()>  
Public Class DataThree  
    'This part will also not be discovered  
    'by the catalog.  
End Class  
```  
  
```csharp  
[Export]  
public class DataOne  
{  
    //This part will be discovered  
    //as normal by the catalog.  
}  
  
[Export]  
public abstract class DataTwo  
{  
    //This part will not be discovered  
    //by the catalog.  
}  
  
[PartNotDiscoverable]  
[Export]  
public class DataThree  
{  
    //This part will also not be discovered  
    //by the catalog.  
}  
```  
  
<a name="metadata_and_metadata_views"></a>   
## <a name="metadata-and-metadata-views"></a>Metadane i widoków metadanych  
 Eksporty umożliwia uzyskanie dodatkowych informacji o sobie znany jako *metadanych*. Metadane może służyć do przekazania właściwości eksportowanego obiektu do importowania części. Podjęcie decyzji, które eksportuje użycia lub zebrać informacje dotyczące eksportu bez konieczności jego konstruowania, importowania części mogą używać tych danych. Z tego powodu importu musi być z opóźnieniem się wykorzystanie metadanych.  
  
 Się wykorzystanie metadanych, zwykle zadeklarować interfejsu nazywane *widoku metadanych*, oświadcza, jakie metadane staną się dostępne. Interfejs widok metadanych musi mieć tylko właściwości, a te właściwości musi mieć `get` metod dostępu. Poniższy interfejs jest przykładowy widok metadanych.  
  
```vb  
Public Interface IPluginMetadata  
  
    ReadOnly Property Name As String  
  
    <DefaultValue(1)>  
    ReadOnly Property Version As Integer  
  
End Interface  
```  
  
```csharp  
public interface IPluginMetadata  
{  
    string Name { get; }  
  
    [DefaultValue(1)]    
    int Version { get; }  
}  
```  
  
 Istnieje również możliwość użycia kolekcji ogólnej, `IDictionary<string, object>`, jako widoku metadanych, ale forfeits zalety sprawdzania typu i należy ich unikać.  
  
 Zazwyczaj wymagane są wszystkie właściwości o nazwie w widoku metadanych i eksportowanie, które nie są oferowane ich nie zostanie uwzględniony dopasowania. `DefaultValue` Atrybut określa, że właściwość jest opcjonalna. Jeśli właściwość nie jest uwzględniona, zostanie do niej przypisana wartość domyślna określona jako parametr `DefaultValue`. Poniżej przedstawiono dwa różne klasy ozdobione metadanymi. Oba te klasy będzie pasował do poprzedniego widoku metadanych.  
  
```vb  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class MyLogger  
    Implements IPlugin  
  
End Class  
  
'Version is not required because of the DefaultValue  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Disk Writer")>  
Public Class DWriter  
    Implements IPlugin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
}  
  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Disk Writer")]   
    //Version is not required because of the DefaultValue  
public class DWriter : IPlugin  
{  
}  
```  
  
 Metadane bazy danych jest wyrażona po `Export` atrybutu przy użyciu `ExportMetadata` atrybutu. Każda część metadanych składa się z pary nazwa/wartość. Część nazwy metadanych musi odpowiadać nazwie odpowiednie właściwości w widoku metadanych, a wartość zostanie przypisany do tej właściwości.  
  
 Jeśli istnieją, będzie używany jest importera, który określa jakie widoku metadanych. Import za pomocą metadanych jest zadeklarowany jako import z opóźnieniem, za pomocą interfejsu metadanych jako drugi parametr typu `Lazy<T,T>`. Następujące klasy importuje poprzedniej części z metadanymi.  
  
```vb  
Public Class Addin  
  
    <Import()>  
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)  
End Class  
```  
  
```csharp  
public class Addin  
{  
    [Import]  
    public Lazy<IPlugin, IPluginMetadata> plugin;  
}  
```  
  
 W wielu przypadkach można połączyć metadanych za pomocą `ImportMany` atrybutu, aby można było analizować za pomocą dostępnych operacji importu i wybierz polecenie i utworzyć tylko jedno wystąpienie lub kolekcję, aby dopasować określony warunek filtrowania. Następujące klasy tworzy tylko `IPlugin` obiektów, które mają `Name` wartość "Rejestratora".  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If Plugin.Metadata.Name = "Logger" Then  
                logger = Plugin.Value  
            End If  
        Next  
        Return logger  
    End Function  
  
End Class  
```  
  
```csharp  
public class User  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;  
  
    public IPlugin InstantiateLogger()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a>Importowanie i eksportowanie dziedziczenia  
 Jeśli klasa dziedziczy z części, tej klasy może również stać się częścią. Importy zawsze są dziedziczone przez podklasy. W związku z tym podklasę części zawsze będzie częścią, za pomocą tej samej operacji importu jako swojej klasy nadrzędnej.  
  
 Eksporty zadeklarowane za pomocą `Export` atrybutów nie są dziedziczone przez podklasy. Jednak część można wyeksportować się za pomocą `InheritedExport` atrybutu. Podklasy części taka, a następnie podaj ten sam eksportu, łącznie z nazwą kontraktu i typ umowy. W odróżnieniu od `Export` atrybutu `InheritedExport` może odnosić się tylko na poziomie klasy, a nie na poziomie elementu członkowskiego. W związku z tym eksportuje poziom elementu członkowskiego nigdy nie mogą być dziedziczone.  
  
 Następujące cztery klasy pokazują zasady importowania i eksportowania dziedziczenia. `NumTwo` dziedziczy `NumOne`, więc `NumTwo` zaimportuje `IMyData`. Zwykłe eksporty nie są dziedziczone, więc `NumTwo` nie eksportuje żadnych elementów. `NumFour` dziedziczy `NumThree`. Ponieważ `NumThree` używane `InheritedExport`, `NumFour` ma jeden Eksport kontraktu typu `NumThree`. Poziom elementu członkowskiego eksporty nigdy nie są dziedziczone, więc `IMyData` nie są eksportowane.  
  
```vb  
<Export()>  
Public Class NumOne  
    <Import()>  
    Public Property MyData As IMyData  
End Class  
  
Public Class NumTwo  
    Inherits NumOne  
  
    'Imports are always inherited, so NumTwo will  
    'Import IMyData  
  
    'Ordinary exports are not inherited, so  
    'NumTwo will NOT export anything.  As a result it  
    'will not be discovered by the catalog!  
  
End Class  
  
<InheritedExport()>  
Public Class NumThree  
  
    <Export()>  
    Public Property MyData As IMyData  
  
    'This part provides two exports, one of  
    'contract type NumThree, and one of   
    'contract type IMyData.  
  
End Class  
  
Public Class NumFour  
    Inherits NumThree  
  
    'Because NumThree used InheritedExport,  
    'this part has one export with contract   
    'type NumThree.  
  
    'Member-level exports are never inherited,  
    'so IMyData is not exported.  
  
End Class  
```  
  
```csharp  
[Export]  
public class NumOne  
{  
    [Import]  
    public IMyData MyData { get; set; }  
}  
  
public class NumTwo : NumOne  
{  
    //Imports are always inherited, so NumTwo will   
    //import IMyData.  
  
    //Ordinary exports are not inherited, so   
    //NumTwo will NOT export anything. As a result it   
    //will not be discovered by the catalog!  
}  
  
[InheritedExport]  
public class NumThree  
{  
    [Export]  
    Public IMyData MyData { get; set; }  
  
    //This part provides two exports, one of  
    //contract type NumThree, and one of  
    //contract type IMyData.  
}  
  
public class NumFour : NumThree  
{  
    //Because NumThree used InheritedExport,  
    //this part has one export with contract  
    //type NumThree.  
  
    //Member-level exports are never inherited,  
    //so IMyData is not exported.  
}  
```  
  
 W przypadku metadane skojarzone z `InheritedExport` atrybutu tych metadanych również będą dziedziczone. (Aby uzyskać więcej informacji, zobacz we wcześniejszej sekcji "Metadanych i widoków metadanych"). Nie można zmodyfikować metadanych dziedziczone przez podklasy. Jednakże, deklarując ponownie `InheritedExport` atrybutu z taką samą nazwę kontraktu i typ umowy, ale z nowymi metadanymi, podklasy mogą zastąpić dziedziczone metadanych nowymi metadanymi. Następujące klasy pokazuje tę zasadę. `MegaLogger` Część dziedziczy `Logger` i zawiera `InheritedExport` atrybutu. Ponieważ `MegaLogger` ponownie nowe metadane o nazwie Status, nie dziedziczy on nazwę i wersję metadanych z `Logger`.  
  
```vb  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class Logger  
    Implements IPlugin  
  
    'Exports with contract type IPlugin  
    'and metadata "Name" and "Version".  
End Class  
  
Public Class SuperLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Name" and "Version", exactly the same  
    'as the Logger class.  
  
End Class  
  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Status", "Green")>  
Public Class MegaLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Status" only. Re-declaring   
    'the attribute replaces all metadata.  
  
End Class  
```  
  
```csharp  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version".  
}  
  
public class SuperLogger : Logger  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version", exactly the same  
    //as the Logger class.  
}  
  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Status", "Green")]  
public class MegaLogger : Logger        {  
    //Exports with contract type IPlugin and   
    //metadata "Status" only. Re-declaring   
    //the attribute replaces all metadata.  
}  
```  
  
 Podczas deklarowania ponownie `InheritedExport` atrybutu, aby zastąpić metadane, upewnij się, że typy kontraktu są takie same. (W poprzednim przykładzie `IPlugin` jest typ kontraktu.) Będą się różnić, zamiast przesłaniać metodę, drugi atrybut utworzy eksportu drugi, niezależne od części. Ogólnie rzecz biorąc, oznacza to, że musisz jawnie określić typ kontraktu, aby zastąpić `InheritedExport` atrybutu, jak pokazano w poprzednim przykładzie.  
  
 Ponieważ nie można bezpośrednio utworzyć wystąpienia interfejsów, ich zwykle nie może być dekorowane za pomocą `Export` lub `Import` atrybutów. Jednakże, interfejs może być dekorowane za pomocą `InheritedExport` atrybut na poziomie interfejsu i że eksportu wraz z wszelkimi skojarzone metadane będą dziedziczone przez wszystkie klasy implementującej. Interfejs, sama nie będą dostępne w ramach jednak.  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>Atrybuty Eksport niestandardowy  
 Atrybuty eksportu podstawowych `Export` i `InheritedExport`, można rozszerzyć do uwzględnienia metadanych jako właściwości atrybutów. Ta technika jest przydatna do stosowania metadanych podobne do wielu elementów lub tworzenia drzewa dziedziczenia atrybutów metadanych.  
  
 Typ kontraktu, Nazwa kontraktu lub inne metadane, można określić atrybutu niestandardowego. Aby zdefiniować niestandardowy atrybut klasy dziedziczącej z `ExportAttribute` (lub `InheritedExportAttribute`) musi posiadać `MetadataAttribute` atrybutu. Następujące klasy definiuje atrybutu niestandardowego.  
  
```vb  
<MetadataAttribute()>  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>  
Public Class MyAttribute  
    Inherits ExportAttribute  
  
    Public Property MyMetadata As String  
  
    Public Sub New(ByVal myMetadata As String)  
        MyBase.New(GetType(IMyAddin))  
  
        myMetadata = myMetadata  
    End Sub  
  
End Class  
```  
  
```csharp  
[MetadataAttribute]  
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]  
public class MyAttribute : ExportAttribute  
{  
    public MyAttribute(string myMetadata)   
        : base(typeof(IMyAddin))  
    {  
        MyMetadata = myMetadata;  
    }  
  
    public string MyMetadata { get; private set; }  
}  
```  
  
 Ta klasa definiuje atrybut niestandardowy o nazwie `MyAttribute` z typem umowy `IMyData` i niektórych metadanych o nazwie `MyMetadata`. Wszystkie właściwości w klasie oznaczone `MetadataAttribute` atrybutu są uznawane za metadanych zdefiniowanych w atrybucie niestandardowym. Poniższe dwie deklaracje są równoważne.  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 W pierwszej deklaracji typu kontraktu i metadane jawnie są zdefiniowane. W drugim deklaracji typu kontraktu i metadane są niejawne w niestandardowych atrybutów. Zwłaszcza w przypadkach, w którym dużej ilości metadanych identyczne należy zastosować do wielu elementów (na przykład, autora lub informacje o prawach autorskich) za pomocą atrybutu niestandardowego można zapisać mnóstwo czasu i dublowania. Dodatkowo umożliwia pozostawienie można utworzyć drzewa dziedziczenia atrybutów niestandardowych.  
  
 Aby utworzyć opcjonalne metadane w atrybucie niestandardowym, można użyć `DefaultValue` atrybutu. Ten atrybut jest stosowany do właściwości w klasie Atrybut niestandardowy, określa się że ozdobione właściwość jest opcjonalna i nie będzie musiał podać eksporter. Jeśli nie podano wartości dla właściwości, zostanie do niej przypisana wartość domyślna dla tego typu właściwości (zazwyczaj `null`, `false`, lub równa 0.)  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>Tworzenie zasad  
 Gdy część określa importu i kompozycji jest wykonywane, pojemnik składu próbuje odnaleźć zgodnego eksportu. Importuj z eksportową pasujący pomyślnie, importowania elementu członkowskiego jest ustawione na wystąpienie eksportowanego obiektu. Z której pochodzi to wystąpienie jest kontrolowana przez część eksportowania *zasad tworzenia*.  
  
 Są dwie zasady może spowodować powstanie *udostępnionego* i *nieudostępnione*. W ramach zasad tworzenia zostaną udostępnione być współużytkowane przez każdego importu w kontenerze dla części z tej Umowy. Gdy aparat kompozycji znalezienia dopasowania i ustawić właściwość importowania, będzie on wystąpienia nową kopię część tylko wtedy, gdy jeszcze nie istnieje; w przeciwnym razie poda istniejącą kopię. Oznacza to, że wiele obiektów może mieć odwołania do tej samej części. Takie części nie należy polegać na stan wewnętrzny, który może ulec zmianie w wielu miejscach. Ta zasada jest odpowiednia dla części statycznych, elementy, które udostępniają usługi i części, które to zajmować dużo pamięci lub innych zasobów.  
  
 Część nieudostępnione z zasadami tworzenia zostanie utworzony, za każdym razem, gdy znajduje pasujące importu dla jednego z jego eksportu. Nowa kopia w związku z tym będzie można utworzyć wystąpienia dla każdego importu w kontenerze, który pasuje do wyeksportowanych kontraktów części. Wewnętrzny stan tych kopii, nie będą udostępniane. Ta zasada jest odpowiednia dla części, w którym każdej operacji importowania wymaga własnej stanu wewnętrznego.  
  
 Importowanie i eksportowanie można określić zasady tworzenia części, spośród wartości `Shared`, `NonShared`, lub `Any`. Wartość domyślna to `Any` dla obu importuje i eksportuje. Eksport określający `Shared` lub `NonShared` spowoduje dopasowanie tylko importu, który określa takie same lub określający `Any`. Podobnie, który określa import `Shared` lub `NonShared` spowoduje dopasowanie tylko eksportu, który określa takie same lub określający `Any`. Przywozu i wywozu przy użyciu zasad tworzenia niezgodne nie są uwzględniane w taki sam sposób jak importu i eksportu, w której nazwa lub kontrakt typu kontraktu nie są zgodne z dopasowania. Jeśli określono zarówno importowania i eksportowania `Any`, lub nie określaj zasad tworzenia i domyślnie `Any`, zasady tworzenia, domyślnie zostanie udostępniony.  
  
 Poniższy przykład pokazuje, importuje i eksportuje Określanie zasad tworzenia. `PartOne` nie określono zasadę tworzenia, więc wartość domyślna to `Any`. `PartTwo` nie określono zasadę tworzenia, więc wartość domyślna to `Any`. Ponieważ zarówno importowania i eksportowania domyślnie `Any`, `PartOne` zostaną udostępnione. `PartThree` Określa `Shared` tworzenia zasad, więc `PartTwo` i `PartThree` współużytkują tę samą kopię `PartOne`. `PartFour` Określa `NonShared` tworzenia zasad, więc `PartFour` będzie nieudostępniany w `PartFive`. `PartSix` Określa `NonShared` tworzenia zasad. `PartFive` i `PartSix` każdego będą otrzymywać osobne kopie `PartFour`. `PartSeven` Określa `Shared` tworzenia zasad. Ponieważ istnieje nie wyeksportowane `PartFour` z zasadami tworzenia `Shared`, `PartSeven` importu nie pasuje do niczego i nie zostaną wypełnione.  
  
```vb  
<Export()>  
Public Class PartOne  
    'The default creation policy for an export is Any.  
End Class  
  
Public Class PartTwo  
  
    <Import()>  
    Public Property partOne As PartOne  
  
    'The default creation policy for an import is Any.  
    'If both policies are Any, the part will be shared.  
  
End Class  
  
Public Class PartThree  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partOne As PartOne  
  
    'The Shared creation policy is explicitly specified.  
    'PartTwo and PartThree will receive references to the  
    'SAME copy of PartOne.  
  
End Class  
  
<Export()>  
<PartCreationPolicy(CreationPolicy.NonShared)>  
Public Class PartFour  
    'The NonShared creation policy is explicitly specified.  
End Class  
  
Public Class PartFive  
  
    <Import()>  
    Public Property partFour As PartFour  
  
    'The default creation policy for an import is Any.  
    'Since the export's creation policy was explictly  
    'defined, the creation policy for this property will  
    'be non-shared.  
  
End Class  
  
Public Class PartSix  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>  
    Public Property partFour As PartFour  
  
    'Both import and export specify matching creation   
    'policies.  PartFive and PartSix will each receive   
    'SEPARATE copies of PartFour, each with its own  
    'internal state.  
  
End Class  
  
Public Class PartSeven  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partFour As PartFour  
  
    'A creation policy mismatch.  Because there is no   
    'exported PartFour with a creation policy of Shared,  
    'this import does not match anything and will not be  
    'filled.  
  
End Class  
```  
  
```csharp  
[Export]  
public class PartOne  
{  
    //The default creation policy for an export is Any.  
}  
  
public class PartTwo  
{  
    [Import]  
    public PartOne partOne { get; set; }  
  
    //The default creation policy for an import is Any.  
    //If both policies are Any, the part will be shared.  
}  
  
public class PartThree  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartOne partOne { get; set; }  
  
    //The Shared creation policy is explicitly specified.  
    //PartTwo and PartThree will receive references to the  
    //SAME copy of PartOne.  
}  
  
[Export]  
[PartCreationPolicy(CreationPolicy.NonShared)]  
public class PartFour  
{  
    //The NonShared creation policy is explicitly specified.  
}  
  
public class PartFive  
{  
    [Import]  
    public PartFour partFour { get; set; }  
  
    //The default creation policy for an import is Any.  
    //Since the export's creation policy was explictly  
    //defined, the creation policy for this property will  
    //be non-shared.  
}  
  
public class PartSix  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]  
    public PartFour partFour { get; set; }  
  
    //Both import and export specify matching creation   
    //policies.  PartFive and PartSix will each receive   
    //SEPARATE copies of PartFour, each with its own  
    //internal state.  
}  
  
public class PartSeven  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartFour partFour { get; set; }  
  
    //A creation policy mismatch.  Because there is no   
    //exported PartFour with a creation policy of Shared,  
    //this import does not match anything and will not be  
    //filled.  
}  
```  
  
<a name="life_cycle_and_disposing"></a>   
## <a name="life-cycle-and-disposing"></a>Cykl życia i usuwania  
 Ponieważ części są przechowywane w kontenerze kompozycji, ich cyklu życia może być bardziej skomplikowane niż zwykłe obiektów. Części mogą zawierać dwie ważne interfejsy związanych z cyklem życia: `IDisposable` i `IPartImportsSatisfiedNotification`.  
  
 Części wymagające pracy do wykonania w zamykania w dół lub wymagające zwolnić zasoby powinny implementować `IDisposable`, jak zwykle dla obiektów .NET Framework. Jednak ponieważ kontener tworzy i obsługuje odwołania do części, kontenera, który jest właścicielem część powinny wywoływać `Dispose` metody na nim. Implementuje samego kontenera `IDisposable`oraz jako część jej oczyszczania w `Dispose` zostanie `Dispose` na wszystkie elementy, które jest właścicielem. Z tego powodu należy zawsze dysponować pojemnik składu podczas jej i częściami, który jest właścicielem nie są już potrzebne.  
  
 Kontenery długotrwałe kompozycji zużycie pamięci przez części za pomocą zasad tworzenia nieudostępnione może stać się problemem. Te częściami nieudostępnionymi można tworzyć wiele razy, a nie zostanie usunięte, dopóki nie zostanie usunięty, samego kontenera. Aby poradzić sobie z tym, zapewnia kontener `ReleaseExport` metody. Wywołanie tej metody na eksport nieudostępnione spowoduje usunięcie tego eksportu z kontener kompozycji i usuwa go. Elementy, które są używane tylko przez usunięto Eksport, i tak dalej na dół drzewa, również są usuwane i usunięty. W ten sposób można odzyskać bez usuwania sam pojemnik składu zasobów.  
  
 `IPartImportsSatisfiedNotification` zawiera jedną metodę o nazwie `OnImportsSatisfied`. Ta metoda jest wywoływana, pojemnik składu w dowolnej części, które implementują interfejs, gdy kompozycja zostało ukończone i Importy części są gotowe do użycia. Elementy są tworzone przez aparat kompozycji, aby wypełnić polecenie importuje inne części. Przed zestawu polecenie importuje element nie może wykonać inicjowanie opiera się na lub zmienia wartości importowanych w Konstruktorze części, chyba że te wartości zostały określone jako warunki wstępne przy użyciu `ImportingConstructor` atrybutu. Zazwyczaj jest to preferowana metoda, ale w niektórych przypadkach iniekcji konstruktora mogą być niedostępne. W takich przypadkach można wykonać inicjowania w `OnImportsSatisfied`, i powinna implementować część `IPartImportsSatisfiedNotification`.  
  
## <a name="see-also"></a>Zobacz także
- [Wideo Channel 9: Otwórz swoje aplikacje za pomocą Managed Extensibility Framework —](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Wideo Channel 9: Struktura Managed Extensibility Framework (MEF) w wersji 2.0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
