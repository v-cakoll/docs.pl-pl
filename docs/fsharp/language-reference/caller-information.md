---
title: "Informacje o wywołującym (F #)"
description: "Informacje dotyczące używania Caller — atrybuty Argument informacji, aby uzyskać informacje o wywołującym z metody."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a><span data-ttu-id="79647-104">Informacje o wywołującym</span><span class="sxs-lookup"><span data-stu-id="79647-104">Caller information</span></span>

<span data-ttu-id="79647-105">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="79647-105">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="79647-106">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="79647-106">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="79647-107">Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="79647-107">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="79647-108">Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="79647-108">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="79647-109">Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="79647-109">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="79647-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="79647-110">Attribute</span></span>|<span data-ttu-id="79647-111">Opis</span><span class="sxs-lookup"><span data-stu-id="79647-111">Description</span></span>|<span data-ttu-id="79647-112">Typ</span><span class="sxs-lookup"><span data-stu-id="79647-112">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="79647-113">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="79647-113">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="79647-114">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="79647-114">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="79647-115">Jest to ścieżka pliku w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="79647-115">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="79647-116">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="79647-116">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="79647-117">Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="79647-117">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="79647-118">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="79647-118">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="79647-119">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="79647-119">Method or property name of the caller.</span></span> <span data-ttu-id="79647-120">Zobacz sekcję nazwy elementów członkowskich w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="79647-120">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="79647-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="79647-121">Example</span></span>

<span data-ttu-id="79647-122">Poniższy przykład pokazuje, jak można użyć tych atrybutów do śledzenia obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="79647-122">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="79647-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79647-123">Remarks</span></span>

<span data-ttu-id="79647-124">Caller — atrybuty informacji dotyczą wyłącznie następujące parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="79647-124">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="79647-125">Należy podać wartość dla każdego parametru opcjonalnego.</span><span class="sxs-lookup"><span data-stu-id="79647-125">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="79647-126">Atrybuty informacji wywołującego spowodować kompilator, aby zapisać poprawną wartość dla każdego parametru opcjonalnego oznaczone atrybutem wywołującego informacji.</span><span class="sxs-lookup"><span data-stu-id="79647-126">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="79647-127">Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="79647-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="79647-128">W odróżnieniu od wyników [ślad stosu](/dotnet/api/system.diagnostics.stacktrace) właściwości wyjątki, wyniki nie dotyczą zaciemnienie.</span><span class="sxs-lookup"><span data-stu-id="79647-128">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="79647-129">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="79647-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="79647-130">Nazwy elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="79647-130">Member names</span></span>

<span data-ttu-id="79647-131">Można użyć [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, aby uniknąć, określając nazwę elementu członkowskiego jako `String` argument wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="79647-131">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="79647-132">Przy użyciu tej metody, można uniknąć problemu, który nie zmieniają się zmienić refaktoryzacji `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="79647-132">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="79647-133">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="79647-133">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="79647-134">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="79647-134">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="79647-135">Implementowanie [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interfejsu podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="79647-135">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="79647-136">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="79647-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="79647-137">Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atrybutu, należy określić nazwę właściwości jako literału.</span><span class="sxs-lookup"><span data-stu-id="79647-137">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="79647-138">W poniższej tabeli przedstawiono element członkowski nazw, które są zwracane, gdy Użyj atrybutu CallerMemberName.</span><span class="sxs-lookup"><span data-stu-id="79647-138">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="79647-139">Wywołanie ma miejsce w</span><span class="sxs-lookup"><span data-stu-id="79647-139">Calls occurs within</span></span>|<span data-ttu-id="79647-140">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="79647-140">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="79647-141">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="79647-141">Method, property, or event</span></span>|<span data-ttu-id="79647-142">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="79647-142">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="79647-143">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="79647-143">Constructor</span></span>|<span data-ttu-id="79647-144">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="79647-144">The string ".ctor"</span></span>|
|<span data-ttu-id="79647-145">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="79647-145">Static constructor</span></span>|<span data-ttu-id="79647-146">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="79647-146">The string ".cctor"</span></span>|
|<span data-ttu-id="79647-147">Destruktor</span><span class="sxs-lookup"><span data-stu-id="79647-147">Destructor</span></span>|<span data-ttu-id="79647-148">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="79647-148">The string "Finalize"</span></span>|
|<span data-ttu-id="79647-149">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="79647-149">User-defined operators or conversions</span></span>|<span data-ttu-id="79647-150">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="79647-150">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="79647-151">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="79647-151">Attribute constructor</span></span>|<span data-ttu-id="79647-152">Nazwa elementu członkowskiego, do którego został zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="79647-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="79647-153">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="79647-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="79647-154">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="79647-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="79647-155">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="79647-155">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="79647-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79647-156">See also</span></span>
 [<span data-ttu-id="79647-157">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79647-157">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="79647-158">Argumenty nazwane</span><span class="sxs-lookup"><span data-stu-id="79647-158">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="79647-159">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="79647-159">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
