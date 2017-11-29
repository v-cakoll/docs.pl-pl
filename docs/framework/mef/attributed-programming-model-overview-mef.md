---
title: "Omówienie modelu programowania opartego na atrybutach (MEF)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16ffe789635ee13c118c63c30ef255cc9b264a9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attributed-programming-model-overview-mef"></a>Omówienie modelu programowania opartego na atrybutach (MEF)
W Managed Extensibility Framework (MEF), *model programowania* jest określonego sposobu definiowania zestawu obiektów pojęciach, na których działa MEF. Te obiekty koncepcyjnej obejmują części, importu i eksportu. MEF używa tych obiektów, ale nie określa, jak powinny być reprezentowane. W związku z tym szerokiej gamy modele programowania są możliwe, w tym dostosowane modele programowania.  
  
 Wartość domyślna jest model programowania używany w MEF *model programowania opartego na atrybutach*. Oparte na atrybutach części modelu programowania Importy, eksportów i inne obiekty są zdefiniowane z atrybutów, które dekoracji zwykłej klasy .NET Framework. W tym temacie wyjaśniono, jak używać atrybutów oparte na atrybutach model programowania do tworzenia aplikacji MEF.  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>Importowanie i eksportowanie podstawy  
 *Wyeksportować* to wartość, która zawiera części do innych części w kontenerze, oraz *zaimportować* jest wymagane określającym części w kontenerze, należy podać z dostępnych eksportu. W modelu programowania oparte na atrybutach importu i eksportu są zadeklarowane przez dekoracji klas lub członków z `Import` i `Export` atrybutów. `Export` Atrybut można dekoracji klasy, pola, właściwości lub metody, gdy `Import` atrybut można dekoracji parametr pola, właściwości lub konstruktora.  
  
 Importowanie i eksportowanie można dopasować, importowanie i eksportowanie musi mieć takie same *kontraktu*. Kontrakt składa się z ciągu o nazwie *Nazwa kontraktu*i typ obiektu wyeksportowane lub zaimportowane, nazywany *typu kontraktu*. Tylko wtedy, gdy nazwę kontraktu i kontraktu wpisz dopasowania eksportu uważa się spełnienia określonego importu.  
  
 Jeden lub oba parametry kontrakt może być jawnych ani niejawnych. Poniższy kod przedstawia klasę, która deklaruje podstawowe importu.  
  
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
  
 Podczas importowania `Import` atrybut nie ma typ kontraktu ani został dołączony parametr nazwy kontraktu. W związku z tym zarówno będzie można wywnioskować na podstawie właściwości dekorowany. W takim przypadku typ kontraktu będzie `IMyAddin`, a Nazwa kontraktu będą unikatowy ciąg utworzone na podstawie typu kontraktu. (Innymi słowy, Nazwa kontraktu jest zgodny tylko eksportu, których nazwy są również wywnioskować na podstawie typu `IMyAddin`.)  
  
 Poniżej przedstawiono Eksport zgodny poprzedniej importu.  
  
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
  
 W tym eksportu jest typ kontraktu `IMyAddin` ponieważ jest on parametr `Export` atrybutu. Wyeksportowanego typu musi być albo taki sam jak typ kontraktu, pochodzi z typu kontraktu lub implementować typ kontraktu, jeśli jest to interfejs. W tym eksportu, rzeczywisty typ `MyLogger` implementuje interfejs `IMyAddin`. Nazwa kontraktu jest wywnioskowany na podstawie typu kontraktu, co oznacza, że tego eksportu będzie odpowiadała poprzedniej importu.  
  
> [!NOTE]
>  Zazwyczaj eksportów i importów powinny zostać zadeklarowane w publicznych klas lub członków. Inne deklaracje są obsługiwane, ale eksportowanie lub importowanie prywatnych, chronionych lub wewnętrzny elementu członkowskiego przerywa model izolacji części i dlatego nie jest zalecana.  
  
 Typ kontraktu musi odpowiadać dokładnie do eksportowania i importowania, aby być uznawane za zgodne. Należy wziąć pod uwagę następujące eksportu.  
  
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
  
 W tym eksportu jest typ kontraktu `MyLogger` zamiast `IMyAddin`. Mimo że `MyLogger` implementuje `IMyAddin`i może być rzutowane na `IMyAddin` obiekt tego eksportu nie będzie odpowiadała poprzedniej importowania, ponieważ typy kontraktu nie są takie same.  
  
 Ogólnie rzecz biorąc nie jest konieczne określić nazwę kontraktu i kontrakty większości powinien być zdefiniowany typ kontraktu i metadanych. Jednak w pewnych okolicznościach, należy określić nazwę kontraktu bezpośrednio. Najbardziej często zdarza się, gdy klasa eksportuje kilka wartości, które mają wspólny typ, takich jak podstawowych. Nazwa kontraktu można określić jako pierwszy parametr `Import` lub `Export` atrybutu. Poniższy kod przedstawia importu i eksportu przy użyciu nazwy określonej kontraktu `MajorRevision`.  
  
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
  
 Jeśli nie określono typu kontraktu, nadal będzie można wywnioskować z typu importu lub eksportu. Jednak nawet wtedy, gdy nazwa kontraktu określono jawnie, typ kontraktu musi być również zgodna dokładnie dla importu i eksportu, aby być uznawane za zgodne. Na przykład jeśli `MajorRevision` pole jest ciągiem, czy niezgodne typy kontraktu wnioskowany i eksportowania będzie niezgodna importu, pomimo o tej samej nazwie kontraktu.  
  
### <a name="importing-and-exporting-a-method"></a>Importowanie i eksportowanie — metoda  
 `Export` Atrybut można również dekoracji metody, w taki sam sposób jak klasy, właściwości lub funkcji. Eksporty — metoda należy określić typ kontraktu lub Nazwa kontraktu, ponieważ nie można wywnioskować typu. Określony typ może być niestandardowych delegata lub typu ogólnego, takich jak `Func`. Następujące klasy eksportuje metodę o nazwie `DoSomething`.  
  
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
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 W tej klasie `DoSomething` metoda przyjmuje jeden `int` parametrów i zwraca `string`. Aby dopasować tego eksportu, importowania części musi zadeklarować właściwego członka. Następujące klasy importów `DoSomething` metody.  
  
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
  
 Aby uzyskać więcej informacji o korzystaniu z `Func<T, T>` obiektów, zobacz <xref:System.Func%602>.  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>Typy importów  
 Wsparcie MEF kilka zaimportować typy w tym dynamiczne, z opóźnieniem, wstępnie wymagane i opcjonalne.  
  
### <a name="dynamic-imports"></a>Importy dynamiczne  
 W niektórych przypadkach importowania klasy może być zgodne eksportuje dowolnego typu, których nazwa umową. W tym scenariuszu można zadeklarować tej klasy *dynamiczne importu*. Importuj następujące odpowiada żadnych eksportu o nazwie kontraktu "TheString".  
  
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
  
 Jeśli typ kontraktu jest wywnioskowany na podstawie `dynamic` — słowo kluczowe, będzie odpowiadała dowolny typ kontraktu. W takim przypadku należy importu **zawsze** Określ nazwę kontraktu na potrzeby dopasowywania. (Jeśli nazwa kontraktu nie zostanie określona, importowanie uznaje się pasuje do żadnego eksportu.) Oba następujące eksportuje umożliwi dopasowanie poprzedniej importu.  
  
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
  
 Oczywiście importowania klasy muszą być przygotowane radzenia sobie z dowolnego typu obiektu.  
  
### <a name="lazy-imports"></a>Importy opóźnieniem  
 W niektórych przypadkach klasy importowania może wymagać pośrednie odwołanie do obiektu zaimportowane tak, aby obiekt nie jest od razu wystąpienia. W tym scenariuszu można zadeklarować tej klasy *importu opóźnionego* przy użyciu typu kontraktu `Lazy<T>`. Następująca właściwość importowania deklaruje opóźnionego importu.  
  
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
  
 Z punktu widzenia aparatu kompozycji, typ kontraktu `Lazy<T>` jest uznawany za taki sam jak typ kontraktu `T`. W związku z tym poprzedniej importu umożliwi dopasowanie następujące eksportu.  
  
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
  
 Nazwa kontraktu i typ kontraktu można określać w `Import` atrybutu do opóźnionego importu, zgodnie z wcześniejszym opisem w sekcji "Podstawowe importuje i eksportuje".  
  
### <a name="prerequisite-imports"></a>Importy wymagań wstępnych  
 Wyeksportowane części MEF są zwykle tworzone przez aparat kompozycji w odpowiedzi na potrzeby wypełnić dopasowane importu lub bezpośrednie żądania. Domyślnie podczas tworzenia części aparat kompozycji używa konstruktor bez parametrów. Aby aparatu, użyj innego konstruktora, możesz oznaczyć go przy użyciu `ImportingConstructor` atrybutu.  
  
 Każda część może mieć tylko jeden konstruktor do użycia przez aparat kompozycji. Brak domyślnego konstruktora i nie `ImportingConstructor` atrybutu lub podając więcej niż jeden `ImportingConstructor` atrybutu, spowoduje błąd.  
  
 Aby wypełnić parametry konstruktora oznaczonego jako z `ImportingConstructor` atrybutu, wszystkie te parametry są automatycznie deklarowane jako importowania. Jest to wygodny sposób, aby zadeklarować Importy, które są używane podczas inicjowania części. Następujące klasy używa `ImportingConstructor` Aby zadeklarować importu.  
  
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
  
 Domyślnie `ImportingConstructor` typy kontraktu wywnioskować używa atrybutów i kontraktu nazwy dla wszystkich importów parametru. Można zastąpić przez dekoracji parametrów z `Import` atrybuty, które następnie można zdefiniować nazwy kontraktu i typ kontraktu jawnie. Poniższy kod przedstawia Konstruktor, który używa tej składni, aby zaimportować klasy pochodnej zamiast klasy nadrzędnej.  
  
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
  
 W szczególności należy zachować ostrożność z kolekcji parametrów. Na przykład jeśli określisz `ImportingConstructor` na konstruktora z parametrem typu `IEnumerable<int>`, importowanie będzie odpowiadała jednego eksportu typu `IEnumerable<int>`, zamiast zestawu eksportuje typu `int`. Odpowiadające zestaw eksportuje typu `int`, masz do dekoracji parametr o `ImportMany` atrybutu.  
  
 Parametry zadeklarowany jako importów przez `ImportingConstructor` atrybutu są również oznaczane jako *importuje wymagań wstępnych*. MEF zwykle umożliwia eksportowanie i importowanie do formularza *cykl*. Na przykład cykl jest, gdzie importuje obiektu A obiekt B, który z kolei importuje A. obiektu W normalnych okolicznościach cyklu nie stanowi to problemu, oraz kontenera kompozycji konstrukcji oba obiekty normalnie.  
  
 Jeśli importowanych wartość jest wymagana przez konstruktora części, tego obiektu nie może brać udziału w cyklu. Jeśli obiekt A wymaga obiektu B można skonstruować przed można konstruować się i obiektu B importuje A obiektu cyklu nie będzie można rozwiązać i wystąpi błąd kompozycji. Importy zadeklarowany w parametrach konstruktora są zatem importów wymagań wstępnych, które wszystkie należy podać przed żadnego eksportu z obiektu, który wymaga ich użyciem.  
  
### <a name="optional-imports"></a>Importy opcjonalne  
 `Import` Atrybut określa wymaganie części funkcji. Nie można przeprowadzić importu, kompozycji części zakończy się niepowodzeniem, a część nie będzie dostępna.  
  
 Można określić, że importowanie jest *opcjonalne* przy użyciu `AllowDefault` właściwości. W takim przypadku kompozycji powiedzie się, nawet jeśli importu jest niezgodny z żadnych dostępnych eksporty i importowania właściwość zostanie ustawiona do domyślnego dla tego typu właściwości (`null` dla właściwości obiektu `false` dla wartości logicznych lub zero dla liczbowe Właściwości). Następujące klasy używa opcjonalny import.  
  
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
 `Import` Atrybut będzie tylko pomyślnie składać się, gdy jest on zgodny tylko jeden Eksport. Innych przypadkach spowoduje błąd kompozycji. Aby zaimportować więcej niż jeden Eksport zgodny ten sam kontrakt, użyj `ImportMany` atrybutu. Importy z tym atrybutem zawsze są opcjonalne. Na przykład kompozycji zakończy się niepowodzeniem, jeśli podano żadnego pasującego eksportu. Następujące klasy importuje dowolnej liczby eksportów typu `IMyAddin`.  
  
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
  
 Importowany tablicy jest możliwy przy użyciu zwykłej `IEnumerable<T>` składni i metod. Istnieje również możliwość użycia zwykłej tablicy (`IMyAddin[]`) zamiast tego.  
  
 Ten wzorzec może być bardzo ważne, gdy jest używany w połączeniu z `Lazy<T>` składni. Na przykład za pomocą `ImportMany`, `IEnumerable<T>`, i `Lazy<T>`, można importować pośredniego odwołania do dowolną liczbę obiektów i wystąpienia tylko te, które stały się niezbędne. Następujące klasy pokazuje tego wzorca.  
  
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
 W niektórych przypadkach można zapobiec odnajdywane jako część wykaz części. Na przykład część może być klasą podstawową mają być dziedziczone z, ale nie używane. Istnieją dwa sposoby, w tym celu. Najpierw należy użyć `abstract` — słowo kluczowe w klasie części. Klasy abstrakcyjne nigdy nie podawaj eksportu, mimo że zapewniają one eksportu odziedziczone do klasy, które pochodzą z nich.  
  
 Jeżeli klasa abstrakcyjna, można go przy użyciu dekoracji `PartNotDiscoverable` atrybutu. Części ozdobione ten atrybut nie będą uwzględniane w dowolnym katalogów. W poniższym przykładzie pokazano tych wzorców. `DataOne`zostaną odnalezione przez wykaz. Ponieważ `DataTwo` jest abstrakcyjna, go nie zostaną odnalezione. Ponieważ `DataThree` używane `PartNotDiscoverable` atrybutu, nie zostaną odnalezione.  
  
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
 Eksporty mogą dostarczać dodatkowych informacji o sobie znany jako *metadanych*. Metadane może służyć do przekazywania właściwości obiektu wyeksportowany do importowania części. Importowania części mogą używać tych danych do określania, które eksportuje do użycia, lub aby zebrać informacje dotyczące eksportu bez konieczności tworzenia go. Z tego powodu importu musi być opóźnieniem do użycia metadanych.  
  
 Aby użyć metadanych, zwykle zadeklarować interfejsu znany jako *widoku metadanych*, deklaruje, jakie metadane będą dostępne. Interfejs widok metadanych musi mieć tylko właściwości i te właściwości muszą mieć `get` metody dostępu. Następujący interfejs jest przykład widoku metadanych.  
  
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
  
 Istnieje również możliwość użycia kolekcji uniwersalnej, `IDictionary<string, object>`, jako widoku metadanych, ale forfeits zalet Sprawdzanie typu i należy unikać.  
  
 Zwykle wszystkie właściwości o nazwie w widoku metadanych są wymagane, a wszelkie eksportu, które nie udostępniają ich nie zostanie uwzględniony dopasowania. `DefaultValue` Atrybut określa, że właściwość jest opcjonalna. Jeśli właściwość nie jest uwzględniona, zostanie do niej przypisana wartość domyślna określona jako parametr `DefaultValue`. Poniżej przedstawiono dwóch różnych klas ozdobione metadanych. Oba te klasy umożliwi dopasowanie w poprzednim widoku metadanych.  
  
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
  
 Metadane jest wyrażone po `Export` atrybutu przy użyciu `ExportMetadata` atrybutu. Metadane każdego z nich składa się z pary nazwa/wartość. Część nazwy metadanych musi odpowiadać nazwie odpowiednie właściwości w widoku metadanych, a wartość zostanie przypisana do tej właściwości.  
  
 Jeśli istnieje, będzie używana jest importera, określająca jakie widoku metadanych. Importuj z metadanymi jest zadeklarowany jako opóźnionego importu, przy użyciu interfejsu metadanych jako drugi parametr typu `Lazy<T,T>`. Następujące klasy importuje poprzedniej części z metadanymi.  
  
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
  
 W wielu przypadkach można połączyć metadanych z `ImportMany` atrybutu, aby przeanalizować za pośrednictwem dostępne importów i wybierz i tylko jednego wystąpienia lub kolekcję, aby dopasować określony warunek filtrowania. Następujące klasy tworzy tylko `IPlugin` obiektów, które mają `Name` wartość "Rejestratora".  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
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
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a>Importowanie i eksportowanie dziedziczenia  
 Jeśli klasa dziedziczy z części, tej klasy może również zostać części. Importy zawsze są dziedziczone przez podklasy. W związku z tym podklasy części zawsze będzie częścią, z tym samym importów jako swojej klasy nadrzędnej.  
  
 Eksporty zadeklarowana przy użyciu `Export` atrybutów nie są dziedziczone przez podklasy. Jednak części można wyeksportować się za pomocą `InheritedExport` atrybutu. Podklasy części będzie dziedziczyć i podaj tego samego eksportu, łącznie z nazwą kontraktu i typ kontraktu. W odróżnieniu od `Export` atrybut `InheritedExport` może odnosić się tylko na poziomie klasy, a nie na poziomie elementu członkowskiego. W związku z tym poziomie członka eksportuje nigdy nie mogą być dziedziczone.  
  
 Następujące klasy cztery zademonstrować zasady importowania i eksportowania dziedziczenia. `NumTwo`dziedziczy `NumOne`, więc `NumTwo` zaimportuje `IMyData`. Zwykłe eksporty nie są dziedziczone, więc `NumTwo` nie eksportuje żadnych elementów. `NumFour`dziedziczy `NumThree`. Ponieważ `NumThree` używane `InheritedExport`, `NumFour` ma jeden Eksport kontraktu typu `NumThree`. Eksportowanie na poziomie członka nigdy nie są dziedziczone, więc `IMyData` nie jest eksportowany.  
  
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
  
 W przypadku metadane skojarzone z `InheritedExport` atrybutu, że metadane również będą dziedziczone. (Aby uzyskać więcej informacji, zobacz we wcześniejszej sekcji "Metadanych i widoków metadanych"). Nie można modyfikować metadanych dziedziczone przez podklasy. Jednak przez ponowne deklarowanie `InheritedExport` atrybutu o takiej samej nazwie kontraktu i typ umowy, ale z nowymi metadanymi, podklasy mogą zastąpić dziedziczone metadane o nowe metadane. Następujące klasy pokazuje tej zasady. `MegaLogger` Części dziedziczy `Logger` i zawiera `InheritedExport` atrybutu. Ponieważ `MegaLogger` ponownie deklaruje nowych metadanych o nazwie stanu, nie dziedziczy on nazwę i wersję metadanych z `Logger`.  
  
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
  
 Podczas ponownego deklarowania `InheritedExport` atrybutu Zastępowanie metadanych, upewnij się, że typy kontraktu są takie same. (W poprzednim przykładzie `IPlugin` jest typ kontraktu.) Jeśli będą się różnić, zamiast przesłaniać metodę, drugi atrybut utworzy export drugiej, niezależnie od z części. Ogólnie rzecz biorąc, oznacza to, że należy jawnie określić typ kontraktu, aby zastąpić `InheritedExport` atrybutu, jak pokazano w poprzednim przykładzie.  
  
 Ponieważ nie można bezpośrednio utworzyć wystąpienia interfejsów, one zazwyczaj nie może mieć atrybutu `Export` lub `Import` atrybutów. Jednak można ozdobione interfejs `InheritedExport` atrybutu na poziomie interfejsu i że eksportu oraz wszelkie skojarzone metadane będą dziedziczone przez wszystkie klasy implementującej. Interfejs sam nie będą dostępne w ramach jednak.  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>Atrybuty niestandardowe eksportu  
 Atrybuty eksportu podstawowych `Export` i `InheritedExport`, może zostać rozszerzony do zawierać metadane jako właściwości atrybutów. Ta metoda jest przydatna do stosowania metadanych podobne do wielu części lub tworzenia drzewa dziedziczenia atrybutów metadanych.  
  
 Typ kontraktu, Nazwa kontraktu lub inne metadane, można określić atrybutu niestandardowego. Aby zdefiniować atrybutu niestandardowego dziedziczenia z klasy `ExportAttribute` (lub `InheritedExportAttribute`) musi być dekorowane za `MetadataAttribute` atrybutu. Następujące klasy definiuje atrybutu niestandardowego.  
  
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
  
 Ta klasa definiuje atrybut niestandardowy o nazwie `MyAttribute` o typie kontraktu `IMyData` i niektóre metadanych o nazwie `MyMetadata`. Wszystkie właściwości w klasie oznaczonej `MetadataAttribute` atrybutu są uważane za metadanych zdefiniowanych w atrybucie niestandardowym. Następujące dwa deklaracje są równoważne.  
  
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
  
 W pierwszej deklaracji typ kontraktu i metadane są zdefiniowane. W drugim deklaracji typu kontraktu i metadanych wynikają z atrybutów niestandardowych. Szczególnie w przypadku, gdy dużej ilości metadanych identyczne musi odnosić się do wielu części (na przykład autora lub informacje o prawach autorskich) za pomocą atrybutu niestandardowego można zapisać dużo czasu i dublowania. Ponadto można utworzyć drzewa dziedziczenia atrybutów niestandardowych umożliwiające zmian.  
  
 Aby utworzyć opcjonalne metadane w atrybucie niestandardowym, należy użyć `DefaultValue` atrybutu. Ten atrybut jest stosowany do właściwości w klasie Atrybut niestandardowy, określa się że ozdobione właściwość jest opcjonalna i nie ma być dostarczane przez eksportera. Jeśli nie podano wartości dla właściwości, zostanie do niej przypisana wartość domyślna dla tego typu właściwości (zazwyczaj `null`, `false`, lub równa 0.)  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>Tworzenie zasad  
 W przypadku części określa importowania i kompozycji jest wykonywane, kontener kompozycji próbuje odnaleźć eksportu zgodnego. Importuj z eksportu pasujący pomyślnie, importowania elementu członkowskiego jest ustawione na wystąpienie eksportowanego obiektu. Skąd pochodzą to wystąpienie jest kontrolowany przez eksportowanie części *zasady tworzenia*.  
  
 Są dwie zasady może spowodować powstanie *udostępnionego* i *nieudostępnione*. Z zasadami tworzenia częścią udostępnionego będzie udostępniać każdego importu w kontenerze części z tej Umowy. Gdy aparat kompozycji znalezienia dopasowania i ustawić wartość właściwości importowania, zostanie on wystąpienia nową kopię części tylko wtedy, gdy jeszcze nie istnieje; w przeciwnym razie poda istniejącą kopię. Oznacza to, że wiele obiektów może mieć odwołania do tej samej części. Takie części nie należy polegać na stan wewnętrzny, który może ulec zmianie w wielu miejscach. Ta zasada jest odpowiednia dla części statycznych, części, które udostępniają usługi i części używające dużej ilości pamięci lub innych zasobów.  
  
 Części z zasadami tworzenia nieudostępnione zostanie utworzona za każdym razem, gdy znajduje dopasowywania importu dla jednego z jego eksportu. W związku z tym będzie można utworzyć wystąpienia nową kopię dla każdego importu w kontenerze, który pasuje do jednej części wyeksportowanego kontraktów. Wewnętrzny stan klasy te kopie nie będą udostępniane. Ta zasada jest odpowiednia dla elementów, których każdej operacji importowania wymaga własnego stan wewnętrzny.  
  
 Zarówno importu i eksportu można określić zasady tworzenia części, spośród wartości `Shared`, `NonShared`, lub `Any`. Wartość domyślna to `Any` zarówno importuje i eksportuje. Export, która określa `Shared` lub `NonShared` spowoduje dopasowanie tylko importu, który określa takie same, lub Określa `Any`. Podobnie, import, która określa `Shared` lub `NonShared` spowoduje dopasowanie tylko eksportu, który określa takie same lub określający `Any`. Importu i eksportu z niezgodną tworzenia zasady nie są uznawane za zgodne, w taki sam sposób jak importu i eksportu, którego nazwa lub kontrakt typ kontraktu nie są dopasowania. Jeśli określono zarówno importowanie i eksportowanie `Any`, lub nie określaj zasadę tworzenia i domyślnie `Any`, domyślnie zostanie ustawiona do udostępnionego zasady tworzenia.  
  
 W poniższym przykładzie pokazano zarówno importuje i eksportuje określania zasad tworzenia. `PartOne`nie określono zasadę tworzenia, wartość domyślna to `Any`. `PartTwo`nie określono zasadę tworzenia, wartość domyślna to `Any`. Ponieważ zarówno importowanie i eksportowanie domyślną `Any`, `PartOne` zostaną udostępnione. `PartThree`Określa `Shared` Tworzenie zasad, więc `PartTwo` i `PartThree` współużytkują tę samą kopię `PartOne`. `PartFour`Określa `NonShared` Tworzenie zasad, więc `PartFour` będzie nieudostępnione w `PartFive`. `PartSix`Określa `NonShared` tworzenia zasad. `PartFive`i `PartSix` każdego otrzymają osobne kopie `PartFour`. `PartSeven`Określa `Shared` tworzenia zasad. Ponieważ istnieje nr wyeksportowane `PartFour` z zasadami tworzenia `Shared`, `PartSeven` importu nie jest zgodna z niczego i nie zostanie wypełnione.  
  
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
 Ponieważ części znajdują się w kontenerze kompozycji, ich cyklu życia mogą być bardziej skomplikowane niż zwykłe obiektów. Części można zaimplementować dwa interfejsy ważne związanych z cyklem życia: `IDisposable` i `IPartImportsSatisfiedNotification`.  
  
 Części, które wymagają pracy do wykonania w zamykania w dół lub wymagające zwolnić zasoby powinny implementować `IDisposable`, jak zwykle dla obiektów .NET Framework. Jednak ponieważ kontenera tworzy i obsługuje odwołań do części, kontenera, który jest właścicielem części powinny wywoływać `Dispose` dla niego metodę. Implementuje sam pojemnik `IDisposable`i jako część jej czyszczenie w `Dispose` zostanie wywołany `Dispose` na części, których jest właścicielem. Z tego powodu należy zawsze usunąć kontener kompozycji podczas jego i żadnych części, który jest właścicielem nie są już potrzebne.  
  
 Kontenery długotrwałe kompozycji użycie pamięci przez części z zasadami tworzenia nieudostępnione może stać się problem. Te częściami nieudostępnionymi można tworzyć wiele razy i nie będzie usunięty, dopóki sam pojemnik zostanie usunięty. Aby poradzić sobie z tym, zapewnia kontener `ReleaseExport` metody. Wywołanie tej metody w eksportu nieudostępnione usuwa tego eksportu z kontenera kompozycji i usuwa go. Elementy, które są używane tylko usunięte eksportu, i tak dalej niżej na drzewie są również usuwane i usunięty. W ten sposób można odzyskać zasoby bez usuwania samego kontenera kompozycji.  
  
 `IPartImportsSatisfiedNotification`zawiera jedną metodę o nazwie `OnImportsSatisfied`. Ta metoda jest wywoływana przez kontener kompozycji na żadnych części, które implementują interfejs, gdy kompozycja została ukończona i Importy części są gotowe do użycia. Elementy są tworzone przez aparat kompozycji do wypełnienia importów z innymi częściami. Przed zestawu importów części nie może wykonać inicjowanie zależy od lub manipuluje importowanych wartości w Konstruktorze części, chyba że te wartości zostały określone jako wymagania wstępne przy użyciu `ImportingConstructor` atrybutu. Zazwyczaj jest to preferowana metoda, ale w niektórych przypadkach iniekcji konstruktora nie mogą być dostępne. W takich przypadkach można wykonać inicjowania w `OnImportsSatisfied`, a część powinny implementować `IPartImportsSatisfiedNotification`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wideo Channel 9: Otwarcie aplikacji przy użyciu Managed Extensibility Framework](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [Wideo Channel 9: Managed Extensibility Framework (MEF) 2.0](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
