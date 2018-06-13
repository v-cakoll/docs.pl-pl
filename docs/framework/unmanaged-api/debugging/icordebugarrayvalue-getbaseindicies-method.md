---
title: ICorDebugArrayValue::GetBaseIndicies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3fe9edf7a635e54aac881a242aca3bc32e21fe1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408128"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="57972-102">ICorDebugArrayValue::GetBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="57972-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="57972-103">Pobiera podstawowy indeks każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="57972-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57972-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57972-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57972-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57972-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="57972-106">[in] Liczba wymiarów tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="57972-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="57972-107">Ta wartość jest również rozmiar `indicies` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="57972-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="57972-108">[out] Tablica liczb całkowitych, z których każdy jest indeksem podstawowej (to znaczy indeks początkowy) wymiaru tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="57972-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57972-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57972-109">Requirements</span></span>  
 <span data-ttu-id="57972-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57972-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57972-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57972-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57972-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57972-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57972-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57972-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
