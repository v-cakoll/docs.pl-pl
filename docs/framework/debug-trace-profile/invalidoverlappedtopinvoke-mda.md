---
title: invalidOverlappedToPinvoke MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 395601c6aaff39bf2acb01ae36d306e57566aa4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="4a0d6-102">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="4a0d6-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="4a0d6-103">`invalidOverlappedToPinvoke` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nachodzący wskaźnik, który nie został utworzony na stercie kolekcji pamięci jest przekazywany do określonych funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a0d6-104">Domyślnie to zdarzenie MDA jest aktywna, tylko jeśli wywołanie platformy połączenia jest zdefiniowana w kodzie i debuger informuje o stanie JustMyCode każdej metody.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="4a0d6-105">Debuger, który nie rozpoznaje JustMyCode (na przykład MDbg.exe bez rozszerzeń) nie zostanie aktywowany to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="4a0d6-106">MDA ten można włączyć dla tych debugery przy użyciu pliku konfiguracji i jawnie settting `justMyCode="false"` w. plik mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span><span class="sxs-lookup"><span data-stu-id="4a0d6-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4a0d6-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="4a0d6-107">Symptoms</span></span>  
 <span data-ttu-id="4a0d6-108">Awarie lub uszkodzenie stosu unexplainable.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4a0d6-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="4a0d6-109">Cause</span></span>  
 <span data-ttu-id="4a0d6-110">Nachodzący wskaźnik, który nie został utworzony na stercie kolekcji pamięci są przekazywane do funkcji określonego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="4a0d6-111">W poniższej tabeli przedstawiono funkcje, że to zdarzenie MDA śledzi.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="4a0d6-112">Moduł</span><span class="sxs-lookup"><span data-stu-id="4a0d6-112">Module</span></span>|<span data-ttu-id="4a0d6-113">Funkcja</span><span class="sxs-lookup"><span data-stu-id="4a0d6-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="4a0d6-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="4a0d6-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="4a0d6-116">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="4a0d6-117">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="4a0d6-118">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="4a0d6-119">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="4a0d6-120">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="4a0d6-121">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="4a0d6-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="4a0d6-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="4a0d6-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="4a0d6-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="4a0d6-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="4a0d6-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="4a0d6-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="4a0d6-128">Jest duże ryzyko uszkodzenia sterty dla tego warunku, ponieważ <xref:System.AppDomain> wywołanie może zwolnić wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="4a0d6-129">Jeśli <xref:System.AppDomain> zwalnia, kod aplikacji albo spowoduje zwolnienie pamięci dla wskaźnika, przyczyną uszkodzenia po zakończeniu operacji lub kod będzie wyciek pamięci, co powoduje trudności później.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4a0d6-130">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="4a0d6-130">Resolution</span></span>  
 <span data-ttu-id="4a0d6-131">Użyj <xref:System.Threading.Overlapped> obiektów i wywoływania <xref:System.Threading.Overlapped.Pack%2A> metodę, aby pobrać <xref:System.Threading.NativeOverlapped> struktury, które mogą zostać przekazane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="4a0d6-132">Jeśli <xref:System.AppDomain> zwalnia, CLR czeka przed zakończeniem operacji asynchronicznych przed zwalnianie wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4a0d6-133">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4a0d6-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="4a0d6-134">To zdarzenie MDA nie miała wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4a0d6-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4a0d6-135">Output</span></span>  
 <span data-ttu-id="4a0d6-136">Oto przykład danych wyjściowych z to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="4a0d6-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="4a0d6-137">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4a0d6-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a0d6-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a0d6-138">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="4a0d6-139">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="4a0d6-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="4a0d6-140">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="4a0d6-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
