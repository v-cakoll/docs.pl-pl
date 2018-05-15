---
title: ICorDebugChain::GetRegisterSet — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfdde1f29300fcdc0f4e267949fdc3f6fd9917ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="3f214-102">ICorDebugChain::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f214-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="3f214-103">Pobiera rejestr dla active część ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="3f214-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f214-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f214-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f214-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f214-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="3f214-106">[out] Wskaźnik do adresu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) obiekt, który reprezentuje rejestru ustawić active części ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="3f214-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f214-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f214-107">Requirements</span></span>  
 <span data-ttu-id="3f214-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f214-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f214-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f214-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f214-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f214-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f214-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f214-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
