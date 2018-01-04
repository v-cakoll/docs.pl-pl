---
title: "ICorDebugHandleValue::GetHandleType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue.GetHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b41e7c14fd0abdd957f0661345a6372074f2ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="4a4f0-102">ICorDebugHandleValue::GetHandleType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a4f0-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="4a4f0-103">Pobiera wartość, która wskazuje typ dojścia odwołuje się ten obiekt ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="4a4f0-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a4f0-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a4f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a4f0-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="4a4f0-106">[out] Wskaźnik do wartości wyliczenia CorDebugHandleType, który wskazuje typ ta dojścia.</span><span class="sxs-lookup"><span data-stu-id="4a4f0-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a4f0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a4f0-107">Requirements</span></span>  
 <span data-ttu-id="4a4f0-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a4f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a4f0-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a4f0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a4f0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a4f0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a4f0-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a4f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
