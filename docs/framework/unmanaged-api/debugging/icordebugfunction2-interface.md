---
title: ICorDebugFunction2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 190e2323fb07dbca6e156d7a24397997e54b6da9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540796"
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="ebf95-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="ebf95-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="ebf95-103">Logicznie umożliwia rozbudowanie interfejsu programu ICorDebugFunction, aby zapewnić obsługę debugowania tylko mój kod krokowym, które pomija kod niezwiązany z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="ebf95-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebf95-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ebf95-104">Methods</span></span>  
  
|<span data-ttu-id="ebf95-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ebf95-105">Method</span></span>|<span data-ttu-id="ebf95-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ebf95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebf95-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="ebf95-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="ebf95-108">(Nie została jeszcze zaimplementowana.) Pobiera wskaźnik interfejsu do icordebugcodeenum —, który zawiera instrukcje kodu natywnego w funkcji odwołuje się ten obiekt icordebugfunction2 —.</span><span class="sxs-lookup"><span data-stu-id="ebf95-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="ebf95-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="ebf95-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="ebf95-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ebf95-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="ebf95-111">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="ebf95-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="ebf95-112">Pobiera Edytuj i Kontynuuj wersja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ebf95-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="ebf95-113">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="ebf95-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="ebf95-114">Zaznacza tę funkcję tylko mój kod przechodzenie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="ebf95-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf95-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebf95-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebf95-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ebf95-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf95-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebf95-117">Requirements</span></span>  
 <span data-ttu-id="ebf95-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf95-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf95-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebf95-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebf95-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf95-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf95-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf95-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf95-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebf95-122">See also</span></span>
- [<span data-ttu-id="ebf95-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ebf95-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
