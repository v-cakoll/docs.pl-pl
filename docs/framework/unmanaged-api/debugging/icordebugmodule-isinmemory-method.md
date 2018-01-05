---
title: "ICorDebugModule::IsInMemory — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsInMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 448458874c4de96503261bc0fe34fae160395c49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="c17c8-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="c17c8-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="c17c8-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c17c8-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c17c8-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c17c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c17c8-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="c17c8-106">[out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c17c8-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c17c8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c17c8-107">Remarks</span></span>  
 <span data-ttu-id="c17c8-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów raw strumienie bajtów.</span><span class="sxs-lookup"><span data-stu-id="c17c8-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="c17c8-109">Takie moduły są nazywane *modułów w pamięci* i nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="c17c8-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17c8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c17c8-110">Requirements</span></span>  
 <span data-ttu-id="c17c8-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c17c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c17c8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c17c8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c17c8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c17c8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c17c8-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c17c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17c8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c17c8-115">See Also</span></span>  
    
 
