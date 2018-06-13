---
title: ICorDebugModule::IsInMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ae5c16f9f508511e4a15b2eae2c28d68238f1d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415896"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="fe3c8-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe3c8-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="fe3c8-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe3c8-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe3c8-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe3c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe3c8-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="fe3c8-106">[out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fe3c8-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe3c8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe3c8-107">Remarks</span></span>  
 <span data-ttu-id="fe3c8-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów raw strumienie bajtów.</span><span class="sxs-lookup"><span data-stu-id="fe3c8-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="fe3c8-109">Takie moduły są nazywane *modułów w pamięci* i nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="fe3c8-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3c8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe3c8-110">Requirements</span></span>  
 <span data-ttu-id="fe3c8-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe3c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3c8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe3c8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe3c8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe3c8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe3c8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3c8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe3c8-115">See Also</span></span>  
    
 
