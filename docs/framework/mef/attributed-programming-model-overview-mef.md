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
ms.openlocfilehash: baa66f11404e2cee83b4d4b32ba02544c9438d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="4d81f-102">Omówienie modelu programowania opartego na atrybutach (MEF)</span><span class="sxs-lookup"><span data-stu-id="4d81f-102">Attributed Programming Model Overview (MEF)</span></span>
<span data-ttu-id="4d81f-103">W Managed Extensibility Framework (MEF), *model programowania* jest określonego sposobu definiowania zestawu obiektów pojęciach, na których działa MEF.</span><span class="sxs-lookup"><span data-stu-id="4d81f-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="4d81f-104">Te obiekty koncepcyjnej obejmują części, importu i eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="4d81f-105">MEF używa tych obiektów, ale nie określa, jak powinny być reprezentowane.</span><span class="sxs-lookup"><span data-stu-id="4d81f-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="4d81f-106">W związku z tym szerokiej gamy modele programowania są możliwe, w tym dostosowane modele programowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>  
  
 <span data-ttu-id="4d81f-107">Wartość domyślna jest model programowania używany w MEF *model programowania opartego na atrybutach*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="4d81f-108">Oparte na atrybutach części modelu programowania Importy, eksportów i inne obiekty są zdefiniowane z atrybutów, które dekoracji zwykłej klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d81f-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="4d81f-109">W tym temacie wyjaśniono, jak używać atrybutów oparte na atrybutach model programowania do tworzenia aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="4d81f-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a><span data-ttu-id="4d81f-110">Importowanie i eksportowanie podstawy</span><span class="sxs-lookup"><span data-stu-id="4d81f-110">Import and Export Basics</span></span>  
 <span data-ttu-id="4d81f-111">*Wyeksportować* to wartość, która zawiera części do innych części w kontenerze, oraz *zaimportować* jest wymagane określającym części w kontenerze, należy podać z dostępnych eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="4d81f-112">W modelu programowania oparte na atrybutach importu i eksportu są zadeklarowane przez dekoracji klas lub członków z `Import` i `Export` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="4d81f-113">`Export` Atrybut można dekoracji klasy, pola, właściwości lub metody, gdy `Import` atrybut można dekoracji parametr pola, właściwości lub konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4d81f-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>  
  
 <span data-ttu-id="4d81f-114">Importowanie i eksportowanie można dopasować, importowanie i eksportowanie musi mieć takie same *kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="4d81f-115">Kontrakt składa się z ciągu o nazwie *Nazwa kontraktu*i typ obiektu wyeksportowane lub zaimportowane, nazywany *typu kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="4d81f-116">Tylko wtedy, gdy nazwę kontraktu i kontraktu wpisz dopasowania eksportu uważa się spełnienia określonego importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>  
  
 <span data-ttu-id="4d81f-117">Jeden lub oba parametry kontrakt może być jawnych ani niejawnych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="4d81f-118">Poniższy kod przedstawia klasę, która deklaruje podstawowe importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-118">The following code shows a class that declares a basic import.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-119">Podczas importowania `Import` atrybut nie ma typ kontraktu ani został dołączony parametr nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="4d81f-120">W związku z tym zarówno będzie można wywnioskować na podstawie właściwości dekorowany.</span><span class="sxs-lookup"><span data-stu-id="4d81f-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="4d81f-121">W takim przypadku typ kontraktu będzie `IMyAddin`, a Nazwa kontraktu będą unikatowy ciąg utworzone na podstawie typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="4d81f-122">(Innymi słowy, Nazwa kontraktu jest zgodny tylko eksportu, których nazwy są również wywnioskować na podstawie typu `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="4d81f-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>  
  
 <span data-ttu-id="4d81f-123">Poniżej przedstawiono Eksport zgodny poprzedniej importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-123">The following shows an export that matches the previous import.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-124">W tym eksportu jest typ kontraktu `IMyAddin` ponieważ jest on parametr `Export` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="4d81f-125">Wyeksportowanego typu musi być albo taki sam jak typ kontraktu, pochodzi z typu kontraktu lub implementować typ kontraktu, jeśli jest to interfejs.</span><span class="sxs-lookup"><span data-stu-id="4d81f-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="4d81f-126">W tym eksportu, rzeczywisty typ `MyLogger` implementuje interfejs `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="4d81f-127">Nazwa kontraktu jest wywnioskowany na podstawie typu kontraktu, co oznacza, że tego eksportu będzie odpowiadała poprzedniej importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d81f-128">Zazwyczaj eksportów i importów powinny zostać zadeklarowane w publicznych klas lub członków.</span><span class="sxs-lookup"><span data-stu-id="4d81f-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="4d81f-129">Inne deklaracje są obsługiwane, ale eksportowanie lub importowanie prywatnych, chronionych lub wewnętrzny elementu członkowskiego przerywa model izolacji części i dlatego nie jest zalecana.</span><span class="sxs-lookup"><span data-stu-id="4d81f-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>  
  
 <span data-ttu-id="4d81f-130">Typ kontraktu musi odpowiadać dokładnie do eksportowania i importowania, aby być uznawane za zgodne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="4d81f-131">Należy wziąć pod uwagę następujące eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-131">Consider the following export.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-132">W tym eksportu jest typ kontraktu `MyLogger` zamiast `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="4d81f-133">Mimo że `MyLogger` implementuje `IMyAddin`i może być rzutowane na `IMyAddin` obiekt tego eksportu nie będzie odpowiadała poprzedniej importowania, ponieważ typy kontraktu nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="4d81f-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>  
  
 <span data-ttu-id="4d81f-134">Ogólnie rzecz biorąc nie jest konieczne określić nazwę kontraktu i kontrakty większości powinien być zdefiniowany typ kontraktu i metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="4d81f-135">Jednak w pewnych okolicznościach, należy określić nazwę kontraktu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="4d81f-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="4d81f-136">Najbardziej często zdarza się, gdy klasa eksportuje kilka wartości, które mają wspólny typ, takich jak podstawowych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="4d81f-137">Nazwa kontraktu można określić jako pierwszy parametr `Import` lub `Export` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="4d81f-138">Poniższy kod przedstawia importu i eksportu przy użyciu nazwy określonej kontraktu `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-139">Jeśli nie określono typu kontraktu, nadal będzie można wywnioskować z typu importu lub eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="4d81f-140">Jednak nawet wtedy, gdy nazwa kontraktu określono jawnie, typ kontraktu musi być również zgodna dokładnie dla importu i eksportu, aby być uznawane za zgodne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="4d81f-141">Na przykład jeśli `MajorRevision` pole jest ciągiem, czy niezgodne typy kontraktu wnioskowany i eksportowania będzie niezgodna importu, pomimo o tej samej nazwie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>  
  
### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="4d81f-142">Importowanie i eksportowanie — metoda</span><span class="sxs-lookup"><span data-stu-id="4d81f-142">Importing and Exporting a Method</span></span>  
 <span data-ttu-id="4d81f-143">`Export` Atrybut można również dekoracji metody, w taki sam sposób jak klasy, właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="4d81f-144">Eksporty — metoda należy określić typ kontraktu lub Nazwa kontraktu, ponieważ nie można wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="4d81f-145">Określony typ może być niestandardowych delegata lub typu ogólnego, takich jak `Func`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="4d81f-146">Następujące klasy eksportuje metodę o nazwie `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-146">The following class exports a method named `DoSomething`.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-147">W tej klasie `DoSomething` metoda przyjmuje jeden `int` parametrów i zwraca `string`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="4d81f-148">Aby dopasować tego eksportu, importowania części musi zadeklarować właściwego członka.</span><span class="sxs-lookup"><span data-stu-id="4d81f-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="4d81f-149">Następujące klasy importów `DoSomething` metody.</span><span class="sxs-lookup"><span data-stu-id="4d81f-149">The following class imports the `DoSomething` method.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-150">Aby uzyskać więcej informacji o korzystaniu z `Func<T, T>` obiektów, zobacz <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="4d81f-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a><span data-ttu-id="4d81f-151">Typy importów</span><span class="sxs-lookup"><span data-stu-id="4d81f-151">Types of Imports</span></span>  
 <span data-ttu-id="4d81f-152">Wsparcie MEF kilka zaimportować typy w tym dynamiczne, z opóźnieniem, wstępnie wymagane i opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>  
  
### <a name="dynamic-imports"></a><span data-ttu-id="4d81f-153">Importy dynamiczne</span><span class="sxs-lookup"><span data-stu-id="4d81f-153">Dynamic Imports</span></span>  
 <span data-ttu-id="4d81f-154">W niektórych przypadkach importowania klasy może być zgodne eksportuje dowolnego typu, których nazwa umową.</span><span class="sxs-lookup"><span data-stu-id="4d81f-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="4d81f-155">W tym scenariuszu można zadeklarować tej klasy *dynamiczne importu*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="4d81f-156">Importuj następujące odpowiada żadnych eksportu o nazwie kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="4d81f-156">The following import matches any export with contract name "TheString".</span></span>  
  
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
  
 <span data-ttu-id="4d81f-157">Jeśli typ kontraktu jest wywnioskowany na podstawie `dynamic` — słowo kluczowe, będzie odpowiadała dowolny typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="4d81f-158">W takim przypadku należy importu **zawsze** Określ nazwę kontraktu na potrzeby dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="4d81f-159">(Jeśli nazwa kontraktu nie zostanie określona, importowanie uznaje się pasuje do żadnego eksportu.) Oba następujące eksportuje umożliwi dopasowanie poprzedniej importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-160">Oczywiście importowania klasy muszą być przygotowane radzenia sobie z dowolnego typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>  
  
### <a name="lazy-imports"></a><span data-ttu-id="4d81f-161">Importy opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="4d81f-161">Lazy Imports</span></span>  
 <span data-ttu-id="4d81f-162">W niektórych przypadkach klasy importowania może wymagać pośrednie odwołanie do obiektu zaimportowane tak, aby obiekt nie jest od razu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4d81f-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="4d81f-163">W tym scenariuszu można zadeklarować tej klasy *importu opóźnionego* przy użyciu typu kontraktu `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="4d81f-164">Następująca właściwość importowania deklaruje opóźnionego importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-164">The following importing property declares a lazy import.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-165">Z punktu widzenia aparatu kompozycji, typ kontraktu `Lazy<T>` jest uznawany za taki sam jak typ kontraktu `T`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="4d81f-166">W związku z tym poprzedniej importu umożliwi dopasowanie następujące eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-166">Therefore, the previous import would match the following export.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-167">Nazwa kontraktu i typ kontraktu można określać w `Import` atrybutu do opóźnionego importu, zgodnie z wcześniejszym opisem w sekcji "Podstawowe importuje i eksportuje".</span><span class="sxs-lookup"><span data-stu-id="4d81f-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>  
  
### <a name="prerequisite-imports"></a><span data-ttu-id="4d81f-168">Importy wymagań wstępnych</span><span class="sxs-lookup"><span data-stu-id="4d81f-168">Prerequisite Imports</span></span>  
 <span data-ttu-id="4d81f-169">Wyeksportowane części MEF są zwykle tworzone przez aparat kompozycji w odpowiedzi na potrzeby wypełnić dopasowane importu lub bezpośrednie żądania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="4d81f-170">Domyślnie podczas tworzenia części aparat kompozycji używa konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="4d81f-171">Aby aparatu, użyj innego konstruktora, możesz oznaczyć go przy użyciu `ImportingConstructor` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>  
  
 <span data-ttu-id="4d81f-172">Każda część może mieć tylko jeden konstruktor do użycia przez aparat kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="4d81f-173">Brak domyślnego konstruktora i nie `ImportingConstructor` atrybutu lub podając więcej niż jeden `ImportingConstructor` atrybutu, spowoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="4d81f-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>  
  
 <span data-ttu-id="4d81f-174">Aby wypełnić parametry konstruktora oznaczonego jako z `ImportingConstructor` atrybutu, wszystkie te parametry są automatycznie deklarowane jako importowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="4d81f-175">Jest to wygodny sposób, aby zadeklarować Importy, które są używane podczas inicjowania części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="4d81f-176">Następujące klasy używa `ImportingConstructor` Aby zadeklarować importu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-176">The following class uses `ImportingConstructor` to declare an import.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-177">Domyślnie `ImportingConstructor` typy kontraktu wywnioskować używa atrybutów i kontraktu nazwy dla wszystkich importów parametru.</span><span class="sxs-lookup"><span data-stu-id="4d81f-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="4d81f-178">Można zastąpić przez dekoracji parametrów z `Import` atrybuty, które następnie można zdefiniować nazwy kontraktu i typ kontraktu jawnie.</span><span class="sxs-lookup"><span data-stu-id="4d81f-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="4d81f-179">Poniższy kod przedstawia Konstruktor, który używa tej składni, aby zaimportować klasy pochodnej zamiast klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4d81f-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-180">W szczególności należy zachować ostrożność z kolekcji parametrów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="4d81f-181">Na przykład jeśli określisz `ImportingConstructor` na konstruktora z parametrem typu `IEnumerable<int>`, importowanie będzie odpowiadała jednego eksportu typu `IEnumerable<int>`, zamiast zestawu eksportuje typu `int`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="4d81f-182">Odpowiadające zestaw eksportuje typu `int`, masz do dekoracji parametr o `ImportMany` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>  
  
 <span data-ttu-id="4d81f-183">Parametry zadeklarowany jako importów przez `ImportingConstructor` atrybutu są również oznaczane jako *importuje wymagań wstępnych*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="4d81f-184">MEF zwykle umożliwia eksportowanie i importowanie do formularza *cykl*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="4d81f-185">Na przykład cykl jest, gdzie importuje obiektu A obiekt B, który z kolei importuje A. obiektu W normalnych okolicznościach cyklu nie stanowi to problemu, oraz kontenera kompozycji konstrukcji oba obiekty normalnie.</span><span class="sxs-lookup"><span data-stu-id="4d81f-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>  
  
 <span data-ttu-id="4d81f-186">Jeśli importowanych wartość jest wymagana przez konstruktora części, tego obiektu nie może brać udziału w cyklu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="4d81f-187">Jeśli obiekt A wymaga obiektu B można skonstruować przed można konstruować się i obiektu B importuje A obiektu cyklu nie będzie można rozwiązać i wystąpi błąd kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="4d81f-188">Importy zadeklarowany w parametrach konstruktora są zatem importów wymagań wstępnych, które wszystkie należy podać przed żadnego eksportu z obiektu, który wymaga ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="4d81f-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>  
  
### <a name="optional-imports"></a><span data-ttu-id="4d81f-189">Importy opcjonalne</span><span class="sxs-lookup"><span data-stu-id="4d81f-189">Optional Imports</span></span>  
 <span data-ttu-id="4d81f-190">`Import` Atrybut określa wymaganie części funkcji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="4d81f-191">Nie można przeprowadzić importu, kompozycji części zakończy się niepowodzeniem, a część nie będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="4d81f-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>  
  
 <span data-ttu-id="4d81f-192">Można określić, że importowanie jest *opcjonalne* przy użyciu `AllowDefault` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d81f-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="4d81f-193">W takim przypadku kompozycji powiedzie się, nawet jeśli importu jest niezgodny z żadnych dostępnych eksporty i importowania właściwość zostanie ustawiona do domyślnego dla tego typu właściwości (`null` dla właściwości obiektu `false` dla wartości logicznych lub zero dla liczbowe Właściwości). Następujące klasy używa opcjonalny import.</span><span class="sxs-lookup"><span data-stu-id="4d81f-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>  
  
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
  
### <a name="importing-multiple-objects"></a><span data-ttu-id="4d81f-194">Importowanie wielu obiektów</span><span class="sxs-lookup"><span data-stu-id="4d81f-194">Importing Multiple Objects</span></span>  
 <span data-ttu-id="4d81f-195">`Import` Atrybut będzie tylko pomyślnie składać się, gdy jest on zgodny tylko jeden Eksport.</span><span class="sxs-lookup"><span data-stu-id="4d81f-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="4d81f-196">Innych przypadkach spowoduje błąd kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="4d81f-197">Aby zaimportować więcej niż jeden Eksport zgodny ten sam kontrakt, użyj `ImportMany` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="4d81f-198">Importy z tym atrybutem zawsze są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="4d81f-199">Na przykład kompozycji zakończy się niepowodzeniem, jeśli podano żadnego pasującego eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="4d81f-200">Następujące klasy importuje dowolnej liczby eksportów typu `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-200">The following class imports any number of exports of type `IMyAddin`.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-201">Importowany tablicy jest możliwy przy użyciu zwykłej `IEnumerable<T>` składni i metod.</span><span class="sxs-lookup"><span data-stu-id="4d81f-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="4d81f-202">Istnieje również możliwość użycia zwykłej tablicy (`IMyAddin[]`) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4d81f-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>  
  
 <span data-ttu-id="4d81f-203">Ten wzorzec może być bardzo ważne, gdy jest używany w połączeniu z `Lazy<T>` składni.</span><span class="sxs-lookup"><span data-stu-id="4d81f-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="4d81f-204">Na przykład za pomocą `ImportMany`, `IEnumerable<T>`, i `Lazy<T>`, można importować pośredniego odwołania do dowolną liczbę obiektów i wystąpienia tylko te, które stały się niezbędne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="4d81f-205">Następujące klasy pokazuje tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="4d81f-205">The following class shows this pattern.</span></span>  
  
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
## <a name="avoiding-discovery"></a><span data-ttu-id="4d81f-206">Unikanie odnajdywania</span><span class="sxs-lookup"><span data-stu-id="4d81f-206">Avoiding Discovery</span></span>  
 <span data-ttu-id="4d81f-207">W niektórych przypadkach można zapobiec odnajdywane jako część wykaz części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="4d81f-208">Na przykład część może być klasą podstawową mają być dziedziczone z, ale nie używane.</span><span class="sxs-lookup"><span data-stu-id="4d81f-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="4d81f-209">Istnieją dwa sposoby, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="4d81f-210">Najpierw należy użyć `abstract` — słowo kluczowe w klasie części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="4d81f-211">Klasy abstrakcyjne nigdy nie podawaj eksportu, mimo że zapewniają one eksportu odziedziczone do klasy, które pochodzą z nich.</span><span class="sxs-lookup"><span data-stu-id="4d81f-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>  
  
 <span data-ttu-id="4d81f-212">Jeżeli klasa abstrakcyjna, można go przy użyciu dekoracji `PartNotDiscoverable` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="4d81f-213">Części ozdobione ten atrybut nie będą uwzględniane w dowolnym katalogów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="4d81f-214">W poniższym przykładzie pokazano tych wzorców.</span><span class="sxs-lookup"><span data-stu-id="4d81f-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="4d81f-215">`DataOne` zostaną odnalezione przez wykaz.</span><span class="sxs-lookup"><span data-stu-id="4d81f-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="4d81f-216">Ponieważ `DataTwo` jest abstrakcyjna, go nie zostaną odnalezione.</span><span class="sxs-lookup"><span data-stu-id="4d81f-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="4d81f-217">Ponieważ `DataThree` używane `PartNotDiscoverable` atrybutu, nie zostaną odnalezione.</span><span class="sxs-lookup"><span data-stu-id="4d81f-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>  
  
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
## <a name="metadata-and-metadata-views"></a><span data-ttu-id="4d81f-218">Metadane i widoków metadanych</span><span class="sxs-lookup"><span data-stu-id="4d81f-218">Metadata and Metadata Views</span></span>  
 <span data-ttu-id="4d81f-219">Eksporty mogą dostarczać dodatkowych informacji o sobie znany jako *metadanych*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="4d81f-220">Metadane może służyć do przekazywania właściwości obiektu wyeksportowany do importowania części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="4d81f-221">Importowania części mogą używać tych danych do określania, które eksportuje do użycia, lub aby zebrać informacje dotyczące eksportu bez konieczności tworzenia go.</span><span class="sxs-lookup"><span data-stu-id="4d81f-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="4d81f-222">Z tego powodu importu musi być opóźnieniem do użycia metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-222">For this reason, an import must be lazy to use metadata.</span></span>  
  
 <span data-ttu-id="4d81f-223">Aby użyć metadanych, zwykle zadeklarować interfejsu znany jako *widoku metadanych*, deklaruje, jakie metadane będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="4d81f-224">Interfejs widok metadanych musi mieć tylko właściwości i te właściwości muszą mieć `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="4d81f-225">Następujący interfejs jest przykład widoku metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-225">The following interface is an example metadata view.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-226">Istnieje również możliwość użycia kolekcji uniwersalnej, `IDictionary<string, object>`, jako widoku metadanych, ale forfeits zalet Sprawdzanie typu i należy unikać.</span><span class="sxs-lookup"><span data-stu-id="4d81f-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>  
  
 <span data-ttu-id="4d81f-227">Zwykle wszystkie właściwości o nazwie w widoku metadanych są wymagane, a wszelkie eksportu, które nie udostępniają ich nie zostanie uwzględniony dopasowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="4d81f-228">`DefaultValue` Atrybut określa, że właściwość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="4d81f-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="4d81f-229">Jeśli właściwość nie jest uwzględniona, zostanie do niej przypisana wartość domyślna określona jako parametr `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="4d81f-230">Poniżej przedstawiono dwóch różnych klas ozdobione metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="4d81f-231">Oba te klasy umożliwi dopasowanie w poprzednim widoku metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-231">Both of these classes would match the previous metadata view.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-232">Metadane jest wyrażone po `Export` atrybutu przy użyciu `ExportMetadata` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="4d81f-233">Metadane każdego z nich składa się z pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4d81f-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="4d81f-234">Część nazwy metadanych musi odpowiadać nazwie odpowiednie właściwości w widoku metadanych, a wartość zostanie przypisana do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d81f-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>  
  
 <span data-ttu-id="4d81f-235">Jeśli istnieje, będzie używana jest importera, określająca jakie widoku metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="4d81f-236">Importuj z metadanymi jest zadeklarowany jako opóźnionego importu, przy użyciu interfejsu metadanych jako drugi parametr typu `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="4d81f-237">Następujące klasy importuje poprzedniej części z metadanymi.</span><span class="sxs-lookup"><span data-stu-id="4d81f-237">The following class imports the previous part with metadata.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-238">W wielu przypadkach można połączyć metadanych z `ImportMany` atrybutu, aby przeanalizować za pośrednictwem dostępne importów i wybierz i tylko jednego wystąpienia lub kolekcję, aby dopasować określony warunek filtrowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="4d81f-239">Następujące klasy tworzy tylko `IPlugin` obiektów, które mają `Name` wartość "Rejestratora".</span><span class="sxs-lookup"><span data-stu-id="4d81f-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>  
  
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
## <a name="import-and-export-inheritance"></a><span data-ttu-id="4d81f-240">Importowanie i eksportowanie dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="4d81f-240">Import and Export Inheritance</span></span>  
 <span data-ttu-id="4d81f-241">Jeśli klasa dziedziczy z części, tej klasy może również zostać części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="4d81f-242">Importy zawsze są dziedziczone przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="4d81f-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="4d81f-243">W związku z tym podklasy części zawsze będzie częścią, z tym samym importów jako swojej klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4d81f-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>  
  
 <span data-ttu-id="4d81f-244">Eksporty zadeklarowana przy użyciu `Export` atrybutów nie są dziedziczone przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="4d81f-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="4d81f-245">Jednak części można wyeksportować się za pomocą `InheritedExport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="4d81f-246">Podklasy części będzie dziedziczyć i podaj tego samego eksportu, łącznie z nazwą kontraktu i typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="4d81f-247">W odróżnieniu od `Export` atrybut `InheritedExport` może odnosić się tylko na poziomie klasy, a nie na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4d81f-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="4d81f-248">W związku z tym poziomie członka eksportuje nigdy nie mogą być dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="4d81f-248">Therefore, member-level exports can never be inherited.</span></span>  
  
 <span data-ttu-id="4d81f-249">Następujące klasy cztery zademonstrować zasady importowania i eksportowania dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="4d81f-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="4d81f-250">`NumTwo` dziedziczy `NumOne`, więc `NumTwo` zaimportuje `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="4d81f-251">Zwykłe eksporty nie są dziedziczone, więc `NumTwo` nie eksportuje żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="4d81f-252">`NumFour` dziedziczy `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="4d81f-253">Ponieważ `NumThree` używane `InheritedExport`, `NumFour` ma jeden Eksport kontraktu typu `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="4d81f-254">Eksportowanie na poziomie członka nigdy nie są dziedziczone, więc `IMyData` nie jest eksportowany.</span><span class="sxs-lookup"><span data-stu-id="4d81f-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-255">W przypadku metadane skojarzone z `InheritedExport` atrybutu, że metadane również będą dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="4d81f-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="4d81f-256">(Aby uzyskać więcej informacji, zobacz we wcześniejszej sekcji "Metadanych i widoków metadanych"). Nie można modyfikować metadanych dziedziczone przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="4d81f-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="4d81f-257">Jednak przez ponowne deklarowanie `InheritedExport` atrybutu o takiej samej nazwie kontraktu i typ umowy, ale z nowymi metadanymi, podklasy mogą zastąpić dziedziczone metadane o nowe metadane.</span><span class="sxs-lookup"><span data-stu-id="4d81f-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="4d81f-258">Następujące klasy pokazuje tej zasady.</span><span class="sxs-lookup"><span data-stu-id="4d81f-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="4d81f-259">`MegaLogger` Części dziedziczy `Logger` i zawiera `InheritedExport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="4d81f-260">Ponieważ `MegaLogger` ponownie deklaruje nowych metadanych o nazwie stanu, nie dziedziczy on nazwę i wersję metadanych z `Logger`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-261">Podczas ponownego deklarowania `InheritedExport` atrybutu Zastępowanie metadanych, upewnij się, że typy kontraktu są takie same.</span><span class="sxs-lookup"><span data-stu-id="4d81f-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="4d81f-262">(W poprzednim przykładzie `IPlugin` jest typ kontraktu.) Jeśli będą się różnić, zamiast przesłaniać metodę, drugi atrybut utworzy export drugiej, niezależnie od z części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="4d81f-263">Ogólnie rzecz biorąc, oznacza to, że należy jawnie określić typ kontraktu, aby zastąpić `InheritedExport` atrybutu, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4d81f-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="4d81f-264">Ponieważ nie można bezpośrednio utworzyć wystąpienia interfejsów, one zazwyczaj nie może mieć atrybutu `Export` lub `Import` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="4d81f-265">Jednak można ozdobione interfejs `InheritedExport` atrybutu na poziomie interfejsu i że eksportu oraz wszelkie skojarzone metadane będą dziedziczone przez wszystkie klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="4d81f-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="4d81f-266">Interfejs sam nie będą dostępne w ramach jednak.</span><span class="sxs-lookup"><span data-stu-id="4d81f-266">The interface itself will not be available as a part, however.</span></span>  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a><span data-ttu-id="4d81f-267">Atrybuty niestandardowe eksportu</span><span class="sxs-lookup"><span data-stu-id="4d81f-267">Custom Export Attributes</span></span>  
 <span data-ttu-id="4d81f-268">Atrybuty eksportu podstawowych `Export` i `InheritedExport`, może zostać rozszerzony do zawierać metadane jako właściwości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="4d81f-269">Ta metoda jest przydatna do stosowania metadanych podobne do wielu części lub tworzenia drzewa dziedziczenia atrybutów metadanych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>  
  
 <span data-ttu-id="4d81f-270">Typ kontraktu, Nazwa kontraktu lub inne metadane, można określić atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="4d81f-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="4d81f-271">Aby zdefiniować atrybutu niestandardowego dziedziczenia z klasy `ExportAttribute` (lub `InheritedExportAttribute`) musi być dekorowane za `MetadataAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="4d81f-272">Następujące klasy definiuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="4d81f-272">The following class defines a custom attribute.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-273">Ta klasa definiuje atrybut niestandardowy o nazwie `MyAttribute` o typie kontraktu `IMyData` i niektóre metadanych o nazwie `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="4d81f-274">Wszystkie właściwości w klasie oznaczonej `MetadataAttribute` atrybutu są uważane za metadanych zdefiniowanych w atrybucie niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="4d81f-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="4d81f-275">Następujące dwa deklaracje są równoważne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-275">The following two declarations are equivalent.</span></span>  
  
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
  
 <span data-ttu-id="4d81f-276">W pierwszej deklaracji typ kontraktu i metadane są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="4d81f-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="4d81f-277">W drugim deklaracji typu kontraktu i metadanych wynikają z atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4d81f-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="4d81f-278">Szczególnie w przypadku, gdy dużej ilości metadanych identyczne musi odnosić się do wielu części (na przykład autora lub informacje o prawach autorskich) za pomocą atrybutu niestandardowego można zapisać dużo czasu i dublowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="4d81f-279">Ponadto można utworzyć drzewa dziedziczenia atrybutów niestandardowych umożliwiające zmian.</span><span class="sxs-lookup"><span data-stu-id="4d81f-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>  
  
 <span data-ttu-id="4d81f-280">Aby utworzyć opcjonalne metadane w atrybucie niestandardowym, należy użyć `DefaultValue` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="4d81f-281">Ten atrybut jest stosowany do właściwości w klasie Atrybut niestandardowy, określa się że ozdobione właściwość jest opcjonalna i nie ma być dostarczane przez eksportera.</span><span class="sxs-lookup"><span data-stu-id="4d81f-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="4d81f-282">Jeśli nie podano wartości dla właściwości, zostanie do niej przypisana wartość domyślna dla tego typu właściwości (zazwyczaj `null`, `false`, lub równa 0.)</span><span class="sxs-lookup"><span data-stu-id="4d81f-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a><span data-ttu-id="4d81f-283">Tworzenie zasad</span><span class="sxs-lookup"><span data-stu-id="4d81f-283">Creation Policies</span></span>  
 <span data-ttu-id="4d81f-284">W przypadku części określa importowania i kompozycji jest wykonywane, kontener kompozycji próbuje odnaleźć eksportu zgodnego.</span><span class="sxs-lookup"><span data-stu-id="4d81f-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="4d81f-285">Importuj z eksportu pasujący pomyślnie, importowania elementu członkowskiego jest ustawione na wystąpienie eksportowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="4d81f-286">Skąd pochodzą to wystąpienie jest kontrolowany przez eksportowanie części *zasady tworzenia*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>  
  
 <span data-ttu-id="4d81f-287">Są dwie zasady może spowodować powstanie *udostępnionego* i *nieudostępnione*.</span><span class="sxs-lookup"><span data-stu-id="4d81f-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="4d81f-288">Z zasadami tworzenia częścią udostępnionego będzie udostępniać każdego importu w kontenerze części z tej Umowy.</span><span class="sxs-lookup"><span data-stu-id="4d81f-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="4d81f-289">Gdy aparat kompozycji znalezienia dopasowania i ustawić wartość właściwości importowania, zostanie on wystąpienia nową kopię części tylko wtedy, gdy jeszcze nie istnieje; w przeciwnym razie poda istniejącą kopię.</span><span class="sxs-lookup"><span data-stu-id="4d81f-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="4d81f-290">Oznacza to, że wiele obiektów może mieć odwołania do tej samej części.</span><span class="sxs-lookup"><span data-stu-id="4d81f-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="4d81f-291">Takie części nie należy polegać na stan wewnętrzny, który może ulec zmianie w wielu miejscach.</span><span class="sxs-lookup"><span data-stu-id="4d81f-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="4d81f-292">Ta zasada jest odpowiednia dla części statycznych, części, które udostępniają usługi i części używające dużej ilości pamięci lub innych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>  
  
 <span data-ttu-id="4d81f-293">Części z zasadami tworzenia nieudostępnione zostanie utworzona za każdym razem, gdy znajduje dopasowywania importu dla jednego z jego eksportu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="4d81f-294">W związku z tym będzie można utworzyć wystąpienia nową kopię dla każdego importu w kontenerze, który pasuje do jednej części wyeksportowanego kontraktów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="4d81f-295">Wewnętrzny stan klasy te kopie nie będą udostępniane.</span><span class="sxs-lookup"><span data-stu-id="4d81f-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="4d81f-296">Ta zasada jest odpowiednia dla elementów, których każdej operacji importowania wymaga własnego stan wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="4d81f-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>  
  
 <span data-ttu-id="4d81f-297">Zarówno importu i eksportu można określić zasady tworzenia części, spośród wartości `Shared`, `NonShared`, lub `Any`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="4d81f-298">Wartość domyślna to `Any` zarówno importuje i eksportuje.</span><span class="sxs-lookup"><span data-stu-id="4d81f-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="4d81f-299">Export, która określa `Shared` lub `NonShared` spowoduje dopasowanie tylko importu, który określa takie same, lub Określa `Any`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="4d81f-300">Podobnie, import, która określa `Shared` lub `NonShared` spowoduje dopasowanie tylko eksportu, który określa takie same lub określający `Any`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="4d81f-301">Importu i eksportu z niezgodną tworzenia zasady nie są uznawane za zgodne, w taki sam sposób jak importu i eksportu, którego nazwa lub kontrakt typ kontraktu nie są dopasowania.</span><span class="sxs-lookup"><span data-stu-id="4d81f-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="4d81f-302">Jeśli określono zarówno importowanie i eksportowanie `Any`, lub nie określaj zasadę tworzenia i domyślnie `Any`, domyślnie zostanie ustawiona do udostępnionego zasady tworzenia.</span><span class="sxs-lookup"><span data-stu-id="4d81f-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>  
  
 <span data-ttu-id="4d81f-303">W poniższym przykładzie pokazano zarówno importuje i eksportuje określania zasad tworzenia.</span><span class="sxs-lookup"><span data-stu-id="4d81f-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="4d81f-304">`PartOne` nie określono zasadę tworzenia, wartość domyślna to `Any`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="4d81f-305">`PartTwo` nie określono zasadę tworzenia, wartość domyślna to `Any`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="4d81f-306">Ponieważ zarówno importowanie i eksportowanie domyślną `Any`, `PartOne` zostaną udostępnione.</span><span class="sxs-lookup"><span data-stu-id="4d81f-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="4d81f-307">`PartThree` Określa `Shared` Tworzenie zasad, więc `PartTwo` i `PartThree` współużytkują tę samą kopię `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="4d81f-308">`PartFour` Określa `NonShared` Tworzenie zasad, więc `PartFour` będzie nieudostępnione w `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="4d81f-309">`PartSix` Określa `NonShared` tworzenia zasad.</span><span class="sxs-lookup"><span data-stu-id="4d81f-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="4d81f-310">`PartFive` i `PartSix` każdego otrzymają osobne kopie `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="4d81f-311">`PartSeven` Określa `Shared` tworzenia zasad.</span><span class="sxs-lookup"><span data-stu-id="4d81f-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="4d81f-312">Ponieważ istnieje nr wyeksportowane `PartFour` z zasadami tworzenia `Shared`, `PartSeven` importu nie jest zgodna z niczego i nie zostanie wypełnione.</span><span class="sxs-lookup"><span data-stu-id="4d81f-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>  
  
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
## <a name="life-cycle-and-disposing"></a><span data-ttu-id="4d81f-313">Cykl życia i usuwania</span><span class="sxs-lookup"><span data-stu-id="4d81f-313">Life Cycle and Disposing</span></span>  
 <span data-ttu-id="4d81f-314">Ponieważ części znajdują się w kontenerze kompozycji, ich cyklu życia mogą być bardziej skomplikowane niż zwykłe obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d81f-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="4d81f-315">Części można zaimplementować dwa interfejsy ważne związanych z cyklem życia: `IDisposable` i `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>  
  
 <span data-ttu-id="4d81f-316">Części, które wymagają pracy do wykonania w zamykania w dół lub wymagające zwolnić zasoby powinny implementować `IDisposable`, jak zwykle dla obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d81f-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="4d81f-317">Jednak ponieważ kontenera tworzy i obsługuje odwołań do części, kontenera, który jest właścicielem części powinny wywoływać `Dispose` dla niego metodę.</span><span class="sxs-lookup"><span data-stu-id="4d81f-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="4d81f-318">Implementuje sam pojemnik `IDisposable`i jako część jej czyszczenie w `Dispose` zostanie wywołany `Dispose` na części, których jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="4d81f-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="4d81f-319">Z tego powodu należy zawsze usunąć kontener kompozycji podczas jego i żadnych części, który jest właścicielem nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>  
  
 <span data-ttu-id="4d81f-320">Kontenery długotrwałe kompozycji użycie pamięci przez części z zasadami tworzenia nieudostępnione może stać się problem.</span><span class="sxs-lookup"><span data-stu-id="4d81f-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="4d81f-321">Te częściami nieudostępnionymi można tworzyć wiele razy i nie będzie usunięty, dopóki sam pojemnik zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="4d81f-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="4d81f-322">Aby poradzić sobie z tym, zapewnia kontener `ReleaseExport` metody.</span><span class="sxs-lookup"><span data-stu-id="4d81f-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="4d81f-323">Wywołanie tej metody w eksportu nieudostępnione usuwa tego eksportu z kontenera kompozycji i usuwa go.</span><span class="sxs-lookup"><span data-stu-id="4d81f-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="4d81f-324">Elementy, które są używane tylko usunięte eksportu, i tak dalej niżej na drzewie są również usuwane i usunięty.</span><span class="sxs-lookup"><span data-stu-id="4d81f-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="4d81f-325">W ten sposób można odzyskać zasoby bez usuwania samego kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="4d81f-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>  
  
 <span data-ttu-id="4d81f-326">`IPartImportsSatisfiedNotification` zawiera jedną metodę o nazwie `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="4d81f-327">Ta metoda jest wywoływana przez kontener kompozycji na żadnych części, które implementują interfejs, gdy kompozycja została ukończona i Importy części są gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="4d81f-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="4d81f-328">Elementy są tworzone przez aparat kompozycji do wypełnienia importów z innymi częściami.</span><span class="sxs-lookup"><span data-stu-id="4d81f-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="4d81f-329">Przed zestawu importów części nie może wykonać inicjowanie zależy od lub manipuluje importowanych wartości w Konstruktorze części, chyba że te wartości zostały określone jako wymagania wstępne przy użyciu `ImportingConstructor` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4d81f-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="4d81f-330">Zazwyczaj jest to preferowana metoda, ale w niektórych przypadkach iniekcji konstruktora nie mogą być dostępne.</span><span class="sxs-lookup"><span data-stu-id="4d81f-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="4d81f-331">W takich przypadkach można wykonać inicjowania w `OnImportsSatisfied`, a część powinny implementować `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="4d81f-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d81f-332">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d81f-332">See Also</span></span>  
 [<span data-ttu-id="4d81f-333">Wideo Channel 9: Otwarcie aplikacji przy użyciu Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="4d81f-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [<span data-ttu-id="4d81f-334">Wideo Channel 9: Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="4d81f-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
