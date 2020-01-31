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
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788706"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="19987-102">ICorDebugEval2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19987-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="19987-103">Rozszerza "ICorDebugEval", aby zapewnić obsługę typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="19987-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19987-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19987-104">Methods</span></span>  
  
|<span data-ttu-id="19987-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19987-105">Method</span></span>|<span data-ttu-id="19987-106">Opis</span><span class="sxs-lookup"><span data-stu-id="19987-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19987-107">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-107">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="19987-108">Konfiguruje wywołanie do określonego elementu "ICorDebugFunction", który może być zagnieżdżony wewnątrz typu, którego Konstruktor pobiera parametry typu, lub sam może przyjmować parametry typu.</span><span class="sxs-lookup"><span data-stu-id="19987-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="19987-109">CreateValueForType, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-109">CreateValueForType Method</span></span>](icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="19987-110">Pobiera wskaźnik do nowego elementu "ICorDebugValue" określonego typu z początkową wartością null lub zero.</span><span class="sxs-lookup"><span data-stu-id="19987-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="19987-111">NewParameterizedArray, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-111">NewParameterizedArray Method</span></span>](icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="19987-112">Przypisuje nową tablicę określonego typu elementu i wymiarów.</span><span class="sxs-lookup"><span data-stu-id="19987-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="19987-113">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-113">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="19987-114">Tworzy wystąpienie nowego obiektu typu sparametryzowanego i wywołuje metodę konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="19987-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="19987-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="19987-116">Tworzy wystąpienie nowego obiektu typu sparametryzowanego określonej klasy bez próby wywołania metody konstruktora</span><span class="sxs-lookup"><span data-stu-id="19987-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="19987-117">NewStringWithLength, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-117">NewStringWithLength Method</span></span>](icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="19987-118">Tworzy nowy ciąg o określonej długości z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="19987-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="19987-119">RudeAbort, metoda</span><span class="sxs-lookup"><span data-stu-id="19987-119">RudeAbort Method</span></span>](icordebugeval2-rudeabort-method.md)|<span data-ttu-id="19987-120">Przerywa Obliczanie wykonywane przez tę `ICorDebugEval2`.</span><span class="sxs-lookup"><span data-stu-id="19987-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19987-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19987-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19987-122">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="19987-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19987-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19987-123">Requirements</span></span>  
 <span data-ttu-id="19987-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19987-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19987-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19987-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19987-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19987-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19987-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19987-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19987-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19987-128">See also</span></span>

- [<span data-ttu-id="19987-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="19987-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
