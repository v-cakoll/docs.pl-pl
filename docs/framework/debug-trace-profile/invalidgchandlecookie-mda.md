---
title: invalidGCHandleCookie MDA
description: Przejrzyj invalidGCHandleCookie Managed Debug Assistant (MDA), który jest uaktywniany w przypadku próby konwersji z nieprawidłowego pliku cookie IntPtr na GCHandle.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 1063b7be902d3063717b6639564d819ef3292c0e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051301"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="6991d-103">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="6991d-103">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="6991d-104">`invalidGCHandleCookie`Asystent debugowania zarządzanego (MDA) jest aktywowany, gdy <xref:System.IntPtr> <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta próba konwersji z nieprawidłowego pliku cookie na plik.</span><span class="sxs-lookup"><span data-stu-id="6991d-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6991d-105">Objawy</span><span class="sxs-lookup"><span data-stu-id="6991d-105">Symptoms</span></span>  
 <span data-ttu-id="6991d-106">Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrania <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr> .</span><span class="sxs-lookup"><span data-stu-id="6991d-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6991d-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="6991d-107">Cause</span></span>  
 <span data-ttu-id="6991d-108">Plik cookie prawdopodobnie jest nieprawidłowy, ponieważ nie został pierwotnie utworzony z programu <xref:System.Runtime.InteropServices.GCHandle> , oznacza, <xref:System.Runtime.InteropServices.GCHandle> że został już zwolniony, jest plikiem cookie <xref:System.Runtime.InteropServices.GCHandle> w innej domenie aplikacji lub został zorganizowany do kodu natywnego jako a, ale został przekierowany z <xref:System.Runtime.InteropServices.GCHandle> powrotem do środowiska CLR jako <xref:System.IntPtr> , gdzie podjęto próbę wykonania rzutowania.</span><span class="sxs-lookup"><span data-stu-id="6991d-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6991d-109">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="6991d-109">Resolution</span></span>  
 <span data-ttu-id="6991d-110">Określ prawidłowy <xref:System.IntPtr> plik cookie dla <xref:System.Runtime.InteropServices.GCHandle> .</span><span class="sxs-lookup"><span data-stu-id="6991d-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6991d-111">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6991d-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="6991d-112">Po włączeniu tego MDA debuger nie będzie już mógł śledzić katalogów głównych z powrotem do swoich obiektów, ponieważ wartości plików cookie przenoszone z powrotem różnią się od tych, które są zwracane, gdy MDA nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="6991d-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6991d-113">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="6991d-113">Output</span></span>  
 <span data-ttu-id="6991d-114"><xref:System.IntPtr>Zgłoszono nieprawidłową wartość pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="6991d-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6991d-115">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="6991d-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6991d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6991d-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="6991d-117">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="6991d-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
