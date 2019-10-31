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
ms.openlocfilehash: bc7d99d0ddb443cba227b7bad0cd53edb94c9101
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138537"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="8c183-102">ICorDebugHandleValue::GetHandleType — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c183-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="8c183-103">Pobiera wartość wskazującą rodzaj dojścia, do którego odwołuje się ten obiekt ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="8c183-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c183-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c183-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c183-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c183-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="8c183-106">określoną Wskaźnik do wartości wyliczenia CorDebugHandleType —, który wskazuje typ tego uchwytu.</span><span class="sxs-lookup"><span data-stu-id="8c183-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c183-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c183-107">Requirements</span></span>  
 <span data-ttu-id="8c183-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c183-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c183-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c183-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c183-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c183-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c183-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c183-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
