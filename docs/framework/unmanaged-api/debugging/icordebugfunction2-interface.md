---
title: ICorDebugFunction2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: da440b7d2da57511545d3b63700662eb544660fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137779"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="38afc-102">ICorDebugFunction2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="38afc-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="38afc-103">Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia Tylko mój kod obsługi debugowania krok po kroku, który pomija kod niebędący użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="38afc-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38afc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="38afc-104">Methods</span></span>  
  
|<span data-ttu-id="38afc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38afc-105">Method</span></span>|<span data-ttu-id="38afc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38afc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38afc-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="38afc-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="38afc-108">(Jeszcze nie zaimplementowano). Pobiera wskaźnik interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu natywnego w funkcji, do której odwołuje się ten obiekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="38afc-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="38afc-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="38afc-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="38afc-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="38afc-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="38afc-111">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="38afc-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="38afc-112">Pobiera wersję Edytuj i Kontynuuj tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="38afc-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="38afc-113">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="38afc-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="38afc-114">Oznacza tę funkcję do Tylko mój kod taktowania.</span><span class="sxs-lookup"><span data-stu-id="38afc-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38afc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38afc-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38afc-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="38afc-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38afc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38afc-117">Requirements</span></span>  
 <span data-ttu-id="38afc-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38afc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38afc-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38afc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38afc-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="38afc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38afc-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38afc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38afc-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38afc-122">See also</span></span>

- [<span data-ttu-id="38afc-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38afc-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
