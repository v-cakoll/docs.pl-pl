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
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976242"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="2e1e4-102">ICorDebugEval::CallFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e1e4-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="2e1e4-103">Konfiguruje wywołanie do określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="2e1e4-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2e1e4-105">Zamiast tego użyj [ICorDebugEval2:: CallParameterizedFunction —](icordebugeval2-callparameterizedfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e1e4-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e1e4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e1e4-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="2e1e4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e1e4-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="2e1e4-108">podczas Wskaźnik do obiektu ICorDebugFunction, który określa funkcję, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="2e1e4-109">podczas Liczba argumentów dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="2e1e4-110">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który określa argument, który ma zostać przesłany do funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e1e4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e1e4-111">Remarks</span></span>

<span data-ttu-id="2e1e4-112">Jeśli funkcja jest wirtualna, `CallFunction` przeprowadzi wirtualną wysyłkę.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="2e1e4-113">Jeśli funkcja znajduje się w innej domenie aplikacji, przejście zostanie przeprowadzone tak długo, jak wszystkie argumenty są również w tej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e1e4-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="2e1e4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e1e4-114">Requirements</span></span>

<span data-ttu-id="2e1e4-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1e4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2e1e4-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e1e4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="2e1e4-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e1e4-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2e1e4-118">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="2e1e4-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="2e1e4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e1e4-119">See also</span></span>

- [<span data-ttu-id="2e1e4-120">CallParameterizedFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="2e1e4-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
