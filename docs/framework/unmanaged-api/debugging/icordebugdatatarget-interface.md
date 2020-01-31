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
ms.openlocfilehash: 9029d53872108bc1953fd22c584b6e01a6f3c7ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788866"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="202bf-102">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="202bf-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="202bf-103">Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="202bf-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="202bf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="202bf-104">Methods</span></span>  
  
|<span data-ttu-id="202bf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="202bf-105">Method</span></span>|<span data-ttu-id="202bf-106">Opis</span><span class="sxs-lookup"><span data-stu-id="202bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="202bf-107">GetPlatform, metoda</span><span class="sxs-lookup"><span data-stu-id="202bf-107">GetPlatform Method</span></span>](icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="202bf-108">Zawiera informacje na temat platformy, w tym architektury procesora i systemu operacyjnego, na których jest uruchomiony proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="202bf-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="202bf-109">ReadVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="202bf-109">ReadVirtual Method</span></span>](icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="202bf-110">Pobiera blok ciągłej pamięci zaczynający się od określonego adresu i zwraca go w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="202bf-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="202bf-111">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="202bf-111">GetThreadContext Method</span></span>](icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="202bf-112">Żąda bieżącego kontekstu wątku dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="202bf-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="202bf-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="202bf-113">Remarks</span></span>  
 <span data-ttu-id="202bf-114">`ICorDebugDataTarget` i jego metody mają następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="202bf-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="202bf-115">Usługi debugowania wywołują metody tego interfejsu w celu uzyskania dostępu do pamięci i innych danych w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="202bf-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="202bf-116">Klient debugera musi zaimplementować ten interfejs stosownie do określonego celu (na przykład procesu na żywo lub zrzutu pamięci).</span><span class="sxs-lookup"><span data-stu-id="202bf-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="202bf-117">Metody `ICorDebugDataTarget` mogą być wywoływane tylko z metod zaimplementowanych w innych interfejsach `ICorDebug*`.</span><span class="sxs-lookup"><span data-stu-id="202bf-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="202bf-118">Dzięki temu klient debugera ma kontrolę nad tym, który wątek jest wywoływany, i kiedy.</span><span class="sxs-lookup"><span data-stu-id="202bf-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="202bf-119">Implementacja `ICorDebugDataTarget` musi zawsze zwracać aktualne informacje o miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="202bf-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="202bf-120">Proces docelowy powinien zostać zatrzymany i nie można go zmienić w jakikolwiek sposób, podczas gdy `ICorDebug*` interfejsy (i w związku z tym `ICorDebugDataTarget` metody) są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="202bf-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="202bf-121">Jeśli obiektem docelowym jest proces na żywo, a jego stan zmieni się, należy ponownie wywołać metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) w celu zapewnienia zastępczego wystąpienia ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="202bf-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="202bf-122">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="202bf-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="202bf-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="202bf-123">Requirements</span></span>  
 <span data-ttu-id="202bf-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="202bf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="202bf-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="202bf-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="202bf-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="202bf-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="202bf-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="202bf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202bf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="202bf-128">See also</span></span>

- [<span data-ttu-id="202bf-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="202bf-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="202bf-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="202bf-130">Debugging</span></span>](index.md)
