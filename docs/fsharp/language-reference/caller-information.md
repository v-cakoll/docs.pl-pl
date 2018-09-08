---
title: 'Informacje o wywołującym (F #)'
description: Opisuje sposób używania Caller — atrybuty Argument informacji, aby uzyskać informacje o wywołującym z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 0f2f4b16804d9156d234cc29d1f72ebe80a5b556
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185487"
---
# <a name="caller-information"></a><span data-ttu-id="57421-103">Informacje o wywołującym</span><span class="sxs-lookup"><span data-stu-id="57421-103">Caller information</span></span>

<span data-ttu-id="57421-104">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="57421-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="57421-105">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="57421-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="57421-106">Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="57421-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="57421-107">Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="57421-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="57421-108">W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="57421-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="57421-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="57421-109">Attribute</span></span>|<span data-ttu-id="57421-110">Opis</span><span class="sxs-lookup"><span data-stu-id="57421-110">Description</span></span>|<span data-ttu-id="57421-111">Typ</span><span class="sxs-lookup"><span data-stu-id="57421-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="57421-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="57421-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="57421-113">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="57421-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="57421-114">Jest to ścieżka pliku w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="57421-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="57421-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="57421-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="57421-116">Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="57421-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="57421-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="57421-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="57421-118">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="57421-118">Method or property name of the caller.</span></span> <span data-ttu-id="57421-119">Zobacz sekcję nazwy elementów członkowskich w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="57421-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="57421-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="57421-120">Example</span></span>

<span data-ttu-id="57421-121">Poniższy przykład pokazuje, jak można wykorzystać te atrybuty do śledzenia obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="57421-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="57421-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57421-122">Remarks</span></span>

<span data-ttu-id="57421-123">Caller — atrybuty informacji dotyczą wyłącznie następujące parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="57421-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="57421-124">Należy podać wartość dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="57421-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="57421-125">Atrybuty informacji o obiekcie wywołującym spowodować, że kompilator, aby zapisać odpowiednie wartości dla każdego opcjonalnego parametru dekorowane za pomocą atrybutów informacji o obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="57421-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="57421-126">Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="57421-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="57421-127">W przeciwieństwie do wyników [ślad stosu](/dotnet/api/system.diagnostics.stacktrace) właściwość dla wyjątków, na wyniki nie ma wpływu zasłanianie.</span><span class="sxs-lookup"><span data-stu-id="57421-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="57421-128">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="57421-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="57421-129">Nazwy elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="57421-129">Member names</span></span>

<span data-ttu-id="57421-130">Możesz użyć [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, aby uniknąć określania nazwy elementu członkowskiego jako `String` argument wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="57421-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="57421-131">Korzystając z tej techniki, można uniknąć problemu, który Refaktoryzacja zmiany nazwy nie zmienia `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="57421-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="57421-132">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="57421-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="57421-133">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="57421-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="57421-134">Implementowanie [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interfejs podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="57421-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="57421-135">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="57421-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="57421-136">Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, należy określić nazwę właściwości jako literał.</span><span class="sxs-lookup"><span data-stu-id="57421-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="57421-137">Na poniższym wykresie przedstawiono elementu członkowskiego nazw, które są zwracane, gdy używasz atrybutu CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="57421-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="57421-138">Wywołanie ma miejsce w</span><span class="sxs-lookup"><span data-stu-id="57421-138">Calls occurs within</span></span>|<span data-ttu-id="57421-139">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="57421-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="57421-140">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="57421-140">Method, property, or event</span></span>|<span data-ttu-id="57421-141">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="57421-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="57421-142">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="57421-142">Constructor</span></span>|<span data-ttu-id="57421-143">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="57421-143">The string ".ctor"</span></span>|
|<span data-ttu-id="57421-144">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="57421-144">Static constructor</span></span>|<span data-ttu-id="57421-145">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="57421-145">The string ".cctor"</span></span>|
|<span data-ttu-id="57421-146">Destruktor</span><span class="sxs-lookup"><span data-stu-id="57421-146">Destructor</span></span>|<span data-ttu-id="57421-147">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="57421-147">The string "Finalize"</span></span>|
|<span data-ttu-id="57421-148">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="57421-148">User-defined operators or conversions</span></span>|<span data-ttu-id="57421-149">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="57421-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="57421-150">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="57421-150">Attribute constructor</span></span>|<span data-ttu-id="57421-151">Nazwa elementu członkowskiego, do którego został zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="57421-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="57421-152">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="57421-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="57421-153">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="57421-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="57421-154">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="57421-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="57421-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57421-155">See also</span></span>

- [<span data-ttu-id="57421-156">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57421-156">Attributes</span></span>](attributes.md)  
- [<span data-ttu-id="57421-157">Argumenty nazwane</span><span class="sxs-lookup"><span data-stu-id="57421-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
- [<span data-ttu-id="57421-158">Następujące parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="57421-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
