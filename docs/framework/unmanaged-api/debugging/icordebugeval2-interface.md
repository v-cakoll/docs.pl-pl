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
ms.openlocfilehash: 3767368c9da8c97cd081787c0945a15552a1da46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995972"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="88bc6-102">ICorDebugEval2, interfejs</span><span class="sxs-lookup"><span data-stu-id="88bc6-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="88bc6-103">Rozszerza "ICorDebugEval" w celu zapewnienia obsługi typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="88bc6-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88bc6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="88bc6-104">Methods</span></span>  
  
|<span data-ttu-id="88bc6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-105">Method</span></span>|<span data-ttu-id="88bc6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="88bc6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88bc6-107">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="88bc6-108">Konfiguruje wywołanie do określonego "ICorDebugFunction", które mogą być zagnieżdżone wewnątrz typu, w której Konstruktor przyjmuje parametry typu lub może zająć się parametry typu.</span><span class="sxs-lookup"><span data-stu-id="88bc6-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="88bc6-109">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="88bc6-110">Pobiera wskaźnik do nowego "ICorDebugValue" określonego typu o wartości początkowej wartości null lub wartość zero.</span><span class="sxs-lookup"><span data-stu-id="88bc6-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="88bc6-111">NewParameterizedArray, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="88bc6-112">Przydziela nową tablicę typu określonego elementu i wymiary.</span><span class="sxs-lookup"><span data-stu-id="88bc6-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="88bc6-113">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="88bc6-114">Tworzy nowy obiekt typ sparametryzowany i wywołuje metodę do konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="88bc6-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="88bc6-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="88bc6-116">Tworzy nowy typ sparametryzowany obiekt określonej klasy bez próby wywołania metody konstruktora</span><span class="sxs-lookup"><span data-stu-id="88bc6-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="88bc6-117">NewStringWithLength, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="88bc6-118">Tworzy nowy ciąg o określonej długości, przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="88bc6-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="88bc6-119">RudeAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="88bc6-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="88bc6-120">Przerywa obliczeń że `ICorDebugEval2` Trwa wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="88bc6-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88bc6-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88bc6-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88bc6-122">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="88bc6-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88bc6-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88bc6-123">Requirements</span></span>  
 <span data-ttu-id="88bc6-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88bc6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88bc6-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88bc6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88bc6-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88bc6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88bc6-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88bc6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88bc6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88bc6-128">See also</span></span>

- [<span data-ttu-id="88bc6-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="88bc6-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
