---
title: ICorDebugType::GetType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418721"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="4dea6-102">ICorDebugType::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4dea6-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="4dea6-103">Pobiera wartość CorElementType, która opisuje typ macierzysty środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Type> reprezentowany przez ten ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="4dea6-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dea6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dea6-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dea6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dea6-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="4dea6-106">[out] Wskaźnik do wartości `CorElementType` wyliczenia, która wskazuje CLR <xref:System.Type> tego `ICorDebugType` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="4dea6-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dea6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dea6-107">Remarks</span></span>  
 <span data-ttu-id="4dea6-108">Jeśli wartość `ty` po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) metodę można wywołać w celu uzyskania bez wystąpień typu dla typu ogólnego; w przeciwnym razie nie wywołuj `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="4dea6-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dea6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dea6-109">Requirements</span></span>  
 <span data-ttu-id="4dea6-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dea6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dea6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dea6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dea6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dea6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dea6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dea6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
