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
ms.openlocfilehash: 6e214131aeb2d6d17ea4b0a730b5fc77428a7ca8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213689"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="b3b51-102">ICorDebugFrame::GetFunctionToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3b51-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="b3b51-103">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="b3b51-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3b51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3b51-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="b3b51-106">określoną Wskaźnik do `mdMethodDef` tokenu, który odwołuje się do metadanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="b3b51-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b51-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3b51-107">Requirements</span></span>  
 <span data-ttu-id="b3b51-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b51-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b51-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3b51-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3b51-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b3b51-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3b51-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b51-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
