---
title: Rozwiązywanie załadowań zestawów
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156442"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="83f62-102">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="83f62-102">Resolve assembly loads</span></span>
<span data-ttu-id="83f62-103">Platforma .NET udostępnia zdarzenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> dla aplikacji, które wymagają większej kontroli nad ładowaniem zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f62-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="83f62-104">Dzięki obsłudze tego zdarzenia aplikacja może załadować zestaw do kontekstu obciążenia spoza normalnej ścieżki sondowania, wybrać kilka wersji zestawu do załadowania, emitować zestaw dynamiczny i zwrócić go i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="83f62-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="83f62-105">Ten temat zawiera wskazówki dotyczące obsługi zdarzenia <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="83f62-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83f62-106">W celu rozpoznawania obciążeń zestawów w kontekście tylko odbicia należy zamiast tego użyć zdarzenia <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83f62-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="83f62-107">Jak działa zdarzenie AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="83f62-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="83f62-108">Po zarejestrowaniu procedury obsługi dla zdarzenia <xref:System.AppDomain.AssemblyResolve>, procedura obsługi jest wywoływana za każdym razem, gdy środowisko uruchomieniowe nie uda się powiązać z zestawem według nazwy.</span><span class="sxs-lookup"><span data-stu-id="83f62-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="83f62-109">Na przykład wywoływanie następujących metod z kodu użytkownika może spowodować podniesienie poziomu zdarzenia <xref:System.AppDomain.AssemblyResolve>:</span><span class="sxs-lookup"><span data-stu-id="83f62-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="83f62-110"><xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> Przeciążenie metody, których pierwszy argument jest ciągiem, który reprezentuje nazwę wyświetlaną zestawu do załadowania (czyli ciąg zwracany przez właściwość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="83f62-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="83f62-111">Przeciążenie metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> lub przeciążenia metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, których pierwszy argument jest obiektem <xref:System.Reflection.AssemblyName>, który identyfikuje zestaw do załadowania.</span><span class="sxs-lookup"><span data-stu-id="83f62-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="83f62-112">Przeciążenie metody <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83f62-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="83f62-113">Przeciążanie metody <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>, które tworzy wystąpienie obiektu w innej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83f62-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="83f62-114">Działanie programu obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="83f62-114">What the event handler does</span></span>  
 <span data-ttu-id="83f62-115">Procedura obsługi dla zdarzenia <xref:System.AppDomain.AssemblyResolve> otrzymuje nazwę wyświetlaną zestawu, który ma zostać załadowany, we właściwości <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83f62-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="83f62-116">Jeśli program obsługi nie rozpoznaje nazwy zestawu, zwraca `null` (C#), `Nothing` (Visual Basic) lub `nullptr` (wizualizacja C++).</span><span class="sxs-lookup"><span data-stu-id="83f62-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="83f62-117">Jeśli program obsługi rozpoznaje nazwę zestawu, może ładować i zwracać zestaw, który spełnia żądanie.</span><span class="sxs-lookup"><span data-stu-id="83f62-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="83f62-118">Na poniższej liście opisano kilka przykładowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="83f62-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="83f62-119">Jeśli program obsługi wie lokalizację wersji zestawu, może załadować zestaw za pomocą metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> i może zwrócić załadowany zestaw, jeśli zakończono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="83f62-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="83f62-120">Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywanych jako tablice bajtowe, może załadować tablicę bajtową przy użyciu jednego z przeciążeń metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, które pobierają tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="83f62-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="83f62-121">Program obsługi może wygenerować zestaw dynamiczny i zwrócić go.</span><span class="sxs-lookup"><span data-stu-id="83f62-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83f62-122">Program obsługi musi załadować zestaw do kontekstu ładowania z w kontekście ładowania lub bez kontekstu. Jeśli program obsługi ładuje zestaw do kontekstu tylko odbicie przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> lub metody <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, próba załadowania, która wywołała zdarzenie <xref:System.AppDomain.AssemblyResolve>, kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="83f62-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="83f62-123">Do zwrócenia odpowiedniego zestawu jest odpowiedzialna procedura obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83f62-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="83f62-124">Program obsługi może przeanalizować nazwę wyświetlaną żądanego zestawu, przekazując wartość właściwości <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> do konstruktora <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="83f62-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="83f62-125">Począwszy od .NET Framework 4, program obsługi może użyć właściwości <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>, aby określić, czy bieżące żądanie jest zależne od innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f62-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="83f62-126">Te informacje mogą ułatwić zidentyfikowanie zestawu, który będzie spełniał zależność.</span><span class="sxs-lookup"><span data-stu-id="83f62-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="83f62-127">Program obsługi zdarzeń może zwrócić inną wersję zestawu niż żądana wersja.</span><span class="sxs-lookup"><span data-stu-id="83f62-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="83f62-128">W większości przypadków zestaw, który jest zwracany przez program obsługi, pojawia się w kontekście ładowania, niezależnie od kontekstu, w którym program obsługi ładuje go do.</span><span class="sxs-lookup"><span data-stu-id="83f62-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="83f62-129">Jeśli na przykład program obsługi używa metody <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> do załadowania zestawu do kontekstu ładowania z, zestaw pojawia się w kontekście ładowania, gdy program obsługi zwróci go.</span><span class="sxs-lookup"><span data-stu-id="83f62-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="83f62-130">Jednak w poniższym przypadku zestaw pojawia się bez kontekstu, gdy program obsługi zwróci go:</span><span class="sxs-lookup"><span data-stu-id="83f62-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="83f62-131">Procedura obsługi ładuje zestaw bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="83f62-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="83f62-132">Właściwość <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="83f62-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="83f62-133">Zestaw żądający (czyli zestaw, który jest zwracany przez właściwość <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) został załadowany bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="83f62-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="83f62-134">Aby uzyskać informacje na temat kontekstów, zobacz Przeciążenie metody <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83f62-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="83f62-135">Wiele wersji tego samego zestawu może być załadowanych do tej samej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83f62-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="83f62-136">Ta metoda nie jest zalecana, ponieważ może to prowadzić do problemów z przypisaniem.</span><span class="sxs-lookup"><span data-stu-id="83f62-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="83f62-137">Zapoznaj się z [najlepszymi rozwiązaniami dotyczącymi ładowania zestawu](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="83f62-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="83f62-138">Czego nie powinien wykonać program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="83f62-138">What the event handler should not do</span></span>  
<span data-ttu-id="83f62-139">Podstawową regułą obsługi zdarzenia <xref:System.AppDomain.AssemblyResolve> jest to, że nie należy próbować zwrócić zestawu, który nie jest rozpoznawany.</span><span class="sxs-lookup"><span data-stu-id="83f62-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="83f62-140">Podczas pisania procedury obsługi należy wiedzieć, które zestawy mogą spowodować podniesienie poziomu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="83f62-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="83f62-141">Program obsługi powinien zwrócić wartość null dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="83f62-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="83f62-142">Począwszy od .NET Framework 4, zdarzenie <xref:System.AppDomain.AssemblyResolve> jest zgłaszane dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="83f62-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="83f62-143">Ta zmiana ma wpływ na procedurę obsługi zdarzeń, która została zapisywana dla starszej wersji .NET Framework, jeśli program obsługi podejmie próbę rozpoznania wszystkich żądań ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="83f62-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="83f62-144">Procedury obsługi zdarzeń, które ignorują zestawy, które nie są rozpoznawane, nie mają wpływ na tę zmianę: zwracają wartości null i są stosowane normalne mechanizmy powrotu.</span><span class="sxs-lookup"><span data-stu-id="83f62-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="83f62-145">Podczas ładowania zestawu, procedura obsługi zdarzeń nie może używać żadnych przeciążeń metody <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, które mogą spowodować rekursywne zdarzenie <xref:System.AppDomain.AssemblyResolve>, ponieważ może to prowadzić do przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="83f62-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="83f62-146">(Zobacz listę znajdującą się wcześniej w tym temacie). Dzieje się tak nawet wtedy, gdy podajesz obsługę wyjątków dla żądania ładowania, ponieważ żaden wyjątek nie jest zgłaszany do momentu zwrócenia wszystkich programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83f62-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="83f62-147">W rezultacie następujący kod powoduje przepełnienie stosu, jeśli nie można odnaleźć `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="83f62-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="83f62-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83f62-148">See also</span></span>

- [<span data-ttu-id="83f62-149">Najlepsze rozwiązania dotyczące ładowania zestawów</span><span class="sxs-lookup"><span data-stu-id="83f62-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="83f62-150">Korzystanie z domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="83f62-150">Use application domains</span></span>](../../framework/app-domains/use.md)
