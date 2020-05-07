---
title: ICorDebugBoxValue::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: 401f052b881c1a0cfa065ba60c93aca1706f34f4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894783"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="b68e0-102">ICorDebugBoxValue::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="b68e0-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="b68e0-103">Pobiera wartość opakowaną.</span><span class="sxs-lookup"><span data-stu-id="b68e0-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b68e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b68e0-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="b68e0-106">określoną Wskaźnik do adresu obiektu ICorDebugObjectValue, który reprezentuje opakowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="b68e0-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68e0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b68e0-107">Requirements</span></span>  
 <span data-ttu-id="b68e0-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b68e0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68e0-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b68e0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b68e0-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b68e0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b68e0-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68e0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
