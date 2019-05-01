---
title: ICorDebugType2::GetTypeID Method
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b19efdedc21f66e4692ce1850eb3947f856e436
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993801"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="a7fe7-102">ICorDebugType2::GetTypeID Method</span><span class="sxs-lookup"><span data-stu-id="a7fe7-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="a7fe7-103">Pobiera [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fe7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7fe7-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7fe7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7fe7-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a7fe7-106">[out] Wskaźnik do [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) dla tego ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7fe7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7fe7-107">Return Value</span></span>  
 <span data-ttu-id="a7fe7-108">Wartość zwracana jest `S_OK` na powodzenie lub niepowodzenie `HRESULT` kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="a7fe7-109">`HRESULT` Kody obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a7fe7-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="a7fe7-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a7fe7-110">Return code</span></span>|<span data-ttu-id="a7fe7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a7fe7-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="a7fe7-112">Metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-112">Method succeeded.</span></span> <span data-ttu-id="a7fe7-113">Metoda pobierze prawidłową [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="a7fe7-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="a7fe7-114">Typ nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="a7fe7-115">Typ nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7fe7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7fe7-116">Remarks</span></span>  
 <span data-ttu-id="a7fe7-117">Ta metoda zapewnia mapowanie z ICorDebugType, który reprezentuje typ, który może być lub może nie zostały załadowane w czasie wykonywania, do [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), który służy jako nieprzezroczystego obsługi, który identyfikuje typ załadowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="a7fe7-118">Jeśli typ, który reprezentuje ICorDebugType jeszcze nie zostały załadowane, Metoda ta zwraca `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="a7fe7-119">Jeśli typ nie jest obsługiwany, zwraca `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="a7fe7-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7fe7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7fe7-120">Requirements</span></span>  
 <span data-ttu-id="a7fe7-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7fe7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7fe7-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7fe7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7fe7-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7fe7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7fe7-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7fe7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7fe7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7fe7-125">See also</span></span>

- [<span data-ttu-id="a7fe7-126">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7fe7-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
