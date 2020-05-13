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
ms.openlocfilehash: 611091d39da6d7f646457457f20ce1eaf37db361
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213208"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="81144-102">ICorDebugFunction2, interfejs</span><span class="sxs-lookup"><span data-stu-id="81144-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="81144-103">Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia Tylko mój kod obsługi debugowania krok po kroku, który pomija kod niebędący użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="81144-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81144-104">Metody</span><span class="sxs-lookup"><span data-stu-id="81144-104">Methods</span></span>  
  
|<span data-ttu-id="81144-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="81144-105">Method</span></span>|<span data-ttu-id="81144-106">Opis</span><span class="sxs-lookup"><span data-stu-id="81144-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81144-107">EnumerateNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="81144-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="81144-108">(Jeszcze nie zaimplementowano). Pobiera wskaźnik interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu natywnego w funkcji, do której odwołuje się ten obiekt ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="81144-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="81144-109">GetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="81144-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="81144-110">Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="81144-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="81144-111">GetVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="81144-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="81144-112">Pobiera wersję Edytuj i Kontynuuj tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="81144-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="81144-113">SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="81144-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="81144-114">Oznacza tę funkcję do Tylko mój kod taktowania.</span><span class="sxs-lookup"><span data-stu-id="81144-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81144-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81144-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81144-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="81144-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81144-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81144-117">Requirements</span></span>  
 <span data-ttu-id="81144-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81144-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81144-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81144-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81144-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81144-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81144-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81144-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81144-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81144-122">See also</span></span>

- [<span data-ttu-id="81144-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="81144-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
