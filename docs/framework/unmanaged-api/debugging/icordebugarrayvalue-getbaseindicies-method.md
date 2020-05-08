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
ms.openlocfilehash: 9aadbe7c6f18c6b15350267d1f9ecaa3a23cdd20
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895070"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="bba69-102">ICorDebugArrayValue::GetBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="bba69-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="bba69-103">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="bba69-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bba69-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bba69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bba69-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="bba69-106">podczas Liczba wymiarów tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bba69-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="bba69-107">Ta wartość jest również rozmiarem `indicies` tablicy, ponieważ jej rozmiar jest równy liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bba69-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="bba69-108">określoną Tablica liczb całkowitych, z których każdy jest indeksem podstawowym (czyli indeksem początkowym) wymiaru tego `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bba69-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba69-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bba69-109">Requirements</span></span>  
 <span data-ttu-id="bba69-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba69-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba69-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bba69-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bba69-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bba69-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bba69-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bba69-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
