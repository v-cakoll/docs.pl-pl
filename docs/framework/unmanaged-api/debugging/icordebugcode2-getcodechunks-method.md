---
title: ICorDebugCode2::GetCodeChunks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700726"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="c2662-102">ICorDebugCode2::GetCodeChunks — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2662-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="c2662-103">Pobiera fragmenty kodu, z których składa się ten obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="c2662-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2662-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2662-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="c2662-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2662-105">Parameters</span></span>

 `cbufSize`  
 <span data-ttu-id="c2662-106">podczas Rozmiar tablicy `chunks`.</span><span class="sxs-lookup"><span data-stu-id="c2662-106">[in] Size of the `chunks` array.</span></span>

 `pcnumChunks`  
 <span data-ttu-id="c2662-107">określoną Liczba fragmentów zwróconych w tablicy `chunks`.</span><span class="sxs-lookup"><span data-stu-id="c2662-107">[out] The number of chunks returned in the `chunks` array.</span></span>

 `chunks`  
 <span data-ttu-id="c2662-108">określoną Tablica struktur "CodeChunkInfo —", z których każdy reprezentuje pojedynczy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="c2662-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="c2662-109">Jeśli wartość `cbufSize` to 0, ten parametr może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="c2662-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2662-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2662-110">Remarks</span></span>

 <span data-ttu-id="c2662-111">Fragmenty kodu nie nakładają się na siebie i będą podążać za kolejnością, w jakiej zostałyby połączone przez [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2662-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="c2662-112">Obiekt kodu języka pośredniego (MSIL) firmy Microsoft w .NET Framework w wersji 2,0 będzie obejmował pojedynczy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="c2662-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2662-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2662-113">Requirements</span></span>

 <span data-ttu-id="c2662-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2662-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c2662-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2662-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="c2662-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2662-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="c2662-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2662-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
