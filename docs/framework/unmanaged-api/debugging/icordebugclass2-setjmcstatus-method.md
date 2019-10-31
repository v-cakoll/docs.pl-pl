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
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125692"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="80fbb-102">ICorDebugClass2::SetJMCStatus — Metoda</span><span class="sxs-lookup"><span data-stu-id="80fbb-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="80fbb-103">Dla każdej metody klasy ustawia wartość wskazującą, czy metoda jest kodem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80fbb-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80fbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80fbb-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="80fbb-106">podczas Ustaw na `true`, aby wskazać, że metoda jest kodem zdefiniowanym przez użytkownika; w przeciwnym razie ustaw wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="80fbb-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80fbb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80fbb-107">Remarks</span></span>  
 <span data-ttu-id="80fbb-108">JMC (Just-My-Code) stepper pominie kod niezdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="80fbb-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="80fbb-109">Kod zdefiniowany przez użytkownika musi być podzbiorem kodu możliwością debugowania.</span><span class="sxs-lookup"><span data-stu-id="80fbb-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="80fbb-110">`SetJMCStatus` zwraca wartość HRESULT elementu S_FALSE, jeśli nie można ustawić wartości dla żadnej metody, nawet jeśli pomyślnie ustawi ona wartość dla wszystkich innych metod.</span><span class="sxs-lookup"><span data-stu-id="80fbb-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80fbb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80fbb-111">Requirements</span></span>  
 <span data-ttu-id="80fbb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80fbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80fbb-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80fbb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80fbb-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="80fbb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80fbb-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80fbb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
