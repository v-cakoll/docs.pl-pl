---
title: ICorDebugFunction2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137795"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="b2215-102">ICorDebugFunction2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2215-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="b2215-103">Oznacza funkcję reprezentowaną przez ten ICorDebugFunction2 do Tylko mój kod wykonywania kroków.</span><span class="sxs-lookup"><span data-stu-id="b2215-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2215-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2215-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2215-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2215-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="b2215-106">podczas Ustaw, aby `true` oznaczyć funkcję jako kod użytkownika; w przeciwnym razie ustaw wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="b2215-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="b2215-107">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b2215-107">Return Values</span></span>  
  
|<span data-ttu-id="b2215-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2215-108">HRESULT</span></span>|<span data-ttu-id="b2215-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b2215-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2215-110">Funkcja została pomyślnie oznaczona.</span><span class="sxs-lookup"><span data-stu-id="b2215-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="b2215-111">Nie można oznaczyć funkcji jako kodu użytkownika, ponieważ nie można jej debugować.</span><span class="sxs-lookup"><span data-stu-id="b2215-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2215-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2215-112">Remarks</span></span>  
 <span data-ttu-id="b2215-113">Tylko mój kod stepper pominie kod niebędący użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="b2215-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="b2215-114">Kod użytkownika musi być podzbiorem kodu możliwością debugowania.</span><span class="sxs-lookup"><span data-stu-id="b2215-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2215-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2215-115">Requirements</span></span>  
 <span data-ttu-id="b2215-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2215-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2215-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2215-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2215-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2215-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2215-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2215-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
