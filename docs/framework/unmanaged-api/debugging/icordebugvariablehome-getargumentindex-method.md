---
title: Metoda ICorDebugVariableHome::GetArgumentIndex
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
ms.openlocfilehash: 163704bf9a71ceda04bdfd73f9ca676c19d8a62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526644"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="b1690-102">Metoda ICorDebugVariableHome::GetArgumentIndex</span><span class="sxs-lookup"><span data-stu-id="b1690-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="b1690-103">Pobiera indeks argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="b1690-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1690-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1690-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1690-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1690-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="b1690-106">[out] Wskaźnik do indeksu argumentu.</span><span class="sxs-lookup"><span data-stu-id="b1690-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1690-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b1690-107">Return Value</span></span>  
 <span data-ttu-id="b1690-108">Metoda zwraca następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="b1690-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="b1690-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="b1690-109">Value</span></span>|<span data-ttu-id="b1690-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b1690-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b1690-111">Wywołanie metody zwracane indeksu nieprawidłowy argument.</span><span class="sxs-lookup"><span data-stu-id="b1690-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b1690-112">Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje zmienną lokalną.</span><span class="sxs-lookup"><span data-stu-id="b1690-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1690-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1690-113">Remarks</span></span>  
 <span data-ttu-id="b1690-114">Indeks argument może służyć do pobierania metadanych dla tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="b1690-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1690-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1690-115">Requirements</span></span>  
 <span data-ttu-id="b1690-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1690-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1690-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1690-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1690-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1690-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1690-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1690-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1690-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1690-120">See also</span></span>
- [<span data-ttu-id="b1690-121">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1690-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
