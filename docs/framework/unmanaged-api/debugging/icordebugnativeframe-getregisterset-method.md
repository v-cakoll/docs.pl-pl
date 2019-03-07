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
ms.openlocfilehash: 18db366bde4211afa0f65052affa0ab9639df122
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498929"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="bf715-102">ICorDebugNativeFrame::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf715-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="bf715-103">Pobiera rejestr, ustaw dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="bf715-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf715-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf715-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf715-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf715-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="bf715-106">[out] Wskaźnik na adres [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) obiekt, który reprezentuje rejestru, ustaw dla tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="bf715-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf715-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf715-107">Requirements</span></span>  
 <span data-ttu-id="bf715-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf715-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf715-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf715-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf715-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf715-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf715-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf715-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf715-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf715-112">See also</span></span>

