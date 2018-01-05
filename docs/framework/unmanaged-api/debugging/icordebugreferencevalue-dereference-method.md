---
title: "ICorDebugReferenceValue::Dereference — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.Dereference
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dbf2775217a78c1cbb9a96093354f0fc0b278bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="29dd8-102">ICorDebugReferenceValue::Dereference — Metoda</span><span class="sxs-lookup"><span data-stu-id="29dd8-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="29dd8-103">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="29dd8-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29dd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29dd8-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29dd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29dd8-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="29dd8-106">[out] Wskaźnik do adresu ICorDebugValue, który reprezentuje obiekt, do którego ten obiekt ICorDebugReferenceValue punktów.</span><span class="sxs-lookup"><span data-stu-id="29dd8-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29dd8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29dd8-107">Remarks</span></span>  
 <span data-ttu-id="29dd8-108">`ICorDebugValue` Obiekt jest prawidłowy tylko wtedy, gdy odwołanie, nie ma jeszcze wyłączone.</span><span class="sxs-lookup"><span data-stu-id="29dd8-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29dd8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29dd8-109">Requirements</span></span>  
 <span data-ttu-id="29dd8-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dd8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dd8-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29dd8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29dd8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29dd8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29dd8-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dd8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
