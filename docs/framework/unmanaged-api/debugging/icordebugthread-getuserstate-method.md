---
title: "ICorDebugThread::GetUserState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9af89f355916f01fad118a4b63b57b23b2671f54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="07e6d-102">ICorDebugThread::GetUserState — Metoda</span><span class="sxs-lookup"><span data-stu-id="07e6d-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="07e6d-103">Pobiera bieżący stan to ICorDebugThread użytkownika.</span><span class="sxs-lookup"><span data-stu-id="07e6d-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07e6d-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07e6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07e6d-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="07e6d-106">[out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugUserState, które opisują bieżący stan użytkownika tego wątku.</span><span class="sxs-lookup"><span data-stu-id="07e6d-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e6d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07e6d-107">Remarks</span></span>  
 <span data-ttu-id="07e6d-108">Stanu użytkownika w wątku jest stan wątku, gdy jest on analizowane przez program, który jest debugowany.</span><span class="sxs-lookup"><span data-stu-id="07e6d-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="07e6d-109">Wątek może mieć wiele bitów stanu.</span><span class="sxs-lookup"><span data-stu-id="07e6d-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e6d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07e6d-110">Requirements</span></span>  
 <span data-ttu-id="07e6d-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e6d-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07e6d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07e6d-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07e6d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e6d-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
