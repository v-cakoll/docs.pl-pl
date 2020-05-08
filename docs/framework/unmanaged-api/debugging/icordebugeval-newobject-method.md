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
ms.openlocfilehash: e9570d3c916123093f69e7f26d3778f1c7184b1f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976190"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="7a632-102">ICorDebugEval::NewObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a632-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="7a632-103">Przydziela nowe wystąpienie obiektu i wywołuje określoną metodę konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7a632-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="7a632-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="7a632-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7a632-105">Zamiast tego użyj [ICorDebugEval2:: NewParameterizedObject —](icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7a632-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a632-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a632-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a632-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a632-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="7a632-108">podczas Konstruktor, który ma zostać wywołany.</span><span class="sxs-lookup"><span data-stu-id="7a632-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="7a632-109">podczas Rozmiar `ppArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7a632-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="7a632-110">podczas Tablica obiektów ICorDebugValue, z których każdy reprezentuje argument, który ma zostać przesłany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7a632-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a632-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a632-111">Requirements</span></span>  
 <span data-ttu-id="7a632-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a632-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a632-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a632-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a632-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7a632-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a632-115">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="7a632-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a632-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a632-116">See also</span></span>

- [<span data-ttu-id="7a632-117">NewParameterizedObject, metoda</span><span class="sxs-lookup"><span data-stu-id="7a632-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
