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
ms.openlocfilehash: 2c82c72350931bf3aed8ec6699cd0af834798e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417218"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="4b225-102">ICorDebugReferenceValue::IsNull — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b225-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="4b225-103">Pobiera wartość wskazującą, czy to ICorDebugReferenceValue jest wartość null, w którym to przypadku `ICorDebugReferenceValue` nie wskazuje na obiekt.</span><span class="sxs-lookup"><span data-stu-id="4b225-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b225-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b225-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b225-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b225-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="4b225-106">[out] Wskaźnik do wartość logiczna, która jest `true` Jeśli `ICorDebugReferenceValue` obiekt jest wartość null; w przeciwnym razie `pbNull` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="4b225-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b225-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b225-107">Requirements</span></span>  
 <span data-ttu-id="4b225-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b225-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b225-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b225-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b225-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b225-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b225-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b225-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
