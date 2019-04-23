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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 159cebc76f732629ed84a3b6c9041cc15f8bbb69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199378"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="d813c-102">ICorDebugFunction2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d813c-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="d813c-103">Logicznie umożliwia rozbudowanie interfejsu programu ICorDebugFunction, aby zapewnić obsługę debugowania tylko mój kod krokowym, które pomija kod niezwiązany z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="d813c-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d813c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d813c-104">Methods</span></span>  
  
|<span data-ttu-id="d813c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d813c-105">Method</span></span>|<span data-ttu-id="d813c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d813c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d813c-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="d813c-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="d813c-108">(Nie została jeszcze zaimplementowana.) Pobiera wskaźnik interfejsu do icordebugcodeenum —, który zawiera instrukcje kodu natywnego w funkcji odwołuje się ten obiekt icordebugfunction2 —.</span><span class="sxs-lookup"><span data-stu-id="d813c-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="d813c-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="d813c-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="d813c-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d813c-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="d813c-111">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="d813c-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="d813c-112">Pobiera Edytuj i Kontynuuj wersja tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d813c-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="d813c-113">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="d813c-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="d813c-114">Zaznacza tę funkcję tylko mój kod przechodzenie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="d813c-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d813c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d813c-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d813c-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="d813c-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d813c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d813c-117">Requirements</span></span>  
 <span data-ttu-id="d813c-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d813c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d813c-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d813c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d813c-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d813c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d813c-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d813c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d813c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d813c-122">See also</span></span>

- [<span data-ttu-id="d813c-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d813c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
