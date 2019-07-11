---
title: ICorDebugFrame::GetFunctionToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50e5fcee3705e05aeed820cf736613c12b00e50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754873"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="4b79a-102">ICorDebugFrame::GetFunctionToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b79a-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="4b79a-103">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="4b79a-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b79a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b79a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b79a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b79a-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="4b79a-106">[out] Wskaźnik do `mdMethodDef` token, który odwołuje się do metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b79a-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b79a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b79a-107">Requirements</span></span>  
 <span data-ttu-id="4b79a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b79a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b79a-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b79a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b79a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b79a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b79a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b79a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
