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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67959b2ebbfb62b47a1b2a770e278d043fc66d21
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754916"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="1ade4-102">ICorDebugFunction2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ade4-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="1ade4-103">Funkcja reprezentowany przez ten icordebugfunction2 — tylko mój kod oznacza przechodzenie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="1ade4-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ade4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ade4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ade4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ade4-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="1ade4-106">[in] Ustaw `true` aby oznaczyć tę funkcję, co kod użytkownika; w przeciwnym wypadku ustaw `false`.</span><span class="sxs-lookup"><span data-stu-id="1ade4-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="1ade4-107">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="1ade4-107">Return Values</span></span>  
  
|<span data-ttu-id="1ade4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ade4-108">HRESULT</span></span>|<span data-ttu-id="1ade4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1ade4-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1ade4-110">Funkcja został pomyślnie oznaczony.</span><span class="sxs-lookup"><span data-stu-id="1ade4-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="1ade4-111">Funkcja nie można oznaczyć jako kod użytkownika, ponieważ nie można debugować.</span><span class="sxs-lookup"><span data-stu-id="1ade4-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ade4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ade4-112">Remarks</span></span>  
 <span data-ttu-id="1ade4-113">Stepper tylko mój kod pozwoli na pominięcie kodu innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1ade4-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="1ade4-114">Kod użytkownika musi być podzestawem kod do debugowania.</span><span class="sxs-lookup"><span data-stu-id="1ade4-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ade4-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ade4-115">Requirements</span></span>  
 <span data-ttu-id="1ade4-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ade4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ade4-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ade4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ade4-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ade4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ade4-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ade4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
