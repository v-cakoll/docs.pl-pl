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
ms.openlocfilehash: 2d075820df534e08bdf4c2b75d36f6a60f979662
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894093"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="e4f93-102">ICorDebugChainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4f93-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="e4f93-103">Pobiera określoną liczbę wystąpień ICorDebugChain z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="e4f93-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4f93-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4f93-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e4f93-106">podczas Liczba `ICorDebugChain` wystąpień do pobrania.</span><span class="sxs-lookup"><span data-stu-id="e4f93-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="e4f93-107">określoną Tablica wskaźników, z których każdy wskazuje `ICorDebugChain` obiekt, który reprezentuje łańcuch.</span><span class="sxs-lookup"><span data-stu-id="e4f93-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e4f93-108">określoną Wskaźnik do liczby faktycznie zwróconych `ICorDebugChain` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e4f93-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="e4f93-109">Ta wartość może być równa `celt` null, jeśli jest taka.</span><span class="sxs-lookup"><span data-stu-id="e4f93-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f93-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4f93-110">Requirements</span></span>  
 <span data-ttu-id="e4f93-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f93-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f93-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4f93-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4f93-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e4f93-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f93-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
