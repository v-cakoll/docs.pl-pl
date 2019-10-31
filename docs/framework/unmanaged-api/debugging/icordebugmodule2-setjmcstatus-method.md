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
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129468"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="14b8a-102">ICorDebugModule2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="14b8a-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="14b8a-103">Ustawia stan Tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym ICorDebugModule2 do określonej wartości, z wyjątkiem tych w tablicy `pTokens`, które są ustawiane na wartość odwrotną.</span><span class="sxs-lookup"><span data-stu-id="14b8a-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14b8a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14b8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14b8a-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="14b8a-106">podczas Ustaw, aby `true`, jeśli kod ma być debugowany; w przeciwnym razie ustaw wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="14b8a-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="14b8a-107">podczas Rozmiar tablicy `pTokens`.</span><span class="sxs-lookup"><span data-stu-id="14b8a-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="14b8a-108">podczas Tablica wartości `mdToken`, z których każdy odwołuje się do metody, która ma ustawiony stan JMC!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="14b8a-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14b8a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14b8a-109">Remarks</span></span>  
 <span data-ttu-id="14b8a-110">Stan JMC każdej metody, która jest określona w tablicy `pTokens` jest ustawiony na odwrotność wartości `bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="14b8a-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="14b8a-111">Stan wszystkich innych metod w tym module jest ustawiony na wartość `bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="14b8a-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="14b8a-112">Metoda `SetJMCStatus` kasuje wszystkie poprzednie ustawienia JMC w tym module.</span><span class="sxs-lookup"><span data-stu-id="14b8a-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="14b8a-113">Metoda `SetJMCStatus` zwraca wartość HRESULT S_OK, jeśli wszystkie funkcje zostały ustawione pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="14b8a-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="14b8a-114">Zwraca CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, jeśli niektóre funkcje oznaczone `true` nie są możliwością debugowania.</span><span class="sxs-lookup"><span data-stu-id="14b8a-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14b8a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14b8a-115">Requirements</span></span>  
 <span data-ttu-id="14b8a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14b8a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14b8a-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="14b8a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14b8a-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="14b8a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14b8a-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14b8a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
