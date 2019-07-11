---
title: ICorDebugRegisterSet2::SetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e11e7eb477d938d3ccba352ef357d927af966bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770655"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="3e020-102">ICorDebugRegisterSet2::SetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="3e020-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="3e020-103">`SetRegisters` nie jest zaimplementowana w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e020-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3e020-104">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="3e020-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e020-105">Używać operacji wyższego poziomu, takich jak [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e020-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e020-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e020-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3e020-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e020-107">Requirements</span></span>  
 <span data-ttu-id="3e020-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e020-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e020-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e020-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e020-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e020-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e020-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e020-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e020-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e020-112">See also</span></span>

- [<span data-ttu-id="3e020-113">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e020-113">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="3e020-114">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e020-114">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
