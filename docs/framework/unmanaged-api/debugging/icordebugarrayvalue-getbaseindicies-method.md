---
title: "ICorDebugArrayValue::GetBaseIndicies — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 820d81b4538c3cf2bf6fa123df2012ea06e2d978
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="613d0-102">ICorDebugArrayValue::GetBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="613d0-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="613d0-103">Pobiera podstawowy indeks każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="613d0-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="613d0-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="613d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="613d0-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="613d0-106">[in] Liczba wymiarów tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="613d0-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="613d0-107">Ta wartość jest również rozmiar `indicies` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="613d0-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="613d0-108">[out] Tablica liczb całkowitych, z których każdy jest indeksem podstawowej (to znaczy indeks początkowy) wymiaru tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="613d0-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="613d0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="613d0-109">Requirements</span></span>  
 <span data-ttu-id="613d0-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="613d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="613d0-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="613d0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="613d0-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="613d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="613d0-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="613d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
