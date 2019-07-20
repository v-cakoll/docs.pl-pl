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
ms.openlocfilehash: bed67019fdd3bb81585d08349715a895dfe5a681
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363960"
---
# <a name="attributed-programming-model-overview-mef"></a>Omówienie modelu programowania opartego na atrybutach (MEF)

W Managed Extensibility Framework (MEF) *model programowania* jest konkretną metodą definiowania zestawu obiektów koncepcyjnych, na których MEF działa. Te obiekty koncepcyjne obejmują części, Importy i eksporty. MEF używa tych obiektów, ale nie określa sposobu ich reprezentowania. W związku z tym możliwe jest szeroką gamę modeli programowania, w tym dostosowane modele programowania.

Domyślny model programowania używany w MEF to *model programowania*z atrybutami. W przypadku częściowych modeli programowania, Importy, eksporty i inne obiekty są definiowane przy użyciu atrybutów, które dekorowaćą zwykłe klasy .NET Framework. W tym temacie wyjaśniono, jak używać atrybutów dostarczonych przez model programowania z atrybutami do tworzenia aplikacji MEF.

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a>Importowanie i eksportowanie podstawowych podstaw

*Eksport* jest wartością, którą część dostarcza do innych części w kontenerze, a *Import* jest wymaganym przez część, która ma zostać wypełniona z dostępnych eksportów. W modelu programowania z atrybutami import i eksporty są deklarowane przez klasy dekorowania nazwy lub elementy członkowskie `Import` z `Export` atrybutami i. Atrybut może dekorować klasę, pole, właściwość lub metodę, `Import` podczas gdy atrybut może dekorować pole, właściwość lub parametr konstruktora. `Export`

Aby import został dopasowany do eksportu, importowanie i eksportowanie musi mieć ten sam *kontrakt*. Umowa składa się z ciągu, zwanego *nazwą kontraktu*, i typu wyeksportowanego lub zaimportowanego obiektu, zwanego *typem kontraktu*. Tylko wtedy, gdy zarówno Nazwa kontraktu, jak i typ kontraktu są uważane za wyeksportowanie w celu spełnienia określonego importu.

Jeden lub oba parametry kontraktu mogą być niejawne lub jawne. Poniższy kod przedstawia klasę, która deklaruje import podstawowy.

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

W przypadku tego importu `Import` atrybut nie ma typu kontraktu ani dołączonego parametru nazwy kontraktu. W związku z tym oba zostaną wywnioskowane z właściwości dekoracyjnej. W takim przypadku typem kontraktu będzie `IMyAddin`, a nazwa kontraktu będzie unikatowym ciągiem utworzonym na podstawie typu kontraktu. (Innymi słowy Nazwa kontraktu będzie odpowiadać wyłącznie eksportom, których nazwy są również wywnioskowane z typu `IMyAddin`).

Poniżej przedstawiono eksport pasujący do poprzedniego importu.

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

W przypadku tego eksportu typ kontraktu to `IMyAddin` , ponieważ jest określony jako parametr `Export` atrybutu. Wyeksportowany typ musi być taki sam jak typ kontraktu, pochodzić od typu kontraktu lub implementować typ kontraktu, jeśli jest to interfejs. W tym wywozie rzeczywisty typ `MyLogger` implementuje interfejs. `IMyAddin` Nazwa kontraktu jest wywnioskowana z typu kontraktu, co oznacza, że ten eksport będzie pasował do poprzedniego importu.

> [!NOTE]
> Eksporty i Importy powinny być zwykle deklarowane dla publicznych klas lub członków. Inne deklaracje są obsługiwane, ale Eksportowanie lub importowanie prywatnego, chronionego lub wewnętrznego elementu członkowskiego dzieli model izolacji części i dlatego nie jest zalecane.

Typ kontraktu musi dokładnie pasować do eksportu i importu, aby można go było uznać za dopasowanie. Rozważmy następujący eksport.

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

W przypadku tego eksportu typ kontraktu to `MyLogger` `IMyAddin`zamiast. Mimo że `MyLogger` implementuje `IMyAddin`i dlatego `IMyAddin` może być rzutowane do obiektu, ten eksport nie będzie pasował do poprzedniego importu, ponieważ typy kontraktu nie są takie same.

Ogólnie rzecz biorąc nie trzeba określać nazwy kontraktu, a większość kontraktów powinna być zdefiniowana na podstawie typu kontraktu i metadanych. Jednak w pewnych okolicznościach ważne jest bezpośrednie określenie nazwy kontraktu. Najczęstszym przypadkiem jest to, że Klasa eksportuje kilka wartości, które współużytkują wspólny typ, takich jak elementy pierwotne. Nazwę kontraktu można określić jako pierwszy parametr `Import` atrybutu lub. `Export` Poniższy kod przedstawia import i eksport z określoną nazwą `MajorRevision`kontraktu.

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

Jeśli typ kontraktu nie zostanie określony, będzie on nadal wywnioskowany na podstawie typu importu lub eksportu. Jednak nawet jeśli nazwa kontraktu jest określona jawnie, typ kontraktu musi również pasować dokładnie do importu i eksportu, aby można go było uznać za dopasowanie. Na przykład, jeśli `MajorRevision` pole było ciągiem, wywnioskowane typy kontraktu nie będą zgodne, a eksport nie jest zgodny z importem, mimo że ma tę samą nazwę kontraktu.

### <a name="importing-and-exporting-a-method"></a>Importowanie i eksportowanie metody

Ten `Export` atrybut może również dekorować metodę w taki sam sposób jak Klasa, właściwość lub funkcja. Eksporty metod muszą określać typ kontraktu lub nazwę kontraktu, ponieważ nie można wywnioskować typu. Określony typ może być niestandardowym delegatem lub typem ogólnym, takim jak `Func`. Następująca Klasa eksportuje metodę o nazwie `DoSomething`.

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

W tej klasie `DoSomething` Metoda przyjmuje jeden `int` parametr i zwraca `string`. Aby można było dopasować ten eksport, część importująca musi deklarować odpowiedni element członkowski. Następująca Klasa importuje `DoSomething` metodę.

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

Aby uzyskać więcej informacji o sposobach korzystania z `Func<T, T>` obiektu, zobacz <xref:System.Func%602>.

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a>Typy importów

MEF obsługuje kilka typów importu, w tym dynamiczne, opóźnione, wymagania wstępne i opcjonalne.

### <a name="dynamic-imports"></a>Importy dynamiczne

W niektórych przypadkach Klasa importowania może chcieć dopasować eksporty dowolnego typu, który ma określoną nazwę kontraktu. W tym scenariuszu Klasa może deklarować *Import dynamiczny*. Następujący import pasuje do dowolnego eksportu z nazwą kontraktu "TheString".

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

Gdy typ kontraktu jest wywnioskowany na podstawie `dynamic` słowa kluczowego, będzie pasować do dowolnego typu kontraktu. W takim przypadku import powinien **zawsze** określać nazwę kontraktu do dopasowania. (Jeśli nazwa kontraktu nie zostanie określona, importowanie zostanie uznane za niezgodne z eksportami). Oba poniższe eksporty byłyby zgodne z poprzednim importowaniem.

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

Oczywiście Importowanie klasy musi być przygotowana do działania z obiektem dowolnego typu.

### <a name="lazy-imports"></a>Importy z opóźnieniem

W niektórych przypadkach Klasa import może wymagać pośredniego odwołania do zaimportowanego obiektu, tak aby obiekt nie został utworzony jako natychmiast. W tym scenariuszu Klasa może deklarować import z *opóźnieniem* przy użyciu typu `Lazy<T>`kontraktu. Następująca właściwość importowania deklaruje import z opóźnieniem.

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

Z punktu widzenia aparatu kompozycji typ `Lazy<T>` kontraktu jest uznawany za identyczny z `T`typem kontraktu. W związku z tym poprzedni import będzie pasował do poniższego eksportu.

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

Nazwę kontraktu i typ kontraktu można określić w `Import` atrybucie dla importu z opóźnieniem, zgodnie z wcześniejszym opisem w sekcji "podstawowe Importy i eksporty".

### <a name="prerequisite-imports"></a>Importy wymagań wstępnych

Wyeksportowane części MEF są zwykle tworzone przez aparat kompozycji, w odpowiedzi na bezpośrednie żądanie lub potrzebę wypełnienia dopasowanego importu. Domyślnie podczas tworzenia części aparat kompozycji używa konstruktora bez parametrów. Aby aparat używał innego konstruktora, można oznaczyć go `ImportingConstructor` atrybutem.

Każda część może mieć tylko jeden Konstruktor do użytku przez aparat kompozycji. Nie ma żadnego konstruktora bez parametrów ani `ImportingConstructor` atrybutu lub nie zawiera więcej niż jednego `ImportingConstructor` atrybutu, spowoduje wystąpienie błędu.

Aby wypełnić parametry konstruktora oznaczonego `ImportingConstructor` atrybutem, wszystkie te parametry są automatycznie deklarowane jako Importy. Jest to wygodny sposób deklarowania importu, które są używane podczas inicjowania części. Następująca Klasa używa `ImportingConstructor` do deklarowania importu.

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
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

    //Parameterless constructor will NOT be
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

Domyślnie `ImportingConstructor` atrybut używa wnioskowanych typów kontraktu i nazw kontraktów dla wszystkich importowanych parametrów. Można to zastąpić, dekorowania nazwy parametry z `Import` atrybutami, a następnie jawnie zdefiniować typ kontraktu i nazwę kontraktu. Poniższy kod demonstruje konstruktora, który używa tej składni do importowania klasy pochodnej zamiast klasy nadrzędnej.

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

W szczególności należy zachować ostrożność przy użyciu parametrów kolekcji. `ImportingConstructor` Na przykład jeśli określisz dla konstruktora z parametrem typu `IEnumerable<int>`, import będzie zgodny z pojedynczym eksportem typu `IEnumerable<int>`, a nie z zestawem eksportów typu `int`. Aby dopasować zestaw eksportów typu `int`, należy dekorować parametr `ImportMany` z atrybutem.

Parametry zadeklarowane jako Importy `ImportingConstructor` przez atrybut są również oznaczone jako *Importy wymagań wstępnych*. MEF zwykle zezwala na Eksporty i Importy w celu utworzenia *cyklu*. Na przykład cykl polega na tym, że obiekt A importuje obiekt B, który z kolei importuje obiekt A. W normalnych warunkach cykl nie jest problemem, a kontener kompozycji konstruuje oba obiekty w normalny sposób.

Gdy importowana wartość jest wymagana przez konstruktora części, ten obiekt nie może uczestniczyć w cyklu. Jeśli obiekt A wymaga skonstruowania obiektu B, zanim będzie mógł być skonstruowany, a obiekt B importuje obiekt A, cykl nie będzie mógł zostać rozpoznany i wystąpi błąd kompozycji. Importy zadeklarowane w parametrach konstruktorów są dlatego Importy wymagające wymagań wstępnych, które muszą zostać wypełnione przed wszelkimi eksportami z obiektu, który go wymaga.

### <a name="optional-imports"></a>Importy opcjonalne

Ten `Import` atrybut określa wymaganie części do działania. Jeśli nie można spełnić importu, kompozycja tej części zakończy się niepowodzeniem, a część nie będzie dostępna.

Można określić, że import jest *opcjonalny* przy użyciu `AllowDefault` właściwości. W takim przypadku kompozycja powiedzie się, nawet jeśli import nie jest zgodny z żadnym dostępnym eksportem, a właściwość import zostanie ustawiona na wartość domyślną dla tego typu właściwości`null` (dla właściwości obiektu `false` , dla wartości logicznych lub zero dla wartości numerycznych Właściwości.) W poniższej klasie jest stosowane opcjonalne importowanie.

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

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a>Importowanie wielu obiektów

Ten `Import` atrybut zostanie utworzony pomyślnie tylko wtedy, gdy pasuje do jednego i tylko jeden eksport. Inne przypadki spowodują powstanie błędu kompozycji. Aby zaimportować więcej niż jeden eksport zgodny z tym samym kontraktem, użyj `ImportMany` atrybutu. Importy oznaczone przy użyciu tego atrybutu są zawsze opcjonalne. Na przykład kompozycja nie powiedzie się, jeśli nie ma pasujących eksportów. Następująca Klasa importuje dowolną liczbę eksportów typu `IMyAddin`.

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

Dostęp do zaimportowanej tablicy można uzyskać przy `IEnumerable<T>` użyciu zwykłej składni i metod. Istnieje również możliwość użycia zwykłej tablicy (`IMyAddin[]`).

Ten wzorzec może być bardzo istotny, gdy jest używany w połączeniu z `Lazy<T>` składnią. Na przykład przy użyciu `ImportMany`, `IEnumerable<T>`, i `Lazy<T>`, można zaimportować odwołania pośrednie do dowolnej liczby obiektów i utworzyć tylko te, które staną się niezbędne. W poniższej klasie przedstawiono ten wzorzec.

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

W niektórych przypadkach może być konieczne uniemożliwienie wykrycia części jako części wykazu. Na przykład część może być klasą bazową, która ma być dziedziczona z, ale nie jest używana. Istnieją dwa sposoby osiągnięcia tego celu. Najpierw można użyć `abstract` słowa kluczowego dla klasy części. Klasy abstrakcyjne nigdy nie zapewniają eksportów, chociaż mogą zapewnić dziedziczone eksporty do klas, które pochodzą z nich.

Jeśli Klasa nie może być abstrakcyjna, można ją dekorować z `PartNotDiscoverable` atrybutem. Część dekoracyjna z tym atrybutem nie zostanie uwzględniona w żadnym wykazie. Poniższy przykład ilustruje te wzorce. `DataOne`zostaną odnalezione przez wykaz. Ponieważ `DataTwo` jest abstrakcyjny, nie zostanie odnaleziony. `DataThree` Ponieważ`PartNotDiscoverable` użyto atrybutu, nie zostanie on odnaleziony.

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

## <a name="metadata-and-metadata-views"></a>Widoki metadanych i metadanych

Eksporty mogą dostarczyć dodatkowe informacje o sobie znane jako *metadane*. Metadane mogą służyć do przekazywania właściwości eksportowanego obiektu do części importującej. Część importująca może używać tych danych do decydowania, które eksporty mają być używane, lub do zbierania informacji na temat eksportu bez konieczności konstruowania go. Z tego powodu import musi być opóźniony, aby można było używać metadanych.

Aby użyć metadanych, zazwyczaj deklaruje interfejs znany jako *widok metadanych*, który deklaruje, jakie metadane będą dostępne. Interfejs widoku metadanych musi mieć tylko właściwości, a te właściwości muszą mieć `get` metody dostępu. Poniższy interfejs to przykładowy widok metadanych.

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

Istnieje również możliwość użycia kolekcji ogólnej, `IDictionary<string, object>`jako widoku metadanych, ale w ten sposób można uniknąć korzystania z sprawdzania typów i należy unikać.

Zwykle wszystkie właściwości o nazwie w widoku metadanych są wymagane, a wszelkie eksporty, które ich nie zapewniają, nie będą uważane za dopasowanie. Ten `DefaultValue` atrybut określa, że właściwość jest opcjonalna. Jeśli właściwość nie jest uwzględniona, zostanie przypisana wartość domyślna określona jako parametr `DefaultValue`. Poniżej znajdują się dwie różne klasy z metadanymi. Obie te klasy byłyby zgodne z poprzednim widokiem metadanych.

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

Metadane są wyrażane po `Export` atrybucie przy `ExportMetadata` użyciu atrybutu. Każda część metadanych składa się z pary nazwa/wartość. Część nazwy metadanych musi być zgodna z nazwą odpowiedniej właściwości w widoku metadanych, a wartość zostanie przypisana do tej właściwości.

Jest importerem, który określa, jaki widok metadanych (jeśli istnieje) będzie używany. Import z metadanymi jest zadeklarowany jako import z opóźnieniem, z interfejsem metadanych jako drugi parametr typu do `Lazy<T,T>`. Następująca Klasa importuje poprzednią część z metadanymi.

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

W wielu przypadkach należy połączyć metadane z `ImportMany` atrybutem, aby przeanalizować przez dostępne Importy i wybrać i utworzyć wystąpienie tylko jednego lub odfiltrować kolekcję w celu dopasowania do określonego warunku. Następująca Klasa tworzy wystąpienia tylko `IPlugin` obiektów, które `Name` mają wartość "rejestrator".

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

Jeśli klasa dziedziczy po części, ta klasa może być również częścią. Importy są zawsze dziedziczone przez podklasy. W związku z tym, podklasa części zawsze będzie częścią, z tym samym importem, który jest klasą nadrzędną.

Eksporty zadeklarowane przy `Export` użyciu atrybutu nie są dziedziczone przez podklasy. Jednak część może eksportować sam siebie przy użyciu `InheritedExport` atrybutu. Podklasy części będą dziedziczyć i udostępniać te same eksporty, w tym nazwy kontraktu i typu kontraktu. W przeciwieństwie `Export` do atrybutu `InheritedExport` , można stosować tylko na poziomie klasy, a nie na poziomie elementu członkowskiego. W związku z tym eksport na poziomie elementu członkowskiego nie może być nigdy dziedziczony.

Poniższe cztery klasy przedstawiają zasady importowania i eksportowania dziedziczenia. `NumTwo`dziedziczy z `NumOne`, więc `NumTwo` spowoduje zaimportowanie `IMyData`. Zwykłe eksporty nie są dziedziczone, `NumTwo` dlatego nie eksportuje żadnych elementów. `NumFour`dziedziczy z `NumThree`. Ponieważ `NumThree` jest `InheritedExport`używany ,`NumFour` ma jeden eksport z typem `NumThree`kontraktu. Eksporty na poziomie elementu członkowskiego nigdy nie `IMyData` są dziedziczone, więc nie są eksportowane.

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

Jeśli istnieją metadane skojarzone z `InheritedExport` atrybutem, te metadane również są dziedziczone. (Aby uzyskać więcej informacji, zobacz wcześniejszą sekcję "widoki metadanych i metadanych"). Dziedziczone metadane nie mogą być modyfikowane przez podklasę. Jednak przez ponowne zadeklarowanie `InheritedExport` atrybutu o tej samej nazwie kontraktu i typie kontraktu, ale z nowymi metadanymi, podklasa może zastąpić dziedziczone metadane nowymi metadanymi. W poniższej klasie przedstawiono tę zasadę. Część dziedziczy z `Logger` i zawiera `InheritedExport` atrybut. `MegaLogger` Ponieważ `MegaLogger` ponowne deklarowanie nowych metadanych o nazwie status nie dziedziczy nazwy i wersji `Logger`metadanych.

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

Podczas ponownego deklarowania `InheritedExport` atrybutu w celu przesłaniania metadanych upewnij się, że typy kontraktu są takie same. (W poprzednim przykładzie `IPlugin` jest typem kontraktu). Jeśli różnią się one zamiast przesłaniać, drugi atrybut utworzy drugi, niezależny eksport od części. Zazwyczaj oznacza to, że trzeba będzie jawnie określić typ kontraktu podczas przesłonięcia `InheritedExport` atrybutu, jak pokazano w poprzednim przykładzie.

Ponieważ interfejsy nie mogą być tworzone bezpośrednio, zazwyczaj nie mogą być dekoracyjne `Export` ani `Import` atrybuty. Jednak interfejs może być uzupełniony `InheritedExport` atrybutem na poziomie interfejsu, a eksportowanie wraz ze wszystkimi skojarzonymi metadanymi będzie dziedziczone przez wszystkie klasy implementujące. Sam interfejs nie będzie jednak dostępny jako część.

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a>Niestandardowe atrybuty eksportu

Podstawowe atrybuty `Export` eksportu i `InheritedExport`, można rozszerzyć w celu uwzględnienia metadanych jako właściwości atrybutów. Ta technika jest przydatna w przypadku stosowania podobnych metadanych do wielu części lub tworzenia drzewa dziedziczenia atrybutów metadanych.

Atrybut niestandardowy może określać typ kontraktu, nazwę kontraktu lub inne metadane. W celu zdefiniowania atrybutu niestandardowego Klasa dziedziczenia z `ExportAttribute` (lub `InheritedExportAttribute`) `MetadataAttribute` musi być uzupełniona atrybutem. Poniższa klasa definiuje atrybut niestandardowy.

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

Ta klasa definiuje niestandardowy atrybut o nazwie `MyAttribute` z typem `IMyData` kontraktu i niektórych metadanych o `MyMetadata`nazwie. Wszystkie właściwości w klasie oznaczonej `MetadataAttribute` atrybutem są uważane za metadane zdefiniowane w atrybucie niestandardowym. Poniższe dwie deklaracje są równoważne.

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

W pierwszej deklaracji typ kontraktu i metadane są jawnie zdefiniowane. W drugiej deklaracji typ kontraktu i metadane są niejawne w dostosowanym atrybucie. Szczególnie w przypadku, gdy należy zastosować dużą ilość identycznych metadanych do wielu części (na przykład informacje o autorze lub prawach autorskich), przy użyciu atrybutu niestandardowego można zaoszczędzić dużo czasu i duplikacji. Ponadto można utworzyć drzewa dziedziczenia atrybutów niestandardowych, aby umożliwić stosowanie odmian.

Aby utworzyć opcjonalne metadane w atrybucie niestandardowym, można użyć `DefaultValue` atrybutu. Gdy ten atrybut jest stosowany do właściwości w klasie atrybutów niestandardowych, określa, że właściwość dekoracyjna jest opcjonalna i nie musi być dostarczana przez eksportera. Jeśli wartość właściwości nie zostanie podana, zostanie przypisana wartość domyślna dla jej typu właściwości (zwykle `null`, `false`lub 0).

<a name="creation_policies"></a>

## <a name="creation-policies"></a>Zasady tworzenia

Gdy część określa Importowanie i składanie jest wykonywane, kontener kompozycji próbuje znaleźć pasujący eksport. Jeśli dopasowanie zostanie zakończone pomyślnie, element członkowski importu jest ustawiany na wystąpienie wyeksportowanego obiektu. Miejsce, z którego pochodzi to wystąpienie, jest kontrolowane przez *zasady tworzenia*części eksportu.

Dwie możliwe zasady tworzenia są *udostępniane* i *nie są udostępniane*. Część z zasadami tworzenia udostępnioną zostanie udostępniona między każdym importem w kontenerze a częścią tego kontraktu. Gdy aparat kompozycji znajdzie dopasowanie i ma ustawić właściwość importowania, utworzy wystąpienie nowej kopii części tylko wtedy, gdy jeszcze nie istnieje; w przeciwnym razie dostarczy istniejącą kopię. Oznacza to, że wiele obiektów może odwoływać się do tej samej części. Takie części nie powinny polegać na stanie wewnętrznym, który można zmienić z wielu miejsc. Te zasady są odpowiednie dla części statycznych, części, które udostępniają usługi, i części, które zużywają wiele pamięci lub innych zasobów.

Część z zasadami tworzenia nieudostępnianych elementów zostanie utworzona za każdym razem, gdy zostanie znaleziony pasujący import dla jednego z jego eksportu. W związku z tym zostanie utworzona nowa kopia dla każdego importu w kontenerze, który jest zgodny z jedną z kontraktów eksportu części. Wewnętrzny stan tych kopii nie zostanie udostępniony. Te zasady są odpowiednie dla części, w których każdy import wymaga własnego stanu wewnętrznego.

Zarówno import, jak i eksport mogą określać zasady tworzenia części, spośród wartości `Shared`, `NonShared`lub `Any`. Wartość domyślna dotyczy `Any` zarówno importu, jak i eksportu. Eksport, który określa `Shared` lub `NonShared` będzie zgodny z importem, który określa ten sam element lub określa `Any`. Analogicznie, importowanie, które `Shared` określa `NonShared` lub będzie zgodne tylko z eksportem, który określa ten sam lub `Any`określa. Importy i eksporty z niezgodnymi zasadami tworzenia nie są uważane za pasujące w taki sam sposób jak Importowanie i eksportowanie, których nazwa kontraktu lub typ kontraktu nie są zgodne. Jeśli określono `Any`zarówno opcję importu, jak i eksportu, albo nie określisz zasad tworzenia i `Any`domyślną wartością, zasady tworzenia zostaną domyślnie udostępnione.

W poniższym przykładzie pokazano import i eksporty określające zasady tworzenia. `PartOne`nie określa zasad tworzenia, dlatego wartość domyślna to `Any`. `PartTwo`nie określa zasad tworzenia, dlatego wartość domyślna to `Any`. Ponieważ wartości domyślne `Any` `PartOne` importu i eksportu są udostępniane. `PartThree`Określa zasady `Shared` `PartOne`tworzenia `PartTwo` i`PartThree` będzie współużytkować tę samą kopię programu. `PartFour`Określa zasady `PartFour` tworzenia, dlatego nie będą udostępniane w programie `PartFive`. `NonShared` `PartSix`Określa zasady `NonShared` tworzenia. `PartFive`i `PartSix` otrzymają osobne `PartFour`kopie. `PartSeven`Określa zasady `Shared` tworzenia. Ponieważ nie ma żadnych wyeksportowanych `PartFour` `Shared`zasad tworzenia, `PartSeven` Importowanie nie jest zgodne i nie zostanie wypełnione.

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
    'Since the export's creation policy was explicitly
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
    //Since the export's creation policy was explicitly
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

## <a name="life-cycle-and-disposing"></a>Cykl życia i usuwanie

Ponieważ części są hostowane w kontenerze kompozycji, ich cykl życia może być bardziej skomplikowany niż zwykłe obiekty. Części mogą zaimplementować dwa ważne interfejsy związane z cyklem życia `IDisposable` : `IPartImportsSatisfiedNotification`i.

Części, które wymagają pracy do wykonania przy zamykaniu lub które wymagają zwolnienia zasobów, powinny być `IDisposable`implementowane w sposób typowy dla .NET Framework obiektów. Jednak ponieważ kontener tworzy i zachowuje odwołania do części, tylko kontener, do którego należy część, powinien wywołać `Dispose` metodę. Sam kontener implementuje `IDisposable`, a jako część jego oczyszczania w `Dispose` tym elemencie zostanie wywołana `Dispose` wszystkie części, które jest właścicielem. Z tego powodu zawsze należy usunąć kontener kompozycji, gdy nie są już potrzebne wszystkie jego części.

W przypadku kontenerów o długim okresie ważności użycie pamięci przez części z zasadami tworzenia nieudostępnianych może stać się problemem. Te części nieudostępnione mogą być tworzone wiele razy i nie zostaną usunięte do momentu usunięcia kontenera. W tym celu kontener udostępnia `ReleaseExport` metodę. Wywołanie tej metody w wywozie nieudostępnionym spowoduje usunięcie tego eksportu z kontenera kompozycji i usunięcia go. Części, które są używane tylko przez usunięty eksport, i tak dalej na drzewie, również zostaną usunięte i usunięte. W ten sposób zasoby mogą być odzyskiwane bez usuwania kontenera kompozycji.

`IPartImportsSatisfiedNotification`zawiera jedną metodę o `OnImportsSatisfied`nazwie. Ta metoda jest wywoływana przez kontener kompozycji dla każdej części implementującej interfejs, gdy kompozycja została ukończona, a Importy części są gotowe do użycia. Części są tworzone przez aparat kompozycji, aby wypełnić Importy innych części. Przed ustawieniem importu części nie można wykonać inicjalizacji, która polega na zaimportowaniu wartości i manipulowaniu nimi w konstruktorze częściowym, chyba że te wartości zostały określone jako wymagania wstępne przy użyciu `ImportingConstructor` atrybutu. Zwykle jest to preferowana metoda, ale w niektórych przypadkach iniekcja konstruktora może być niedostępna. W takich przypadkach Inicjalizacja może być wykonywana w `OnImportsSatisfied`, a część powinna zostać zaimplementowana. `IPartImportsSatisfiedNotification`

## <a name="see-also"></a>Zobacz także

- [Wideo Channel 9: Otwórz aplikacje za pomocą Managed Extensibility Framework](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [Wideo Channel 9: Managed Extensibility Framework (MEF) 2,0](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
