---
title: "ICorDebugThread::GetHandle — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3cd5f7191c00b7c6b07bacc463d906982c994578
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="57b35-102">ICorDebugThread::GetHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="57b35-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="57b35-103">Pobiera bieżący dojście active części tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="57b35-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57b35-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57b35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57b35-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="57b35-106">[out] Wskaźnik do HTHREAD będący dojście active częścią tego wątku.</span><span class="sxs-lookup"><span data-stu-id="57b35-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57b35-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57b35-107">Remarks</span></span>  
 <span data-ttu-id="57b35-108">Dojście może zmienić proces wykonuje i mogą być różne dla różnych części wątku.</span><span class="sxs-lookup"><span data-stu-id="57b35-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="57b35-109">Ta dojścia jest własnością interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="57b35-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="57b35-110">Debuger powinien zduplikowane go przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="57b35-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57b35-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57b35-111">Requirements</span></span>  
 <span data-ttu-id="57b35-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57b35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57b35-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57b35-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57b35-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57b35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57b35-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57b35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
