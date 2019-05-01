---
title: ICorDebugGenericValue::GetValue — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53db4dcb13303c9e7bdd77a46b3c9526364bac06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995648"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="2fa90-102">ICorDebugGenericValue::GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fa90-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="2fa90-103">Kopiuje wartości z tym ogólnego do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="2fa90-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa90-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fa90-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="2fa90-106">[out] Wskaźnik do wartości, który jest reprezentowany przez ten obiekt icordebuggenericvalue —.</span><span class="sxs-lookup"><span data-stu-id="2fa90-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="2fa90-107">Wartość może być typu prostego lub typ odwołania (wskaźnik).</span><span class="sxs-lookup"><span data-stu-id="2fa90-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa90-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fa90-108">Requirements</span></span>  
 <span data-ttu-id="2fa90-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa90-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa90-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fa90-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fa90-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fa90-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fa90-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa90-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
