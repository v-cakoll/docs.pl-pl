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
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790971"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="1a730-102">ICorDebugVariableHome:: GetSlotIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="1a730-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="1a730-103">Pobiera zarządzany indeks szczeliny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1a730-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a730-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a730-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a730-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a730-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="1a730-106">określoną Wskaźnik do indeksu szczeliny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1a730-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a730-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="1a730-107">Return Value</span></span>  
 <span data-ttu-id="1a730-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="1a730-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="1a730-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="1a730-109">Value</span></span>|<span data-ttu-id="1a730-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1a730-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1a730-111">Wywołanie metody zwróciło wartość indeksu szczeliny w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="1a730-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1a730-112">Bieżące wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) reprezentuje argument funkcji.</span><span class="sxs-lookup"><span data-stu-id="1a730-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a730-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a730-113">Remarks</span></span>  
 <span data-ttu-id="1a730-114">Za pomocą indeksu miejsca można pobrać metadane dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1a730-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a730-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a730-115">Requirements</span></span>  
 <span data-ttu-id="1a730-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a730-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a730-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a730-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a730-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a730-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a730-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a730-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a730-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a730-120">See also</span></span>

- [<span data-ttu-id="1a730-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a730-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
