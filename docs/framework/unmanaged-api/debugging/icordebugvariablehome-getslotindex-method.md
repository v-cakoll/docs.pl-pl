---
title: 'ICorDebugVariableHome:: GetSlotIndex, Metoda'
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
ms.openlocfilehash: dfc2e91599e7f05d90d56af07b71313e9eecaa51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121051"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="d408c-102">ICorDebugVariableHome:: GetSlotIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="d408c-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="d408c-103">Pobiera zarządzany indeks szczeliny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d408c-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d408c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d408c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d408c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d408c-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d408c-106">określoną Wskaźnik do indeksu szczeliny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d408c-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d408c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d408c-107">Return Value</span></span>  
 <span data-ttu-id="d408c-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="d408c-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d408c-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d408c-109">Value</span></span>|<span data-ttu-id="d408c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d408c-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d408c-111">Wywołanie metody zwróciło wartość indeksu szczeliny w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="d408c-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d408c-112">Bieżące wystąpienie [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) reprezentuje argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="d408c-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d408c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d408c-113">Remarks</span></span>  
 <span data-ttu-id="d408c-114">Za pomocą indeksu miejsca można pobrać metadane dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d408c-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d408c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d408c-115">Requirements</span></span>  
 <span data-ttu-id="d408c-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d408c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d408c-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d408c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d408c-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d408c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d408c-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d408c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d408c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d408c-120">See also</span></span>

- [<span data-ttu-id="d408c-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="d408c-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
