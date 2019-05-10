---
title: ICorDebugDataTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9a87ae4381ec5bc0d8c416ef4ee4c13b04a862f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606899"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="7793d-102">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7793d-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="7793d-103">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7793d-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7793d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7793d-104">Methods</span></span>  
  
|<span data-ttu-id="7793d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7793d-105">Method</span></span>|<span data-ttu-id="7793d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7793d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7793d-107">GetPlatform, metoda</span><span class="sxs-lookup"><span data-stu-id="7793d-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="7793d-108">Zawiera informacje dotyczące platformy, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="7793d-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="7793d-109">ReadVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="7793d-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="7793d-110">Pobiera blok pamięci ciągłej uruchamianie pod podanym adresem i zwraca go w dostarczony bufor.</span><span class="sxs-lookup"><span data-stu-id="7793d-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="7793d-111">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="7793d-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="7793d-112">Żąda bieżący kontekst wątku określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="7793d-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7793d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7793d-113">Remarks</span></span>  
 <span data-ttu-id="7793d-114">`ICorDebugDataTarget` i jego metody mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="7793d-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="7793d-115">Debugowanie usług wywoływać metody, w tym interfejsie dostępu do pamięci i innych danych w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="7793d-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="7793d-116">Klient debugera musi implementować ten interfejs stosownie do określonego celu (na przykład żywy proces lub zrzutu pamięci).</span><span class="sxs-lookup"><span data-stu-id="7793d-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="7793d-117">`ICorDebugDataTarget` Metody może być wywołana tylko z w ramach metod zaimplementowanych w innych `ICorDebug*` interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7793d-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="7793d-118">Daje to gwarancję, że klient debugera ma kontroluje, przez który wątek jest wywoływana na i.</span><span class="sxs-lookup"><span data-stu-id="7793d-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="7793d-119">`ICorDebugDataTarget` Implementacji zwracana zawsze aktualne informacje dotyczące obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7793d-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="7793d-120">Proces docelowy powinien być zatrzymana i nie uległy zmianie w jakikolwiek sposób podczas `ICorDebug*` interfejsów (i w związku z tym `ICorDebugDataTarget` metody) jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7793d-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="7793d-121">Jeśli obiektem docelowym są żywy proces i zmiany jego stanu, [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda musi zostać ponownie wywoływana w celu zapewnienia wystąpienia icordebugprocess — zastąpienie.</span><span class="sxs-lookup"><span data-stu-id="7793d-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7793d-122">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="7793d-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7793d-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7793d-123">Requirements</span></span>  
 <span data-ttu-id="7793d-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7793d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7793d-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7793d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7793d-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7793d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7793d-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7793d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7793d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7793d-128">See also</span></span>

- [<span data-ttu-id="7793d-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7793d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7793d-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7793d-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
