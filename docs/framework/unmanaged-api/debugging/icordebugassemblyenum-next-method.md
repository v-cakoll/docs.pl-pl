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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b94ae83f2fb5f71abb8cb3a5c96aac9e268fc5db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="1717c-102">ICorDebugAssemblyEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1717c-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="1717c-103">Pobiera określoną liczbę zestawów z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="1717c-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1717c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1717c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1717c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1717c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1717c-106">[in] Liczba zestawów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1717c-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="1717c-107">[out] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugAssembly, który reprezentuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="1717c-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1717c-108">[out] Wskaźnik do liczby zestawów faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="1717c-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="1717c-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="1717c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1717c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1717c-110">Requirements</span></span>  
 <span data-ttu-id="1717c-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1717c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1717c-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1717c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1717c-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1717c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1717c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1717c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
