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
ms.openlocfilehash: 186f4a939cb3e01a527cf6ef06029232e7f5c22a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489372"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="dfa46-102">Metoda ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="dfa46-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="dfa46-103">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="dfa46-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfa46-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa46-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="dfa46-106">[out] Wskaźnik do gniazda indeksu do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="dfa46-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfa46-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dfa46-107">Return Value</span></span>  
 <span data-ttu-id="dfa46-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="dfa46-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="dfa46-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="dfa46-109">Value</span></span>|<span data-ttu-id="dfa46-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dfa46-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="dfa46-111">Wywołanie metody zwróciła wartość indeksu miejsca w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="dfa46-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="dfa46-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="dfa46-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfa46-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfa46-113">Remarks</span></span>  
 <span data-ttu-id="dfa46-114">Indeks gniazda może służyć do pobierania metadanych dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="dfa46-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa46-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfa46-115">Requirements</span></span>  
 <span data-ttu-id="dfa46-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa46-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa46-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfa46-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa46-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfa46-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa46-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa46-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa46-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfa46-120">See also</span></span>
- [<span data-ttu-id="dfa46-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="dfa46-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
