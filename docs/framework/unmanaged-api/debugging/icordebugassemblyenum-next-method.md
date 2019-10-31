---
title: ICorDebugAssemblyEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
ms.openlocfilehash: 86fa44b609b4b89cfaa28f0bfa7bbdce6217623f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122854"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="c456b-102">ICorDebugAssemblyEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="c456b-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="c456b-103">Pobiera określoną liczbę zestawów z kolekcji, rozpoczynając od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="c456b-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c456b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c456b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c456b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c456b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c456b-106">podczas Liczba zestawów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c456b-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c456b-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="c456b-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c456b-108">określoną Wskaźnik do liczby faktycznie zwróconych zestawów.</span><span class="sxs-lookup"><span data-stu-id="c456b-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="c456b-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="c456b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c456b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c456b-110">Requirements</span></span>  
 <span data-ttu-id="c456b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c456b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c456b-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c456b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c456b-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c456b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c456b-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c456b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
