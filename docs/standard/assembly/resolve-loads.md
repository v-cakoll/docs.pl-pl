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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156442"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="3d618-102">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="3d618-102">Resolve assembly loads</span></span>
<span data-ttu-id="3d618-103">.NET udostępnia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie dla aplikacji, które wymagają większej kontroli nad ładowaniem zestawu.</span><span class="sxs-lookup"><span data-stu-id="3d618-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="3d618-104">Obsługując to zdarzenie, aplikacja może załadować zestaw do kontekstu obciążenia spoza normalnych ścieżek sondowania, wybrać, która z kilku wersji zestawu do załadowania, emitują zestaw dynamiczny i zwracają go i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3d618-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="3d618-105">W tym temacie przedstawiono <xref:System.AppDomain.AssemblyResolve> wskazówki dotyczące obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3d618-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d618-106">Do rozpoznawania obciążeń złożenia w kontekście <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> tylko do odbicia, należy użyć zdarzenia zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3d618-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="3d618-107">Jak działa zdarzenie AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="3d618-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="3d618-108">Podczas rejestrowania programu <xref:System.AppDomain.AssemblyResolve> obsługi dla zdarzenia, program obsługi jest wywoływany za każdym razem, gdy czas wykonywania nie powiedzie się powiązać z zestawem według nazwy.</span><span class="sxs-lookup"><span data-stu-id="3d618-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="3d618-109">Na przykład wywołanie następujących metod z kodu <xref:System.AppDomain.AssemblyResolve> użytkownika może spowodować zdarzenie, które mają być wywoływane:</span><span class="sxs-lookup"><span data-stu-id="3d618-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="3d618-110">Przeciążenie <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub przeciążenie metody, którego pierwszy argument jest ciągiem reprezentującym nazwę wyświetlaną zestawu <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> do załadowania (czyli ciąg zwrócony przez właściwość).</span><span class="sxs-lookup"><span data-stu-id="3d618-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="3d618-111">Przeciążenie <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub przeciążenie metody, którego pierwszy argument jest obiektem identyfikującym <xref:System.Reflection.AssemblyName> zestaw do załadowania.</span><span class="sxs-lookup"><span data-stu-id="3d618-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="3d618-112">Przeciążenie <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3d618-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="3d618-113">Przeciążenie <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> metoda, która tworzy obiekt w innej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d618-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="3d618-114">Co robi program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="3d618-114">What the event handler does</span></span>  
 <span data-ttu-id="3d618-115">Program obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenia odbiera nazwę wyświetlana zestawu, który <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> ma zostać załadowany we właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d618-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3d618-116">Jeśli program obsługi nie rozpoznaje nazwy `null` zestawu, zwraca `Nothing` (C#), `nullptr` (Visual Basic) lub (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="3d618-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="3d618-117">Jeśli program obsługi rozpoznaje nazwę zestawu, można załadować i zwrócić zestaw, który spełnia żądanie.</span><span class="sxs-lookup"><span data-stu-id="3d618-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="3d618-118">Na poniższej liście opisano niektóre przykładowe scenariusze.</span><span class="sxs-lookup"><span data-stu-id="3d618-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="3d618-119">Jeśli program obsługi zna lokalizację wersji zestawu, można załadować <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> zestawu przy użyciu lub metody i może zwrócić załadowany zestaw, jeśli zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3d618-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="3d618-120">Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywanych jako tablice bajtów, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> można załadować tablicy bajtów przy użyciu jednego z przeciążeń metody, które przyjmują tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="3d618-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="3d618-121">Program obsługi może wygenerować zestaw dynamiczny i zwrócić go.</span><span class="sxs-lookup"><span data-stu-id="3d618-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d618-122">Program obsługi musi załadować zestaw do kontekstu obciążenia z kontekstu, do kontekstu obciążenia lub bez kontekstu. Jeśli program obsługi ładuje zestaw do kontekstu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> tylko <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> do odbicia przy użyciu <xref:System.AppDomain.AssemblyResolve> lub metody, próba obciążenia, który wywołał zdarzenie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3d618-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="3d618-123">Jest odpowiedzialny za program obsługi zdarzeń, aby zwrócić odpowiedni zestaw.</span><span class="sxs-lookup"><span data-stu-id="3d618-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="3d618-124">Program obsługi można przeanalizować nazwę wyświetlaną żądanego <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> zestawu, przekazując wartość właściwości do <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3d618-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="3d618-125">Począwszy od .NET Framework 4, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> program obsługi można użyć właściwości, aby ustalić, czy bieżące żądanie jest zależność innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3d618-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="3d618-126">Te informacje mogą pomóc zidentyfikować zestaw, który spełni zależność.</span><span class="sxs-lookup"><span data-stu-id="3d618-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="3d618-127">Program obsługi zdarzeń może zwrócić inną wersję zestawu niż żądana wersja.</span><span class="sxs-lookup"><span data-stu-id="3d618-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="3d618-128">W większości przypadków zestawu, który jest zwracany przez program obsługi pojawia się w kontekście obciążenia, niezależnie od kontekstu obsługi ładuje go do.</span><span class="sxs-lookup"><span data-stu-id="3d618-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="3d618-129">Na przykład jeśli program <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> obsługi używa metody do ładowania zestawu do kontekstu obciążenia z, zestaw pojawia się w kontekście obciążenia, gdy program obsługi zwraca go.</span><span class="sxs-lookup"><span data-stu-id="3d618-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="3d618-130">Jednak w następującym przypadku zestaw pojawia się bez kontekstu, gdy program obsługi zwraca go:</span><span class="sxs-lookup"><span data-stu-id="3d618-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="3d618-131">Program obsługi ładuje zestaw bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3d618-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="3d618-132">Właściwość <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> nie jest null.</span><span class="sxs-lookup"><span data-stu-id="3d618-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="3d618-133">Żądający zestaw (czyli zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwość) został załadowany bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="3d618-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="3d618-134">Aby uzyskać informacje o <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> kontekstach, zobacz przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="3d618-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="3d618-135">Wiele wersji tego samego zestawu można załadować do tej samej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d618-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="3d618-136">Ta praktyka nie jest zalecana, ponieważ może prowadzić do problemów z przypisaniem typu.</span><span class="sxs-lookup"><span data-stu-id="3d618-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="3d618-137">Zobacz [Najważniejsze wskazówki dotyczące ładowania zestawu](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="3d618-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="3d618-138">Czego program obsługi zdarzeń nie powinien robić</span><span class="sxs-lookup"><span data-stu-id="3d618-138">What the event handler should not do</span></span>  
<span data-ttu-id="3d618-139">Podstawową regułą <xref:System.AppDomain.AssemblyResolve> obsługi zdarzenia jest, że nie należy próbować zwrócić zestawu, który nie rozpoznaje.</span><span class="sxs-lookup"><span data-stu-id="3d618-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="3d618-140">Podczas pisania programu obsługi, należy wiedzieć, które zestawy mogą spowodować zdarzenie, które mają być wywoływane.</span><span class="sxs-lookup"><span data-stu-id="3d618-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="3d618-141">Program obsługi powinien zwracać null dla innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="3d618-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="3d618-142">Począwszy od .NET Framework <xref:System.AppDomain.AssemblyResolve> 4, zdarzenie jest wywoływane dla zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="3d618-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="3d618-143">Ta zmiana ma wpływ na program obsługi zdarzeń, który został napisany dla starszej wersji programu .NET Framework, jeśli program obsługi próbuje rozwiązać wszystkie żądania ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="3d618-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="3d618-144">Programy obsługi zdarzeń, które ignorują zestawy, których nie rozpoznają, nie mają wpływu na tę zmianę: zwracają wartość null i przestrzegane są normalne mechanizmy rezerwowe.</span><span class="sxs-lookup"><span data-stu-id="3d618-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="3d618-145">Podczas ładowania zestawu, program obsługi zdarzeń <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> nie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> może używać żadnych <xref:System.AppDomain.AssemblyResolve> przeciążeń lub metody, które mogą spowodować zdarzenie, które mają być wywoływane cyklicznie, ponieważ może to prowadzić do przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="3d618-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="3d618-146">(Zobacz listę podanych wcześniej w tym temacie). Dzieje się tak, nawet jeśli podasz obsługę wyjątków dla żądania obciążenia, ponieważ nie wyjątek, dopóki nie zostaną zwrócone wszystkie programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3d618-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="3d618-147">W związku z tym następujący kod `MyAssembly` powoduje przepełnienie stosu, jeśli nie zostanie znaleziony:</span><span class="sxs-lookup"><span data-stu-id="3d618-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="3d618-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d618-148">See also</span></span>

- [<span data-ttu-id="3d618-149">Najważniejsze wskazówki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="3d618-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="3d618-150">Korzystanie z domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d618-150">Use application domains</span></span>](../../framework/app-domains/use.md)
