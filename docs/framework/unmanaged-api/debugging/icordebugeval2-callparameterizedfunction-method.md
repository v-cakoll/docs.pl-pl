---
title: ICorDebugEval2::CallParameterizedFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487732"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="f14a9-102">ICorDebugEval2::CallParameterizedFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="f14a9-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="f14a9-103">Konfiguruje wywołanie do określonego ICorDebugFunction, które mogą być zagnieżdżone wewnątrz klasy, której Konstruktor przyjmuje <xref:System.Type> parametrów lub mogą się zająć <xref:System.Type> parametrów.</span><span class="sxs-lookup"><span data-stu-id="f14a9-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f14a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f14a9-104">Syntax</span></span>  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f14a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f14a9-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="f14a9-106">[in] Wskaźnik do `ICorDebugFunction` obiekt, który reprezentuje funkcja do wywołania.</span><span class="sxs-lookup"><span data-stu-id="f14a9-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f14a9-107">[in] Liczba argumentów, które funkcja przyjmuje.</span><span class="sxs-lookup"><span data-stu-id="f14a9-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f14a9-108">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f14a9-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="f14a9-109">[in] Liczba wartości przekazywane w funkcji.</span><span class="sxs-lookup"><span data-stu-id="f14a9-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="f14a9-110">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugValue, która reprezentuje wartość przekazanego argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f14a9-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f14a9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f14a9-111">Remarks</span></span>  
 <span data-ttu-id="f14a9-112">`CallParameterizedFunction` przypomina [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) z tą różnicą, że funkcja może być wewnątrz klasy z parametrami typu, może się zająć parametrów typu i / lub.</span><span class="sxs-lookup"><span data-stu-id="f14a9-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="f14a9-113">Argumenty typu powinien być podawany najpierw dla klasy, a następnie dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f14a9-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="f14a9-114">Jeśli funkcja znajduje się w domenie innej aplikacji, nastąpi przejście.</span><span class="sxs-lookup"><span data-stu-id="f14a9-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="f14a9-115">Jednak wszystkie argumenty typu i wartości musi należeć do domeny aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="f14a9-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="f14a9-116">Obliczanie funkcji mogą być wykonywane tylko w ograniczonej liczbie scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f14a9-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="f14a9-117">Jeśli `CallParameterizedFunction` lub `ICorDebugEval::CallFunction` zakończy się niepowodzeniem, zwrócona wartość HRESULT będą wskazywać najbardziej ogólną możliwe przyczyny błędu.</span><span class="sxs-lookup"><span data-stu-id="f14a9-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f14a9-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f14a9-118">Requirements</span></span>  
 <span data-ttu-id="f14a9-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f14a9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f14a9-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f14a9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f14a9-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f14a9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f14a9-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f14a9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
