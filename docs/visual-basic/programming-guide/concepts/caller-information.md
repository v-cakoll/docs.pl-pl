---
title: Informacje o wywołującym
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 7c87b540a68f4d0219918fed66de6c1b635104a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349474"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="5f1c9-102">Informacje o wywołującym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f1c9-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="5f1c9-103">Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="5f1c9-104">Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="5f1c9-105">Te informacje są przydatne do śledzenia, debugowania i tworzenia narzędzi diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="5f1c9-106">Aby uzyskać te informacje, należy użyć atrybutów stosowanych do opcjonalnych parametrów, z których każdy ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="5f1c9-107">W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="5f1c9-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="5f1c9-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5f1c9-108">Attribute</span></span>|<span data-ttu-id="5f1c9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5f1c9-109">Description</span></span>|<span data-ttu-id="5f1c9-110">Type</span><span class="sxs-lookup"><span data-stu-id="5f1c9-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="5f1c9-111">Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="5f1c9-112">Jest to ścieżka pliku w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="5f1c9-113">Numer wiersza w pliku źródłowym, w którym to wierszu jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="5f1c9-114">Nazwa metody lub właściwości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-114">Method or property name of the caller.</span></span> <span data-ttu-id="5f1c9-115">Zobacz [nazwy członków](#MEMBERNAMES) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="5f1c9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f1c9-116">Example</span></span>  
 <span data-ttu-id="5f1c9-117">Poniższy przykład przedstawia, jak używać atrybutów informacji o obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="5f1c9-118">Dla każdego wywołania metody `TraceMessage` informacje o wywołującym są zastępowane jako argumenty parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f1c9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f1c9-119">Remarks</span></span>  
 <span data-ttu-id="5f1c9-120">Należy jawnie określić wartość domyślną dla każdego opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="5f1c9-121">Nie można zastosować atrybutów informacji o obiekcie wywołującym do parametrów, które nie są określone jako opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="5f1c9-122">Atrybuty informacji o obiekcie wywołującym nie czynią parametru opcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="5f1c9-123">Zamiast tego wpływają na domyślną wartość, która jest przekazywana, gdy argument zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="5f1c9-124">Wartości informacji o obiekcie wywołującym są emitowane jako literały do języka pośredniego (IL, Intermediate Language) w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="5f1c9-125">W przeciwieństwie do wyników właściwości <xref:System.Exception.StackTrace%2A> wyjątków, nie ma to wpływu na wyniki.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="5f1c9-126">Można jawnie dostarczyć opcjonalne argumenty do sterowania informacjami o obiekcie wywołującym lub ukryć te informacje.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="MEMBERNAMES"></a><span data-ttu-id="5f1c9-127">Nazwy elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="5f1c9-127">Member Names</span></span>  
 <span data-ttu-id="5f1c9-128">Można użyć atrybutu `CallerMemberName`, aby uniknąć określania nazwy elementu członkowskiego jako argumentu `String` dla wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="5f1c9-129">Korzystając z tej techniki, można uniknąć problemu, którego **Refaktoryzacja zmiany nazwy** nie zmienia wartości `String`.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="5f1c9-130">Jest to szczególnie przydatne w następujących zadaniach:</span><span class="sxs-lookup"><span data-stu-id="5f1c9-130">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="5f1c9-131">Używanie procedur do śledzenia i diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-131">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="5f1c9-132">Implementowanie interfejsu <xref:System.ComponentModel.INotifyPropertyChanged> podczas wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="5f1c9-133">Ten interfejs umożliwia właściwości obiektu powiadamianie powiązanego formantu, że właściwość zmieniła się, dzięki czemu formant może wyświetlić zaktualizowane informacje.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="5f1c9-134">Bez atrybutu `CallerMemberName` należy określić nazwę właściwości jako literału.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="5f1c9-135">Poniższy wykres pokazuje nazwy elementów członkowskich, które są zwracane przy użyciu atrybutu `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="5f1c9-136">Wywołanie ma miejsce w</span><span class="sxs-lookup"><span data-stu-id="5f1c9-136">Calls occurs within</span></span>|<span data-ttu-id="5f1c9-137">Wynikowa nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="5f1c9-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="5f1c9-138">Metoda, właściwość lub zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5f1c9-138">Method, property, or event</span></span>|<span data-ttu-id="5f1c9-139">Nazwa metody, właściwości lub zdarzenia, gdzie zainicjowane było wywołanie.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="5f1c9-140">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="5f1c9-140">Constructor</span></span>|<span data-ttu-id="5f1c9-141">Ciąg „.ctor”</span><span class="sxs-lookup"><span data-stu-id="5f1c9-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="5f1c9-142">Statyczny konstruktor</span><span class="sxs-lookup"><span data-stu-id="5f1c9-142">Static constructor</span></span>|<span data-ttu-id="5f1c9-143">Ciąg „.cctor”</span><span class="sxs-lookup"><span data-stu-id="5f1c9-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="5f1c9-144">Destruktor</span><span class="sxs-lookup"><span data-stu-id="5f1c9-144">Destructor</span></span>|<span data-ttu-id="5f1c9-145">Ciąg „Finalize”.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="5f1c9-146">Zdefiniowane przez użytkownika operatory lub konwersje</span><span class="sxs-lookup"><span data-stu-id="5f1c9-146">User-defined operators or conversions</span></span>|<span data-ttu-id="5f1c9-147">Nazwa wygenerowana dla elementu członkowskiego, na przykład „op_Addition”.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="5f1c9-148">Konstruktor atrybutu</span><span class="sxs-lookup"><span data-stu-id="5f1c9-148">Attribute constructor</span></span>|<span data-ttu-id="5f1c9-149">Nazwa elementu członkowskiego, do którego został zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="5f1c9-150">Jeśli atrybut jest dowolnym elementem elementu członkowskiego (takim jak parametr, wartość zwracana lub parametr typu ogólnego), to wynikiem jest nazwa elementu członkowskiego, który jest skojarzony z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="5f1c9-151">Brak nadrzędnego elementu członkowskiego (na przykład poziom zestawu lub atrybuty, które są stosowane do typów)</span><span class="sxs-lookup"><span data-stu-id="5f1c9-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="5f1c9-152">Wartość domyślna opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="5f1c9-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f1c9-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f1c9-153">See also</span></span>

- [<span data-ttu-id="5f1c9-154">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f1c9-154">Attributes (Visual Basic)</span></span>](../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="5f1c9-155">Atrybuty wspólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f1c9-155">Common Attributes (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="5f1c9-156">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="5f1c9-156">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="5f1c9-157">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f1c9-157">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
