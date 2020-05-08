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
ms.openlocfilehash: 9fb2f960098e970b4d3d9f0be499f4d9fda6558e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893893"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="41073-102">ICorDebugClass2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="41073-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="41073-103">Dla każdej metody klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41073-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41073-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41073-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41073-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41073-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="41073-106">podczas Ustaw na `true` , aby wskazać, że metoda jest kodem zdefiniowanym przez użytkownika; w przeciwnym razie ustaw `false`wartość.</span><span class="sxs-lookup"><span data-stu-id="41073-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41073-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41073-107">Remarks</span></span>  
 <span data-ttu-id="41073-108">JMC (Just-My-Code) stepper pominie kod niezdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="41073-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="41073-109">Kod zdefiniowany przez użytkownika musi być podzbiorem kodu możliwością debugowania.</span><span class="sxs-lookup"><span data-stu-id="41073-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="41073-110">`SetJMCStatus`Zwraca wartość HRESULT S_FALSE, jeśli nie można ustawić wartości dla żadnej metody, nawet jeśli pomyślnie ustawi wartość dla wszystkich innych metod.</span><span class="sxs-lookup"><span data-stu-id="41073-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41073-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41073-111">Requirements</span></span>  
 <span data-ttu-id="41073-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41073-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41073-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41073-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41073-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41073-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41073-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41073-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
