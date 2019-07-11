---
title: ICorDebugArrayValue::HasBaseIndicies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737431"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="d99df-102">ICorDebugArrayValue::HasBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="d99df-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="d99df-103">Pobiera wartość wskazującą, czy żadnych wymiarów tej tablicy mają podstawowy indeks różna od zera.</span><span class="sxs-lookup"><span data-stu-id="d99df-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d99df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d99df-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d99df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d99df-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="d99df-106">[out] Wskaźnik na wartość logiczną, która jest `true` Jeśli jeden lub więcej wymiarów tego `ICorDebugArrayValue` obiekt ma podstawowy indeks różna od zera; w przeciwnym razie jest wartość logiczna `false`.</span><span class="sxs-lookup"><span data-stu-id="d99df-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99df-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d99df-107">Requirements</span></span>  
 <span data-ttu-id="d99df-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d99df-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d99df-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d99df-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d99df-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d99df-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d99df-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d99df-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
