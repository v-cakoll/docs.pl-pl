---
title: Asystent debugowania zarządzanego jitCompilationStart (MDA)
description: Raporty Asystent debugowania zarządzanego jitCompilationStart (MDA), gdy kompilator just in Time (JIT) rozpoczyna Kompilowanie funkcji platformy .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325530"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="b2a73-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="b2a73-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="b2a73-104">`jitCompilationStart`Asystent debugowania zarządzanego (MDA) jest aktywowany do raportowania, gdy kompilator just in Time (JIT) rozpocznie Kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="b2a73-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b2a73-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="b2a73-105">Symptoms</span></span>  
 <span data-ttu-id="b2a73-106">Rozmiar zestawu roboczego rośnie dla programu, który jest już w formacie obrazu natywnego, ponieważ mscorjit.dll jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="b2a73-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b2a73-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="b2a73-107">Cause</span></span>  
<span data-ttu-id="b2a73-108">Nie wszystkie zestawy, od których zależy program, zostały wygenerowane w formacie natywnym lub zestaw nie został poprawnie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="b2a73-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="b2a73-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="b2a73-109">Resolution</span></span>  
 <span data-ttu-id="b2a73-110">Włączenie tego MDA umożliwia zidentyfikowanie, która funkcja jest skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="b2a73-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="b2a73-111">Upewnij się, że zestaw, który zawiera funkcję, jest generowany w formacie natywnym i poprawnie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="b2a73-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b2a73-112">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b2a73-112">Effect on the runtime</span></span>  
 <span data-ttu-id="b2a73-113">To zdarzenie jest rejestrowane tuż przed użyciem metody z kompilacją JIT, dlatego włączenie tego elementu MDA ma znaczny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="b2a73-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="b2a73-114">Jeśli metoda jest wbudowana, to MDA nie będzie generować osobnego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b2a73-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b2a73-115">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b2a73-115">Output</span></span>  
 <span data-ttu-id="b2a73-116">Poniższy przykład kodu pokazuje przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b2a73-116">The following code sample shows sample output.</span></span> <span data-ttu-id="b2a73-117">W takim przypadku dane wyjściowe pokazują, że w teście zestawu Metoda "m" w klasie "ns2.CO" została skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="b2a73-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="b2a73-118">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b2a73-118">Configuration</span></span>  
 <span data-ttu-id="b2a73-119">Poniższy plik konfiguracji przedstawia różne filtry, które mogą być stosowane do filtrowania metod zgłaszanych podczas pierwszego kompilowania JIT.</span><span class="sxs-lookup"><span data-stu-id="b2a73-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="b2a73-120">Możesz określić, że wszystkie metody mają być zgłaszane przez ustawienie wartości atrybutu Name na \* .</span><span class="sxs-lookup"><span data-stu-id="b2a73-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="b2a73-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2a73-121">Example</span></span>  
 <span data-ttu-id="b2a73-122">Poniższy przykład kodu jest przeznaczony do użycia w poprzednim pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="b2a73-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2a73-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2a73-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b2a73-124">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b2a73-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b2a73-125">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="b2a73-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
