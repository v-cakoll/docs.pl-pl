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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994828"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="a56ba-102">ICorDebugModule2::ResolveAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="a56ba-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="a56ba-103">Usuwa zestaw odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="a56ba-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="a56ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a56ba-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="a56ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a56ba-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="a56ba-106">[in] `mdToken` Wartość, która odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a56ba-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="a56ba-107">[out] Wskaźnik na adres obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="a56ba-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="a56ba-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a56ba-108">Remarks</span></span>

<span data-ttu-id="a56ba-109">Jeśli zestaw nie jest już załadowany gdy `ResolveAssembly` nosi nazwę, wartość HRESULT zostanie zwrócona wartość CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="a56ba-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="a56ba-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a56ba-110">Requirements</span></span>

<span data-ttu-id="a56ba-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a56ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="a56ba-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a56ba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a56ba-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a56ba-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a56ba-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
