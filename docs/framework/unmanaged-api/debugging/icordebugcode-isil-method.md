---
title: ICorDebugCode::IsIL — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a81f4a53954c559ab12e27bcf039b7b1a1804cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700796"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="c461b-102">ICorDebugCode::IsIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="c461b-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="c461b-103">Pobiera wartość wskazującą, czy ten "ICorDebugCode" reprezentuje kod, który został skompilowany w języku pośrednim firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="c461b-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="c461b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c461b-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="c461b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c461b-105">Parameters</span></span>
 `pbIL`  
 <span data-ttu-id="c461b-106">[out] `true`, jeśli ten `ICorDebugCode` reprezentuje kod, który został skompilowany w języku MSIL; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c461b-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c461b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c461b-107">Requirements</span></span>

 <span data-ttu-id="c461b-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c461b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  

 <span data-ttu-id="c461b-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c461b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  

 <span data-ttu-id="c461b-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c461b-110">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="c461b-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c461b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
 
