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
ms.openlocfilehash: e542145e888049231a6c5e4cccbb4ee96c62f98b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213260"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="770fe-102">ICorDebugFunction::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="770fe-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="770fe-103">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="770fe-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="770fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="770fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="770fe-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="770fe-106">określoną Wskaźnik do `mdMethodDef` tokenu, który odwołuje się do metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="770fe-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="770fe-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="770fe-107">Requirements</span></span>  
 <span data-ttu-id="770fe-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="770fe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="770fe-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="770fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="770fe-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="770fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="770fe-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="770fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
