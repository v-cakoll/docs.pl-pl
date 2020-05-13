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
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379757"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="dcf98-102">ICorDebugThread::GetDebugState — Metoda</span><span class="sxs-lookup"><span data-stu-id="dcf98-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="dcf98-103">Pobiera bieżący stan debugowania tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="dcf98-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcf98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcf98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcf98-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="dcf98-106">określoną Wskaźnik do bitowej kombinacji wartości wyliczenia CorDebugThreadState —, który opisuje bieżący stan debugowania tego wątku.</span><span class="sxs-lookup"><span data-stu-id="dcf98-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcf98-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcf98-107">Remarks</span></span>  
 <span data-ttu-id="dcf98-108">Jeśli proces jest aktualnie zatrzymany, `pState` reprezentuje stan debugowania dla tego wątku, jeśli proces ma być kontynuowany, a nie z rzeczywistym bieżącym stanem tego wątku.</span><span class="sxs-lookup"><span data-stu-id="dcf98-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf98-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcf98-109">Requirements</span></span>  
 <span data-ttu-id="dcf98-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf98-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf98-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dcf98-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcf98-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dcf98-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcf98-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf98-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
