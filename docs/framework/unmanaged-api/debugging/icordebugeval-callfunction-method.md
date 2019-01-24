---
title: ICorDebugEval::CallFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589402"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="bc2b4-102">ICorDebugEval::CallFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc2b4-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="bc2b4-103">Konfiguruje wywołanie do określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="bc2b4-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bc2b4-105">Użyj [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2b4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc2b4-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc2b4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc2b4-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="bc2b4-108">[in] Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="bc2b4-109">[in] Liczba argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="bc2b4-110">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, który określa argument, który zostanie przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc2b4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc2b4-111">Remarks</span></span>  
 <span data-ttu-id="bc2b4-112">Jeśli funkcja znajduje się wirtualny, `CallFunction` wykona wirtualnego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="bc2b4-113">Jeśli funkcja znajduje się w domenie innej aplikacji, przejście wystąpi tak długo, jak wszystkie argumenty mają również w tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc2b4-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2b4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc2b4-114">Requirements</span></span>  
 <span data-ttu-id="bc2b4-115">**Platformy:** WindowSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2b4-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2b4-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc2b4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc2b4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc2b4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc2b4-118">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="bc2b4-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2b4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc2b4-119">See also</span></span>
- [<span data-ttu-id="bc2b4-120">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="bc2b4-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
