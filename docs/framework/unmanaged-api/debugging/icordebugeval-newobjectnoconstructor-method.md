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
ms.openlocfilehash: 45efa1939813a319e996a72fef62ada167b877c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788702"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="8f2e9-102">ICorDebugEval::NewObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f2e9-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="8f2e9-103">Przydziela nowe wystąpienie obiektu określonego typu, bez próby wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="8f2e9-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="8f2e9-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="8f2e9-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8f2e9-105">Zamiast tego użyj [ICorDebugEval2:: NewParameterizedObjectNoConstructor —](icordebugeval2-newparameterizedobjectnoconstructor-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8f2e9-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f2e9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f2e9-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f2e9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f2e9-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="8f2e9-108">podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje typ obiektu do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8f2e9-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f2e9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f2e9-109">Requirements</span></span>  
 <span data-ttu-id="8f2e9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f2e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f2e9-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f2e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f2e9-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f2e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f2e9-113">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="8f2e9-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2e9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f2e9-114">See also</span></span>

- [<span data-ttu-id="8f2e9-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="8f2e9-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
