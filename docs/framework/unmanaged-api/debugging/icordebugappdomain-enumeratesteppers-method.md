---
title: "ICorDebugAppDomain::EnumerateSteppers — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.EnumerateSteppers
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5e58059bbd3e9bf8d3db80d36e84e1f4496eb0bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="e8552-102">ICorDebugAppDomain::EnumerateSteppers — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8552-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="e8552-103">Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8552-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8552-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8552-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="e8552-106">[out] Wskaźnik do adresu ICorDebugStepperEnum obiektu, który moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e8552-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8552-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8552-107">Requirements</span></span>  
 <span data-ttu-id="e8552-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8552-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8552-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8552-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8552-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8552-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8552-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8552-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
