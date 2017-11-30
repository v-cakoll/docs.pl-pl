---
title: "ICorDebugVariableHome::GetArgumentIndex — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 175e45758d26d8168279c825d41ee58d049edf0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="18e44-102">ICorDebugVariableHome::GetArgumentIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="18e44-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="18e44-103">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="18e44-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18e44-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18e44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18e44-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="18e44-106">[out] Wskaźnik do indeksu argumentu.</span><span class="sxs-lookup"><span data-stu-id="18e44-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18e44-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="18e44-107">Return Value</span></span>  
 <span data-ttu-id="18e44-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="18e44-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="18e44-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="18e44-109">Value</span></span>|<span data-ttu-id="18e44-110">Opis</span><span class="sxs-lookup"><span data-stu-id="18e44-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="18e44-111">Wywołanie metody zwrócił indeks nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="18e44-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="18e44-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="18e44-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18e44-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18e44-113">Remarks</span></span>  
 <span data-ttu-id="18e44-114">Indeks argument może być używany do pobierania metadanych dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="18e44-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e44-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18e44-115">Requirements</span></span>  
 <span data-ttu-id="18e44-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e44-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e44-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18e44-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18e44-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18e44-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18e44-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e44-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e44-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18e44-120">See Also</span></span>  
 [<span data-ttu-id="18e44-121">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="18e44-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
