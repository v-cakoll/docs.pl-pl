---
title: ICorDebugHeapValue2::CreateHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498539"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="6c388-102">ICorDebugHeapValue2::CreateHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c388-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="6c388-103">Tworzy dojście do określonego typu dla wartości sterty, reprezentowane przez ten obiekt icordebugheapvalue2 —.</span><span class="sxs-lookup"><span data-stu-id="6c388-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c388-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c388-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c388-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c388-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="6c388-106">[in] Wartość cordebughandletype — wyliczenie, który określa typ dojścia do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="6c388-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="6c388-107">[out] Wskaźnik na adres icordebughandlevalue — obiekt, który reprezentuje nowy uchwyt dla tej wartości na stosie.</span><span class="sxs-lookup"><span data-stu-id="6c388-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c388-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c388-108">Remarks</span></span>  
 <span data-ttu-id="6c388-109">Dojście zostaną utworzone w domenie aplikacji, która jest skojarzona z wartością sterty i staną się nieprawidłowe, jeśli domena aplikacji zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="6c388-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="6c388-110">Spowoduje to utworzenie wielu wywołań tej funkcji dla tej samej wartości sterty obsługuje wiele.</span><span class="sxs-lookup"><span data-stu-id="6c388-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="6c388-111">Ponieważ uchwyty wpływa na wydajność modułu odśmiecania pamięci, debuger należy ograniczyć do stosunkowo małej liczby dojść (około 256), które są aktywne w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="6c388-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c388-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c388-112">Requirements</span></span>  
 <span data-ttu-id="6c388-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c388-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c388-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c388-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c388-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c388-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c388-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c388-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
