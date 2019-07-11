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
ms.openlocfilehash: 00adc852a0940766cdd4188ffa5d6be2b472e51f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744880"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="085f2-102">ICorDebugAssemblyEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="085f2-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="085f2-103">Pobiera określoną liczbę zestawów z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="085f2-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="085f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="085f2-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="085f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="085f2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="085f2-106">[in] Liczba zestawów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="085f2-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="085f2-107">[out] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="085f2-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="085f2-108">[out] Wskaźnik do liczby zestawów rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="085f2-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="085f2-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="085f2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="085f2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="085f2-110">Requirements</span></span>  
 <span data-ttu-id="085f2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="085f2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="085f2-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="085f2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="085f2-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="085f2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="085f2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="085f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
