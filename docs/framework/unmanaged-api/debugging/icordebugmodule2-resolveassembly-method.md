---
title: ICorDebugModule2::ResolveAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125305"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="289cd-102">ICorDebugModule2::ResolveAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="289cd-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="289cd-103">Rozwiązuje zestaw, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="289cd-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="289cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="289cd-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="289cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="289cd-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="289cd-106">podczas Wartość `mdToken`, która odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="289cd-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="289cd-107">określoną Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="289cd-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="289cd-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="289cd-108">Remarks</span></span>

<span data-ttu-id="289cd-109">Jeśli zestaw nie jest już załadowany po wywołaniu `ResolveAssembly`, zwracana jest wartość HRESULT elementu CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="289cd-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="289cd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="289cd-110">Requirements</span></span>

<span data-ttu-id="289cd-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="289cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="289cd-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="289cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="289cd-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="289cd-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="289cd-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
