---
title: ICorDebugHandleValue::GetHandleType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51fd8e9728955e8f426a38b8bf6cdc78dfa9bbde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412350"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="25896-102">ICorDebugHandleValue::GetHandleType — Metoda</span><span class="sxs-lookup"><span data-stu-id="25896-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="25896-103">Pobiera wartość, która wskazuje typ dojścia odwołuje się ten obiekt ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="25896-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25896-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25896-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25896-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25896-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="25896-106">[out] Wskaźnik do wartości wyliczenia CorDebugHandleType, który wskazuje typ ta dojścia.</span><span class="sxs-lookup"><span data-stu-id="25896-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25896-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25896-107">Requirements</span></span>  
 <span data-ttu-id="25896-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25896-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25896-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25896-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25896-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25896-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25896-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25896-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
