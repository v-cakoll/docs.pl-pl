---
title: "ICorDebugRegisterSet2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2
helpviewer_keywords: ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f01a1d291216fca84b70fce8389efee3d7e2dd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="aa21a-102">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="aa21a-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="aa21a-103">Rozszerza możliwości [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interfejs dla platform sprzętowych, które mają ponad 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="aa21a-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa21a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aa21a-104">Methods</span></span>  
  
|<span data-ttu-id="aa21a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa21a-105">Method</span></span>|<span data-ttu-id="aa21a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="aa21a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa21a-107">GetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="aa21a-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="aa21a-108">Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kodu) określonym przez maska bitowa.</span><span class="sxs-lookup"><span data-stu-id="aa21a-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="aa21a-109">GetRegistersAvailable, metoda</span><span class="sxs-lookup"><span data-stu-id="aa21a-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="aa21a-110">Pobiera tablicę bajtów zawiera mapę bitową rejestry dostępne.</span><span class="sxs-lookup"><span data-stu-id="aa21a-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="aa21a-111">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="aa21a-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="aa21a-112">Nie zaimplementowano w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="aa21a-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa21a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa21a-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa21a-114">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="aa21a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa21a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa21a-115">Requirements</span></span>  
 <span data-ttu-id="aa21a-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa21a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa21a-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa21a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa21a-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa21a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa21a-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa21a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa21a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa21a-120">See Also</span></span>  
 [<span data-ttu-id="aa21a-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="aa21a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="aa21a-122">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa21a-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
