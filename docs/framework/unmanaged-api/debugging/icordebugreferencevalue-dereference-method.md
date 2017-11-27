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
ms.openlocfilehash: 4eb3287612a8301d551a1443d803e60e4d03f7db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="915c4-102">ICorDebugReferenceValue::Dereference — Metoda</span><span class="sxs-lookup"><span data-stu-id="915c4-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="915c4-103">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="915c4-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="915c4-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="915c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="915c4-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="915c4-106">[out] Wskaźnik do adresu ICorDebugValue, który reprezentuje obiekt, do którego ten obiekt ICorDebugReferenceValue punktów.</span><span class="sxs-lookup"><span data-stu-id="915c4-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="915c4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="915c4-107">Remarks</span></span>  
 <span data-ttu-id="915c4-108">`ICorDebugValue` Obiekt jest prawidłowy tylko wtedy, gdy odwołanie, nie ma jeszcze wyłączone.</span><span class="sxs-lookup"><span data-stu-id="915c4-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915c4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="915c4-109">Requirements</span></span>  
 <span data-ttu-id="915c4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="915c4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915c4-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="915c4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="915c4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="915c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="915c4-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
