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
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934774"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="fc2b5-102">ICorDebugEval::CallFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc2b5-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="fc2b5-103">Konfiguruje wywołanie do określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="fc2b5-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fc2b5-105">Użyj [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc2b5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc2b5-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="fc2b5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc2b5-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="fc2b5-108">[in] Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="fc2b5-109">[in] Liczba argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="fc2b5-110">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, który określa argument, który zostanie przekazany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc2b5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc2b5-111">Remarks</span></span>

<span data-ttu-id="fc2b5-112">Jeśli funkcja znajduje się wirtualny, `CallFunction` wykona wirtualnego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="fc2b5-113">Jeśli funkcja znajduje się w domenie innej aplikacji, przejście wystąpi tak długo, jak wszystkie argumenty mają również w tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc2b5-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc2b5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc2b5-114">Requirements</span></span>

<span data-ttu-id="fc2b5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="fc2b5-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc2b5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fc2b5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc2b5-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fc2b5-118">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="fc2b5-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="fc2b5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc2b5-119">See also</span></span>

- [<span data-ttu-id="fc2b5-120">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="fc2b5-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)