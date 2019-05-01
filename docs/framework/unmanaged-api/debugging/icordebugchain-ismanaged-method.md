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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989342"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="39c16-102">ICorDebugChain::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="39c16-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="39c16-103">Pobiera wartość wskazującą, czy ten łańcuch działa dla kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="39c16-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39c16-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39c16-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="39c16-106">[out] `true` Jeśli ten łańcuch działa kod zarządzany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="39c16-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c16-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39c16-107">Requirements</span></span>  
 <span data-ttu-id="39c16-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39c16-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c16-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39c16-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39c16-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39c16-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39c16-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c16-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
