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
ms.openlocfilehash: ecc0b46618cd00ba4442e30c23a7b7e950382fee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775697"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="aed89-102">ICorDebugHandleValue::GetHandleType — Metoda</span><span class="sxs-lookup"><span data-stu-id="aed89-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="aed89-103">Pobiera wartość wskazującą rodzaj uchwyt odwołuje się ten obiekt icordebughandlevalue —.</span><span class="sxs-lookup"><span data-stu-id="aed89-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aed89-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aed89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aed89-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="aed89-106">[out] Wskaźnik do wartości cordebughandletype — wyliczenie, który wskazuje na typ dojścia tego.</span><span class="sxs-lookup"><span data-stu-id="aed89-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aed89-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aed89-107">Requirements</span></span>  
 <span data-ttu-id="aed89-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aed89-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aed89-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aed89-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aed89-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aed89-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aed89-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aed89-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
