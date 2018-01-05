---
title: "ICorDebugVariableHome::GetSlotIndex — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ff62b79fbbb0896941730797473209872e6bfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="76e0f-102">ICorDebugVariableHome::GetSlotIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="76e0f-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="76e0f-103">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="76e0f-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76e0f-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76e0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76e0f-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="76e0f-106">[out] Wskaźnik do indeksu w gnieździe zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="76e0f-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76e0f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="76e0f-107">Return Value</span></span>  
 <span data-ttu-id="76e0f-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="76e0f-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="76e0f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="76e0f-109">Value</span></span>|<span data-ttu-id="76e0f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="76e0f-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="76e0f-111">Wywołanie metody zwróciła wartość indeksu miejsca w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="76e0f-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="76e0f-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="76e0f-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76e0f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76e0f-113">Remarks</span></span>  
 <span data-ttu-id="76e0f-114">Gniazdo — indeks może być używany do pobierania metadanych dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="76e0f-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76e0f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76e0f-115">Requirements</span></span>  
 <span data-ttu-id="76e0f-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e0f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e0f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76e0f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76e0f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76e0f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76e0f-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76e0f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e0f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76e0f-120">See Also</span></span>  
 [<span data-ttu-id="76e0f-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="76e0f-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
