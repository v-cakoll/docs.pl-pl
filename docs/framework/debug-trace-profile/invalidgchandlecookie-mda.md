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
ms.openlocfilehash: 1f1542cf9d0568fe2ec35c046c358b7249231d42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392908"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="7ee4b-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="7ee4b-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="7ee4b-103">`invalidGCHandleCookie` Zarządzany Asystent debugowania (MDA) jest uaktywniany podczas konwersji z nieprawidłową <xref:System.IntPtr> pliku cookie do <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7ee4b-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="7ee4b-104">Symptoms</span></span>  
 <span data-ttu-id="7ee4b-105">Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrać <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7ee4b-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="7ee4b-106">Cause</span></span>  
 <span data-ttu-id="7ee4b-107">Plik cookie jest prawdopodobnie nieprawidłowa, ponieważ nie został pierwotnie utworzony z <xref:System.Runtime.InteropServices.GCHandle>, reprezentuje <xref:System.Runtime.InteropServices.GCHandle> który już został zwolniony, plik cookie do <xref:System.Runtime.InteropServices.GCHandle> w domenie innej aplikacji lub został przekazywane do kodu macierzystego jako <xref:System.Runtime.InteropServices.GCHandle>ale przekazany do środowiska CLR jako <xref:System.IntPtr>, gdzie próbowano wykonać rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7ee4b-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="7ee4b-108">Resolution</span></span>  
 <span data-ttu-id="7ee4b-109">Określ prawidłowe <xref:System.IntPtr> plik cookie <xref:System.Runtime.InteropServices.GCHandle>.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7ee4b-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7ee4b-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="7ee4b-111">Po włączeniu to zdarzenie MDA debuger nie jest już możliwość śledzenia certyfikaty główne do nich obiekty, ponieważ inne niż zwracany, gdy nie włączono MDA są przekazywane z powrotem wartości pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7ee4b-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7ee4b-112">Output</span></span>  
 <span data-ttu-id="7ee4b-113">Nieprawidłowa <xref:System.IntPtr> jest zgłaszana wartość pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="7ee4b-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7ee4b-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="7ee4b-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee4b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ee4b-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [<span data-ttu-id="7ee4b-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="7ee4b-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
