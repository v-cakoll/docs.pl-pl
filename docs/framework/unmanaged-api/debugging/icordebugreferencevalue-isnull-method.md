---
title: "ICorDebugReferenceValue::IsNull — Metoda"
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
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53eaa411dc405142461de99bc787eba7a5d52db6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="d8ae9-102">ICorDebugReferenceValue::IsNull — Metoda</span><span class="sxs-lookup"><span data-stu-id="d8ae9-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="d8ae9-103">Pobiera wartość wskazującą, czy to ICorDebugReferenceValue jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ae9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8ae9-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ae9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8ae9-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="d8ae9-106">[out] Wskaźnik do wartość logiczna, która jest `true` Jeśli `ICorDebugReferenceValue` obiekt jest wartość null; w przeciwnym razie `pbNull` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ae9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8ae9-107">Requirements</span></span>  
 <span data-ttu-id="d8ae9-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ae9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ae9-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ae9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ae9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ae9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ae9-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ae9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
