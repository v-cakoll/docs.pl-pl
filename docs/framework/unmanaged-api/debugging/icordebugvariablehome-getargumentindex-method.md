---
title: ICorDebugVariableHome::GetArgumentIndex — metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20f65218928ee07d67ea742154469ac3cbea9241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="7d9fe-102">ICorDebugVariableHome::GetArgumentIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="7d9fe-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="7d9fe-103">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d9fe-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d9fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d9fe-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="7d9fe-106">[out] Wskaźnik do indeksu argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d9fe-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d9fe-107">Return Value</span></span>  
 <span data-ttu-id="7d9fe-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="7d9fe-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="7d9fe-109">Value</span></span>|<span data-ttu-id="7d9fe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7d9fe-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="7d9fe-111">Wywołanie metody zwrócił indeks nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="7d9fe-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d9fe-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d9fe-113">Remarks</span></span>  
 <span data-ttu-id="7d9fe-114">Indeks argument może być używany do pobierania metadanych dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d9fe-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d9fe-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d9fe-115">Requirements</span></span>  
 <span data-ttu-id="7d9fe-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d9fe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d9fe-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d9fe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d9fe-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d9fe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d9fe-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d9fe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9fe-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d9fe-120">See Also</span></span>  
 [<span data-ttu-id="7d9fe-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d9fe-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
