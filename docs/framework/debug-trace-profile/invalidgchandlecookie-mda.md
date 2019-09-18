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
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052611"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="9cefc-102">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="9cefc-102">invalidGCHandleCookie MDA</span></span>
<span data-ttu-id="9cefc-103">Asystent `invalidGCHandleCookie` debugowania zarządzanego (MDA) jest aktywowany, gdy <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta próba konwersji <xref:System.IntPtr> z nieprawidłowego pliku cookie na plik.</span><span class="sxs-lookup"><span data-stu-id="9cefc-103">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9cefc-104">Symptomy</span><span class="sxs-lookup"><span data-stu-id="9cefc-104">Symptoms</span></span>  
 <span data-ttu-id="9cefc-105">Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrania <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr>z.</span><span class="sxs-lookup"><span data-stu-id="9cefc-105">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9cefc-106">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="9cefc-106">Cause</span></span>  
 <span data-ttu-id="9cefc-107">Plik cookie prawdopodobnie jest nieprawidłowy, ponieważ nie został pierwotnie utworzony z <xref:System.Runtime.InteropServices.GCHandle>, <xref:System.Runtime.InteropServices.GCHandle> oznacza, że został już zwolniony, <xref:System.Runtime.InteropServices.GCHandle> jest plikiem cookie w innej domenie aplikacji lub został zorganizowany do kodu natywnego jako <xref:System.Runtime.InteropServices.GCHandle>ale przeszedł z powrotem do środowiska CLR <xref:System.IntPtr>jako, gdzie podjęto próbę rzutowania.</span><span class="sxs-lookup"><span data-stu-id="9cefc-107">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9cefc-108">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="9cefc-108">Resolution</span></span>  
 <span data-ttu-id="9cefc-109">Określ prawidłowy <xref:System.IntPtr> plik cookie <xref:System.Runtime.InteropServices.GCHandle>dla.</span><span class="sxs-lookup"><span data-stu-id="9cefc-109">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9cefc-110">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9cefc-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="9cefc-111">Po włączeniu tego MDA debuger nie będzie już mógł śledzić katalogów głównych z powrotem do swoich obiektów, ponieważ wartości plików cookie przenoszone z powrotem różnią się od tych, które są zwracane, gdy MDA nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="9cefc-111">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9cefc-112">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9cefc-112">Output</span></span>  
 <span data-ttu-id="9cefc-113">Zgłoszono <xref:System.IntPtr> nieprawidłową wartość pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="9cefc-113">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9cefc-114">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9cefc-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cefc-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cefc-115">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="9cefc-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9cefc-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
