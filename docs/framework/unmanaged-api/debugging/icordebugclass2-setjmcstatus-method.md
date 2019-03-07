---
title: ICorDebugClass2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471388"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="4aeab-102">ICorDebugClass2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="4aeab-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="4aeab-103">Ustawia wartość wskazującą, czy metoda jest zdefiniowany przez użytkownika kod dla każdej metody klasy.</span><span class="sxs-lookup"><span data-stu-id="4aeab-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aeab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4aeab-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aeab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4aeab-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="4aeab-106">[in] Ustaw `true` do wskazania, że metoda jest zdefiniowana przez użytkownika kod; w przeciwnym wypadku ustaw `false`.</span><span class="sxs-lookup"><span data-stu-id="4aeab-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4aeab-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4aeab-107">Remarks</span></span>  
 <span data-ttu-id="4aeab-108">Stepper (JMC) just my kodu pominie kod zdefiniowane użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4aeab-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="4aeab-109">Zdefiniowane przez użytkownika kod musi być podzestawem kod do debugowania.</span><span class="sxs-lookup"><span data-stu-id="4aeab-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="4aeab-110">`SetJMCStatus` Zwraca wartość HRESULT S_FALSE, jeśli nie można ustawić wartości dla dowolnej metody nawet, jeśli pomyślnie ustawia wartość dla wszystkich innych metod.</span><span class="sxs-lookup"><span data-stu-id="4aeab-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aeab-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4aeab-111">Requirements</span></span>  
 <span data-ttu-id="4aeab-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4aeab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aeab-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4aeab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4aeab-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aeab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4aeab-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aeab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
