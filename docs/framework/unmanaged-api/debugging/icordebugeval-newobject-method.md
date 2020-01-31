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
ms.openlocfilehash: 38cc98f1bfd966d1f764e43b30003a2bae66297d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793468"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="33e19-102">ICorDebugEval::NewObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="33e19-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="33e19-103">Przydziela nowe wystąpienie obiektu i wywołuje określoną metodę konstruktora.</span><span class="sxs-lookup"><span data-stu-id="33e19-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="33e19-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="33e19-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="33e19-105">Zamiast tego użyj [ICorDebugEval2:: NewParameterizedObject —](icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33e19-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e19-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="33e19-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33e19-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="33e19-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="33e19-108">podczas Konstruktor, który ma zostać wywołany.</span><span class="sxs-lookup"><span data-stu-id="33e19-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="33e19-109">podczas Rozmiar tablicy `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="33e19-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="33e19-110">podczas Tablica obiektów ICorDebugValue, z których każdy reprezentuje argument, który ma zostać przesłany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="33e19-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e19-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33e19-111">Requirements</span></span>  
 <span data-ttu-id="33e19-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33e19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e19-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33e19-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33e19-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33e19-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33e19-115">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="33e19-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e19-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33e19-116">See also</span></span>

- [<span data-ttu-id="33e19-117">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="33e19-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
