---
title: "ICorDebugFunction2::SetJMCStatus — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 315e036481f0454bf68b2da9e496c441ee843ba2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="6c45c-102">ICorDebugFunction2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c45c-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="6c45c-103">Funkcja reprezentowany przez ten ICorDebugFunction2 dla tylko mój kod oznacza wykonywanie krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="6c45c-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c45c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c45c-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c45c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c45c-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="6c45c-106">[in] Ustaw `true` do oznaczenia funkcji jako kodu użytkownika; w przeciwnym razie wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="6c45c-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="6c45c-107">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="6c45c-107">Return Values</span></span>  
  
|<span data-ttu-id="6c45c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c45c-108">HRESULT</span></span>|<span data-ttu-id="6c45c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6c45c-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6c45c-110">Funkcja została pomyślnie oznaczona.</span><span class="sxs-lookup"><span data-stu-id="6c45c-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="6c45c-111">Funkcja nie można oznaczyć jako kodu użytkownika, ponieważ nie można debugować.</span><span class="sxs-lookup"><span data-stu-id="6c45c-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c45c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c45c-112">Remarks</span></span>  
 <span data-ttu-id="6c45c-113">Stepper tylko mój kod pozwoli na pominięcie kodu innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="6c45c-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="6c45c-114">Kod użytkownika muszą być podzbiorem możliwością debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="6c45c-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c45c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c45c-115">Requirements</span></span>  
 <span data-ttu-id="6c45c-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c45c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c45c-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c45c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c45c-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c45c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c45c-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c45c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
