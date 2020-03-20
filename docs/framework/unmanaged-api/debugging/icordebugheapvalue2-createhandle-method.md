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
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178878"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="1ec84-102">ICorDebugHeapValue2::CreateHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ec84-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="1ec84-103">Tworzy dojście określonego typu dla wartości sterty reprezentowanej przez ten obiekt ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="1ec84-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ec84-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ec84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ec84-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="1ec84-106">[w] Wartość wyliczenia CorDebugHandleType, która określa typ dojścia do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="1ec84-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="1ec84-107">[na zewnątrz] Wskaźnik do adresu obiektu ICorDebugHandleValue, który reprezentuje nowy dojście dla tej wartości sterty.</span><span class="sxs-lookup"><span data-stu-id="1ec84-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ec84-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ec84-108">Remarks</span></span>  
 <span data-ttu-id="1ec84-109">Dojście zostanie utworzony w domenie aplikacji, która jest skojarzona z wartością sterty i stanie się nieprawidłowa, jeśli domena aplikacji zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="1ec84-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="1ec84-110">Wiele wywołań tej funkcji dla tej samej wartości sterty utworzy wiele uchwytów.</span><span class="sxs-lookup"><span data-stu-id="1ec84-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="1ec84-111">Ponieważ uchwyty wpływają na wydajność modułu zbierającego elementy bezużyteczne, debuger powinien ograniczyć się do stosunkowo niewielkiej liczby uchwytów (około 256), które są aktywne w czasie.</span><span class="sxs-lookup"><span data-stu-id="1ec84-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ec84-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ec84-112">Requirements</span></span>  
 <span data-ttu-id="1ec84-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ec84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ec84-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ec84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ec84-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ec84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ec84-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ec84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
