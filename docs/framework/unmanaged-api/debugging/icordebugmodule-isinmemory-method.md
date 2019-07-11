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
ms.openlocfilehash: 223989d883c421be228fb3d6a608643a5246c060
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763699"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="52aa2-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="52aa2-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="52aa2-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="52aa2-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52aa2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52aa2-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52aa2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52aa2-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="52aa2-106">[out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="52aa2-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52aa2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52aa2-107">Remarks</span></span>  
 <span data-ttu-id="52aa2-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów z pierwotnych strumieni bajtów.</span><span class="sxs-lookup"><span data-stu-id="52aa2-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="52aa2-109">Takie moduły są nazywane *modułów w pamięci* i nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="52aa2-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52aa2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52aa2-110">Requirements</span></span>  
 <span data-ttu-id="52aa2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52aa2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52aa2-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52aa2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52aa2-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52aa2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52aa2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52aa2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52aa2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52aa2-115">See also</span></span>
