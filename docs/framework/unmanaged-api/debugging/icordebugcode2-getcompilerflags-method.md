---
title: ICorDebugCode2::GetCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: 734a05d96aed309541708d4e6f80ed61cab85637
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893498"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="32747-102">ICorDebugCode2::GetCompilerFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="32747-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="32747-103">Pobiera flagi określające warunki, w których ten obiekt kodu był skompilowany lub generowany przy użyciu natywnego generatora obrazu (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="32747-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="32747-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32747-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="32747-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32747-105">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="32747-106">określoną Wskaźnik do wartości wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) , który określa zachowanie kompilatora JIT lub generatora obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="32747-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="32747-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32747-107">Requirements</span></span>

<span data-ttu-id="32747-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32747-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="32747-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32747-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="32747-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32747-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="32747-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32747-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
