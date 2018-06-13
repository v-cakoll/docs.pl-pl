---
title: ICorDebugChainEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4f27b958aa4b25c2662d8a5e9da6bcdc73d5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404459"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="29dfa-102">ICorDebugChainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="29dfa-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="29dfa-103">Pobiera określoną liczbę wystąpień ICorDebugChain z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="29dfa-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29dfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29dfa-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29dfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29dfa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="29dfa-106">[in] Liczba `ICorDebugChain` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="29dfa-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="29dfa-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugChain` obiekt, który reprezentuje łańcucha.</span><span class="sxs-lookup"><span data-stu-id="29dfa-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="29dfa-108">[out] Wskaźnik do liczby `ICorDebugChain` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="29dfa-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="29dfa-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="29dfa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29dfa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29dfa-110">Requirements</span></span>  
 <span data-ttu-id="29dfa-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dfa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dfa-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29dfa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29dfa-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29dfa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29dfa-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dfa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
