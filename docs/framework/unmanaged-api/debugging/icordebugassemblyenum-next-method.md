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
ms.openlocfilehash: 25861b2635605042acc1bf81f3f7a4739e678522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645451"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="9dc8e-102">ICorDebugAssemblyEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="9dc8e-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="9dc8e-103">Pobiera określoną liczbę zestawów z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="9dc8e-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9dc8e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dc8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dc8e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9dc8e-106">[in] Liczba zestawów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="9dc8e-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9dc8e-107">[out] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="9dc8e-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9dc8e-108">[out] Wskaźnik do liczby zestawów rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="9dc8e-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="9dc8e-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="9dc8e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc8e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9dc8e-110">Requirements</span></span>  
 <span data-ttu-id="9dc8e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc8e-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dc8e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dc8e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dc8e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dc8e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc8e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
