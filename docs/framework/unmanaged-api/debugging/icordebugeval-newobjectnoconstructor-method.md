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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e4a09db3cedce7b0ae6049c7e550c0c3e21cc8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753172"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="7fceb-102">ICorDebugEval::NewObjectNoConstructor — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fceb-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="7fceb-103">Przydziela nowe wystąpienie obiektu określonego typu bez próby wywołania metody konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7fceb-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="7fceb-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="7fceb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7fceb-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span><span class="sxs-lookup"><span data-stu-id="7fceb-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fceb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fceb-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fceb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fceb-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="7fceb-108">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje typ obiektu, który ma zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="7fceb-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fceb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fceb-109">Requirements</span></span>  
 <span data-ttu-id="7fceb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fceb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fceb-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fceb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fceb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fceb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fceb-113">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="7fceb-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fceb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fceb-114">See also</span></span>

- [<span data-ttu-id="7fceb-115">NewParameterizedObjectNoConstructor, metoda</span><span class="sxs-lookup"><span data-stu-id="7fceb-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
