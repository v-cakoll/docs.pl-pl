---
title: "ICorDebugProcess5::EnableNGENPolicy — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dca0df7b0be643d53bb5b9a03bd3abbb186d69dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="0c085-102">ICorDebugProcess5::EnableNGENPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c085-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="0c085-103">Ustawia wartość określającą, jak ładowania obrazów natywnych podczas uruchamiania w debugerze zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c085-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c085-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c085-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c085-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c085-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="0c085-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) stała, który określa sposób ładowania obrazów natywnych podczas uruchamiania w debugerze zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c085-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c085-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c085-107">Remarks</span></span>  
 <span data-ttu-id="0c085-108">Jeśli zasady zostały ustawione pomyślnie, metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="0c085-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="0c085-109">Jeśli `ePolicy` znajduje się poza zakresem wartości wyliczenia zdefiniowanych przez [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), metoda zwraca `E_INVALIDARG` i wywołanie metody nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="0c085-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="0c085-110">Jeśli nie można zaktualizować zasad Generator obrazu natywnego (Ngen.exe), metoda zwraca `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="0c085-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="0c085-111">`ICorDebugProcess5::EnableNGenPolicy` Metodę można wywołać w dowolnym momencie przez cały okres istnienia procesu.</span><span class="sxs-lookup"><span data-stu-id="0c085-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="0c085-112">Zasady są włączone dla wszelkich modułów, które są ładowane po ustawieniu zasad.</span><span class="sxs-lookup"><span data-stu-id="0c085-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c085-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c085-113">Requirements</span></span>  
 <span data-ttu-id="0c085-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c085-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c085-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c085-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c085-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c085-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c085-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c085-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c085-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c085-118">See Also</span></span>  
 [<span data-ttu-id="0c085-119">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c085-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="0c085-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c085-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0c085-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0c085-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
