---
title: Silverlight — debugowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139135"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="0f830-102">Silverlight — debugowanie</span><span class="sxs-lookup"><span data-stu-id="0f830-102">Silverlight Debugging</span></span>
<span data-ttu-id="0f830-103">Tematy w tej sekcji opisują środowisko i interfejsy, które zapewnia środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji opartych na technologii Silverlight, które są uruchomione w systemie operacyjnym Windows lub na platformie Macintosh.</span><span class="sxs-lookup"><span data-stu-id="0f830-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f830-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0f830-104">In This Section</span></span>  
 [<span data-ttu-id="0f830-105">EnumerateCLRs, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="0f830-106">Zapewnia mechanizm wyliczania CLRs w procesie.</span><span class="sxs-lookup"><span data-stu-id="0f830-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="0f830-107">CloseCLREnumeration, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="0f830-108">Zamyka wszystkie prawidłowe zdarzenia Kontynuuj środowiska CLR znajdujące się w tablicy dojść zwracanych przez [funkcję EnumerateCLRs —](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic uchwytów i ścieżek ciągów.</span><span class="sxs-lookup"><span data-stu-id="0f830-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="0f830-109">CreateCoreClrDebugTarget, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="0f830-110">Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0f830-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0f830-111">CreateCordbObject, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="0f830-112">Tworzy interfejs debugera, który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.</span><span class="sxs-lookup"><span data-stu-id="0f830-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="0f830-113">CreateVersionStringFromModule, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="0f830-114">Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0f830-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="0f830-115">CreateDebuggingInterfaceFromVersion, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="0f830-116">Akceptuje ciąg wersji środowiska CLR zwrócony z funkcji [funkcji CreateVersionStringFromModule —](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedni interfejs debugera.</span><span class="sxs-lookup"><span data-stu-id="0f830-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="0f830-117">CoreClrDebugProcInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="0f830-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="0f830-118">Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="0f830-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="0f830-119">CoreClrDebugRuntimeInfo, struktura</span><span class="sxs-lookup"><span data-stu-id="0f830-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="0f830-120">Reprezentuje wystąpienie CLR, które jest ładowane w procesie na maszynie zdalnej.</span><span class="sxs-lookup"><span data-stu-id="0f830-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="0f830-121">GetStartupNotificationEvent, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="0f830-122">Tworzy lub otwiera dojście zdarzenia, które będzie sygnalizowane przez środowisko uruchomieniowe języka wspólnego (CLR) ładowane w określonym procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="0f830-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="0f830-123">ICoreClrDebugTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f830-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="0f830-124">Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0f830-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0f830-125">InitDbgTransportManager, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="0f830-126">Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0f830-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="0f830-127">ShutdownDbgTransportManager, funkcja</span><span class="sxs-lookup"><span data-stu-id="0f830-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="0f830-128">Zamyka menedżera transportu dla połączenia ze zdalnym komputerem docelowym.</span><span class="sxs-lookup"><span data-stu-id="0f830-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f830-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f830-129">See also</span></span>

- [<span data-ttu-id="0f830-130">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="0f830-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [<span data-ttu-id="0f830-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0f830-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0f830-132">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0f830-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [<span data-ttu-id="0f830-133">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0f830-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="0f830-134">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="0f830-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
