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
ms.openlocfilehash: 015085cff23028814937dfef9aea19af7438b4f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173813"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="bfe8e-102">ICorDebugClass2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfe8e-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="bfe8e-103">Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="bfe8e-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="bfe8e-104">Ten interfejs rozszerza [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bfe8e-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfe8e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bfe8e-105">Methods</span></span>  
  
|<span data-ttu-id="bfe8e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bfe8e-106">Method</span></span>|<span data-ttu-id="bfe8e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bfe8e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bfe8e-108">GetParameterizedType, metoda</span><span class="sxs-lookup"><span data-stu-id="bfe8e-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="bfe8e-109">Pobiera deklaracji typu dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="bfe8e-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="bfe8e-110">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="bfe8e-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="bfe8e-111">Ustawia wartość wskazującą, czy metoda jest zdefiniowany przez użytkownika kod dla każdej metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="bfe8e-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfe8e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfe8e-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfe8e-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="bfe8e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfe8e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfe8e-114">Requirements</span></span>  
 <span data-ttu-id="bfe8e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfe8e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfe8e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfe8e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfe8e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfe8e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfe8e-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe8e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe8e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfe8e-119">See also</span></span>

- [<span data-ttu-id="bfe8e-120">ICorDebugClass Interface</span><span class="sxs-lookup"><span data-stu-id="bfe8e-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="bfe8e-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bfe8e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
