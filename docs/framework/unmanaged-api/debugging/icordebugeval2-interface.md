---
title: ICorDebugEval2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cad998ec30ee97cf6c1eb27640567b3fe233a19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951948"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="6cc27-102">ICorDebugEval2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6cc27-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="6cc27-103">Rozszerza "ICorDebugEval", aby zapewnić obsługę typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="6cc27-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cc27-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6cc27-104">Methods</span></span>  
  
|<span data-ttu-id="6cc27-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-105">Method</span></span>|<span data-ttu-id="6cc27-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6cc27-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cc27-107">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="6cc27-108">Konfiguruje wywołanie do określonego elementu "ICorDebugFunction", który może być zagnieżdżony wewnątrz typu, którego Konstruktor pobiera parametry typu, lub sam może przyjmować parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6cc27-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="6cc27-109">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="6cc27-110">Pobiera wskaźnik do nowego elementu "ICorDebugValue" określonego typu z początkową wartością null lub zero.</span><span class="sxs-lookup"><span data-stu-id="6cc27-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="6cc27-111">NewParameterizedArray, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="6cc27-112">Przypisuje nową tablicę określonego typu elementu i wymiarów.</span><span class="sxs-lookup"><span data-stu-id="6cc27-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="6cc27-113">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="6cc27-114">Tworzy wystąpienie nowego obiektu typu sparametryzowanego i wywołuje metodę konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="6cc27-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="6cc27-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="6cc27-116">Tworzy wystąpienie nowego obiektu typu sparametryzowanego określonej klasy bez próby wywołania metody konstruktora</span><span class="sxs-lookup"><span data-stu-id="6cc27-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="6cc27-117">NewStringWithLength, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="6cc27-118">Tworzy nowy ciąg o określonej długości z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="6cc27-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="6cc27-119">RudeAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="6cc27-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="6cc27-120">Przerywa obliczenia, które `ICorDebugEval2` jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="6cc27-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cc27-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cc27-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cc27-122">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6cc27-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cc27-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cc27-123">Requirements</span></span>  
 <span data-ttu-id="6cc27-124">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cc27-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cc27-125">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cc27-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cc27-126">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cc27-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cc27-127">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cc27-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc27-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cc27-128">See also</span></span>

- [<span data-ttu-id="6cc27-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6cc27-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
