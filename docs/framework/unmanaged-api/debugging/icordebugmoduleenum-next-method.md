---
title: ICorDebugModuleEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f71901acf8227d018bf288b6cd0265f053e6a3a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510835"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="72975-102">ICorDebugModuleEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="72975-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="72975-103">Pobiera liczbę wystąpień "ICorDebugModule" określonego przez `celt` z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="72975-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72975-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72975-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72975-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72975-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="72975-106">[in] Liczba `ICorDebugModule` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="72975-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="72975-107">[out] Tablica wskaźników, z których każdy wskazuje `ICorDebugModule` obiektu.</span><span class="sxs-lookup"><span data-stu-id="72975-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="72975-108">[out] Wskaźnik do liczby `ICorDebugModule` wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="72975-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="72975-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="72975-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72975-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72975-110">Requirements</span></span>  
 <span data-ttu-id="72975-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72975-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72975-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72975-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72975-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72975-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72975-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72975-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72975-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72975-115">See also</span></span>

