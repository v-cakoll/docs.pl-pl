---
title: 'Atrybuty zastrzeżone języka C#: śledzenie informacji o dzwoniącym'
ms.date: 04/09/2020
description: Te atrybuty instruują kompilator do generowania informacji o kodzie, który wywołuje członka. Do dostarczania szczegółowych informacji śledzenia za pomocą callerfilepath, CallerLineNumber i CallerMemberName
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389878"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="7d641-104">Atrybuty zarezerwowane: określanie informacji o dzwoniącym</span><span class="sxs-lookup"><span data-stu-id="7d641-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="7d641-105">Za pomocą atrybutów informacji można uzyskać informacje o wywołującym do metody.</span><span class="sxs-lookup"><span data-stu-id="7d641-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="7d641-106">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę członka wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7d641-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="7d641-107">Aby uzyskać informacje o wywołującym element członkowski, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="7d641-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="7d641-108">Każdy parametr opcjonalny określa wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="7d641-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="7d641-109">W poniższej tabeli wymieniono atrybuty <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informacje o dzwoniącym zdefiniowane w obszarze nazw:</span><span class="sxs-lookup"><span data-stu-id="7d641-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="7d641-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d641-110">Attribute</span></span>|<span data-ttu-id="7d641-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7d641-111">Description</span></span>|<span data-ttu-id="7d641-112">Typ</span><span class="sxs-lookup"><span data-stu-id="7d641-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="7d641-113">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="7d641-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="7d641-114">Pełna ścieżka jest ścieżką w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7d641-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="7d641-115">Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.</span><span class="sxs-lookup"><span data-stu-id="7d641-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="7d641-116">Nazwa metody lub nazwa właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7d641-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="7d641-117">Te informacje ułatwiają pisanie śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="7d641-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="7d641-118">W poniższym przykładzie pokazano, jak używać atrybutów informacji o wywołującym.</span><span class="sxs-lookup"><span data-stu-id="7d641-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="7d641-119">Przy każdym wywołaniu `TraceMessage` metody informacje o wywołującym są zastępowane jako argumenty parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="7d641-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="7d641-120">Można określić jawną wartość domyślną dla każdego parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="7d641-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="7d641-121">Nie można zastosować atrybutów informacji o wywołującym do parametrów, które nie są określone jako opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7d641-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="7d641-122">Atrybuty informacji wywołującego nie sprawiają, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7d641-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="7d641-123">Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="7d641-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="7d641-124">Wartości informacji wywołującego są emitowane jako literały do języka pośredniego (IL) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7d641-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="7d641-125">W przeciwieństwie do <xref:System.Exception.StackTrace%2A> wyników właściwości dla wyjątków, wyniki nie są narażone na zaciemnienie.</span><span class="sxs-lookup"><span data-stu-id="7d641-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="7d641-126">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="7d641-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="7d641-127">Nazwy członków</span><span class="sxs-lookup"><span data-stu-id="7d641-127">Member names</span></span>

<span data-ttu-id="7d641-128">Można użyć `CallerMemberName` atrybutu, aby uniknąć określania `String` nazwy elementu członkowskiego jako argumentu do metody wywoływane.</span><span class="sxs-lookup"><span data-stu-id="7d641-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="7d641-129">Korzystając z tej techniki, można uniknąć problemu, który **rename refaktoryzacji** nie zmienia `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="7d641-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="7d641-130">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="7d641-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="7d641-131">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="7d641-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="7d641-132">Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="7d641-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="7d641-133">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="7d641-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="7d641-134">Bez `CallerMemberName` atrybutu należy określić nazwę właściwości jako literał.</span><span class="sxs-lookup"><span data-stu-id="7d641-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="7d641-135">Na poniższym wykresie przedstawiono nazwy członków, które są zwracane podczas korzystania z atrybutu. `CallerMemberName`</span><span class="sxs-lookup"><span data-stu-id="7d641-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="7d641-136">Połączenia następować są w ciągu</span><span class="sxs-lookup"><span data-stu-id="7d641-136">Calls occur within</span></span>|<span data-ttu-id="7d641-137">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="7d641-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="7d641-138">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="7d641-138">Method, property, or event</span></span>|<span data-ttu-id="7d641-139">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="7d641-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="7d641-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="7d641-140">Constructor</span></span>|<span data-ttu-id="7d641-141">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="7d641-141">The string ".ctor"</span></span>|
|<span data-ttu-id="7d641-142">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="7d641-142">Static constructor</span></span>|<span data-ttu-id="7d641-143">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="7d641-143">The string ".cctor"</span></span>|
|<span data-ttu-id="7d641-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="7d641-144">Destructor</span></span>|<span data-ttu-id="7d641-145">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="7d641-145">The string "Finalize"</span></span>|
|<span data-ttu-id="7d641-146">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="7d641-146">User-defined operators or conversions</span></span>|<span data-ttu-id="7d641-147">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="7d641-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="7d641-148">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="7d641-148">Attribute constructor</span></span>|<span data-ttu-id="7d641-149">Nazwa metody lub właściwości, do której jest stosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="7d641-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="7d641-150">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="7d641-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="7d641-151">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="7d641-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="7d641-152">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="7d641-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7d641-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d641-153">See also</span></span>

- [<span data-ttu-id="7d641-154">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="7d641-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="7d641-155">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d641-155">Attributes</span></span>](../../../standard/attributes/index.md)
