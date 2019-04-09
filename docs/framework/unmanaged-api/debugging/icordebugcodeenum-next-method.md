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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113051"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="0b776-102">ICorDebugCodeEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b776-102">ICorDebugCodeEnum::Next Method</span></span>
<span data-ttu-id="0b776-103">Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="0b776-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b776-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b776-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugCode *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b776-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b776-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0b776-106">[in] Liczba `ICorDebugCode` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="0b776-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0b776-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugCode` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b776-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0b776-108">[out] Wskaźnik do liczby `ICorDebugCode` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="0b776-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="0b776-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="0b776-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b776-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b776-110">Requirements</span></span>  
 <span data-ttu-id="0b776-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b776-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b776-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b776-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b776-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b776-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0b776-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0b776-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b776-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b776-115">See also</span></span>
