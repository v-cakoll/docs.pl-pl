---
title: ICorDebugFunction2, interfejs
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
ms.openlocfilehash: 5364e39f7e0a9b6c9cd10cd8f17bab4a03a4b7af
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794481"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="265bc-102">ICorDebugFunction2, interfejs</span><span class="sxs-lookup"><span data-stu-id="265bc-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="265bc-103">Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia Tylko mój kod obsługi debugowania krok po kroku, który pomija kod niebędący użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="265bc-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="265bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="265bc-104">Methods</span></span>  
  
|<span data-ttu-id="265bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="265bc-105">Method</span></span>|<span data-ttu-id="265bc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="265bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="265bc-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="265bc-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="265bc-108">(Jeszcze nie zaimplementowano). Pobiera wskaźnik interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu natywnego w funkcji, do której odwołuje się ten obiekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="265bc-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="265bc-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="265bc-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="265bc-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="265bc-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="265bc-111">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="265bc-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="265bc-112">Pobiera wersję Edytuj i Kontynuuj tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="265bc-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="265bc-113">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="265bc-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="265bc-114">Oznacza tę funkcję do Tylko mój kod taktowania.</span><span class="sxs-lookup"><span data-stu-id="265bc-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="265bc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="265bc-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="265bc-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="265bc-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="265bc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="265bc-117">Requirements</span></span>  
 <span data-ttu-id="265bc-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="265bc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="265bc-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="265bc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="265bc-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="265bc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="265bc-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="265bc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="265bc-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="265bc-122">See also</span></span>

- [<span data-ttu-id="265bc-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="265bc-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
