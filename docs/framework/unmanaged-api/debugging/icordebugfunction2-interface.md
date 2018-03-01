---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="968a1-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="968a1-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="968a1-103">Logicznie rozszerza interfejs ICorDebugFunction zapewnia obsługę tylko mój kod krokowym debugowania, który powoduje pominięcie kodu innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="968a1-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="968a1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="968a1-104">Methods</span></span>  
  
|<span data-ttu-id="968a1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="968a1-105">Method</span></span>|<span data-ttu-id="968a1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="968a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="968a1-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="968a1-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="968a1-108">(Nie została jeszcze zaimplementowana.) Pobiera wskaźnika interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu macierzystego w funkcji odwołuje się ten obiekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="968a1-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="968a1-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="968a1-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="968a1-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczony jako kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="968a1-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="968a1-111">GetVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="968a1-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="968a1-112">Pobiera wersję tej funkcji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="968a1-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="968a1-113">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="968a1-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="968a1-114">Zaznacza tę funkcję tylko mój kod wykonywanie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="968a1-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="968a1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="968a1-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="968a1-116">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="968a1-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968a1-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="968a1-117">Requirements</span></span>  
 <span data-ttu-id="968a1-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="968a1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968a1-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="968a1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="968a1-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="968a1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="968a1-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968a1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968a1-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="968a1-122">See Also</span></span>  
 [<span data-ttu-id="968a1-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="968a1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
