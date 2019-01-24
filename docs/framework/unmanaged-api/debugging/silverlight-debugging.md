---
title: Silverlight — debugowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414526d498b39e894c6bd3530a446f8c06f46378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572750"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="7a8d2-102">Silverlight — debugowanie</span><span class="sxs-lookup"><span data-stu-id="7a8d2-102">Silverlight Debugging</span></span>
<span data-ttu-id="7a8d2-103">Tematy w tej sekcji opisano środowisko i interfejsów udostępnianych przez środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji opartych na technologii Silverlight, uruchomionych w systemie operacyjnym Windows lub na platformie dla komputerów Macintosh.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a8d2-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7a8d2-104">In This Section</span></span>  
 [<span data-ttu-id="7a8d2-105">EnumerateCLRs, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="7a8d2-106">Udostępnia mechanizm wyliczania CLRs w procesie.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="7a8d2-107">CloseCLREnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="7a8d2-108">Zamyka wszystkie prawidłowe zdarzenia uruchamiania nadal CLR, znajduje się w tablicy, uchwyt zwracany przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic ścieżka dojścia i parametry.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="7a8d2-109">CreateCoreClrDebugTarget, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="7a8d2-110">Tworzy połączenie do zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="7a8d2-111">CreateCordbObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="7a8d2-112">Tworzy interfejs debugera, który oferuje funkcję podczas tworzenia wystąpienia zarządzanego sesji debugowania zdalnego procesu.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="7a8d2-113">CreateVersionStringFromModule, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="7a8d2-114">Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="7a8d2-115">CreateDebuggingInterfaceFromVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="7a8d2-116">Akceptuje ciąg wersji środowiska CLR zwróciło [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)funkcji i zwraca odpowiedniego interfejsu debugera.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="7a8d2-117">CoreClrDebugProcInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="7a8d2-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="7a8d2-118">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="7a8d2-119">CoreClrDebugRuntimeInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="7a8d2-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="7a8d2-120">Reprezentuje wystąpienie CLR, który jest załadowany do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="7a8d2-121">GetStartupNotificationEvent, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="7a8d2-122">Tworzy lub zostanie otwarte dojście zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie docelowym określonym.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="7a8d2-123">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a8d2-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="7a8d2-124">Tworzy połączenie do zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="7a8d2-125">InitDbgTransportManager, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="7a8d2-126">Inicjuje menedżera transportu nawiązać zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="7a8d2-127">ShutdownDbgTransportManager, funkcja</span><span class="sxs-lookup"><span data-stu-id="7a8d2-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="7a8d2-128">Zamknie menedżera transportu dla połączenia do maszyny zdalnej docelowego.</span><span class="sxs-lookup"><span data-stu-id="7a8d2-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a8d2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a8d2-129">See also</span></span>
- [<span data-ttu-id="7a8d2-130">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="7a8d2-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [<span data-ttu-id="7a8d2-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7a8d2-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7a8d2-132">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="7a8d2-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [<span data-ttu-id="7a8d2-133">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7a8d2-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="7a8d2-134">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="7a8d2-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
