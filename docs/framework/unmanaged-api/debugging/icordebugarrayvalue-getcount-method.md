---
title: "ICorDebugArrayValue::GetCount — Metoda"
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
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a4dfdf6ad1fc50cbca039d50b32bc81b6b977ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="f99fb-102">ICorDebugArrayValue::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="f99fb-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="f99fb-103">Pobiera całkowitą liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f99fb-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f99fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f99fb-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f99fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f99fb-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="f99fb-106">[out] Wskaźnik do całkowita liczba elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f99fb-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f99fb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f99fb-107">Requirements</span></span>  
 <span data-ttu-id="f99fb-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f99fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f99fb-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f99fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f99fb-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f99fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f99fb-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f99fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
