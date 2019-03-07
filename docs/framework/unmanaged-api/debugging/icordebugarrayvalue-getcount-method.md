---
title: ICorDebugArrayValue::GetCount — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d00c04f3719d6fb340541d3301d4dc4a3f95ca40
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495627"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="3285f-102">ICorDebugArrayValue::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="3285f-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="3285f-103">Pobiera całkowitą liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3285f-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3285f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3285f-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3285f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3285f-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="3285f-106">[out] Wskaźnik do całkowitą liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3285f-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3285f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3285f-107">Requirements</span></span>  
 <span data-ttu-id="3285f-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3285f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3285f-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3285f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3285f-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3285f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3285f-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3285f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
