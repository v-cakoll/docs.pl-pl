---
title: "ICorDebugDataTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 030ad5e61d215bd840da5b16a56e4b8f8b7791ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="e98ad-102">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e98ad-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="e98ad-103">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e98ad-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e98ad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e98ad-104">Methods</span></span>  
  
|<span data-ttu-id="e98ad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e98ad-105">Method</span></span>|<span data-ttu-id="e98ad-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e98ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e98ad-107">GetPlatform — metoda</span><span class="sxs-lookup"><span data-stu-id="e98ad-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="e98ad-108">Zawiera informacje o platformie, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="e98ad-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="e98ad-109">ReadVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="e98ad-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="e98ad-110">Pobiera blok pamięci ciągłej, zaczynając od określonego adresu i zwraca go do dostarczonego buforu.</span><span class="sxs-lookup"><span data-stu-id="e98ad-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="e98ad-111">GetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="e98ad-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="e98ad-112">Żąda bieżący kontekst wątku określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="e98ad-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e98ad-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e98ad-113">Remarks</span></span>  
 <span data-ttu-id="e98ad-114">`ICorDebugDataTarget`i jego metody mają następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="e98ad-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="e98ad-115">Debugowanie usług wywoływać metod w tym interfejsie dostęp do pamięci i innych danych w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e98ad-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="e98ad-116">Klient debugera musi implementować ten interfejs na potrzeby określonego elementu docelowego (na przykład procesu na żywo lub zrzut pamięci).</span><span class="sxs-lookup"><span data-stu-id="e98ad-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="e98ad-117">`ICorDebugDataTarget` Metody można wywołać tylko z wewnątrz metody implementowane w innych `ICorDebug*` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="e98ad-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="e98ad-118">Dzięki temu klient debugera ma kontroli, przez który wątek jest wywoływana na i.</span><span class="sxs-lookup"><span data-stu-id="e98ad-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="e98ad-119">`ICorDebugDataTarget` Implementacji zawsze musi zwracać aktualnych informacji dotyczących obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e98ad-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="e98ad-120">Proces docelowy powinien zatrzymana i nie uległy zmianie w jakikolwiek sposób podczas `ICorDebug*` interfejsów (i w związku z tym `ICorDebugDataTarget` metody) są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="e98ad-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="e98ad-121">Jeśli obiektem docelowym jest procesem na żywo i jego zmiany stanu [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda musi ponownie wywołany, aby zapewnić wystąpienie ICorDebugProcess zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="e98ad-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e98ad-122">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="e98ad-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e98ad-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e98ad-123">Requirements</span></span>  
 <span data-ttu-id="e98ad-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e98ad-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e98ad-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e98ad-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e98ad-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e98ad-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e98ad-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e98ad-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98ad-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e98ad-128">See Also</span></span>  
 [<span data-ttu-id="e98ad-129">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e98ad-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e98ad-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e98ad-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
