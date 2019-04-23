---
title: ICorDebugTypeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d47f14ff2adb37fca16cf6774a2b80cb2e074b17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157316"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="3368b-102">ICorDebugTypeEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="3368b-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="3368b-103">Pobiera liczbę wystąpień "ICorDebugType" określonego przez `celt` z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="3368b-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3368b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3368b-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3368b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3368b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3368b-106">[in] Liczba `ICorDebugType` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="3368b-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3368b-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugType` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3368b-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3368b-108">[out] Wskaźnik do liczby `ICorDebugType` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="3368b-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="3368b-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="3368b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3368b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3368b-110">Requirements</span></span>  
 <span data-ttu-id="3368b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3368b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3368b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3368b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3368b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3368b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3368b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3368b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3368b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3368b-115">See also</span></span>
