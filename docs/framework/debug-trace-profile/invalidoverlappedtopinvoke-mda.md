---
title: invalidOverlappedToPinvoke MDA
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5709e4ef883ba2750f1efd0ae2e9a72f1cf43b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967305"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="c3d38-102">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="c3d38-102">invalidOverlappedToPinvoke MDA</span></span>
<span data-ttu-id="c3d38-103">Asystent `invalidOverlappedToPinvoke` debugowania zarządzanego (MDA) jest uaktywniany, gdy nakładający się wskaźnik, który nie został utworzony na stercie wyrzucania elementów bezużytecznych, jest przesyłany do określonych funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="c3d38-103">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3d38-104">Domyślnie to zdarzenie MDA jest uaktywniane tylko wtedy, gdy wywołanie wywoływana przez platformę jest zdefiniowane w kodzie, a debuger raportuje stan JustMyCode każdej z tych metod.</span><span class="sxs-lookup"><span data-stu-id="c3d38-104">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="c3d38-105">Debuger, który nie rozpoznaje JustMyCode (na przykład MDbg. exe bez rozszerzeń), nie aktywuje tego MDA.</span><span class="sxs-lookup"><span data-stu-id="c3d38-105">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="c3d38-106">To zdarzenie MDA można włączyć dla tych debugerów przy użyciu pliku konfiguracji i jawnie wyraźnych `justMyCode="false"` w pliku `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`. MDA. config).</span><span class="sxs-lookup"><span data-stu-id="c3d38-106">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c3d38-107">Symptomy</span><span class="sxs-lookup"><span data-stu-id="c3d38-107">Symptoms</span></span>  
 <span data-ttu-id="c3d38-108">Awarie stosu lub niewyjaśnione uszkodzenia sterty.</span><span class="sxs-lookup"><span data-stu-id="c3d38-108">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c3d38-109">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="c3d38-109">Cause</span></span>  
 <span data-ttu-id="c3d38-110">Nakładający się wskaźnik, który nie został utworzony na stercie wyrzucania elementów bezużytecznych, jest przesyłany do określonych funkcji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c3d38-110">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="c3d38-111">W poniższej tabeli przedstawiono funkcje, które są śledzone przez to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="c3d38-111">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="c3d38-112">Moduł</span><span class="sxs-lookup"><span data-stu-id="c3d38-112">Module</span></span>|<span data-ttu-id="c3d38-113">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c3d38-113">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="c3d38-114">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-114">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="c3d38-115">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-115">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="c3d38-116">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-116">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="c3d38-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-117">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="c3d38-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-118">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="c3d38-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-119">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="c3d38-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-120">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="c3d38-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-121">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="c3d38-122">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-122">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="c3d38-123">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-123">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="c3d38-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-124">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="c3d38-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-125">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="c3d38-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-126">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="c3d38-127">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="c3d38-127">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="c3d38-128">Prawdopodobieństwo uszkodzenia sterty jest wysokie dla tego warunku, <xref:System.AppDomain> ponieważ wywołanie może zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="c3d38-128">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="c3d38-129"><xref:System.AppDomain> Jeśli zwalnia, kod aplikacji zwalnia pamięć dla nakładającego się wskaźnika, powodując uszkodzenie po zakończeniu operacji lub kod przecieka pamięć, co spowoduje problemy później.</span><span class="sxs-lookup"><span data-stu-id="c3d38-129">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c3d38-130">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="c3d38-130">Resolution</span></span>  
 <span data-ttu-id="c3d38-131">Użyj obiektu, <xref:System.Threading.Overlapped.Pack%2A> wywołując metodę, aby uzyskać <xref:System.Threading.NativeOverlapped> strukturę, która może zostać przeniesiona do funkcji. <xref:System.Threading.Overlapped></span><span class="sxs-lookup"><span data-stu-id="c3d38-131">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="c3d38-132"><xref:System.AppDomain> Jeśli zwalnia, CLR czeka na zakończenie operacji asynchronicznej przed zwolnieniem wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="c3d38-132">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c3d38-133">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c3d38-133">Effect on the Runtime</span></span>  
 <span data-ttu-id="c3d38-134">To zdarzenie MDA nie ma wpływu na środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="c3d38-134">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c3d38-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c3d38-135">Output</span></span>  
 <span data-ttu-id="c3d38-136">Poniżej znajduje się przykład danych wyjściowych z tego MDA.</span><span class="sxs-lookup"><span data-stu-id="c3d38-136">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="c3d38-137">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c3d38-137">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3d38-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3d38-138">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c3d38-139">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c3d38-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c3d38-140">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="c3d38-140">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
