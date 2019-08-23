---
title: ICorDebugClass2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6a8b0ead430ffdd0e4e30cacae54d68fa9d730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969262"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="d1500-102">ICorDebugClass2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1500-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="d1500-103">Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d1500-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d1500-104">Ten interfejs rozszerza [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d1500-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1500-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d1500-105">Methods</span></span>  
  
|<span data-ttu-id="d1500-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1500-106">Method</span></span>|<span data-ttu-id="d1500-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d1500-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1500-108">GetParameterizedType, metoda</span><span class="sxs-lookup"><span data-stu-id="d1500-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="d1500-109">Pobiera deklarację typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="d1500-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="d1500-110">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="d1500-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="d1500-111">Dla każdej metody tej klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d1500-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1500-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1500-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1500-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d1500-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1500-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1500-114">Requirements</span></span>  
 <span data-ttu-id="d1500-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1500-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1500-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1500-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1500-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1500-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1500-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1500-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1500-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1500-119">See also</span></span>

- [<span data-ttu-id="d1500-120">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1500-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="d1500-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1500-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
