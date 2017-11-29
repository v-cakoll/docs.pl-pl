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
ms.openlocfilehash: 58f7964faee19f85c83d1b9b1c3e176354ae9588
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="e6479-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="e6479-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="e6479-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e6479-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6479-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6479-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6479-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6479-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="e6479-106">[out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e6479-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6479-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6479-107">Remarks</span></span>  
 <span data-ttu-id="e6479-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów raw strumienie bajtów.</span><span class="sxs-lookup"><span data-stu-id="e6479-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="e6479-109">Takie moduły są nazywane *modułów w pamięci* i nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="e6479-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6479-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6479-110">Requirements</span></span>  
 <span data-ttu-id="e6479-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6479-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6479-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6479-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6479-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6479-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6479-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6479-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6479-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6479-115">See Also</span></span>  
    
 
