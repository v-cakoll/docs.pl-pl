---
title: ICorDebugThread::GetDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="ba6f3-102">ICorDebugThread::GetDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba6f3-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="ba6f3-103">Pobiera bieżący stan tego obiektu ICorDebugThread debugowania.</span><span class="sxs-lookup"><span data-stu-id="ba6f3-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba6f3-104">Syntax</span></span>  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba6f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba6f3-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="ba6f3-106">[out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugThreadState, które opisują bieżący stan debugowania tego wątku.</span><span class="sxs-lookup"><span data-stu-id="ba6f3-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba6f3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba6f3-107">Remarks</span></span>  
 <span data-ttu-id="ba6f3-108">Jeśli proces jest obecnie zatrzymana, `pState` reprezentuje stan debugowania, czy istnieje dla tego wątku, jeśli proces będzie kontynuowane, nie rzeczywiste bieżący stan tego wątku.</span><span class="sxs-lookup"><span data-stu-id="ba6f3-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba6f3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba6f3-109">Requirements</span></span>  
 <span data-ttu-id="ba6f3-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba6f3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba6f3-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba6f3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba6f3-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba6f3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba6f3-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba6f3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
