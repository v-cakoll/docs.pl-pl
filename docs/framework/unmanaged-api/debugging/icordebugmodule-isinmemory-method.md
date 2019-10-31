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
ms.openlocfilehash: 1384acff4ea3d1aa820b065cd2c56f649f0cbdbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127921"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="d282b-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="d282b-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="d282b-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d282b-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d282b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d282b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d282b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d282b-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="d282b-106">[out] `true`, jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d282b-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d282b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d282b-107">Remarks</span></span>  
 <span data-ttu-id="d282b-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów z nieprzetworzonych strumieni bajtów.</span><span class="sxs-lookup"><span data-stu-id="d282b-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="d282b-109">Takie moduły są wywoływane *w modułach pamięci* i nie istnieją na dysku.</span><span class="sxs-lookup"><span data-stu-id="d282b-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d282b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d282b-110">Requirements</span></span>  
 <span data-ttu-id="d282b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d282b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d282b-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d282b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d282b-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d282b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d282b-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d282b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d282b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d282b-115">See also</span></span>
