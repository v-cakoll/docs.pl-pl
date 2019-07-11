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
ms.openlocfilehash: 199c3ba5d5b9588db4c665070b4dec6266cefc2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760346"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="04343-102">Metoda ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="04343-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="04343-103">Pobiera zarządzane miejsce indeks zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="04343-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04343-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04343-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04343-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04343-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="04343-106">[out] Wskaźnik do gniazda indeksu do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="04343-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04343-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04343-107">Return Value</span></span>  
 <span data-ttu-id="04343-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="04343-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="04343-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="04343-109">Value</span></span>|<span data-ttu-id="04343-110">Opis</span><span class="sxs-lookup"><span data-stu-id="04343-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="04343-111">Wywołanie metody zwróciła wartość indeksu miejsca w `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="04343-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="04343-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="04343-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04343-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04343-113">Remarks</span></span>  
 <span data-ttu-id="04343-114">Indeks gniazda może służyć do pobierania metadanych dla tej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="04343-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04343-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04343-115">Requirements</span></span>  
 <span data-ttu-id="04343-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04343-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04343-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04343-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04343-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04343-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04343-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04343-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04343-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04343-120">See also</span></span>

- [<span data-ttu-id="04343-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="04343-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
