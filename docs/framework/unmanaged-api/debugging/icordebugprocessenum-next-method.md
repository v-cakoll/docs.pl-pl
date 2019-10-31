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
ms.openlocfilehash: 0666becb5a34688d3f4cf5bddd1e2fa71785b38a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139787"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="a3888-102">ICorDebugProcessEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3888-102">ICorDebugProcessEnum::Next Method</span></span>
<span data-ttu-id="a3888-103">Pobiera określoną liczbę wystąpień ICorDebugProcess z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="a3888-103">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3888-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3888-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3888-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3888-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a3888-106">podczas Liczba wystąpień `ICorDebugProcess` do pobrania.</span><span class="sxs-lookup"><span data-stu-id="a3888-106">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="a3888-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugProcess`, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="a3888-107">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a3888-108">określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="a3888-108">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="a3888-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="a3888-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3888-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3888-110">Requirements</span></span>  
 <span data-ttu-id="a3888-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3888-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3888-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3888-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3888-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3888-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3888-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3888-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
