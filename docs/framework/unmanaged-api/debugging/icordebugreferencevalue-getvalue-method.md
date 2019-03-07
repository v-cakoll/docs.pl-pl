---
title: ICorDebugReferenceValue::GetValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e52ef20f2b8e3937911dc37e68f8a338ab0d85d9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468874"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="95b1c-102">ICorDebugReferenceValue::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="95b1c-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="95b1c-103">Pobiera bieżący adres pamięci przywoływanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="95b1c-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95b1c-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95b1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95b1c-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="95b1c-106">[out] Wskaźnik do `CORDB_ADDRESS` wartość, która określa adres obiektu, na który wskazuje ten obiekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="95b1c-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b1c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95b1c-107">Requirements</span></span>  
 <span data-ttu-id="95b1c-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b1c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b1c-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b1c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b1c-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b1c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95b1c-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b1c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
