---
title: ICorDebugThread::GetActiveChain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05f5a3f29c7b72ed83c1456175f68ef9b986e3e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483319"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="18880-102">ICorDebugThread::GetActiveChain — Metoda</span><span class="sxs-lookup"><span data-stu-id="18880-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="18880-103">Pobiera wskaźnik interfejsu do aktywnego łańcucha stosu (najnowsze) dla tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="18880-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18880-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18880-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18880-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18880-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="18880-106">[out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje łańcucha stosu.</span><span class="sxs-lookup"><span data-stu-id="18880-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18880-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18880-107">Remarks</span></span>  
 <span data-ttu-id="18880-108">`ppChain` Parametr ma wartość null, jeśli żaden łańcuch stosu jest obecnie aktywna.</span><span class="sxs-lookup"><span data-stu-id="18880-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18880-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18880-109">Requirements</span></span>  
 <span data-ttu-id="18880-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18880-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18880-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18880-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18880-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18880-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18880-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18880-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
