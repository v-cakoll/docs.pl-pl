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
ms.openlocfilehash: ed37e6eae3ec4f6e69215be6a42afe7fe86ff393
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768657"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="0aabc-102">ICorDebugReferenceValue::IsNull — Metoda</span><span class="sxs-lookup"><span data-stu-id="0aabc-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="0aabc-103">Pobiera wartość wskazującą, czy ten ICorDebugReferenceValue jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="0aabc-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aabc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0aabc-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aabc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0aabc-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="0aabc-106">[out] Wskaźnik na wartość logiczną, która jest `true` Jeśli `ICorDebugReferenceValue` obiekt jest wartość null; w przeciwnym razie `pbNull` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0aabc-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aabc-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0aabc-107">Requirements</span></span>  
 <span data-ttu-id="0aabc-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aabc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aabc-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0aabc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aabc-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0aabc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aabc-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aabc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
