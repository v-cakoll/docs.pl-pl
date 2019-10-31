---
title: ICorDebugEval::NewObjectNoConstructor — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 255d88dcdd880c73a7535cddcad410dcfdcf1d70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132660"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="3a84c-102">ICorDebugEval::NewObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a84c-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="3a84c-103">Przydziela nowe wystąpienie obiektu określonego typu, bez próby wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3a84c-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="3a84c-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="3a84c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3a84c-105">Zamiast tego użyj [ICorDebugEval2:: NewParameterizedObjectNoConstructor —](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a84c-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a84c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a84c-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a84c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a84c-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="3a84c-108">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje typ obiektu do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3a84c-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a84c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a84c-109">Requirements</span></span>  
 <span data-ttu-id="3a84c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a84c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a84c-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a84c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a84c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a84c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a84c-113">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3a84c-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a84c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a84c-114">See also</span></span>

- [<span data-ttu-id="3a84c-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="3a84c-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
