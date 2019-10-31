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
ms.openlocfilehash: 3c11a0547ad5acc5613324d7e9d7439d44549dbc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125811"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="730a4-102">ICorDebugChainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="730a4-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="730a4-103">Pobiera określoną liczbę wystąpień ICorDebugChain z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="730a4-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="730a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="730a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="730a4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="730a4-106">podczas Liczba wystąpień `ICorDebugChain` do pobrania.</span><span class="sxs-lookup"><span data-stu-id="730a4-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="730a4-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugChain`, który reprezentuje łańcuch.</span><span class="sxs-lookup"><span data-stu-id="730a4-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="730a4-108">określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugChain`.</span><span class="sxs-lookup"><span data-stu-id="730a4-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="730a4-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="730a4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="730a4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="730a4-110">Requirements</span></span>  
 <span data-ttu-id="730a4-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="730a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="730a4-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="730a4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="730a4-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="730a4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="730a4-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="730a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
