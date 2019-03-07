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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6f5f1da94e1ae07a604a616c631a38d02caea9d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496199"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="93307-102">ICorDebugArrayValue::GetElementType — Metoda</span><span class="sxs-lookup"><span data-stu-id="93307-102">ICorDebugArrayValue::GetElementType Method</span></span>
<span data-ttu-id="93307-103">Pobiera wartość wskazującą, prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="93307-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93307-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93307-104">Syntax</span></span>  
  
```  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93307-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="93307-106">[out] Wskaźnik do wartości corelementtype — wyliczenie, które wskazuje typ.</span><span class="sxs-lookup"><span data-stu-id="93307-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93307-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93307-107">Requirements</span></span>  
 <span data-ttu-id="93307-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93307-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93307-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93307-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93307-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93307-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93307-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93307-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
