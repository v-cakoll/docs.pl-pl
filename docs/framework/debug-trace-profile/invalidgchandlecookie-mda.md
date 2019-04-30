---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 876f0fe3c40cb6754b4ba714833dd160dc4de3a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754404"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="bac8d-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="bac8d-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="bac8d-103">`invalidGCHandleCookie` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas konwersji z nieprawidłową <xref:System.IntPtr> pliku cookie do <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="bac8d-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bac8d-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="bac8d-104">Symptoms</span></span>  
 <span data-ttu-id="bac8d-105">Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrać <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="bac8d-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bac8d-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="bac8d-106">Cause</span></span>  
 <span data-ttu-id="bac8d-107">Plik cookie jest prawdopodobnie nieprawidłowy, ponieważ nie został pierwotnie utworzony z <xref:System.Runtime.InteropServices.GCHandle>, reprezentuje <xref:System.Runtime.InteropServices.GCHandle> który już został zwolniony, plik cookie do <xref:System.Runtime.InteropServices.GCHandle> w domenie innej aplikacji lub został przekazywania do kodu macierzystego jako <xref:System.Runtime.InteropServices.GCHandle>ale przekazany do CLR jako <xref:System.IntPtr>, gdzie próbowano rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bac8d-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bac8d-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="bac8d-108">Resolution</span></span>  
 <span data-ttu-id="bac8d-109">Podaj prawidłową <xref:System.IntPtr> plik cookie na potrzeby <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="bac8d-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bac8d-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bac8d-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="bac8d-111">Gdy to zdarzenie MDA jest włączona, debuger nie jest już możliwość prześledzenia korzenie powrót do ich obiektów, ponieważ wartości plików cookie przekazane z powrotem różnią się od tych zwracane, gdy zdarzenie MDA nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="bac8d-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bac8d-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="bac8d-112">Output</span></span>  
 <span data-ttu-id="bac8d-113">Nieprawidłowa <xref:System.IntPtr> zgłaszane wartości pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="bac8d-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="bac8d-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="bac8d-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bac8d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bac8d-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="bac8d-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="bac8d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
