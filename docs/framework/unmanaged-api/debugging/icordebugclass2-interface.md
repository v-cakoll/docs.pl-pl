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
ms.openlocfilehash: ff15297eb479f7474c9f07123a29263fb4da3205
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893975"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="6bddd-102">ICorDebugClass2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bddd-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="6bddd-103">Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="6bddd-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="6bddd-104">Ten interfejs rozszerza [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6bddd-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bddd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6bddd-105">Methods</span></span>  
  
|<span data-ttu-id="6bddd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6bddd-106">Method</span></span>|<span data-ttu-id="6bddd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6bddd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bddd-108">GetParameterizedType, metoda</span><span class="sxs-lookup"><span data-stu-id="6bddd-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="6bddd-109">Pobiera deklarację typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bddd-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="6bddd-110">SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="6bddd-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="6bddd-111">Dla każdej metody tej klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6bddd-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bddd-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bddd-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bddd-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6bddd-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bddd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bddd-114">Requirements</span></span>  
 <span data-ttu-id="6bddd-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bddd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bddd-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bddd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bddd-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6bddd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bddd-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bddd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bddd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bddd-119">See also</span></span>

- [<span data-ttu-id="6bddd-120">ICorDebugClass, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bddd-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="6bddd-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6bddd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
