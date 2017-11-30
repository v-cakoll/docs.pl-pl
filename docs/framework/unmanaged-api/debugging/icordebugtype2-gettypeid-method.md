---
title: "ICorDebugType2::GetTypeID — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30b5259bfd39ac0c8c8b717d59a8d3165f6b6cbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="b9a41-102">ICorDebugType2::GetTypeID — metoda</span><span class="sxs-lookup"><span data-stu-id="b9a41-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="b9a41-103">Pobiera [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="b9a41-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9a41-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9a41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9a41-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b9a41-106">[out] Wskaźnik do [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="b9a41-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9a41-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b9a41-107">Return Value</span></span>  
 <span data-ttu-id="b9a41-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b9a41-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b9a41-109">`HRESULT` Kody są następujące:</span><span class="sxs-lookup"><span data-stu-id="b9a41-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="b9a41-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="b9a41-110">Return code</span></span>|<span data-ttu-id="b9a41-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b9a41-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9a41-112">Metoda zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9a41-112">Method succeeded.</span></span> <span data-ttu-id="b9a41-113">Metoda ma pobrać prawidłowej [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b9a41-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="b9a41-114">Typ nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="b9a41-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="b9a41-115">Typ nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="b9a41-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9a41-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9a41-116">Remarks</span></span>  
 <span data-ttu-id="b9a41-117">Ta metoda zapewnia mapowanie z ICorDebugType, który reprezentuje typ, który może lub może nie zostały załadowane w czasie wykonywania, do [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), który służy jako nieprzezroczyste obsługi, który identyfikuje typu załadowanego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9a41-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="b9a41-118">Jeśli typ, który reprezentuje ICorDebugType jeszcze nie został załadowany, ta metoda zwraca `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="b9a41-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="b9a41-119">Jeśli typ nie jest obsługiwany, zwraca `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="b9a41-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a41-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9a41-120">Requirements</span></span>  
 <span data-ttu-id="b9a41-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a41-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a41-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9a41-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9a41-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9a41-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a41-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a41-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a41-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9a41-125">See Also</span></span>  
 [<span data-ttu-id="b9a41-126">Interfejs ICorDebugType2</span><span class="sxs-lookup"><span data-stu-id="b9a41-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
