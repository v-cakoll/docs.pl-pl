---
title: ICorDebugModule2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764104"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="37caa-102">ICorDebugModule2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="37caa-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="37caa-103">Ustawia stan tylko mój kod (JMC) wszystkich metod wszystkie klasy w tym icordebugmodule2 — do określonej wartości, z wyjątkiem tych `pTokens` tablicy, która ustawia przeciwną wartość.</span><span class="sxs-lookup"><span data-stu-id="37caa-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37caa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37caa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37caa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37caa-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="37caa-106">[in] Ustaw `true` Jeśli kod ma być debugowany; w przeciwnym razie, wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="37caa-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="37caa-107">[in] Rozmiar `pTokens` tablicy.</span><span class="sxs-lookup"><span data-stu-id="37caa-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="37caa-108">[in] Tablica `mdToken` wartości, z których każdy odwołuje się do metody, która będzie miał stan JMC równa!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="37caa-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37caa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37caa-109">Remarks</span></span>  
 <span data-ttu-id="37caa-110">Stan JMC każdej metody, która została określona w `pTokens` tablicy jest równa przeciwieństwo `bIsJustMycode` wartość.</span><span class="sxs-lookup"><span data-stu-id="37caa-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="37caa-111">Stan wszystkich innych metod, w tym module jest ustawiony na `bIsJustMycode` wartość.</span><span class="sxs-lookup"><span data-stu-id="37caa-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="37caa-112">`SetJMCStatus` Metoda usuwa wszystkie poprzednie ustawienia JMC, w tym module.</span><span class="sxs-lookup"><span data-stu-id="37caa-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="37caa-113">`SetJMCStatus` Metoda zwraca wartość HRESULT S_OK, jeśli wszystkie funkcje zostały pomyślnie ustawiono.</span><span class="sxs-lookup"><span data-stu-id="37caa-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="37caa-114">Zwraca HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE, jeśli niektóre funkcje, które są oznaczone `true` nie są debugowania.</span><span class="sxs-lookup"><span data-stu-id="37caa-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37caa-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37caa-115">Requirements</span></span>  
 <span data-ttu-id="37caa-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37caa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37caa-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37caa-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37caa-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37caa-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37caa-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37caa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
