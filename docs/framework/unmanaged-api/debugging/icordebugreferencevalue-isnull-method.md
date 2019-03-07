---
title: ICorDebugReferenceValue::IsNull — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972df4613255dc1b71801e02d387a735dfc632c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477260"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="dfa87-102">ICorDebugReferenceValue::IsNull — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfa87-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="dfa87-103">Pobiera wartość wskazującą, czy ten ICorDebugReferenceValue jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="dfa87-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfa87-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa87-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="dfa87-106">[out] Wskaźnik na wartość logiczną, która jest `true` Jeśli `ICorDebugReferenceValue` obiekt jest wartość null; w przeciwnym razie `pbNull` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="dfa87-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa87-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfa87-107">Requirements</span></span>  
 <span data-ttu-id="dfa87-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa87-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa87-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfa87-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa87-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa87-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa87-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa87-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
