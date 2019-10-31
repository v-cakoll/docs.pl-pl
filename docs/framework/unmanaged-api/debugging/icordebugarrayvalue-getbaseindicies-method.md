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
ms.openlocfilehash: e103401b85626e53db53e1894c22b161774e5163
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088688"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="e813c-102">ICorDebugArrayValue::GetBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="e813c-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="e813c-103">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e813c-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e813c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e813c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e813c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e813c-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e813c-106">podczas Liczba wymiarów tego obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="e813c-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="e813c-107">Ta wartość jest również rozmiarem tablicy `indicies`, ponieważ jej rozmiar jest równy liczbie wymiarów obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="e813c-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="e813c-108">określoną Tablica liczb całkowitych, z których każdy jest indeksem podstawowym (czyli indeksem początkowym) wymiaru tego obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="e813c-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e813c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e813c-109">Requirements</span></span>  
 <span data-ttu-id="e813c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e813c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e813c-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e813c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e813c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e813c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e813c-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e813c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
