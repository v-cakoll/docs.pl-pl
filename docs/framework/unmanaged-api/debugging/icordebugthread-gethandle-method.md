---
title: ICorDebugThread::GetHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 900fece1dd29f73f77b85ff08e4deff1396f8aaf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484514"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="5ed0a-102">ICorDebugThread::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="5ed0a-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="5ed0a-103">Pobiera bieżący uchwyt active część tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5ed0a-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ed0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ed0a-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ed0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ed0a-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="5ed0a-106">[out] Wskaźnik do HTHREAD będącego uchwytu aktywnego część tego wątku.</span><span class="sxs-lookup"><span data-stu-id="5ed0a-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ed0a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ed0a-107">Remarks</span></span>  
 <span data-ttu-id="5ed0a-108">Uchwyt może zmienić proces wykonywany i mogą być różne dla różnych części wątku.</span><span class="sxs-lookup"><span data-stu-id="5ed0a-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="5ed0a-109">Tego dojścia jest własnością interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="5ed0a-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="5ed0a-110">Debuger powinien zduplikować go przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="5ed0a-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ed0a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ed0a-111">Requirements</span></span>  
 <span data-ttu-id="5ed0a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ed0a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ed0a-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ed0a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ed0a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ed0a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ed0a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ed0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
