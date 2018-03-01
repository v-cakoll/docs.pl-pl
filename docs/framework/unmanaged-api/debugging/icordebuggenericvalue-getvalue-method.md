---
title: "ICorDebugGenericValue::GetValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ebb681d32c3ba805fd2e413ceeb007cb2cee57f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="c2c6a-102">ICorDebugGenericValue::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2c6a-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="c2c6a-103">Kopiuje wartości z tym ogólnego w buforze określona.</span><span class="sxs-lookup"><span data-stu-id="c2c6a-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2c6a-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2c6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2c6a-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="c2c6a-106">[out] Wskaźnik do wartości, który jest reprezentowany przez ten obiekt ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="c2c6a-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="c2c6a-107">Wartość może być typu prostego lub typu odwołania (wskaźnika).</span><span class="sxs-lookup"><span data-stu-id="c2c6a-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c6a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2c6a-108">Requirements</span></span>  
 <span data-ttu-id="c2c6a-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c6a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c6a-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2c6a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2c6a-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2c6a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c6a-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c6a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
