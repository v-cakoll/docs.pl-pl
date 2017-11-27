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
ms.openlocfilehash: c8705e31e99effd8741029f9709f3982e097a693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="09f7b-102">ICorDebugArrayValue::GetBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="09f7b-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="09f7b-103">Pobiera podstawowy indeks każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="09f7b-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09f7b-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09f7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09f7b-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="09f7b-106">[in] Liczba wymiarów tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="09f7b-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="09f7b-107">Ta wartość jest również rozmiar `indicies` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="09f7b-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="09f7b-108">[out] Tablica liczb całkowitych, z których każdy jest indeksem podstawowej (to znaczy indeks początkowy) wymiaru tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="09f7b-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f7b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09f7b-109">Requirements</span></span>  
 <span data-ttu-id="09f7b-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09f7b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f7b-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09f7b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09f7b-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09f7b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09f7b-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09f7b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
