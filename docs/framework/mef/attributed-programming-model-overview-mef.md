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
ms.openlocfilehash: 63fb3d627364810fac5ddb0bfd3adc3c0421c9cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126384"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="e997d-102">Omówienie modelu programowania opartego na atrybutach (MEF)</span><span class="sxs-lookup"><span data-stu-id="e997d-102">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="e997d-103">W Managed Extensibility Framework (MEF) *model programowania* jest konkretną metodą definiowania zestawu obiektów koncepcyjnych, na których MEF działa.</span><span class="sxs-lookup"><span data-stu-id="e997d-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="e997d-104">Te obiekty koncepcyjne obejmują części, Importy i eksporty.</span><span class="sxs-lookup"><span data-stu-id="e997d-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="e997d-105">MEF używa tych obiektów, ale nie określa sposobu ich reprezentowania.</span><span class="sxs-lookup"><span data-stu-id="e997d-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="e997d-106">W związku z tym możliwe jest szeroką gamę modeli programowania, w tym dostosowane modele programowania.</span><span class="sxs-lookup"><span data-stu-id="e997d-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="e997d-107">Domyślny model programowania używany w MEF to *model programowania z atrybutami*.</span><span class="sxs-lookup"><span data-stu-id="e997d-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="e997d-108">W przypadku częściowych modeli programowania, Importy, eksporty i inne obiekty są definiowane przy użyciu atrybutów, które dekorowaćą zwykłe klasy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e997d-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="e997d-109">W tym temacie wyjaśniono, jak używać atrybutów dostarczonych przez model programowania z atrybutami do tworzenia aplikacji MEF.</span><span class="sxs-lookup"><span data-stu-id="e997d-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="e997d-110">Importowanie i eksportowanie podstawowych podstaw</span><span class="sxs-lookup"><span data-stu-id="e997d-110">Import and Export Basics</span></span>

<span data-ttu-id="e997d-111">*Eksport* jest wartością, którą część dostarcza do innych części w kontenerze, a *Import* jest wymaganym przez część, która ma zostać wypełniona z dostępnych eksportów.</span><span class="sxs-lookup"><span data-stu-id="e997d-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="e997d-112">W modelu programowania z atrybutami Importy i eksporty są deklarowane przez klasy dekorowania nazwy lub elementy członkowskie z atrybutami `Import` i `Export`.</span><span class="sxs-lookup"><span data-stu-id="e997d-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="e997d-113">Atrybut `Export` może dekorować klasę, pole, właściwość lub metodę, podczas gdy atrybut `Import` może dekorować pole, właściwość lub parametr konstruktora.</span><span class="sxs-lookup"><span data-stu-id="e997d-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="e997d-114">Aby import został dopasowany do eksportu, importowanie i eksportowanie musi mieć ten sam *kontrakt*.</span><span class="sxs-lookup"><span data-stu-id="e997d-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="e997d-115">Umowa składa się z ciągu, zwanego *nazwą kontraktu*, i typu wyeksportowanego lub zaimportowanego obiektu, zwanego *typem kontraktu*.</span><span class="sxs-lookup"><span data-stu-id="e997d-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="e997d-116">Tylko wtedy, gdy zarówno Nazwa kontraktu, jak i typ kontraktu są uważane za wyeksportowanie w celu spełnienia określonego importu.</span><span class="sxs-lookup"><span data-stu-id="e997d-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="e997d-117">Jeden lub oba parametry kontraktu mogą być niejawne lub jawne.</span><span class="sxs-lookup"><span data-stu-id="e997d-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="e997d-118">Poniższy kod przedstawia klasę, która deklaruje import podstawowy.</span><span class="sxs-lookup"><span data-stu-id="e997d-118">The following code shows a class that declares a basic import.</span></span>

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

<span data-ttu-id="e997d-119">W przypadku tego importu atrybut `Import` nie ma typu kontraktu ani dołączonego parametru nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="e997d-120">W związku z tym oba zostaną wywnioskowane z właściwości dekoracyjnej.</span><span class="sxs-lookup"><span data-stu-id="e997d-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="e997d-121">W takim przypadku typ kontraktu zostanie `IMyAddin`, a nazwa kontraktu będzie unikatowym ciągiem utworzonym na podstawie typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="e997d-122">(Innymi słowy Nazwa kontraktu będzie pasować wyłącznie do eksportów, których nazwy są również wywnioskowane z typu `IMyAddin`.)</span><span class="sxs-lookup"><span data-stu-id="e997d-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="e997d-123">Poniżej przedstawiono eksport pasujący do poprzedniego importu.</span><span class="sxs-lookup"><span data-stu-id="e997d-123">The following shows an export that matches the previous import.</span></span>

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

<span data-ttu-id="e997d-124">W przypadku tego eksportu typ kontraktu to `IMyAddin`, ponieważ jest określony jako parametr atrybutu `Export`.</span><span class="sxs-lookup"><span data-stu-id="e997d-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="e997d-125">Wyeksportowany typ musi być taki sam jak typ kontraktu, pochodzić od typu kontraktu lub implementować typ kontraktu, jeśli jest to interfejs.</span><span class="sxs-lookup"><span data-stu-id="e997d-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="e997d-126">W tym wywozie rzeczywisty typ `MyLogger` implementuje interfejs `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="e997d-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="e997d-127">Nazwa kontraktu jest wywnioskowana z typu kontraktu, co oznacza, że ten eksport będzie pasował do poprzedniego importu.</span><span class="sxs-lookup"><span data-stu-id="e997d-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="e997d-128">Eksporty i Importy powinny być zwykle deklarowane dla publicznych klas lub członków.</span><span class="sxs-lookup"><span data-stu-id="e997d-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="e997d-129">Inne deklaracje są obsługiwane, ale Eksportowanie lub importowanie prywatnego, chronionego lub wewnętrznego elementu członkowskiego dzieli model izolacji części i dlatego nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="e997d-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="e997d-130">Typ kontraktu musi dokładnie pasować do eksportu i importu, aby można go było uznać za dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="e997d-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="e997d-131">Rozważmy następujący eksport.</span><span class="sxs-lookup"><span data-stu-id="e997d-131">Consider the following export.</span></span>

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

<span data-ttu-id="e997d-132">W przypadku tego eksportu typ kontraktu to `MyLogger`, a nie `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="e997d-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="e997d-133">Mimo że `MyLogger` implementuje `IMyAddin`i dlatego może być rzutowane do obiektu `IMyAddin`, ten eksport nie będzie pasował do poprzedniego importu, ponieważ typy kontraktu nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="e997d-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="e997d-134">Ogólnie rzecz biorąc nie trzeba określać nazwy kontraktu, a większość kontraktów powinna być zdefiniowana na podstawie typu kontraktu i metadanych.</span><span class="sxs-lookup"><span data-stu-id="e997d-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="e997d-135">Jednak w pewnych okolicznościach ważne jest bezpośrednie określenie nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="e997d-136">Najczęstszym przypadkiem jest to, że Klasa eksportuje kilka wartości, które współużytkują wspólny typ, takich jak elementy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="e997d-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="e997d-137">Nazwę kontraktu można określić jako pierwszy parametr `Import` lub `Export` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e997d-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="e997d-138">Poniższy kod przedstawia import i eksport z określoną nazwą kontraktu `MajorRevision`.</span><span class="sxs-lookup"><span data-stu-id="e997d-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

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

<span data-ttu-id="e997d-139">Jeśli typ kontraktu nie zostanie określony, będzie on nadal wywnioskowany na podstawie typu importu lub eksportu.</span><span class="sxs-lookup"><span data-stu-id="e997d-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="e997d-140">Jednak nawet jeśli nazwa kontraktu jest określona jawnie, typ kontraktu musi również pasować dokładnie do importu i eksportu, aby można go było uznać za dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="e997d-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="e997d-141">Jeśli na przykład pole `MajorRevision` było ciągiem, wywnioskowane typy kontraktu nie będą zgodne, a eksport nie jest zgodny z importem, mimo że ma tę samą nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="e997d-142">Importowanie i eksportowanie metody</span><span class="sxs-lookup"><span data-stu-id="e997d-142">Importing and Exporting a Method</span></span>

<span data-ttu-id="e997d-143">Atrybut `Export` może również dekorować metodę w taki sam sposób jak Klasa, właściwość lub funkcja.</span><span class="sxs-lookup"><span data-stu-id="e997d-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="e997d-144">Eksporty metod muszą określać typ kontraktu lub nazwę kontraktu, ponieważ nie można wywnioskować typu.</span><span class="sxs-lookup"><span data-stu-id="e997d-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="e997d-145">Określony typ może być niestandardowym delegatem lub typem ogólnym, takim jak `Func`.</span><span class="sxs-lookup"><span data-stu-id="e997d-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="e997d-146">Następująca Klasa eksportuje metodę o nazwie `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="e997d-146">The following class exports a method named `DoSomething`.</span></span>

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

<span data-ttu-id="e997d-147">W tej klasie Metoda `DoSomething` przyjmuje jeden parametr `int` i zwraca `string`.</span><span class="sxs-lookup"><span data-stu-id="e997d-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="e997d-148">Aby można było dopasować ten eksport, część importująca musi deklarować odpowiedni element członkowski.</span><span class="sxs-lookup"><span data-stu-id="e997d-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="e997d-149">W poniższej klasie zaimportowano metodę `DoSomething`.</span><span class="sxs-lookup"><span data-stu-id="e997d-149">The following class imports the `DoSomething` method.</span></span>

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

<span data-ttu-id="e997d-150">Aby uzyskać więcej informacji o sposobach używania obiektu `Func<T, T>`, zobacz <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="e997d-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="e997d-151">Typy importów</span><span class="sxs-lookup"><span data-stu-id="e997d-151">Types of Imports</span></span>

<span data-ttu-id="e997d-152">MEF obsługuje kilka typów importu, w tym dynamiczne, opóźnione, wymagania wstępne i opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e997d-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="e997d-153">Importy dynamiczne</span><span class="sxs-lookup"><span data-stu-id="e997d-153">Dynamic Imports</span></span>

<span data-ttu-id="e997d-154">W niektórych przypadkach Klasa importowania może chcieć dopasować eksporty dowolnego typu, który ma określoną nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="e997d-155">W tym scenariuszu Klasa może deklarować *Import dynamiczny*.</span><span class="sxs-lookup"><span data-stu-id="e997d-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="e997d-156">Następujący import pasuje do dowolnego eksportu z nazwą kontraktu "TheString".</span><span class="sxs-lookup"><span data-stu-id="e997d-156">The following import matches any export with contract name "TheString".</span></span>

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

<span data-ttu-id="e997d-157">Gdy typ kontraktu jest wywnioskowany na podstawie słowa kluczowego `dynamic`, będzie on pasować do dowolnego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="e997d-158">W takim przypadku import powinien **zawsze** określać nazwę kontraktu do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="e997d-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="e997d-159">(Jeśli nazwa kontraktu nie zostanie określona, importowanie zostanie uznane za niezgodne z eksportami). Oba poniższe eksporty byłyby zgodne z poprzednim importowaniem.</span><span class="sxs-lookup"><span data-stu-id="e997d-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

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

<span data-ttu-id="e997d-160">Oczywiście Importowanie klasy musi być przygotowana do działania z obiektem dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="e997d-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="e997d-161">Importy z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="e997d-161">Lazy Imports</span></span>

<span data-ttu-id="e997d-162">W niektórych przypadkach Klasa import może wymagać pośredniego odwołania do zaimportowanego obiektu, tak aby obiekt nie został utworzony jako natychmiast.</span><span class="sxs-lookup"><span data-stu-id="e997d-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="e997d-163">W tym scenariuszu Klasa może deklarować import z *opóźnieniem* przy użyciu typu kontraktu `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="e997d-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="e997d-164">Następująca właściwość importowania deklaruje import z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="e997d-164">The following importing property declares a lazy import.</span></span>

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

<span data-ttu-id="e997d-165">Z punktu widzenia aparatu kompozycji typ kontraktu `Lazy<T>` jest uznawany za identyczny z typem kontraktu `T`.</span><span class="sxs-lookup"><span data-stu-id="e997d-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="e997d-166">W związku z tym poprzedni import będzie pasował do poniższego eksportu.</span><span class="sxs-lookup"><span data-stu-id="e997d-166">Therefore, the previous import would match the following export.</span></span>

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

<span data-ttu-id="e997d-167">Nazwę kontraktu i typ kontraktu można określić w atrybucie `Import` dla importu z opóźnieniem, zgodnie z wcześniejszym opisem w sekcji "podstawowe Importy i eksporty".</span><span class="sxs-lookup"><span data-stu-id="e997d-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="e997d-168">Importy wymagań wstępnych</span><span class="sxs-lookup"><span data-stu-id="e997d-168">Prerequisite Imports</span></span>

<span data-ttu-id="e997d-169">Wyeksportowane części MEF są zwykle tworzone przez aparat kompozycji, w odpowiedzi na bezpośrednie żądanie lub potrzebę wypełnienia dopasowanego importu.</span><span class="sxs-lookup"><span data-stu-id="e997d-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="e997d-170">Domyślnie podczas tworzenia części aparat kompozycji używa konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="e997d-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="e997d-171">Aby aparat używał innego konstruktora, można oznaczyć go atrybutem `ImportingConstructor`.</span><span class="sxs-lookup"><span data-stu-id="e997d-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="e997d-172">Każda część może mieć tylko jeden Konstruktor do użytku przez aparat kompozycji.</span><span class="sxs-lookup"><span data-stu-id="e997d-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="e997d-173">Nie podawanie konstruktora bez parametrów ani `ImportingConstructor` atrybutu lub dostarczenie więcej niż jednego atrybutu `ImportingConstructor` spowoduje wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="e997d-173">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="e997d-174">Aby wypełnić parametry konstruktora oznaczonego atrybutem `ImportingConstructor`, wszystkie te parametry są automatycznie deklarowane jako Importy.</span><span class="sxs-lookup"><span data-stu-id="e997d-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="e997d-175">Jest to wygodny sposób deklarowania importu, które są używane podczas inicjowania części.</span><span class="sxs-lookup"><span data-stu-id="e997d-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="e997d-176">W poniższej klasie zadeklaruje import przy użyciu `ImportingConstructor`.</span><span class="sxs-lookup"><span data-stu-id="e997d-176">The following class uses `ImportingConstructor` to declare an import.</span></span>

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

<span data-ttu-id="e997d-177">Domyślnie atrybut `ImportingConstructor` używa wnioskowanych typów kontraktu i nazw kontraktów dla wszystkich importowanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="e997d-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="e997d-178">Można to zastąpić, dekorowania nazwy parametry z atrybutami `Import`, a następnie jawnie zdefiniować typ kontraktu i nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="e997d-179">Poniższy kod demonstruje konstruktora, który używa tej składni do importowania klasy pochodnej zamiast klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e997d-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

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

<span data-ttu-id="e997d-180">W szczególności należy zachować ostrożność przy użyciu parametrów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e997d-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="e997d-181">Na przykład jeśli określisz `ImportingConstructor` w konstruktorze z parametrem typu `IEnumerable<int>`, import będzie zgodny z pojedynczym eksportem typu `IEnumerable<int>`, a nie z zestawem eksportów typu `int`.</span><span class="sxs-lookup"><span data-stu-id="e997d-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="e997d-182">Aby dopasować zestaw eksportów typu `int`, należy dekorować parametr z atrybutem `ImportMany`.</span><span class="sxs-lookup"><span data-stu-id="e997d-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="e997d-183">Parametry zadeklarowane jako Importy przez atrybut `ImportingConstructor` są również oznaczone jako *Importy wymagań wstępnych*.</span><span class="sxs-lookup"><span data-stu-id="e997d-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="e997d-184">MEF zwykle zezwala na Eksporty i Importy w celu utworzenia *cyklu*.</span><span class="sxs-lookup"><span data-stu-id="e997d-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="e997d-185">Na przykład cykl polega na tym, że obiekt A importuje obiekt B, który z kolei importuje obiekt A. W normalnych warunkach cykl nie jest problemem, a kontener kompozycji konstruuje oba obiekty w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="e997d-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="e997d-186">Gdy importowana wartość jest wymagana przez konstruktora części, ten obiekt nie może uczestniczyć w cyklu.</span><span class="sxs-lookup"><span data-stu-id="e997d-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="e997d-187">Jeśli obiekt A wymaga skonstruowania obiektu B, zanim będzie mógł być skonstruowany, a obiekt B importuje obiekt A, cykl nie będzie mógł zostać rozpoznany i wystąpi błąd kompozycji.</span><span class="sxs-lookup"><span data-stu-id="e997d-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="e997d-188">Importy zadeklarowane w parametrach konstruktorów są dlatego Importy wymagające wymagań wstępnych, które muszą zostać wypełnione przed wszelkimi eksportami z obiektu, który go wymaga.</span><span class="sxs-lookup"><span data-stu-id="e997d-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="e997d-189">Importy opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e997d-189">Optional Imports</span></span>

<span data-ttu-id="e997d-190">Atrybut `Import` określa wymaganie części do działania.</span><span class="sxs-lookup"><span data-stu-id="e997d-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="e997d-191">Jeśli nie można spełnić importu, kompozycja tej części zakończy się niepowodzeniem, a część nie będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="e997d-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="e997d-192">Można określić, że import jest *opcjonalny* przy użyciu właściwości `AllowDefault`.</span><span class="sxs-lookup"><span data-stu-id="e997d-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="e997d-193">W takim przypadku kompozycja powiedzie się, nawet jeśli import nie pasuje do żadnych dostępnych eksportów, a właściwość import zostanie ustawiona na wartość domyślną dla tego typu właściwości (`null` dla właściwości obiektu, `false` dla wartości logicznych lub zero dla właściwości liczbowych). W poniższej klasie jest stosowane opcjonalne importowanie.</span><span class="sxs-lookup"><span data-stu-id="e997d-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

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

### <a name="importing-multiple-objects"></a><span data-ttu-id="e997d-194">Importowanie wielu obiektów</span><span class="sxs-lookup"><span data-stu-id="e997d-194">Importing Multiple Objects</span></span>

<span data-ttu-id="e997d-195">Atrybut `Import` zostanie utworzony pomyślnie tylko wtedy, gdy pasuje do jednego i tylko jeden eksport.</span><span class="sxs-lookup"><span data-stu-id="e997d-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="e997d-196">Inne przypadki spowodują powstanie błędu kompozycji.</span><span class="sxs-lookup"><span data-stu-id="e997d-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="e997d-197">Aby zaimportować więcej niż jeden eksport zgodny z tym samym kontraktem, Użyj atrybutu `ImportMany`.</span><span class="sxs-lookup"><span data-stu-id="e997d-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="e997d-198">Importy oznaczone przy użyciu tego atrybutu są zawsze opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e997d-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="e997d-199">Na przykład kompozycja nie powiedzie się, jeśli nie ma pasujących eksportów.</span><span class="sxs-lookup"><span data-stu-id="e997d-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="e997d-200">Następująca Klasa importuje dowolną liczbę eksportów typu `IMyAddin`.</span><span class="sxs-lookup"><span data-stu-id="e997d-200">The following class imports any number of exports of type `IMyAddin`.</span></span>

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

<span data-ttu-id="e997d-201">Dostęp do zaimportowanej tablicy można uzyskać przy użyciu zwykłej składni `IEnumerable<T>` i metod.</span><span class="sxs-lookup"><span data-stu-id="e997d-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="e997d-202">Istnieje również możliwość użycia zwykłej tablicy (`IMyAddin[]`).</span><span class="sxs-lookup"><span data-stu-id="e997d-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="e997d-203">Ten wzorzec może być bardzo istotny, gdy jest używany w połączeniu z składnią `Lazy<T>`.</span><span class="sxs-lookup"><span data-stu-id="e997d-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="e997d-204">Na przykład za pomocą `ImportMany`, `IEnumerable<T>`i `Lazy<T>`można zaimportować odwołania pośrednie do dowolnej liczby obiektów i utworzyć tylko te, które staną się niezbędne.</span><span class="sxs-lookup"><span data-stu-id="e997d-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="e997d-205">W poniższej klasie przedstawiono ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="e997d-205">The following class shows this pattern.</span></span>

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

## <a name="avoiding-discovery"></a><span data-ttu-id="e997d-206">Unikanie odnajdywania</span><span class="sxs-lookup"><span data-stu-id="e997d-206">Avoiding Discovery</span></span>

<span data-ttu-id="e997d-207">W niektórych przypadkach może być konieczne uniemożliwienie wykrycia części jako części wykazu.</span><span class="sxs-lookup"><span data-stu-id="e997d-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="e997d-208">Na przykład część może być klasą bazową, która ma być dziedziczona z, ale nie jest używana.</span><span class="sxs-lookup"><span data-stu-id="e997d-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="e997d-209">Istnieją dwa sposoby osiągnięcia tego celu.</span><span class="sxs-lookup"><span data-stu-id="e997d-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="e997d-210">Najpierw można użyć słowa kluczowego `abstract` w klasie części.</span><span class="sxs-lookup"><span data-stu-id="e997d-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="e997d-211">Klasy abstrakcyjne nigdy nie zapewniają eksportów, chociaż mogą zapewnić dziedziczone eksporty do klas, które pochodzą z nich.</span><span class="sxs-lookup"><span data-stu-id="e997d-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="e997d-212">Jeśli Klasa nie może być abstrakcyjna, można ją dekorować z atrybutem `PartNotDiscoverable`.</span><span class="sxs-lookup"><span data-stu-id="e997d-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="e997d-213">Część dekoracyjna z tym atrybutem nie zostanie uwzględniona w żadnym wykazie.</span><span class="sxs-lookup"><span data-stu-id="e997d-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="e997d-214">Poniższy przykład ilustruje te wzorce.</span><span class="sxs-lookup"><span data-stu-id="e997d-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="e997d-215">`DataOne` zostanie odnalezione przez wykaz.</span><span class="sxs-lookup"><span data-stu-id="e997d-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="e997d-216">Ponieważ `DataTwo` jest abstrakcyjna, nie zostanie odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="e997d-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="e997d-217">Ponieważ `DataThree` użyto atrybutu `PartNotDiscoverable`, nie zostanie on odnaleziony.</span><span class="sxs-lookup"><span data-stu-id="e997d-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

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

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="e997d-218">Widoki metadanych i metadanych</span><span class="sxs-lookup"><span data-stu-id="e997d-218">Metadata and Metadata Views</span></span>

<span data-ttu-id="e997d-219">Eksporty mogą dostarczyć dodatkowe informacje o sobie znane jako *metadane*.</span><span class="sxs-lookup"><span data-stu-id="e997d-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="e997d-220">Metadane mogą służyć do przekazywania właściwości eksportowanego obiektu do części importującej.</span><span class="sxs-lookup"><span data-stu-id="e997d-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="e997d-221">Część importująca może używać tych danych do decydowania, które eksporty mają być używane, lub do zbierania informacji na temat eksportu bez konieczności konstruowania go.</span><span class="sxs-lookup"><span data-stu-id="e997d-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="e997d-222">Z tego powodu import musi być opóźniony, aby można było używać metadanych.</span><span class="sxs-lookup"><span data-stu-id="e997d-222">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="e997d-223">Aby użyć metadanych, zazwyczaj deklaruje interfejs znany jako *widok metadanych*, który deklaruje, jakie metadane będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="e997d-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="e997d-224">Interfejs widoku metadanych musi mieć tylko właściwości, a te właściwości muszą mieć metody dostępu `get`.</span><span class="sxs-lookup"><span data-stu-id="e997d-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="e997d-225">Poniższy interfejs to przykładowy widok metadanych.</span><span class="sxs-lookup"><span data-stu-id="e997d-225">The following interface is an example metadata view.</span></span>

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

<span data-ttu-id="e997d-226">Istnieje również możliwość użycia kolekcji ogólnej, `IDictionary<string, object>`, jako widoku metadanych, ale spowoduje to przekazanie korzyści kontroli typu i należy unikać.</span><span class="sxs-lookup"><span data-stu-id="e997d-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="e997d-227">Zwykle wszystkie właściwości o nazwie w widoku metadanych są wymagane, a wszelkie eksporty, które ich nie zapewniają, nie będą uważane za dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="e997d-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="e997d-228">Atrybut `DefaultValue` określa, że właściwość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e997d-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="e997d-229">Jeśli właściwość nie jest uwzględniona, zostanie przypisana wartość domyślna określona jako parametr `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="e997d-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="e997d-230">Poniżej znajdują się dwie różne klasy z metadanymi.</span><span class="sxs-lookup"><span data-stu-id="e997d-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="e997d-231">Obie te klasy byłyby zgodne z poprzednim widokiem metadanych.</span><span class="sxs-lookup"><span data-stu-id="e997d-231">Both of these classes would match the previous metadata view.</span></span>

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

<span data-ttu-id="e997d-232">Metadane są wyrażane po atrybucie `Export` przy użyciu atrybutu `ExportMetadata`.</span><span class="sxs-lookup"><span data-stu-id="e997d-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="e997d-233">Każda część metadanych składa się z pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="e997d-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="e997d-234">Część nazwy metadanych musi być zgodna z nazwą odpowiedniej właściwości w widoku metadanych, a wartość zostanie przypisana do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e997d-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="e997d-235">Jest importerem, który określa, jaki widok metadanych (jeśli istnieje) będzie używany.</span><span class="sxs-lookup"><span data-stu-id="e997d-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="e997d-236">Import z metadanymi jest zadeklarowany jako import z opóźnieniem, z interfejsem metadanych jako drugi parametr typu do `Lazy<T,T>`.</span><span class="sxs-lookup"><span data-stu-id="e997d-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="e997d-237">Następująca Klasa importuje poprzednią część z metadanymi.</span><span class="sxs-lookup"><span data-stu-id="e997d-237">The following class imports the previous part with metadata.</span></span>

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

<span data-ttu-id="e997d-238">W wielu przypadkach należy połączyć metadane z atrybutem `ImportMany`, aby przeanalizować przez dostępne Importy i wybrać i utworzyć wystąpienie tylko jednego lub odfiltrować kolekcję w celu dopasowania do określonego warunku.</span><span class="sxs-lookup"><span data-stu-id="e997d-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="e997d-239">Następujące klasy tworzy wystąpienia tylko `IPlugin` obiektów, które mają `Name` wartość "rejestrator".</span><span class="sxs-lookup"><span data-stu-id="e997d-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

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

## <a name="import-and-export-inheritance"></a><span data-ttu-id="e997d-240">Importowanie i eksportowanie dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="e997d-240">Import and Export Inheritance</span></span>

<span data-ttu-id="e997d-241">Jeśli klasa dziedziczy po części, ta klasa może być również częścią.</span><span class="sxs-lookup"><span data-stu-id="e997d-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="e997d-242">Importy są zawsze dziedziczone przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="e997d-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="e997d-243">W związku z tym, podklasa części zawsze będzie częścią, z tym samym importem, który jest klasą nadrzędną.</span><span class="sxs-lookup"><span data-stu-id="e997d-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="e997d-244">Eksporty zadeklarowane za pomocą atrybutu `Export` nie są dziedziczone przez podklasy.</span><span class="sxs-lookup"><span data-stu-id="e997d-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="e997d-245">Jednak część może eksportować sam siebie przy użyciu atrybutu `InheritedExport`.</span><span class="sxs-lookup"><span data-stu-id="e997d-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="e997d-246">Podklasy części będą dziedziczyć i udostępniać te same eksporty, w tym nazwy kontraktu i typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="e997d-247">W przeciwieństwie do atrybutu `Export`, `InheritedExport` można stosować tylko na poziomie klasy, a nie na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e997d-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="e997d-248">W związku z tym eksport na poziomie elementu członkowskiego nie może być nigdy dziedziczony.</span><span class="sxs-lookup"><span data-stu-id="e997d-248">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="e997d-249">Poniższe cztery klasy przedstawiają zasady importowania i eksportowania dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e997d-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="e997d-250">`NumTwo` dziedziczy po `NumOne`, więc `NumTwo` zaimportuje `IMyData`.</span><span class="sxs-lookup"><span data-stu-id="e997d-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="e997d-251">Zwykłe eksporty nie są dziedziczone, dlatego `NumTwo` nie eksportuje żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="e997d-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="e997d-252">`NumFour` dziedziczy z `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="e997d-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="e997d-253">Ponieważ `NumThree` użyto `InheritedExport`, `NumFour` ma jeden eksport z typem kontraktu `NumThree`.</span><span class="sxs-lookup"><span data-stu-id="e997d-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="e997d-254">Eksporty na poziomie elementu członkowskiego nigdy nie są dziedziczone, dlatego `IMyData` nie są eksportowane.</span><span class="sxs-lookup"><span data-stu-id="e997d-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

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

<span data-ttu-id="e997d-255">Jeśli istnieją metadane skojarzone z atrybutem `InheritedExport`, te metadane również zostaną Odziedziczone.</span><span class="sxs-lookup"><span data-stu-id="e997d-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="e997d-256">(Aby uzyskać więcej informacji, zobacz wcześniejszą sekcję "widoki metadanych i metadanych"). Dziedziczone metadane nie mogą być modyfikowane przez podklasę.</span><span class="sxs-lookup"><span data-stu-id="e997d-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="e997d-257">Jednak przez ponowne deklarowanie atrybutu `InheritedExport` z tą samą nazwą kontraktu i typem kontraktu, ale z nowymi metadanymi, podklasa może zastąpić dziedziczone metadane nowymi metadanymi.</span><span class="sxs-lookup"><span data-stu-id="e997d-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="e997d-258">W poniższej klasie przedstawiono tę zasadę.</span><span class="sxs-lookup"><span data-stu-id="e997d-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="e997d-259">Składnik `MegaLogger` dziedziczy po `Logger` i zawiera atrybut `InheritedExport`.</span><span class="sxs-lookup"><span data-stu-id="e997d-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="e997d-260">Ponieważ `MegaLogger` redeklaruje nowe metadane o nazwie status, nie dziedziczy on nazw i wersji metadanych z `Logger`.</span><span class="sxs-lookup"><span data-stu-id="e997d-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

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

<span data-ttu-id="e997d-261">Podczas ponownego deklarowania atrybutu `InheritedExport` w celu przesłaniania metadanych upewnij się, że typy kontraktu są takie same.</span><span class="sxs-lookup"><span data-stu-id="e997d-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="e997d-262">(W poprzednim przykładzie `IPlugin` jest typem kontraktu). Jeśli różnią się one zamiast przesłaniać, drugi atrybut utworzy drugi, niezależny eksport od części.</span><span class="sxs-lookup"><span data-stu-id="e997d-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="e997d-263">Zazwyczaj oznacza to, że trzeba będzie jawnie określić typ kontraktu podczas przesłonięcia atrybutu `InheritedExport`, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e997d-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="e997d-264">Ponieważ interfejsy nie mogą być tworzone bezpośrednio, zazwyczaj nie mogą mieć atrybutów `Export` ani `Import`.</span><span class="sxs-lookup"><span data-stu-id="e997d-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="e997d-265">Jednak interfejs może mieć atrybut `InheritedExport` na poziomie interfejsu, a eksportowanie wraz ze wszystkimi skojarzonymi metadanymi będzie dziedziczone przez wszystkie klasy implementujące.</span><span class="sxs-lookup"><span data-stu-id="e997d-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="e997d-266">Sam interfejs nie będzie jednak dostępny jako część.</span><span class="sxs-lookup"><span data-stu-id="e997d-266">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="e997d-267">Niestandardowe atrybuty eksportu</span><span class="sxs-lookup"><span data-stu-id="e997d-267">Custom Export Attributes</span></span>

<span data-ttu-id="e997d-268">Podstawowe atrybuty eksportu, `Export` i `InheritedExport`, można rozszerzyć w celu uwzględnienia metadanych jako właściwości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e997d-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="e997d-269">Ta technika jest przydatna w przypadku stosowania podobnych metadanych do wielu części lub tworzenia drzewa dziedziczenia atrybutów metadanych.</span><span class="sxs-lookup"><span data-stu-id="e997d-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="e997d-270">Atrybut niestandardowy może określać typ kontraktu, nazwę kontraktu lub inne metadane.</span><span class="sxs-lookup"><span data-stu-id="e997d-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="e997d-271">W celu zdefiniowania atrybutu niestandardowego Klasa dziedziczenia z `ExportAttribute` (lub `InheritedExportAttribute`) musi być uzupełniona atrybutem `MetadataAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e997d-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="e997d-272">Poniższa klasa definiuje atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="e997d-272">The following class defines a custom attribute.</span></span>

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

<span data-ttu-id="e997d-273">Ta klasa definiuje niestandardowy atrybut o nazwie `MyAttribute` z typem kontraktu `IMyData` i pewnych metadanych o nazwie `MyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="e997d-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="e997d-274">Wszystkie właściwości klasy oznaczonej atrybutem `MetadataAttribute` są uważane za metadane zdefiniowane w atrybucie niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="e997d-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="e997d-275">Poniższe dwie deklaracje są równoważne.</span><span class="sxs-lookup"><span data-stu-id="e997d-275">The following two declarations are equivalent.</span></span>

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

<span data-ttu-id="e997d-276">W pierwszej deklaracji typ kontraktu i metadane są jawnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="e997d-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="e997d-277">W drugiej deklaracji typ kontraktu i metadane są niejawne w dostosowanym atrybucie.</span><span class="sxs-lookup"><span data-stu-id="e997d-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="e997d-278">Szczególnie w przypadku, gdy należy zastosować dużą ilość identycznych metadanych do wielu części (na przykład informacje o autorze lub prawach autorskich), przy użyciu atrybutu niestandardowego można zaoszczędzić dużo czasu i duplikacji.</span><span class="sxs-lookup"><span data-stu-id="e997d-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="e997d-279">Ponadto można utworzyć drzewa dziedziczenia atrybutów niestandardowych, aby umożliwić stosowanie odmian.</span><span class="sxs-lookup"><span data-stu-id="e997d-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="e997d-280">Aby utworzyć opcjonalne metadane w atrybucie niestandardowym, można użyć atrybutu `DefaultValue`.</span><span class="sxs-lookup"><span data-stu-id="e997d-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="e997d-281">Gdy ten atrybut jest stosowany do właściwości w klasie atrybutów niestandardowych, określa, że właściwość dekoracyjna jest opcjonalna i nie musi być dostarczana przez eksportera.</span><span class="sxs-lookup"><span data-stu-id="e997d-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="e997d-282">Jeśli wartość właściwości nie zostanie podana, zostanie przypisana wartość domyślna dla jej typu właściwości (zwykle `null`, `false`lub 0).</span><span class="sxs-lookup"><span data-stu-id="e997d-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="e997d-283">Zasady tworzenia</span><span class="sxs-lookup"><span data-stu-id="e997d-283">Creation Policies</span></span>

<span data-ttu-id="e997d-284">Gdy część określa Importowanie i składanie jest wykonywane, kontener kompozycji próbuje znaleźć pasujący eksport.</span><span class="sxs-lookup"><span data-stu-id="e997d-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="e997d-285">Jeśli dopasowanie zostanie zakończone pomyślnie, element członkowski importu jest ustawiany na wystąpienie wyeksportowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e997d-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="e997d-286">Miejsce, z którego pochodzi to wystąpienie, jest kontrolowane przez *zasady tworzenia*części eksportu.</span><span class="sxs-lookup"><span data-stu-id="e997d-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="e997d-287">Dwie możliwe zasady tworzenia są *udostępniane* i *nie są udostępniane*.</span><span class="sxs-lookup"><span data-stu-id="e997d-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="e997d-288">Część z zasadami tworzenia udostępnioną zostanie udostępniona między każdym importem w kontenerze a częścią tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e997d-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="e997d-289">Gdy aparat kompozycji znajdzie dopasowanie i ma ustawić właściwość importowania, utworzy wystąpienie nowej kopii części tylko wtedy, gdy jeszcze nie istnieje; w przeciwnym razie dostarczy istniejącą kopię.</span><span class="sxs-lookup"><span data-stu-id="e997d-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="e997d-290">Oznacza to, że wiele obiektów może odwoływać się do tej samej części.</span><span class="sxs-lookup"><span data-stu-id="e997d-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="e997d-291">Takie części nie powinny polegać na stanie wewnętrznym, który można zmienić z wielu miejsc.</span><span class="sxs-lookup"><span data-stu-id="e997d-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="e997d-292">Te zasady są odpowiednie dla części statycznych, części, które udostępniają usługi, i części, które zużywają wiele pamięci lub innych zasobów.</span><span class="sxs-lookup"><span data-stu-id="e997d-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="e997d-293">Część z zasadami tworzenia nieudostępnianych elementów zostanie utworzona za każdym razem, gdy zostanie znaleziony pasujący import dla jednego z jego eksportu.</span><span class="sxs-lookup"><span data-stu-id="e997d-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="e997d-294">W związku z tym zostanie utworzona nowa kopia dla każdego importu w kontenerze, który jest zgodny z jedną z kontraktów eksportu części.</span><span class="sxs-lookup"><span data-stu-id="e997d-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="e997d-295">Wewnętrzny stan tych kopii nie zostanie udostępniony.</span><span class="sxs-lookup"><span data-stu-id="e997d-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="e997d-296">Te zasady są odpowiednie dla części, w których każdy import wymaga własnego stanu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="e997d-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="e997d-297">Zarówno import, jak i eksport mogą określać zasady tworzenia części, spośród wartości `Shared`, `NonShared`lub `Any`.</span><span class="sxs-lookup"><span data-stu-id="e997d-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="e997d-298">Wartość domyślna to `Any` dla importu i eksportu.</span><span class="sxs-lookup"><span data-stu-id="e997d-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="e997d-299">Eksport, który określa `Shared` lub `NonShared`, będzie zgodny z importem, który określa ten sam element lub określa `Any`.</span><span class="sxs-lookup"><span data-stu-id="e997d-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="e997d-300">Podobnie importowanie, które określa `Shared` lub `NonShared`, będzie zgodne z eksportem, który określa ten sam element lub określa `Any`.</span><span class="sxs-lookup"><span data-stu-id="e997d-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="e997d-301">Importy i eksporty z niezgodnymi zasadami tworzenia nie są uważane za pasujące w taki sam sposób jak Importowanie i eksportowanie, których nazwa kontraktu lub typ kontraktu nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="e997d-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="e997d-302">Jeśli dla elementu import i Export określono `Any`lub nie określisz zasad tworzenia i domyślna wartość `Any`, zasady tworzenia zostaną domyślnie udostępnione.</span><span class="sxs-lookup"><span data-stu-id="e997d-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="e997d-303">W poniższym przykładzie pokazano import i eksporty określające zasady tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e997d-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="e997d-304">`PartOne` nie określa zasad tworzenia, dlatego wartość domyślna to `Any`.</span><span class="sxs-lookup"><span data-stu-id="e997d-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="e997d-305">`PartTwo` nie określa zasad tworzenia, dlatego wartość domyślna to `Any`.</span><span class="sxs-lookup"><span data-stu-id="e997d-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="e997d-306">Ponieważ domyślne wartości import i Export są `Any`, `PartOne` zostanie udostępniona.</span><span class="sxs-lookup"><span data-stu-id="e997d-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="e997d-307">`PartThree` określa zasady tworzenia `Shared`, dlatego `PartTwo` i `PartThree` będą współużytkować tę samą kopię `PartOne`.</span><span class="sxs-lookup"><span data-stu-id="e997d-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="e997d-308">`PartFour` określa zasady tworzenia `NonShared`, dlatego `PartFour` nie będą udostępniane w `PartFive`.</span><span class="sxs-lookup"><span data-stu-id="e997d-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="e997d-309">`PartSix` określa `NonShared` zasady tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e997d-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="e997d-310">`PartFive` i `PartSix` otrzymają osobne kopie `PartFour`.</span><span class="sxs-lookup"><span data-stu-id="e997d-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="e997d-311">`PartSeven` określa `Shared` zasady tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e997d-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="e997d-312">Ponieważ nie ma żadnych wyeksportowanych `PartFour` z zasadami tworzenia `Shared`, import `PartSeven` nie pasuje do żadnego elementu i nie zostanie wypełniony.</span><span class="sxs-lookup"><span data-stu-id="e997d-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

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

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="e997d-313">Cykl życia i usuwanie</span><span class="sxs-lookup"><span data-stu-id="e997d-313">Life Cycle and Disposing</span></span>

<span data-ttu-id="e997d-314">Ponieważ części są hostowane w kontenerze kompozycji, ich cykl życia może być bardziej skomplikowany niż zwykłe obiekty.</span><span class="sxs-lookup"><span data-stu-id="e997d-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="e997d-315">Części mogą zaimplementować dwa ważne interfejsy związane z cyklem życia: `IDisposable` i `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="e997d-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="e997d-316">Części, które wymagają wykonania pracy przy zamknięciu lub które wymagają zwolnienia zasobów, powinny implementować `IDisposable`, jak zwykle w przypadku obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e997d-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="e997d-317">Jednak ponieważ kontener tworzy i zachowuje odwołania do części, tylko kontener, do którego należy część, powinien wywołać metodę `Dispose`.</span><span class="sxs-lookup"><span data-stu-id="e997d-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="e997d-318">Kontener implementuje `IDisposable`i jako część jego oczyszczania w `Dispose` wywoła `Dispose` na wszystkich częściach, do których należy.</span><span class="sxs-lookup"><span data-stu-id="e997d-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="e997d-319">Z tego powodu zawsze należy usunąć kontener kompozycji, gdy nie są już potrzebne wszystkie jego części.</span><span class="sxs-lookup"><span data-stu-id="e997d-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="e997d-320">W przypadku kontenerów o długim okresie ważności użycie pamięci przez części z zasadami tworzenia nieudostępnianych może stać się problemem.</span><span class="sxs-lookup"><span data-stu-id="e997d-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="e997d-321">Te części nieudostępnione mogą być tworzone wiele razy i nie zostaną usunięte do momentu usunięcia kontenera.</span><span class="sxs-lookup"><span data-stu-id="e997d-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="e997d-322">W tym celu kontener udostępnia metodę `ReleaseExport`.</span><span class="sxs-lookup"><span data-stu-id="e997d-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="e997d-323">Wywołanie tej metody w wywozie nieudostępnionym spowoduje usunięcie tego eksportu z kontenera kompozycji i usunięcia go.</span><span class="sxs-lookup"><span data-stu-id="e997d-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="e997d-324">Części, które są używane tylko przez usunięty eksport, i tak dalej na drzewie, również zostaną usunięte i usunięte.</span><span class="sxs-lookup"><span data-stu-id="e997d-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="e997d-325">W ten sposób zasoby mogą być odzyskiwane bez usuwania kontenera kompozycji.</span><span class="sxs-lookup"><span data-stu-id="e997d-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="e997d-326">`IPartImportsSatisfiedNotification` zawiera jedną metodę o nazwie `OnImportsSatisfied`.</span><span class="sxs-lookup"><span data-stu-id="e997d-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="e997d-327">Ta metoda jest wywoływana przez kontener kompozycji dla każdej części implementującej interfejs, gdy kompozycja została ukończona, a Importy części są gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="e997d-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="e997d-328">Części są tworzone przez aparat kompozycji, aby wypełnić Importy innych części.</span><span class="sxs-lookup"><span data-stu-id="e997d-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="e997d-329">Przed ustawieniem importu części nie można wykonać inicjalizacji, która polega na zaimportowaniu wartości i manipulowaniu nimi w konstruktorze częściowym, chyba że te wartości zostały określone jako wymagania wstępne przy użyciu atrybutu `ImportingConstructor`.</span><span class="sxs-lookup"><span data-stu-id="e997d-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="e997d-330">Zwykle jest to preferowana metoda, ale w niektórych przypadkach iniekcja konstruktora może być niedostępna.</span><span class="sxs-lookup"><span data-stu-id="e997d-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="e997d-331">W takich przypadkach Inicjalizacja może być wykonywana w `OnImportsSatisfied`, a część powinna implementować `IPartImportsSatisfiedNotification`.</span><span class="sxs-lookup"><span data-stu-id="e997d-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e997d-332">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e997d-332">See also</span></span>

- [<span data-ttu-id="e997d-333">Wideo Channel 9: Otwieranie aplikacji za pomocą Managed Extensibility Framework</span><span class="sxs-lookup"><span data-stu-id="e997d-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="e997d-334">Wideo Channel 9: Managed Extensibility Framework (MEF) 2,0</span><span class="sxs-lookup"><span data-stu-id="e997d-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
