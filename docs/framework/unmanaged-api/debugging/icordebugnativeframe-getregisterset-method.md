---
title: ICorDebugNativeFrame::GetRegisterSet — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6880ed3a2519ad7d4a415e4fcc4510668a0852f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="e7f9d-102">ICorDebugNativeFrame::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7f9d-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="e7f9d-103">Pobiera rejestr, ustaw dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e7f9d-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f9d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7f9d-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7f9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7f9d-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="e7f9d-106">[out] Wskaźnik do adresu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) obiekt, który reprezentuje rejestru ustawić dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e7f9d-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f9d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7f9d-107">Requirements</span></span>  
 <span data-ttu-id="e7f9d-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f9d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f9d-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7f9d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7f9d-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7f9d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7f9d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f9d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f9d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7f9d-112">See Also</span></span>  
 
