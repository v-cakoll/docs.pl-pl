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
ms.openlocfilehash: 2dce97db3d209c51270a51ae92e9dce0b6861998
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792000"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="42be1-102">ICorDebugRegisterSet2::SetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="42be1-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="42be1-103">`SetRegisters` nie została zaimplementowana w .NET Framework wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="42be1-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="42be1-104">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="42be1-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42be1-105">Użyj operacji wyższego poziomu, takich jak [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) lub [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="42be1-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42be1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="42be1-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="42be1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42be1-107">Requirements</span></span>  
 <span data-ttu-id="42be1-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42be1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42be1-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42be1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42be1-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42be1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42be1-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42be1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42be1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42be1-112">See also</span></span>

- [<span data-ttu-id="42be1-113">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42be1-113">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="42be1-114">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="42be1-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
