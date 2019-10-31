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
ms.openlocfilehash: f8b216d370f7278f6d2a4beed5bab88afa666200
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122211"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="06011-102">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06011-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="06011-103">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="06011-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06011-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06011-104">Methods</span></span>  
  
|<span data-ttu-id="06011-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06011-105">Method</span></span>|<span data-ttu-id="06011-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06011-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06011-107">GetPlatform, metoda</span><span class="sxs-lookup"><span data-stu-id="06011-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="06011-108">Zawiera informacje na temat platformy, w tym architektury procesora i systemu operacyjnego, na których jest uruchomiony proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="06011-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="06011-109">ReadVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="06011-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="06011-110">Pobiera blok ciągłej pamięci zaczynający się od określonego adresu i zwraca go w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="06011-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="06011-111">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="06011-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="06011-112">Żąda bieżącego kontekstu wątku dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="06011-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06011-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06011-113">Remarks</span></span>  
 <span data-ttu-id="06011-114">`ICorDebugDataTarget` i jego metody mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="06011-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="06011-115">Usługi debugowania wywołują metody tego interfejsu w celu uzyskania dostępu do pamięci i innych danych w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="06011-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="06011-116">Klient debugera musi zaimplementować ten interfejs stosownie do określonego celu (na przykład procesu na żywo lub zrzutu pamięci).</span><span class="sxs-lookup"><span data-stu-id="06011-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="06011-117">Metody `ICorDebugDataTarget` mogą być wywoływane tylko z metod zaimplementowanych w innych interfejsach `ICorDebug*`.</span><span class="sxs-lookup"><span data-stu-id="06011-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="06011-118">Dzięki temu klient debugera ma kontrolę nad tym, który wątek jest wywoływany, i kiedy.</span><span class="sxs-lookup"><span data-stu-id="06011-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="06011-119">Implementacja `ICorDebugDataTarget` musi zawsze zwracać aktualne informacje o miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="06011-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="06011-120">Proces docelowy powinien zostać zatrzymany i nie można go zmienić w jakikolwiek sposób, podczas gdy `ICorDebug*` interfejsy (i w związku z tym `ICorDebugDataTarget` metody) są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="06011-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="06011-121">Jeśli obiektem docelowym jest proces na żywo, a jego stan zmieni się, należy ponownie wywołać metodę [ICLRDebugging:: OpenVirtualProcess —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) w celu zapewnienia zastępczego wystąpienia ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="06011-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06011-122">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="06011-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06011-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06011-123">Requirements</span></span>  
 <span data-ttu-id="06011-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06011-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06011-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06011-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06011-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06011-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06011-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06011-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06011-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06011-128">See also</span></span>

- [<span data-ttu-id="06011-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="06011-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="06011-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="06011-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
