---
title: ICorDebugRegisterSet2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da2759219901a4f49808300ea3b038b10ce2d032
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101175"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="ae072-102">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ae072-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="ae072-103">Rozszerza możliwości [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interfejsu dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="ae072-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae072-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae072-104">Methods</span></span>  
  
|<span data-ttu-id="ae072-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae072-105">Method</span></span>|<span data-ttu-id="ae072-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ae072-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae072-107">GetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="ae072-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="ae072-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.</span><span class="sxs-lookup"><span data-stu-id="ae072-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="ae072-109">GetRegistersAvailable, metoda</span><span class="sxs-lookup"><span data-stu-id="ae072-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="ae072-110">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrach.</span><span class="sxs-lookup"><span data-stu-id="ae072-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="ae072-111">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="ae072-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="ae072-112">Nie jest zaimplementowana w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="ae072-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae072-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae072-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae072-114">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ae072-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae072-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae072-115">Requirements</span></span>  
 <span data-ttu-id="ae072-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae072-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae072-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae072-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae072-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae072-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ae072-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ae072-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae072-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae072-120">See also</span></span>

- [<span data-ttu-id="ae072-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ae072-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ae072-122">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ae072-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
