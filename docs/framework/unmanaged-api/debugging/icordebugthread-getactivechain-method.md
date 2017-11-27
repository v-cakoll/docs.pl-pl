---
title: "ICorDebugThread::GetActiveChain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3f104933bc70682a531c0853cfc6eabcd357831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="30b13-102">ICorDebugThread::GetActiveChain — Metoda</span><span class="sxs-lookup"><span data-stu-id="30b13-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="30b13-103">Pobiera wskaźnika interfejsu active (najnowsze) łańcucha stosu dla tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="30b13-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30b13-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30b13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30b13-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="30b13-106">[out] Wskaźnik do adresu ICorDebugChain obiekt, który reprezentuje łańcucha stosu.</span><span class="sxs-lookup"><span data-stu-id="30b13-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b13-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30b13-107">Remarks</span></span>  
 <span data-ttu-id="30b13-108">`ppChain` Parametr ma wartość null, jeśli żaden łańcuch stosu jest obecnie aktywny.</span><span class="sxs-lookup"><span data-stu-id="30b13-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b13-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30b13-109">Requirements</span></span>  
 <span data-ttu-id="30b13-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b13-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b13-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30b13-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30b13-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30b13-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30b13-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
