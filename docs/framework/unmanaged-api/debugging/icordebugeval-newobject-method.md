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
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137620"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="1c825-102">ICorDebugEval::NewObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c825-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="1c825-103">Przydziela nowe wystąpienie obiektu i wywołuje określoną metodę konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1c825-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="1c825-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="1c825-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1c825-105">Zamiast tego użyj [ICorDebugEval2:: NewParameterizedObject —](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c825-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c825-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c825-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c825-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c825-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="1c825-108">podczas Konstruktor, który ma zostać wywołany.</span><span class="sxs-lookup"><span data-stu-id="1c825-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="1c825-109">podczas Rozmiar tablicy `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="1c825-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="1c825-110">podczas Tablica obiektów ICorDebugValue, z których każdy reprezentuje argument, który ma zostać przesłany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1c825-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c825-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c825-111">Requirements</span></span>  
 <span data-ttu-id="1c825-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c825-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c825-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c825-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c825-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c825-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c825-115">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="1c825-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c825-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c825-116">See also</span></span>

- [<span data-ttu-id="1c825-117">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="1c825-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
