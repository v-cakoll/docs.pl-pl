---
title: ICorDebugReferenceValue::Dereference — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b436fa14322d444a6c8b515ba8e50698eecb95ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783022"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="328eb-102">ICorDebugReferenceValue::Dereference — Metoda</span><span class="sxs-lookup"><span data-stu-id="328eb-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="328eb-103">Pobiera obiekt, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="328eb-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="328eb-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="328eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="328eb-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="328eb-106">[out] Wskaźnik na adres ICorDebugValue, który reprezentuje obiekt, na który wskazuje ten obiekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="328eb-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="328eb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="328eb-107">Remarks</span></span>  
 <span data-ttu-id="328eb-108">`ICorDebugValue` Obiekt jest prawidłowy tylko w przypadku, gdy odwołanie, nie ma jeszcze wyłączone.</span><span class="sxs-lookup"><span data-stu-id="328eb-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328eb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="328eb-109">Requirements</span></span>  
 <span data-ttu-id="328eb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328eb-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="328eb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="328eb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="328eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="328eb-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
