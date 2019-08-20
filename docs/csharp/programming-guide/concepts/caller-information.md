---
title: Informacje o obiekcieC#wywołującym ()
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595340"
---
# <a name="caller-information-c"></a><span data-ttu-id="8cc3c-102">Informacje o obiekcieC#wywołującym ()</span><span class="sxs-lookup"><span data-stu-id="8cc3c-102">Caller Information (C#)</span></span>

<span data-ttu-id="8cc3c-103">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="8cc3c-104">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="8cc3c-105">Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="8cc3c-106">Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="8cc3c-107">W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> zdefiniowane w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="8cc3c-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="8cc3c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8cc3c-108">Attribute</span></span>|<span data-ttu-id="8cc3c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8cc3c-109">Description</span></span>|<span data-ttu-id="8cc3c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="8cc3c-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="8cc3c-111">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="8cc3c-112">Jest to ścieżka pliku w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="8cc3c-113">Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="8cc3c-114">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-114">Method or property name of the caller.</span></span> <span data-ttu-id="8cc3c-115">Zobacz [nazwy członków](#member-names) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="8cc3c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cc3c-116">Example</span></span>

<span data-ttu-id="8cc3c-117">Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="8cc3c-118">Dla każdego wywołania `TraceMessage` metody informacje o wywołującym są zastępowane jako argumenty parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="8cc3c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cc3c-119">Remarks</span></span>

<span data-ttu-id="8cc3c-120">Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="8cc3c-121">Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="8cc3c-122">Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="8cc3c-123">Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="8cc3c-124">Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="8cc3c-125">W przeciwieństwie do wyników <xref:System.Exception.StackTrace%2A> właściwości dla wyjątków, nie ma to wpływu na wyniki.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="8cc3c-126">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="8cc3c-127">Nazwy elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="8cc3c-127">Member names</span></span>

<span data-ttu-id="8cc3c-128">Możesz użyć atrybutu, `CallerMemberName` aby uniknąć określania nazwy elementu członkowskiego `String` jako argumentu wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="8cc3c-129">Korzystając z tej techniki, można uniknąć problemu, którego **zmiana nazwy Refaktoryzacja** nie zmienia `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="8cc3c-130">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="8cc3c-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="8cc3c-131">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="8cc3c-132">Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="8cc3c-133">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="8cc3c-134">`CallerMemberName` Bez atrybutu, należy określić nazwę właściwości jako literału.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="8cc3c-135">Poniższy wykres pokazuje nazwy elementów członkowskich, które są zwracane przy użyciu `CallerMemberName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="8cc3c-136">Wywołanie ma miejsce w</span><span class="sxs-lookup"><span data-stu-id="8cc3c-136">Calls occurs within</span></span>|<span data-ttu-id="8cc3c-137">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="8cc3c-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="8cc3c-138">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="8cc3c-138">Method, property, or event</span></span>|<span data-ttu-id="8cc3c-139">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="8cc3c-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="8cc3c-140">Constructor</span></span>|<span data-ttu-id="8cc3c-141">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="8cc3c-141">The string ".ctor"</span></span>|
|<span data-ttu-id="8cc3c-142">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="8cc3c-142">Static constructor</span></span>|<span data-ttu-id="8cc3c-143">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="8cc3c-143">The string ".cctor"</span></span>|
|<span data-ttu-id="8cc3c-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="8cc3c-144">Destructor</span></span>|<span data-ttu-id="8cc3c-145">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-145">The string "Finalize"</span></span>|
|<span data-ttu-id="8cc3c-146">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="8cc3c-146">User-defined operators or conversions</span></span>|<span data-ttu-id="8cc3c-147">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="8cc3c-148">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="8cc3c-148">Attribute constructor</span></span>|<span data-ttu-id="8cc3c-149">Nazwa metody lub właściwości, do której zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="8cc3c-150">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="8cc3c-151">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="8cc3c-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="8cc3c-152">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="8cc3c-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8cc3c-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cc3c-153">See also</span></span>

- [<span data-ttu-id="8cc3c-154">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="8cc3c-154">Attributes (C#)</span></span>](./attributes/index.md)
- [<span data-ttu-id="8cc3c-155">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="8cc3c-155">Common Attributes (C#)</span></span>](./attributes/common-attributes.md)
- [<span data-ttu-id="8cc3c-156">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="8cc3c-156">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="8cc3c-157">Koncepcje programowaniaC#()</span><span class="sxs-lookup"><span data-stu-id="8cc3c-157">Programming Concepts (C#)</span></span>](./index.md)
