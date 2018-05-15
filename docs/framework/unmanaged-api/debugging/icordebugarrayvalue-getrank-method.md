---
title: ICorDebugArrayValue::GetRank — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac5bc1d205184771388b13e9b5380ff42bfba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="8adc9-102">ICorDebugArrayValue::GetRank — Metoda</span><span class="sxs-lookup"><span data-stu-id="8adc9-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="8adc9-103">Pobiera liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="8adc9-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8adc9-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8adc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8adc9-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="8adc9-106">[out] Wskaźnik do liczby wymiarów w tym `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8adc9-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8adc9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8adc9-107">Requirements</span></span>  
 <span data-ttu-id="8adc9-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adc9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adc9-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8adc9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8adc9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8adc9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8adc9-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adc9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
