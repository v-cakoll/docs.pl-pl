---
title: ICorDebugGenericValue::SetValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83aebad108a743d25b8ea93c99060d10bf5c3980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413211"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="4f560-102">ICorDebugGenericValue::SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f560-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="4f560-103">Kopiuje nową wartość z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="4f560-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f560-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f560-104">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f560-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f560-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="4f560-106">[in] Wskaźnik do buforu z którego można skopiować wartości.</span><span class="sxs-lookup"><span data-stu-id="4f560-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f560-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f560-107">Remarks</span></span>  
 <span data-ttu-id="4f560-108">Dla typów referencyjnych wartość jest odwołanie, nie zawartość.</span><span class="sxs-lookup"><span data-stu-id="4f560-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f560-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f560-109">Requirements</span></span>  
 <span data-ttu-id="4f560-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f560-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f560-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f560-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f560-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f560-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f560-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f560-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
