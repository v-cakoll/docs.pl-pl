---
title: ICorDebugReferenceValue::Dereference — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a0fd1981e7da5af19cf3a422c6008d373e9ac92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416596"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="e74e6-102">ICorDebugReferenceValue::Dereference — Metoda</span><span class="sxs-lookup"><span data-stu-id="e74e6-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="e74e6-103">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e74e6-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e74e6-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e74e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e74e6-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="e74e6-106">[out] Wskaźnik do adresu ICorDebugValue, który reprezentuje obiekt, do którego ten obiekt ICorDebugReferenceValue punktów.</span><span class="sxs-lookup"><span data-stu-id="e74e6-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e74e6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e74e6-107">Remarks</span></span>  
 <span data-ttu-id="e74e6-108">`ICorDebugValue` Obiekt jest prawidłowy tylko wtedy, gdy odwołanie, nie ma jeszcze wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e74e6-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e74e6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e74e6-109">Requirements</span></span>  
 <span data-ttu-id="e74e6-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74e6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e74e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e74e6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e74e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e74e6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
