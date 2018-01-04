---
title: "ICorDebugChainEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e78340d26e4a7ab67fa6c312b1dbd537c5c0a28c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="28797-102">ICorDebugChainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="28797-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="28797-103">Pobiera określoną liczbę wystąpień ICorDebugChain z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="28797-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28797-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28797-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28797-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28797-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="28797-106">[in] Liczba `ICorDebugChain` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="28797-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="28797-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugChain` obiekt, który reprezentuje łańcucha.</span><span class="sxs-lookup"><span data-stu-id="28797-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="28797-108">[out] Wskaźnik do liczby `ICorDebugChain` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="28797-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="28797-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="28797-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28797-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28797-110">Requirements</span></span>  
 <span data-ttu-id="28797-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28797-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28797-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28797-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28797-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28797-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28797-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28797-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
