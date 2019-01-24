---
title: ICorDebugProcess5::EnableNGENPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca656aeba04526164a65760af990455965c5288e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665217"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="26492-102">ICorDebugProcess5::EnableNGENPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="26492-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="26492-103">Ustawia wartość określającą, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="26492-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26492-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26492-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26492-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26492-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="26492-106">[in] A [cordebugngenpolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) stałą, która określa, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="26492-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26492-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26492-107">Remarks</span></span>  
 <span data-ttu-id="26492-108">Jeśli zasady zostały ustawione pomyślnie, metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="26492-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="26492-109">Jeśli `ePolicy` znajduje się poza zakresem wartości wyliczane definicją [cordebugngenpolicy —](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), metoda zwraca `E_INVALIDARG` i wywołania metody które nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="26492-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="26492-110">Jeśli nie można zaktualizować zasad Native Image Generator (Ngen.exe), metoda zwraca `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="26492-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="26492-111">`ICorDebugProcess5::EnableNGenPolicy` Metodę można wywołać w dowolnym momencie podczas okresu istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="26492-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="26492-112">Zasady są włączone dla wszelkich modułów, które są ładowane po ustawieniu zasad.</span><span class="sxs-lookup"><span data-stu-id="26492-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26492-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26492-113">Requirements</span></span>  
 <span data-ttu-id="26492-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26492-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26492-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26492-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26492-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26492-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26492-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26492-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26492-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26492-118">See also</span></span>
- [<span data-ttu-id="26492-119">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="26492-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="26492-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="26492-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="26492-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="26492-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
