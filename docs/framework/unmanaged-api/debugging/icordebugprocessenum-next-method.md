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
ms.openlocfilehash: 6cd5dbc27376f8cd391f9ecc006c04d9a3a1eea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419747"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="e3cbe-102">ICorDebugProcessEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3cbe-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="e3cbe-103">Pobiera określoną liczbę wystąpień ICorDebugProcess z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="e3cbe-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3cbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3cbe-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3cbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3cbe-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e3cbe-106">[in] Liczba `ICorDebugProcess` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e3cbe-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processess`  
 <span data-ttu-id="e3cbe-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugProcess` obiekt, który reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="e3cbe-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e3cbe-108">[out] Wskaźnik do liczby `ICorDebugProcess` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="e3cbe-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="e3cbe-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="e3cbe-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3cbe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3cbe-110">Requirements</span></span>  
 <span data-ttu-id="e3cbe-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3cbe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3cbe-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3cbe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3cbe-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3cbe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3cbe-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3cbe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
