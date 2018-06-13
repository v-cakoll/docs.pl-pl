---
title: Informacje o wywołującym (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 6f0cd4d9d8fc85cb15431ccb4c76eee14b3f67c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320693"
---
# <a name="caller-information-c"></a><span data-ttu-id="ceff3-102">Informacje o wywołującym (C#)</span><span class="sxs-lookup"><span data-stu-id="ceff3-102">Caller Information (C#)</span></span>
<span data-ttu-id="ceff3-103">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="ceff3-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="ceff3-104">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ceff3-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="ceff3-105">Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="ceff3-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="ceff3-106">Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="ceff3-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="ceff3-107">Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="ceff3-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="ceff3-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ceff3-108">Attribute</span></span>|<span data-ttu-id="ceff3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ceff3-109">Description</span></span>|<span data-ttu-id="ceff3-110">Typ</span><span class="sxs-lookup"><span data-stu-id="ceff3-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="ceff3-111">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="ceff3-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ceff3-112">Jest to ścieżka pliku w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ceff3-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="ceff3-113">Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="ceff3-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="ceff3-114">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ceff3-114">Method or property name of the caller.</span></span> <span data-ttu-id="ceff3-115">Zobacz [nazwy elementów członkowskich](#MEMBERNAMES) dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ceff3-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="ceff3-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ceff3-116">Example</span></span>  
 <span data-ttu-id="ceff3-117">Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="ceff3-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="ceff3-118">Na każde wywołanie `TraceMessage` zastępuje metodę, informacje o wywołującym jako argumenty następujące parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ceff3-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
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
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a><span data-ttu-id="ceff3-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ceff3-119">Remarks</span></span>  
 <span data-ttu-id="ceff3-120">Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="ceff3-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="ceff3-121">Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ceff3-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="ceff3-122">Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="ceff3-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="ceff3-123">Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="ceff3-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="ceff3-124">Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ceff3-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="ceff3-125">W odróżnieniu od wyników <xref:System.Exception.StackTrace%2A> właściwości wyjątki, wyniki nie dotyczą zaciemnienie.</span><span class="sxs-lookup"><span data-stu-id="ceff3-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="ceff3-126">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="ceff3-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <a name="MEMBERNAMES"></a> <span data-ttu-id="ceff3-127">Nazwy elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="ceff3-127">Member Names</span></span>  
 <span data-ttu-id="ceff3-128">Można użyć `CallerMemberName` atrybutu, aby uniknąć, określając nazwę elementu członkowskiego jako `String` argument wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="ceff3-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="ceff3-129">Przy użyciu tej metody, można uniknąć który **zmienić refaktoryzacji** nie ulega zmianie `String` wartości.</span><span class="sxs-lookup"><span data-stu-id="ceff3-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="ceff3-130">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="ceff3-130">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="ceff3-131">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="ceff3-131">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="ceff3-132">Implementowanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="ceff3-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="ceff3-133">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="ceff3-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="ceff3-134">Bez `CallerMemberName` atrybutu, należy określić nazwę właściwości jako literału.</span><span class="sxs-lookup"><span data-stu-id="ceff3-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="ceff3-135">W poniższej tabeli przedstawiono element członkowski nazw, które są zwracane, gdy używasz `CallerMemberName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ceff3-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="ceff3-136">Wywołanie ma miejsce w</span><span class="sxs-lookup"><span data-stu-id="ceff3-136">Calls occurs within</span></span>|<span data-ttu-id="ceff3-137">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ceff3-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="ceff3-138">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ceff3-138">Method, property, or event</span></span>|<span data-ttu-id="ceff3-139">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="ceff3-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="ceff3-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="ceff3-140">Constructor</span></span>|<span data-ttu-id="ceff3-141">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="ceff3-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="ceff3-142">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="ceff3-142">Static constructor</span></span>|<span data-ttu-id="ceff3-143">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="ceff3-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="ceff3-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="ceff3-144">Destructor</span></span>|<span data-ttu-id="ceff3-145">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="ceff3-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="ceff3-146">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="ceff3-146">User-defined operators or conversions</span></span>|<span data-ttu-id="ceff3-147">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="ceff3-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="ceff3-148">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="ceff3-148">Attribute constructor</span></span>|<span data-ttu-id="ceff3-149">Nazwa elementu członkowskiego, do którego został zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="ceff3-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="ceff3-150">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="ceff3-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="ceff3-151">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="ceff3-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="ceff3-152">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="ceff3-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceff3-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ceff3-153">See Also</span></span>  
 [<span data-ttu-id="ceff3-154">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="ceff3-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="ceff3-155">Atrybuty wspólne (C#)</span><span class="sxs-lookup"><span data-stu-id="ceff3-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
 [<span data-ttu-id="ceff3-156">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="ceff3-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="ceff3-157">Koncepcje programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="ceff3-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
