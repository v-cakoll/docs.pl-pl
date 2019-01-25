---
title: ICorDebugEval::NewObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ff4f86105fd1dfbd12360c01046492f3a6dbdcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589953"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="c7668-102">ICorDebugEval::NewObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7668-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="c7668-103">Przydziela nowe wystąpienie obiektu, a następnie wywołuje metodę określonej konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c7668-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="c7668-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c7668-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c7668-105">Użyj [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c7668-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7668-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7668-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7668-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7668-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="c7668-108">[in] Konstruktor, który ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="c7668-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="c7668-109">[in] Rozmiar `ppArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c7668-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="c7668-110">[in] Tablica obiektów ICorDebugValue, z których każdy reprezentuje argument do przekazania do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c7668-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7668-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7668-111">Requirements</span></span>  
 <span data-ttu-id="c7668-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7668-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7668-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7668-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7668-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7668-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7668-115">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="c7668-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7668-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7668-116">See also</span></span>
- [<span data-ttu-id="c7668-117">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="c7668-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
