---
title: Metoda ICorDebugVariableHome::GetSlotIndex
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3534160e14c46bc3f8f5da81c4c14a3191a6238b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553196"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="1981d-102">Metoda ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="1981d-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="1981d-103">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1981d-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1981d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1981d-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1981d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1981d-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="1981d-106">[out] Wskaźnik do gniazda indeksu do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1981d-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1981d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1981d-107">Return Value</span></span>  
 <span data-ttu-id="1981d-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="1981d-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="1981d-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="1981d-109">Value</span></span>|<span data-ttu-id="1981d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1981d-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1981d-111">Wywołanie metody zwróciła wartość indeksu miejsca w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="1981d-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1981d-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="1981d-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1981d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1981d-113">Remarks</span></span>  
 <span data-ttu-id="1981d-114">Indeks gniazda może służyć do pobierania metadanych dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1981d-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1981d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1981d-115">Requirements</span></span>  
 <span data-ttu-id="1981d-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1981d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1981d-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1981d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1981d-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1981d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1981d-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1981d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1981d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1981d-120">See also</span></span>
- [<span data-ttu-id="1981d-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="1981d-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
