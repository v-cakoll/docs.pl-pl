---
title: ICorDebugClass2 — Interfejs
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
ms.openlocfilehash: cb2ab28824d209dd1eed627600e30e9ddb0d7c7a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125723"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="09bea-102">ICorDebugClass2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="09bea-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="09bea-103">Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="09bea-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="09bea-104">Ten interfejs rozszerza [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="09bea-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09bea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="09bea-105">Methods</span></span>  
  
|<span data-ttu-id="09bea-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="09bea-106">Method</span></span>|<span data-ttu-id="09bea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="09bea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09bea-108">GetParameterizedType, metoda</span><span class="sxs-lookup"><span data-stu-id="09bea-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="09bea-109">Pobiera deklarację typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="09bea-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="09bea-110">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="09bea-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="09bea-111">Dla każdej metody tej klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="09bea-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09bea-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09bea-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09bea-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="09bea-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09bea-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09bea-114">Requirements</span></span>  
 <span data-ttu-id="09bea-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09bea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09bea-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09bea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09bea-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09bea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09bea-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09bea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09bea-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09bea-119">See also</span></span>

- [<span data-ttu-id="09bea-120">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="09bea-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="09bea-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09bea-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
