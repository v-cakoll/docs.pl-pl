---
title: ICorDebugArrayValue::GetElementType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 8b5a6f4447730ebc6e4b23d3cd06df85b2d7fee6
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895006"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="e0254-102">ICorDebugArrayValue::GetElementType — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0254-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="e0254-103">Pobiera wartość wskazującą typ prosty elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e0254-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0254-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0254-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0254-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0254-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="e0254-106">określoną Wskaźnik do wartości wyliczenia CorElementType —, która wskazuje typ.</span><span class="sxs-lookup"><span data-stu-id="e0254-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0254-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0254-107">Requirements</span></span>  
 <span data-ttu-id="e0254-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0254-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0254-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0254-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0254-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0254-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0254-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0254-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
