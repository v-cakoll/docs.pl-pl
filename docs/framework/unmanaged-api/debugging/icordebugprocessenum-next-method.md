---
title: ICorDebugProcessEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c298107983f4835569cfee7503537537ad11a165
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493586"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="b1a79-102">ICorDebugProcessEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1a79-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="b1a79-103">Pobiera określoną liczbę wystąpień ICorDebugProcess z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="b1a79-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1a79-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1a79-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b1a79-106">[in] Liczba `ICorDebugProcess` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b1a79-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="b1a79-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugProcess` obiekt, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="b1a79-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b1a79-108">[out] Wskaźnik do liczby `ICorDebugProcess` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="b1a79-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="b1a79-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="b1a79-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a79-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1a79-110">Requirements</span></span>  
 <span data-ttu-id="b1a79-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a79-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a79-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1a79-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1a79-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1a79-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1a79-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a79-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
