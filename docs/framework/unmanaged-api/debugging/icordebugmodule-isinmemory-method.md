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
ms.openlocfilehash: c5fa55a84ed8907a5072f6099c3bf02cd6d78683
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213133"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="1f242-102">ICorDebugModule::IsInMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f242-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="1f242-103">Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1f242-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f242-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f242-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f242-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="1f242-106">[out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="1f242-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f242-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f242-107">Remarks</span></span>  
 <span data-ttu-id="1f242-108">Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów z nieprzetworzonych strumieni bajtów.</span><span class="sxs-lookup"><span data-stu-id="1f242-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="1f242-109">Takie moduły są wywoływane *w modułach pamięci* i nie istnieją na dysku.</span><span class="sxs-lookup"><span data-stu-id="1f242-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f242-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f242-110">Requirements</span></span>  
 <span data-ttu-id="1f242-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f242-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f242-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f242-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f242-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1f242-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f242-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f242-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f242-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f242-115">See also</span></span>
