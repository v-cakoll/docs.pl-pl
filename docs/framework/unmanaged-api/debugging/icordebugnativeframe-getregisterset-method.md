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
ms.openlocfilehash: 8714cecb343d21fd119a925d2fc7c23abbaebbe1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664450"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="9fe2e-102">ICorDebugNativeFrame::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="9fe2e-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="9fe2e-103">Pobiera rejestr, ustaw dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fe2e-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fe2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fe2e-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="9fe2e-106">[out] Wskaźnik na adres [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) obiekt, który reprezentuje rejestru, ustaw dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe2e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fe2e-107">Requirements</span></span>  
 <span data-ttu-id="9fe2e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fe2e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe2e-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fe2e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fe2e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fe2e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fe2e-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe2e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe2e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fe2e-112">See also</span></span>

