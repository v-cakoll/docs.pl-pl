---
title: ICorDebugEval2 Interface1
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
ms.openlocfilehash: da4364e132e2a9d578a761eea77d0dfc8d0b92aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418239"
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="6dfee-102">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="6dfee-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="6dfee-103">Rozszerza "ICorDebugEval" Aby zapewnić obsługę dla typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="6dfee-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6dfee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6dfee-104">Methods</span></span>  
  
|<span data-ttu-id="6dfee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-105">Method</span></span>|<span data-ttu-id="6dfee-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6dfee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6dfee-107">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="6dfee-108">Konfiguruje wywołanie do określonego "ICorDebugFunction", które mogą być zagnieżdżone wewnątrz typu, których konstruktora przyjmuje parametry typu lub mogą się zająć parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="6dfee-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="6dfee-109">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="6dfee-110">Pobiera wskaźnik do nowego "ICorDebugValue" określonego typu o początkowej wartości null lub zero.</span><span class="sxs-lookup"><span data-stu-id="6dfee-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="6dfee-111">NewParameterizedArray, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="6dfee-112">Przydziela nowej tablicy o typie określonym elemencie i wymiary.</span><span class="sxs-lookup"><span data-stu-id="6dfee-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="6dfee-113">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="6dfee-114">Tworzy nowy obiekt sparametryzowany typ i wywołuje metodę konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="6dfee-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="6dfee-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="6dfee-116">Tworzy nowy obiekt sparametryzowany typ określonej klasy bez próba wywołania metody konstruktora</span><span class="sxs-lookup"><span data-stu-id="6dfee-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="6dfee-117">NewStringWithLength, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="6dfee-118">Tworzy nowy ciąg o określonej długości, przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="6dfee-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="6dfee-119">RudeAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="6dfee-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="6dfee-120">Przerywa obliczenia tego `ICorDebugEval2` wykonuje obecnie.</span><span class="sxs-lookup"><span data-stu-id="6dfee-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dfee-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dfee-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dfee-122">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="6dfee-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfee-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dfee-123">Requirements</span></span>  
 <span data-ttu-id="6dfee-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dfee-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfee-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6dfee-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dfee-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dfee-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dfee-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfee-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfee-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dfee-128">See Also</span></span>  
 [<span data-ttu-id="6dfee-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6dfee-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
