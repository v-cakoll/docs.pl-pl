---
title: ICorDebugAppDomain::EnumerateSteppers — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: a46d1b4ebf84514a77e62a4108f6aa34cd2dd94e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895263"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="e5bad-102">ICorDebugAppDomain::EnumerateSteppers — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5bad-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="e5bad-103">Pobiera moduł wyliczający dla wszystkich aktywnych współdziałań w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5bad-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5bad-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5bad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5bad-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="e5bad-106">określoną Wskaźnik do adresu obiektu ICorDebugStepperEnum, który jest modułem wyliczającym dla wszystkich aktywnych współdziałań w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5bad-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5bad-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5bad-107">Requirements</span></span>  
 <span data-ttu-id="e5bad-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5bad-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5bad-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5bad-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5bad-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5bad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5bad-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5bad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
