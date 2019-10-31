---
title: ICorDebugChain::IsManaged — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 481f6d08e11a5f315c64b3d58df4ab291fa42e78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123847"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="84013-102">ICorDebugChain::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="84013-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="84013-103">Pobiera wartość wskazującą, czy w tym łańcuchu działa kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="84013-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84013-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84013-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84013-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84013-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="84013-106">[out] `true`, jeśli ten łańcuch działa w kodzie zarządzanym; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="84013-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84013-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84013-107">Requirements</span></span>  
 <span data-ttu-id="84013-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84013-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84013-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="84013-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84013-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="84013-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84013-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84013-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
