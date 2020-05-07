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
ms.openlocfilehash: 55036fcdbd186f91c0e94fb05f3023cf614751f7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894250"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="6b8da-102">ICorDebugChain::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b8da-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="6b8da-103">Pobiera wartość wskazującą, czy w tym łańcuchu działa kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6b8da-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b8da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b8da-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b8da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b8da-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="6b8da-106">określoną `true` Jeśli w tym łańcuchu działa kod zarządzany; w przeciwnym `false`razie.</span><span class="sxs-lookup"><span data-stu-id="6b8da-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b8da-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b8da-107">Requirements</span></span>  
 <span data-ttu-id="6b8da-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b8da-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b8da-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b8da-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b8da-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b8da-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b8da-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b8da-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
