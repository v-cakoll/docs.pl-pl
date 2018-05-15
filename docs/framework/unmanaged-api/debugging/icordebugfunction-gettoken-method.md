---
title: ICorDebugFunction::GetToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acfb8910df6e20bf55ed33fdbb9b1c30d22f4684
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="c9521-102">ICorDebugFunction::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9521-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="c9521-103">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c9521-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9521-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9521-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9521-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9521-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="c9521-106">[out] Wskaźnik do `mdMethodDef` token, który odwołuje się do metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c9521-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9521-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9521-107">Requirements</span></span>  
 <span data-ttu-id="c9521-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9521-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9521-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9521-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9521-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9521-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9521-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9521-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
