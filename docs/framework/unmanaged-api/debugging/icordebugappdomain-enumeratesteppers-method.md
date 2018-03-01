---
title: "ICorDebugAppDomain::EnumerateSteppers — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b410eabee546307488449e577d9e102ac6a210b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="b1be1-102">ICorDebugAppDomain::EnumerateSteppers — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1be1-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="b1be1-103">Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1be1-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1be1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1be1-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1be1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1be1-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="b1be1-106">[out] Wskaźnik do adresu ICorDebugStepperEnum obiektu, który moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1be1-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1be1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1be1-107">Requirements</span></span>  
 <span data-ttu-id="b1be1-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1be1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1be1-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1be1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1be1-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1be1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1be1-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1be1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
