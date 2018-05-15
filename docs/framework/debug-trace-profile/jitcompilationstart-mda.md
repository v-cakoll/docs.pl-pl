---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9643a2d2ea0967b8cf6d8e18ce2e9073ae583f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="814e8-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="814e8-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="814e8-103">`jitCompilationStart` Zarządzany Asystent debugowania (MDA) został aktywowany do raportu podczas uruchamiania kompilatora just-in-time (JIT) skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="814e8-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="814e8-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="814e8-104">Symptoms</span></span>  
 <span data-ttu-id="814e8-105">Zestaw roboczy zwiększania rozmiaru dla programu, który jest już w formacie obrazu macierzystego, ponieważ mscorjit.dll jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="814e8-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="814e8-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="814e8-106">Cause</span></span>  
 <span data-ttu-id="814e8-107">Nie wszystkie zestawy, których program jest zależny od zostały wygenerowane do formatu macierzystego lub te, które mają nie zostały poprawnie zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="814e8-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="814e8-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="814e8-108">Resolution</span></span>  
 <span data-ttu-id="814e8-109">Włączanie to zdarzenie MDA pozwala określić, funkcji, które są kompilowane JIT.</span><span class="sxs-lookup"><span data-stu-id="814e8-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="814e8-110">Określ, czy zestaw zawierający funkcję jest generowane w celu formatu macierzystego i poprawnie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="814e8-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="814e8-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="814e8-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="814e8-112">To zdarzenie MDA rejestruje komunikat tuż przed metodą jest kompilacji JIT, dlatego włączenie tego MDA ma znaczący wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="814e8-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="814e8-113">Należy pamiętać, że jeśli metoda jest wbudowany, to zdarzenie MDA nie wygeneruje osobnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="814e8-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="814e8-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="814e8-114">Output</span></span>  
 <span data-ttu-id="814e8-115">Poniższy przykład kodu pokazuje przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="814e8-115">The following code sample shows sample output.</span></span> <span data-ttu-id="814e8-116">W takim przypadku pokazuje dane wyjściowe, które w zestawie testów metody "m" w klasie "ns2.CO" został skompilowany JIT.</span><span class="sxs-lookup"><span data-stu-id="814e8-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="814e8-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="814e8-117">Configuration</span></span>  
 <span data-ttu-id="814e8-118">Następujący plik konfiguracji zawiera szereg filtry, które można zastosować do odfiltrowywania które metody są zgłaszane, gdy są one najpierw kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="814e8-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="814e8-119">Można określić, że wszystkie metody zgłoszone przez ustawienie wartości atrybutu nazwy \*.</span><span class="sxs-lookup"><span data-stu-id="814e8-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="814e8-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="814e8-120">Example</span></span>  
 <span data-ttu-id="814e8-121">Poniższy przykładowy kod jest przeznaczony do użycia z poprzedniego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="814e8-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="814e8-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="814e8-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="814e8-123">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="814e8-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="814e8-124">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="814e8-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
