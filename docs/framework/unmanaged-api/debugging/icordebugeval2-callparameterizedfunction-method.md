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
ms.openlocfilehash: ab31ab8f83a71372c8e12b460458a26996f65ff5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782988"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="8d852-102">ICorDebugEval2::CallParameterizedFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d852-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="8d852-103">Konfiguruje wywołanie do określonego ICorDebugFunction, które może być zagnieżdżone wewnątrz klasy, której Konstruktor przyjmuje <xref:System.Type> parametry, lub sama może przyjmować <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="8d852-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d852-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d852-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d852-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d852-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="8d852-106">podczas Wskaźnik do obiektu `ICorDebugFunction`, który reprezentuje funkcję, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="8d852-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="8d852-107">podczas Liczba argumentów, które wykonuje funkcja.</span><span class="sxs-lookup"><span data-stu-id="8d852-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="8d852-108">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d852-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="8d852-109">podczas Liczba wartości przekazaną w funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d852-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="8d852-110">podczas Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugValue, który reprezentuje wartość przekazaną w argumencie funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d852-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d852-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d852-111">Remarks</span></span>  
 <span data-ttu-id="8d852-112">`CallParameterizedFunction` przypomina [ICorDebugEval:: CallFunction —](icordebugeval-callfunction-method.md) , z tą różnicą, że funkcja może znajdować się wewnątrz klasy z parametrami typu, może same przyjmować parametry typu lub oba te metody.</span><span class="sxs-lookup"><span data-stu-id="8d852-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="8d852-113">Argumenty typu powinny być określone jako pierwsze dla klasy, a następnie dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="8d852-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="8d852-114">Jeśli funkcja znajduje się w innej domenie aplikacji, nastąpi przejście.</span><span class="sxs-lookup"><span data-stu-id="8d852-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="8d852-115">Jednak wszystkie argumenty typu i wartości muszą znajdować się w domenie aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="8d852-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="8d852-116">Obliczanie funkcji można wykonać tylko w ograniczonych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="8d852-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="8d852-117">Jeśli `CallParameterizedFunction` lub `ICorDebugEval::CallFunction` nie powiedzie się, zwrócony wynik HRESULT będzie wskazywał największą możliwą przyczynę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="8d852-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d852-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d852-118">Requirements</span></span>  
 <span data-ttu-id="8d852-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d852-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d852-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8d852-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d852-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d852-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d852-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d852-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
