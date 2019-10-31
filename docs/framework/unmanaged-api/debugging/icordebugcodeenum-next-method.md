---
title: ICorDebugCodeEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125524"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="52e8f-102">ICorDebugCodeEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="52e8f-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="52e8f-103">Pobiera określoną liczbę wystąpień "ICorDebugCode" z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="52e8f-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="52e8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52e8f-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="52e8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52e8f-105">Parameters</span></span>

`celt`  
<span data-ttu-id="52e8f-106">podczas Liczba wystąpień `ICorDebugCode` do pobrania.</span><span class="sxs-lookup"><span data-stu-id="52e8f-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="52e8f-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="52e8f-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="52e8f-108">określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="52e8f-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="52e8f-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="52e8f-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="52e8f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52e8f-110">Requirements</span></span>

<span data-ttu-id="52e8f-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e8f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="52e8f-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52e8f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="52e8f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="52e8f-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="52e8f-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
