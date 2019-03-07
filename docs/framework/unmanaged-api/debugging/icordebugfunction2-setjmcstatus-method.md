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
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501009"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="f1a15-102">ICorDebugFunction2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1a15-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="f1a15-103">Funkcja reprezentowany przez ten icordebugfunction2 — tylko mój kod oznacza przechodzenie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="f1a15-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1a15-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1a15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1a15-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="f1a15-106">[in] Ustaw `true` aby oznaczyć tę funkcję, co kod użytkownika; w przeciwnym wypadku ustaw `false`.</span><span class="sxs-lookup"><span data-stu-id="f1a15-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="f1a15-107">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f1a15-107">Return Values</span></span>  
  
|<span data-ttu-id="f1a15-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1a15-108">HRESULT</span></span>|<span data-ttu-id="f1a15-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a15-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1a15-110">Funkcja został pomyślnie oznaczony.</span><span class="sxs-lookup"><span data-stu-id="f1a15-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="f1a15-111">Funkcja nie można oznaczyć jako kod użytkownika, ponieważ nie można debugować.</span><span class="sxs-lookup"><span data-stu-id="f1a15-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1a15-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1a15-112">Remarks</span></span>  
 <span data-ttu-id="f1a15-113">Stepper tylko mój kod pozwoli na pominięcie kodu innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f1a15-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="f1a15-114">Kod użytkownika musi być podzestawem kod do debugowania.</span><span class="sxs-lookup"><span data-stu-id="f1a15-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a15-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1a15-115">Requirements</span></span>  
 <span data-ttu-id="f1a15-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a15-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1a15-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a15-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a15-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a15-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
