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
ms.openlocfilehash: 62064286fecc4736f39ad790f0fd7f0e6d84b149
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162348"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="ad9d2-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="ad9d2-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="ad9d2-103">`jitCompilationStart` Zarządzanego Asystenta debugowania (MDA) jest aktywowany do raportu, gdy kompilator just-in-time (JIT) zaczyna kompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="ad9d2-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="ad9d2-104">Symptoms</span></span>  
 <span data-ttu-id="ad9d2-105">Zestaw roboczy zwiększania rozmiaru dla programu, który jest już w formacie obrazu natywnego, ponieważ mscorjit.dll jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="ad9d2-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ad9d2-106">Cause</span></span>  
 <span data-ttu-id="ad9d2-107">Nie wszystkie zestawy, których program jest zależny od zostały wygenerowane w formacie natywnym lub tych, które mają nie zostały poprawnie zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="ad9d2-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ad9d2-108">Resolution</span></span>  
 <span data-ttu-id="ad9d2-109">Włączanie to zdarzenie MDA pozwala określić, która funkcja jest kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="ad9d2-110">Ustalić, czy zestaw, który zawiera funkcję jest generowany w celu natywnego formatu oraz poprawnie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ad9d2-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ad9d2-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="ad9d2-112">To zdarzenie MDA rejestruje wiadomość, przed metodą jest kompilowany dokładnie na czas, dlatego włączenie to zdarzenie MDA ma znaczący wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="ad9d2-113">Należy pamiętać, że jeśli metoda jest wbudowany, to zdarzenie MDA nie wygeneruje oddzielną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ad9d2-114">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ad9d2-114">Output</span></span>  
 <span data-ttu-id="ad9d2-115">Poniższy przykładowy kod przedstawia przykładowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-115">The following code sample shows sample output.</span></span> <span data-ttu-id="ad9d2-116">W tym przypadku pokazano w danych wyjściowych, które w zestawie testów metody "m" w klasie "ns2.CO" jest kompilowany dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="ad9d2-117">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ad9d2-117">Configuration</span></span>  
 <span data-ttu-id="ad9d2-118">Następujący plik konfiguracji zawiera szereg filtry, które można zastosować, aby odfiltrować metody, które są zgłaszane, gdy są one najpierw kompilowanego dokładnie na czas.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="ad9d2-119">Można określić, że wszystkie metody należy podać, ustawiając wartość atrybutu nazwy \*.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ad9d2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad9d2-120">Example</span></span>  
 <span data-ttu-id="ad9d2-121">Poniższy przykładowy kod jest przeznaczony do użycia z poprzedniego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ad9d2-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad9d2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad9d2-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="ad9d2-123">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ad9d2-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="ad9d2-124">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="ad9d2-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
