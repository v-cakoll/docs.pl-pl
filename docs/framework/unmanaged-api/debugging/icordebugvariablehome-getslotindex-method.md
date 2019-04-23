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
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093757"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="c4e17-102">Metoda ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="c4e17-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="c4e17-103">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c4e17-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4e17-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4e17-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="c4e17-106">[out] Wskaźnik do gniazda indeksu do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c4e17-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4e17-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4e17-107">Return Value</span></span>  
 <span data-ttu-id="c4e17-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="c4e17-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="c4e17-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="c4e17-109">Value</span></span>|<span data-ttu-id="c4e17-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c4e17-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="c4e17-111">Wywołanie metody zwróciła wartość indeksu miejsca w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="c4e17-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="c4e17-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="c4e17-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4e17-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4e17-113">Remarks</span></span>  
 <span data-ttu-id="c4e17-114">Indeks gniazda może służyć do pobierania metadanych dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c4e17-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e17-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4e17-115">Requirements</span></span>  
 <span data-ttu-id="c4e17-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e17-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e17-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4e17-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4e17-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4e17-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4e17-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e17-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e17-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4e17-120">See also</span></span>

- [<span data-ttu-id="c4e17-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4e17-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
