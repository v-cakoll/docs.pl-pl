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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a27ea95ca78f7db8f67ec2a13f02767e67619e97
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488061"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="8bf90-102">ICorDebugChain::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="8bf90-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="8bf90-103">Pobiera wartość wskazującą, czy ten łańcuch działa dla kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8bf90-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bf90-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bf90-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="8bf90-106">[out] `true` Jeśli ten łańcuch działa kod zarządzany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8bf90-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf90-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bf90-107">Requirements</span></span>  
 <span data-ttu-id="8bf90-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf90-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf90-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bf90-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bf90-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf90-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf90-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf90-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
