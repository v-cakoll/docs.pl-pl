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
ms.openlocfilehash: 75cc729a3d0ffa7ac67b29be2defb84b05cc6bb0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894473"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="a2c21-102">ICorDebugChain::GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2c21-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="a2c21-103">Pobiera zestaw rejestru dla aktywnej części tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="a2c21-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2c21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2c21-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="a2c21-106">określoną Wskaźnik do adresu obiektu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla aktywnej części tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="a2c21-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c21-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2c21-107">Requirements</span></span>  
 <span data-ttu-id="a2c21-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c21-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c21-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2c21-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c21-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a2c21-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c21-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c21-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
