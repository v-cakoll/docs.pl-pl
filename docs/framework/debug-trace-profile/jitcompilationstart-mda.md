---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 9cae942bc01e9263720dbfe9acfb21bbb70bc548
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216261"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="df247-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="df247-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="df247-103">Asystent debugowania zarządzanego `jitCompilationStart` (MDA) jest aktywowany w celu raportowania, gdy kompilator just in Time (JIT) rozpocznie Kompilowanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="df247-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="df247-104">Objawy</span><span class="sxs-lookup"><span data-stu-id="df247-104">Symptoms</span></span>  
 <span data-ttu-id="df247-105">Rozmiar zestawu roboczego rośnie dla programu, który jest już w formacie obrazu natywnego, ponieważ MSCORJIT. dll jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="df247-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="df247-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="df247-106">Cause</span></span>  
 <span data-ttu-id="df247-107">Nie wszystkie zestawy, od których zależy program, zostały wygenerowane w formacie natywnym lub te, które nie zostały poprawnie zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="df247-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="df247-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="df247-108">Resolution</span></span>  
 <span data-ttu-id="df247-109">Włączenie tego MDA pozwala określić, która funkcja jest skompilowana w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="df247-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="df247-110">Ustal, czy zestaw, który zawiera funkcję, jest generowany w formacie natywnym i poprawnie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="df247-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="df247-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="df247-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="df247-112">To zdarzenie jest rejestrowane tuż przed użyciem metody z kompilacją JIT, dlatego włączenie tego elementu MDA ma znaczny wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="df247-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="df247-113">Należy pamiętać, że jeśli metoda jest wbudowana, to MDA nie będzie generować osobnego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="df247-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="df247-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="df247-114">Output</span></span>  
 <span data-ttu-id="df247-115">Poniższy przykład kodu pokazuje przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="df247-115">The following code sample shows sample output.</span></span> <span data-ttu-id="df247-116">W takim przypadku dane wyjściowe pokazują, że w teście zestawu Metoda "m" w klasie "ns2.CO" została skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="df247-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="df247-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="df247-117">Configuration</span></span>  
 <span data-ttu-id="df247-118">Poniższy plik konfiguracji przedstawia różne filtry, które mogą być stosowane do filtrowania metod zgłaszanych podczas pierwszego kompilowania JIT.</span><span class="sxs-lookup"><span data-stu-id="df247-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="df247-119">Możesz określić, że wszystkie metody mają być zgłaszane przez ustawienie wartości atrybutu Name na \*.</span><span class="sxs-lookup"><span data-stu-id="df247-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="df247-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="df247-120">Example</span></span>  
 <span data-ttu-id="df247-121">Poniższy przykład kodu jest przeznaczony do użycia w poprzednim pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="df247-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df247-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df247-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="df247-123">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="df247-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="df247-124">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="df247-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
