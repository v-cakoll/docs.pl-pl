---
title: ICorDebugChain::GetPrevious — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fdcdf23dfee01e8bad1c95adb4de66f270d5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474972"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="eef4f-102">ICorDebugChain::GetPrevious — Metoda</span><span class="sxs-lookup"><span data-stu-id="eef4f-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="eef4f-103">Pobiera łańcuch poprzedniej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="eef4f-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eef4f-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eef4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eef4f-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="eef4f-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje łańcuch poprzedniej ramki dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="eef4f-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="eef4f-107">Jeśli ten łańcuch jest pierwszym łańcucha `ppChain` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="eef4f-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eef4f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eef4f-108">Requirements</span></span>  
 <span data-ttu-id="eef4f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eef4f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eef4f-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eef4f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eef4f-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eef4f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eef4f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eef4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
