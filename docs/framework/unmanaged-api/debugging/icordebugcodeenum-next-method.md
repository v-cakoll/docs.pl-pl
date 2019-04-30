---
title: ICorDebugCodeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db87cd4ad965654b63a68828cd088b8d2f7d07c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749790"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="e3102-102">ICorDebugCodeEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3102-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="e3102-103">Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="e3102-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3102-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3102-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3102-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3102-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e3102-106">[in] Liczba `ICorDebugCode` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e3102-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="e3102-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugCode` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3102-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e3102-108">[out] Wskaźnik do liczby `ICorDebugCode` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="e3102-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="e3102-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="e3102-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3102-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3102-110">Requirements</span></span>  
 <span data-ttu-id="e3102-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3102-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3102-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3102-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3102-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3102-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3102-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3102-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3102-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3102-115">See also</span></span>
